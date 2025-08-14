<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>PMI Creation</title>
  <meta name="description" content="PMI Creation - HSC Physics, Math & ICT courses | Free & Paid batches" />
  <style>
    :root{
      --accent:#0ea5a4;
      --dark:#0f172a;
      --muted:#6b7280;
      --card:#f8fafc;
      font-family: Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
    }
    *{box-sizing:border-box}
    body{margin:0;background:linear-gradient(180deg,#f1f5f9 0%, #ffffff 100%);color:var(--dark);}
    .container{max-width:1100px;margin:0 auto;padding:28px}
    header{display:flex;align-items:center;justify-content:space-between;padding:12px 0}
    .brand{display:flex;gap:12px;align-items:center}
    .logo{width:52px;height:52px;border-radius:10px;background:var(--accent);display:flex;align-items:center;justify-content:center;color:white;font-weight:700;font-size:18px}
    nav a{margin-left:14px;text-decoration:none;color:var(--dark);font-weight:600}
    .hero{display:grid;grid-template-columns:1fr 420px;gap:28px;align-items:center;padding:30px 0}
    .hero h1{font-size:34px;margin:0 0 12px}
    .hero p{color:var(--muted);margin:0 0 18px;line-height:1.6}
    .cta{display:flex;gap:10px}
    .btn{padding:12px 16px;border-radius:10px;border:0;cursor:pointer;font-weight:700}
    .btn-primary{background:var(--accent);color:white}
    .btn-ghost{background:transparent;border:2px solid var(--accent);color:var(--accent)}
    .card{background:var(--card);border-radius:12px;padding:18px;box-shadow:0 6px 20px rgba(2,6,23,0.06)}
    .course-list{display:grid;grid-template-columns:repeat(2,1fr);gap:16px;margin-top:18px}
    .course{padding:12px;border-radius:10px;background:white;border:1px solid #eef2f7}
    .course h4{margin:0 0 6px}
    .course p{margin:0;color:var(--muted);font-size:14px}
    footer{padding:28px 0;color:var(--muted);font-size:14px}
    @media (max-width:880px){
      .hero{grid-template-columns:1fr;}
      .course-list{grid-template-columns:1fr}
      nav a{display:none}
      header{gap:12px}
    }
    form .row{display:flex;gap:10px}
    input,textarea,select{width:100%;padding:10px;border-radius:8px;border:1px solid #e6edf3}
    textarea{min-height:100px}
    .muted{color:var(--muted);font-size:13px}
    .badge{background:#e6fffa;color:#065f46;padding:6px 8px;border-radius:999px;font-weight:700;font-size:12px}
    .youtube-embed{width:100%;height:210px;border-radius:8px;border:0}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">PMI</div>
        <div>
          <div style="font-weight:800">PMI Creation</div>
          <div class="muted" style="font-size:13px">HSC Physics · Math · ICT</div>
        </div>
      </div>
      <nav>
        <a href="#courses">Courses</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
      </nav>
    </header>

    <section class="hero">
      <div>
        <div class="badge">Free + Paid Batches</div>
        <h1>PMI Creation — HSC পারফর্ম্যান্স বাড়ান, প্রতিদিন ভিডিও</h1>
        <p>প্রফেশনাল কনটেন্ট — সংক্ষিপ্ত টপিক, ক্লিয়ার কনসেপ্ট, প্রতিদিন একটি ভিডিও। ফ্রি টিউটোরিয়াল থেকে অ্যাডভান্সড পেইড ব্যাচ — আপনার প্রয়োজন মতো পরিকল্পনা আছে।</p>
        <div class="cta">
          <button class="btn btn-primary" onclick="openLink('https://youtube.com')">YouTube Channel</button>
          <button class="btn btn-ghost" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Join Batch</button>
        </div>
      </div>
      <aside>
        <div class="card">
          <strong>Featured video</strong>
          <iframe class="youtube-embed" src="https://www.youtube.com/embed/VIDEO_ID" title="YouTube video" allowfullscreen></iframe>
          <div style="margin-top:10px" class="muted">ভিডিও: HSC Physics - Motion (Lecture 1)</div>
        </div>
      </aside>
    </section>

    <section id="courses">
      <h2>Courses</h2>
      <div class="course-list">
        <div class="course">
          <h4>HSC Physics (1st Paper)</h4>
          <p>Concept videos, solved problems, past questions practice.</p>
        </div>
        <div class="course">
          <h4>HSC Math</h4>
          <p>Higher math, calculus, and algebra sessions with step-by-step solutions.</p>
        </div>
        <div class="course">
          <h4>HSC ICT</h4>
          <p>Practical and theory — HTML, CSS, basic programming & ICT projects.</p>
        </div>
        <div class="course">
          <h4>Paid Crash Course</h4>
          <p>Exam strategy, mock tests, and personal feedback.</p>
        </div>
      </div>
    </section>

    <section id="about" style="margin-top:20px">
      <div class="card">
        <h3>About PMI Creation</h3>
        <p class="muted">PMI Creation aims to provide concise, exam-focused tutorials for HSC students. Daily videos, clear notes, and both free and paid options to match different budgets.</p>
      </div>
    </section>

    <section id="contact" style="margin-top:18px">
      <div class="card">
        <h3>Contact & Registration</h3>
        <form id="regForm" onsubmit="handleSubmit(event)">
          <div class="row" style="margin-top:10px">
            <input type="text" id="name" placeholder="Full name" required />
            <input type="text" id="phone" placeholder="Phone / WhatsApp" required />
          </div>
          <div style="margin-top:10px">
            <input type="email" id="email" placeholder="Email (optional)" />
          </div>
          <div style="margin-top:10px">
            <select id="interest">
              <option value="physics">HSC Physics</option>
              <option value="math">HSC Math</option>
              <option value="ict">HSC ICT</option>
              <option value="paid">Paid Crash Course</option>
            </select>
          </div>
          <div style="margin-top:10px">
            <textarea id="note" placeholder="Message / Questions (optional)"></textarea>
          </div>
          <div style="margin-top:12px;display:flex;gap:8px">
            <button class="btn btn-primary" type="submit">Request Info</button>
            <button class="btn" type="button" onclick="clearForm()">Clear</button>
          </div>
          <div id="result" style="margin-top:8px;color:green;font-weight:700;display:none">Request sent (demo)</div>
        </form>
      </div>
    </section>

    <footer>
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap">
        <div class="muted">© PMI Creation — Designed for HSC students</div>
        <div class="muted">Made by Nur</div>
      </div>
    </footer>
  </div>

  <script>
    function openLink(url){ window.open(url, '_blank') }
    function handleSubmit(e){
      e.preventDefault();
      document.getElementById('result').style.display='block';
      setTimeout(()=>{
        document.getElementById('result').style.display='none';
      },3500);
    }
    function clearForm(){ document.getElementById('regForm').reset(); }
  </script>
</body>
</html>
