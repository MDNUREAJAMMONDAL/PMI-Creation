# PMI-Creation

This repo contains **Frontend (React + Tailwind + Firebase)** and **Backend (Node.js + Express + Firebase Admin + Payment Integration)** for paid video platform.

## Structure


## Deployment

1. Create Firebase project and storage bucket.
2. Add Firebase service account JSON in `.env`.
3. Set payment gateway credentials (SSLCOMMERZ/bKash/Nagad) in `.env`.
4. Deploy backend (Railway, Vercel, or local Node.js).
5. Deploy frontend (Vercel, Firebase Hosting, or local React app).
PORT=5000
PUBLIC_URL=http://localhost:5173
FIREBASE_SERVICE_ACCOUNT_JSON="{...paste service account JSON here...}"
FIREBASE_STORAGE_BUCKET=your-bucket-name.appspot.com

# SSLCOMMERZ
SSLCOMMERZ_STORE_ID=your_store_id
SSLCOMMERZ_STORE_PASS=your_store_pass
SSLCOMMERZ_SANDBOX_URL=https://sandbox.sslcommerz.com/gwprocess/v4/api.php

# Telegram (optional)
TELEGRAM_BOT_TOKEN=123456:ABC-DEF...
{
  "name": "pmi-creation-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "body-parser": "^1.20.2",
    "firebase-admin": "^11.10.0",
    "node-fetch": "^2.6.7",
    "cors": "^2.8.5",
    "crypto": "^1.0.1",
    "node-telegram-bot-api": "^0.61.0"
  }
}
require('dotenv').config();
const express = require('express');
const bodyParser = require('body-parser');
const admin = require('firebase-admin');
const fetch = require('node-fetch');
const crypto = require('crypto');
const cors = require('cors');

const serviceAccount = JSON.parse(process.env.FIREBASE_SERVICE_ACCOUNT_JSON);
admin.initializeApp({
  credential: admin.credential.cert(serviceAccount),
  storageBucket: process.env.FIREBASE_STORAGE_BUCKET
});

const db = admin.firestore();
const bucket = admin.storage().bucket();
const app = express();
app.use(cors());
app.use(bodyParser.json());

function makeToken(len = 16) {
  return crypto.randomBytes(len).toString('hex');
}

// Create payment
app.post('/api/create-payment', async (req, res) => {
  try {
    const { amount, buyer_name, buyer_email, videoId, returnUrl } = req.body;
    if (!amount || !videoId) return res.status(400).json({ error: 'missing fields' });

    const orderRef = await db.collection('orders').add({
      videoId, amount, status: 'pending', buyer_name, buyer_email,
      createdAt: admin.firestore.FieldValue.serverTimestamp()
    });

    const payload = {
      store_id: process.env.SSLCOMMERZ_STORE_ID,
      store_passwd: process.env.SSLCOMMERZ_STORE_PASS,
      total_amount: amount,
      currency: 'BDT',
      tran_id: orderRef.id,
      success_url: (returnUrl || process.env.PUBLIC_URL) + '/payment-success',
      fail_url: (returnUrl || process.env.PUBLIC_URL) + '/payment-fail',
      cancel_url: (returnUrl || process.env.PUBLIC_URL) + '/payment-cancel',
      product_category: 'Video',
      product_name: 'Course Video Access',
      cus_name: buyer_name || '',
      cus_email: buyer_email || ''
    };

    const resp = await fetch(process.env.SSLCOMMERZ_SANDBOX_URL, {
      method: 'POST',
      body: new URLSearchParams(payload)
    });
    const json = await resp.json();
    if (json && json.GatewayPageURL) return res.json({ url: json.GatewayPageURL });
    return res.status(500).json({ error: 'payment init failed', detail: json });
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: err.message });
  }
});

// Payment callback
app.post('/api/payment-callback', async (req, res) => {
  try {
    const data = req.body;
    const tran_id = data.tran_id;
    if (!tran_id) return res.status(400).send('no tran_id');

    const orderRef = db.collection('orders').doc(tran_id);
    const orderSnap = await orderRef.get();
    if (!orderSnap.exists) return res.status(404).send('order not found');

    await orderRef.update({
      status: 'paid',
      gatewayData: data,
      paidAt: admin.firestore.FieldValue.serverTimestamp()
    });

    const accessToken = makeToken(12);
    await db.collection('access').add({
      orderId: tran_id,
      videoId: orderSnap.data().videoId,
      token: accessToken,
      expiresAt: admin.firestore.Timestamp.fromDate(new Date(Date.now() + (24*60*60*1000))),
      createdAt: admin.firestore.FieldValue.serverTimestamp()
    });

    res.send('OK');
  } catch (err) {
    console.error(err);
    res.status(500).send('error');
  }
});

// Get signed URL
app.get('/api/signed-url', async (req, res) => {
  try {
    const { token } = req.query;
    if (!token) return res.status(400).json({ error: 'missing token' });

    const q = await db.collection('access').where('token', '==', token).limit(1).get();
    if (q.empty) return res.status(403).json({ error: 'invalid token' });
    const acc = q.docs[0].data();
    if (acc.expiresAt.toDate() < new Date()) return res.status(403).json({ error: 'expired' });

    const vidSnap = await db.collection('videos').doc(acc.videoId).get();
    if (!vidSnap.exists) return res.status(404).json({ error: 'video not found' });

    const filePath = vidSnap.data().storagePath;
    const expires = Date.now() + 15*60*1000;
    const [url] = await bucket.file(filePath).getSignedUrl({ action: 'read', expires: expires });
    return res.json({ url });
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: err.message });
  }
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log('Backend running on port', PORT));
const TelegramBot = require('node-telegram-bot-api');
const token = process.env.TELEGRAM_BOT_TOKEN;
const bot = new TelegramBot(token, { polling: false });

async function sendTokenToUser(chatId, tokenValue) {
  try {
    await bot.sendMessage(chatId, `আপনার ভিডিও access token: ${tokenValue}\nUse it at: ${process.env.PUBLIC_URL}/redeem`);
    return true;
  } catch (err) {
    console.error(err);
    return false;
  }
}

module.exports = { sendTokenToUser };
