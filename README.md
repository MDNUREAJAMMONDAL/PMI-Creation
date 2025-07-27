# PMI-Creation
<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>PMI Creation - AI Learning for HSC</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet" />
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: #fff;
      color: #333;
    }
    header {
      background: #00bfff;
      color: white;
      padding: 50px 20px;
      text-align: center;
    }
    nav {
      background: #f0f8ff;
      padding: 10px 20px;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 10;
    }
    nav a {
      margin: 0 15px;
      text-decoration: none;
      color: #00bfff;
      font-weight: bold;
      font-size: 16px;
    }
    section {
      padding: 40px 20px;
      text-align: center;
    }
    .highlight {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
    }
    .card {
      background: #f5faff;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      width: 260px;
    }
    form {
      max-width: 500px;
      margin: 0 auto;
      text-align: left;
    }
    label {
      display: block;
      margin-top: 15px;
      font-weight: 600;
    }
    input, select, textarea, button {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-family: 'Poppins', sans-serif;
      font-size: 15px;
    }
    button {
      background-color: #00bfff;
      color: white;
      border: none;
      margin-top: 20px;
      cursor: pointer;
      font-weight: 700;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #008fcc;
    }
    iframe {
      width: 100%;
      max-width: 700px;
      height: 400px;
      border: none;
      margin-top: 20px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,191,255,0.3);
    }
    footer {
      background-color: #00bfff;
      color: white;
      text-align: center;
      padding: 20px;
      margin-top: 50px;
      font-size: 14px;
    }
    @media (max-width: 700px) {
      .highlight {
        flex-direction: column;
        align-items: center;
      }
      .card {
        width: 90%;
      }
    }
    /* Login modal styles */
    #loginModal {
      display: none;
      position: fixed;
      z-index: 1000;
      left: 0; top: 0;
      width: 100%; height: 100%;
      overflow: auto;
      background-color: rgba(0,0,0,0.5);
    }
    #loginModal .modal-content {
      background-color: #fefefe;
      margin: 10% auto;
      padding: 30px;
      border-radius: 15px;
      width: 90%;
      max-width: 400px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    }
    #loginModal label {
      font-weight: 600;
    }
    #loginModal input {
      margin-top: 10px;
      padding: 10px;
      font-size: 16px;
      width: 100%;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    #loginModal button {
      margin-top: 20px;
      width: 100%;
      font-weight: 700;
    }
    #loginModal .close-btn {
      background: #ccc;
      color: black;
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <header>
    <h1>AI-র মাধ্যমে স্মার্ট লার্নিং — PMI Creation</h1>
  </header>

  <nav>
    <a href="#home">হোম</a>
    <a href="#courses">কোর্সসমূহ</a>
    <a href="#about">আমাদের সম্পর্কে</a>
    <a href="#join">ব্যাচে যোগ দিন</a>
    <a href="#portal" id="studentPortalLink">স্টুডেন্ট পোর্টাল</a>
    <a href="#contact">যোগাযোগ</a>
  </nav>

  <section id="highlight" style="scroll-margin-top: 70px;">
    <h2>PMI Creation এর সেবা</h2>
    <div class="highlight">
      <div class="card">
        <h3>AI Video Classes</h3>
        <p>HSC Physics, Math এবং ICT-এর জন্য কৃত্রিম বুদ্ধিমত্তা নির্ভর ভিডিও ক্লাস।</p>
      </div>
      <div class="card">
        <h3>ফ্রি ও পেইড ব্যাচ</h3>
        <p>বিভিন্ন ব্যাচ টাইপ অনুযায়ী কোর্স ফিল্টার ও সিলেকশন সুবিধা।</p>
      </div>
      <div class="card">
        <h3>Weekly Notes & Exams</h3>
        <p>স্মার্ট নোট ও সাপ্তাহিক এক্সামের মাধ্যমে রিভিশন সিস্টেম।</p>
      </div>
    </div>
  </section>

  <section id="about" style="scroll-margin-top: 70px;">
    <h2>আমাদের সম্পর্কে</h2>
    <p>PMI Creation হল একটি AI-ভিত্তিক প্ল্যাটফর্ম যা HSC শিক্ষার্থীদের জন্য ফিজিক্স, ম্যাথ ও আইসিটি সহজভাবে শেখানোর লক্ষ্য নিয়ে কাজ করে।</p>
  </section>

  <section id="join" style="scroll-margin-top: 70px;">
    <h2>ব্যাচে যোগ দিন</h2>
    <form id="joinForm" onsubmit="return submitJoinForm(event)">
      <label>আপনার নাম</label>
      <input type="text" name="name" required />

      <label>মোবাইল নাম্বার</label>
      <input type="tel" name="phone" required pattern="[0-9]{11}" placeholder="১১ সংখ্যার মোবাইল নাম্বার" />

      <label>বিষয় নির্বাচন করুন</label>
      <select name="subject" required>
        <option value="" disabled selected>বিষয় নির্বাচন করুন</option>
        <option value="physics">Physics</option>
        <option value="math">Math</option>
        <option value="ict">ICT</option>
      </select>

      <label>ব্যাচ টাইপ</label>
      <select name="batch" required>
        <option value="" disabled selected>ব্যাচ টাইপ নির্বাচন করুন</option>
        <option value="free">Free</option>
        <option value="paid">Paid</option>
      </select>

      <label>পেমেন্ট পদ্ধতি</label>
      <select name="payment" required>
        <option value="" disabled selected>পেমেন্ট পদ্ধতি নির্বাচন করুন</option>
        <option value="bkash">Bkash</option>
        <option value="nagad">Nagad</option>
      </select>

      <label>Transaction ID (যদি প্রযোজ্য)</label>
      <input type="text" name="trxid" placeholder="যদি পেইড ব্যাচ হয় তবে দিন" />

      <button type="submit">জমা দিন</button>
    </form>
  </section>

  <section id="portal" style="scroll-margin-top: 70px;">
    <h2>স্টুডেন্ট লগইন পোর্টাল</h2>
    <p>লগইন করে শিক্ষার্থীরা ভিডিও, নোট এবং এক্সাম অ্যাক্সেস করতে পারবেন।</p>
    <button onclick="openLoginModal()">লগইন করুন</button>

    <div id="studentContent" style="display:none; margin-top:20px;">
      <h3>আপনার ভিডিও ক্লাস</h3>
      <iframe src="https://www.youtube.com/embed/VzGxVZP_Cc8" allowfullscreen></iframe>
      <h3>স্মার্ট নোট</h3>
      <p>এই অংশে স্মার্ট নোট ও এক্সাম দেওয়া হবে ভবিষ্যতে।</p>
    </div>
  </section>

  <section id="contact" style="scroll-margin-top: 70px;">
    <h2>যোগাযোগ</h2>
    <form id="contactForm" onsubmit="return submitContactForm(event)">
      <label>আপনার নাম</label>
      <input type="text" name="name" required />

      <label>ইমেইল</label>
      <input type="email" name="email" required />

      <label>বার্তা</label>
      <textarea name="message" rows="4" placeholder="আপনার বার্তা লিখুন"></textarea>

      <button type="submit">পাঠান</button>
    </form>
    <p style="margin-top: 20px;">
      Telegram: <a href="https://t.me/pmicreation" target="_blank" rel="noopener" style="color:#00bfff;">@pmicreation</a> <br />
      YouTube: <a href="https://www.youtube.com/channel/UCMY0VzGxVZP_Cc8" target="_blank" rel="noopener" style="color:#00bfff;">PMI Creation</a>
    </p>
  </section>

  <footer>
    <p>&copy; 2025 PMI Creation | Powered by AI</p>
    <p>Future Features: Chatbot, Quiz Generator, Note Summarizer</p>
  </footer>

  <!-- Login Modal -->
  <div id="loginModal">
    <div class="modal-content">
      <h3>স্টুডেন্ট লগইন</h3>
      <form id="loginForm" onsubmit="return loginStudent(event)">
        <label>ইমেইল</label>
        <input type="email" id="loginEmail" required />
        <label>পাসওয়ার্ড</label>
        <input type="password" id="loginPassword" required />
        <button type="submit">লগইন</button>
        <button type="button" class="close-btn" onclick="closeLoginModal()">বাতিল</button>
      </form>
    </div>
  </div>

  <script>
    // Join Form submit handler (dummy, just alert)
    function submitJoinForm(event) {
      event.preventDefault();
      const form = event.target;
      alert(
        'ধন্যবাদ, ' +
          form.name.value +
          '! আপনার আবেদন গ্রহণ করা হয়েছে। আমরা শীঘ্রই যোগাযোগ করবো।'
      );
      form.reset();
      return false;
    }

    // Contact form submit handler (dummy)
    function submitContactForm(event) {
      event.preventDefault();
      const form = event.target;
      alert(
        'ধন্যবাদ, ' + form.name.value + '! আপনার বার্তা আমাদের কাছে পৌঁছেছে।'
      );
      form.reset();
      return false;
    }

    // Login modal open/close
    function openLoginModal() {
      document.getElementById('loginModal').style.display = 'block';
    }
    function closeLoginModal() {
      document.getElementById('loginModal').style.display = 'none';
    }

    // Dummy login system
    function loginStudent(event) {
      event.preventDefault();
      const email = document.getElementById('loginEmail').value;
      const password = document.getElementById('loginPassword').value;

      // Dummy check
      if (email === 'student@example.com' && password === 'password123') {
        alert('লগইন সফল!');
        closeLoginModal();
        document.getElementById('studentContent').style.display = 'block';
        window.location.hash = '#portal';
      } else {
        alert('ইমেইল বা পাসওয়ার্ড ভুল!');
      }
      return false;
    }

    // Close modal on clicking outside content
    window.onclick = function(event) {
      const modal = document.getElementById('loginModal');
      if (event.target === modal) {
        closeLoginModal();
      }
    };

    // Prevent empty subject or batch or payment in form
    document.querySelectorAll('form select').forEach((sel) => {
      sel.addEventListener('invalid', (e) => {
        e.target.setCustomValidity('অনুগ্রহ করে একটি বিকল্প নির্বাচন করুন');
      });
      sel.addEventListener('input', (e) => {
        e.target.setCustomValidity('');
      });
    });
  </script>

</body>
</html>

