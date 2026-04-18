 <!DOCTYPE html>

<html lang="ur" dir="ltr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Shayari Generator — شاعری</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Nastaliq+Urdu:wght@400;700&family=Playfair+Display:ital,wght@0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0608;
    --surface: #140d10;
    --card: #1e1218;
    --border: #3d2030;
    --accent: #e8936a;
    --accent2: #c45e8a;
    --gold: #d4a853;
    --text: #f0e6ec;
    --muted: #8a6878;
  }

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–bg);
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
min-height: 100vh;
overflow-x: hidden;
}

/* Animated background */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background:
radial-gradient(ellipse 60% 50% at 20% 20%, rgba(196,94,138,0.12) 0%, transparent 60%),
radial-gradient(ellipse 50% 60% at 80% 80%, rgba(232,147,106,0.10) 0%, transparent 60%),
radial-gradient(ellipse 40% 40% at 50% 50%, rgba(212,168,83,0.05) 0%, transparent 70%);
pointer-events: none;
z-index: 0;
}

.container {
position: relative;
z-index: 1;
max-width: 680px;
margin: 0 auto;
padding: 2rem 1.2rem 4rem;
}

/* Header */
header {
text-align: center;
padding: 3rem 0 2.5rem;
}

.logo-tag {
display: inline-block;
font-size: 0.7rem;
letter-spacing: 0.25em;
text-transform: uppercase;
color: var(–accent2);
border: 1px solid var(–accent2);
padding: 0.3em 0.9em;
border-radius: 2px;
margin-bottom: 1.2rem;
opacity: 0.85;
}

h1 {
font-family: ‘Playfair Display’, serif;
font-size: clamp(2.2rem, 7vw, 3.5rem);
font-weight: 700;
line-height: 1.1;
background: linear-gradient(135deg, var(–accent) 0%, var(–gold) 50%, var(–accent2) 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
margin-bottom: 0.6rem;
}

.urdu-title {
font-family: ‘Noto Nastaliq Urdu’, serif;
font-size: 1.4rem;
color: var(–gold);
opacity: 0.8;
display: block;
margin-bottom: 0.8rem;
}

header p {
color: var(–muted);
font-size: 0.95rem;
font-weight: 300;
letter-spacing: 0.02em;
}

/* Divider */
.divider {
display: flex;
align-items: center;
gap: 1rem;
margin: 2rem 0;
opacity: 0.3;
}
.divider::before, .divider::after {
content: ‘’;
flex: 1;
height: 1px;
background: linear-gradient(90deg, transparent, var(–accent), transparent);
}
.divider span { font-size: 1rem; }

/* Card */
.card {
background: var(–card);
border: 1px solid var(–border);
border-radius: 16px;
padding: 1.8rem;
margin-bottom: 1.2rem;
position: relative;
overflow: hidden;
}

.card::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 2px;
background: linear-gradient(90deg, var(–accent2), var(–gold), var(–accent));
}

.card-label {
font-size: 0.72rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–muted);
margin-bottom: 1rem;
display: flex;
align-items: center;
gap: 0.5rem;
}

/* Mood selector */
.mood-grid {
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 0.6rem;
}

.mood-btn {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 10px;
padding: 0.75rem 1rem;
cursor: pointer;
transition: all 0.2s ease;
text-align: left;
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
font-size: 0.9rem;
}

.mood-btn:hover {
border-color: var(–accent);
background: rgba(232,147,106,0.08);
transform: translateY(-1px);
}

.mood-btn.active {
border-color: var(–accent);
background: rgba(232,147,106,0.15);
box-shadow: 0 0 20px rgba(232,147,106,0.15);
}

.mood-btn .emoji { font-size: 1.3rem; display: block; margin-bottom: 0.2rem; }
.mood-btn .mood-name { font-weight: 500; display: block; }
.mood-btn .mood-urdu {
font-family: ‘Noto Nastaliq Urdu’, serif;
font-size: 0.85rem;
color: var(–muted);
display: block;
}

/* Input */
.input-group { margin-bottom: 0.8rem; }

input[type=“text”], textarea {
width: 100%;
background: var(–surface);
border: 1px solid var(–border);
border-radius: 10px;
padding: 0.85rem 1rem;
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
font-size: 0.95rem;
outline: none;
transition: border-color 0.2s;
resize: none;
}

input[type=“text”]:focus, textarea:focus {
border-color: var(–accent);
box-shadow: 0 0 0 3px rgba(232,147,106,0.1);
}

input::placeholder, textarea::placeholder { color: var(–muted); }

/* Style selector */
.style-pills {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
}

.style-pill {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 20px;
padding: 0.4rem 0.9rem;
cursor: pointer;
font-size: 0.82rem;
color: var(–muted);
transition: all 0.2s;
font-family: ‘DM Sans’, sans-serif;
}

.style-pill:hover, .style-pill.active {
border-color: var(–accent2);
color: var(–accent2);
background: rgba(196,94,138,0.1);
}

/* Generate button */
.generate-btn {
width: 100%;
padding: 1rem;
background: linear-gradient(135deg, var(–accent2), var(–accent));
border: none;
border-radius: 12px;
color: white;
font-family: ‘DM Sans’, sans-serif;
font-size: 1rem;
font-weight: 500;
cursor: pointer;
transition: all 0.25s ease;
position: relative;
overflow: hidden;
letter-spacing: 0.02em;
margin-top: 0.5rem;
}

.generate-btn:hover {
transform: translateY(-2px);
box-shadow: 0 8px 30px rgba(196,94,138,0.4);
}

.generate-btn:active { transform: translateY(0); }

.generate-btn:disabled {
opacity: 0.6;
cursor: not-allowed;
transform: none;
}

/* Loader */
.loader {
display: none;
text-align: center;
padding: 2rem;
color: var(–muted);
font-size: 0.9rem;
}

.loader.show { display: block; }

.loader-dots {
display: flex;
justify-content: center;
gap: 0.4rem;
margin-bottom: 0.8rem;
}

.loader-dots span {
width: 8px; height: 8px;
background: var(–accent);
border-radius: 50%;
animation: bounce 1.2s infinite;
}
.loader-dots span:nth-child(2) { animation-delay: 0.2s; background: var(–gold); }
.loader-dots span:nth-child(3) { animation-delay: 0.4s; background: var(–accent2); }

@keyframes bounce {
0%, 80%, 100% { transform: translateY(0); opacity: 0.4; }
40% { transform: translateY(-10px); opacity: 1; }
}

/* Result card */
.result-card {
display: none;
background: var(–card);
border: 1px solid var(–border);
border-radius: 16px;
padding: 2rem;
position: relative;
animation: fadeIn 0.5s ease;
}

.result-card.show { display: block; }

@keyframes fadeIn {
from { opacity: 0; transform: translateY(10px); }
to { opacity: 1; transform: translateY(0); }
}

.result-card::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 2px;
background: linear-gradient(90deg, var(–gold), var(–accent2), var(–accent));
}

.result-label {
font-size: 0.7rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–gold);
margin-bottom: 1.5rem;
display: flex;
align-items: center;
gap: 0.5rem;
}

.shayari-text {
font-family: ‘Noto Nastaliq Urdu’, serif;
font-size: clamp(1.1rem, 3.5vw, 1.4rem);
line-height: 2.2;
color: var(–text);
text-align: right;
direction: rtl;
white-space: pre-wrap;
padding: 1rem 0;
border-top: 1px solid var(–border);
border-bottom: 1px solid var(–border);
margin-bottom: 1.5rem;
}

.shayari-roman {
font-family: ‘Playfair Display’, serif;
font-style: italic;
font-size: 0.95rem;
color: var(–muted);
line-height: 1.9;
white-space: pre-wrap;
margin-bottom: 1.5rem;
}

/* Action buttons */
.action-row {
display: flex;
gap: 0.6rem;
flex-wrap: wrap;
}

.action-btn {
flex: 1;
min-width: 100px;
padding: 0.65rem 1rem;
border-radius: 8px;
border: 1px solid var(–border);
background: var(–surface);
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
font-size: 0.82rem;
cursor: pointer;
transition: all 0.2s;
display: flex;
align-items: center;
justify-content: center;
gap: 0.4rem;
}

.action-btn:hover {
border-color: var(–accent);
color: var(–accent);
background: rgba(232,147,106,0.08);
}

.action-btn.whatsapp:hover {
border-color: #25d366;
color: #25d366;
background: rgba(37,211,102,0.08);
}

/* Toast */
.toast {
position: fixed;
bottom: 2rem;
left: 50%;
transform: translateX(-50%) translateY(100px);
background: var(–card);
border: 1px solid var(–accent);
color: var(–text);
padding: 0.7rem 1.4rem;
border-radius: 8px;
font-size: 0.85rem;
transition: transform 0.3s ease;
z-index: 100;
}

.toast.show { transform: translateX(-50%) translateY(0); }

/* Error */
.error-msg {
display: none;
background: rgba(196,94,138,0.1);
border: 1px solid rgba(196,94,138,0.3);
border-radius: 10px;
padding: 1rem;
color: var(–accent2);
font-size: 0.88rem;
margin-top: 0.8rem;
text-align: center;
}
.error-msg.show { display: block; }

/* Footer */
footer {
text-align: center;
margin-top: 3rem;
color: var(–muted);
font-size: 0.78rem;
opacity: 0.6;
}

/* Ornament */
.ornament {
text-align: center;
color: var(–gold);
opacity: 0.4;
font-size: 1.2rem;
margin: 0.5rem 0;
letter-spacing: 0.5em;
}
</style>

</head>
<body>

<div class="container">

  <header>
    <span class="logo-tag">✨ AI Powered</span>
    <h1>Shayari Generator</h1>
    <span class="urdu-title">شاعری جنریٹر</span>
    <p>Apne jazbaat ko alfazon mein dhalo — AI ke saath</p>
  </header>

  <div class="ornament">❧ ✦ ❧</div>

  <!-- Mood Selection -->

  <div class="card">
    <div class="card-label">🎭 Mood Chunein</div>
    <div class="mood-grid">
      <button class="mood-btn active" onclick="selectMood(this, 'ishq')" >
        <span class="emoji">💕</span>
        <span class="mood-name">Ishq</span>
        <span class="mood-urdu">عشق</span>
      </button>
      <button class="mood-btn" onclick="selectMood(this, 'dard')">
        <span class="emoji">🥀</span>
        <span class="mood-name">Dard</span>
        <span class="mood-urdu">درد</span>
      </button>
      <button class="mood-btn" onclick="selectMood(this, 'dosti')">
        <span class="emoji">🤝</span>
        <span class="mood-name">Dosti</span>
        <span class="mood-urdu">دوستی</span>
      </button>
      <button class="mood-btn" onclick="selectMood(this, 'mazaah')">
        <span class="emoji">😄</span>
        <span class="mood-name">Mazaah</span>
        <span class="mood-urdu">مزاح</span>
      </button>
      <button class="mood-btn" onclick="selectMood(this, 'judai')">
        <span class="emoji">🌙</span>
        <span class="mood-name">Judai</span>
        <span class="mood-urdu">جدائی</span>
      </button>
      <button class="mood-btn" onclick="selectMood(this, 'khushi')">
        <span class="emoji">🌹</span>
        <span class="mood-name">Khushi</span>
        <span class="mood-urdu">خوشی</span>
      </button>
    </div>
  </div>

  <!-- Name Input -->

  <div class="card">
    <div class="card-label">👤 Naam (Optional)</div>
    <div class="input-group">
      <input type="text" id="nameInput" placeholder="Jis ke liye shayari ho — uska naam likho..." maxlength="30">
    </div>
    <div class="card-label" style="margin-top:1rem">✍️ Apna Khayal (Optional)</div>
    <textarea id="themeInput" rows="2" placeholder="Koi khaas baat jo shayari mein ho... (e.g. aankhein, intezaar, baarish)"></textarea>
  </div>

  <!-- Style -->

  <div class="card">
    <div class="card-label">🖋️ Style</div>
    <div class="style-pills">
      <button class="style-pill active" onclick="selectStyle(this, 'ghazal')">Ghazal غزل</button>
      <button class="style-pill" onclick="selectStyle(this, 'nazm')">Nazm نظم</button>
      <button class="style-pill" onclick="selectStyle(this, 'rubai')">Rubai رباعی</button>
      <button class="style-pill" onclick="selectStyle(this, 'doha')">Doha دوہا</button>
      <button class="style-pill" onclick="selectStyle(this, 'modern')">Modern ماڈرن</button>
    </div>
  </div>

  <!-- Generate -->

  <button class="generate-btn" onclick="generateShayari()" id="genBtn">
    ✨ Shayari Banao
  </button>

  <div class="error-msg" id="errorMsg">
    Kuch masla hua! Dobara try karein. 🙏
  </div>

  <!-- Loader -->

  <div class="loader" id="loader">
    <div class="loader-dots">
      <span></span><span></span><span></span>
    </div>
    AI shayari likh raha hai... 🖊️
  </div>

  <!-- Result -->

  <div class="result-card" id="resultCard">
    <div class="result-label">✦ Aapki Shayari</div>
    <div class="shayari-text" id="shayariUrdu"></div>
    <div class="shayari-roman" id="shayariRoman"></div>
    <div class="action-row">
      <button class="action-btn" onclick="copyShayari()">📋 Copy</button>
      <button class="action-btn whatsapp" onclick="shareWhatsApp()">💬 WhatsApp</button>
      <button class="action-btn" onclick="generateShayari()">🔄 Nai Shayari</button>
    </div>
  </div>

  <div class="divider"><span>✦</span></div>

  <footer>
    Made with 💕 for Urdu lovers everywhere<br>
    AI Shayari Generator — Har jazbaat ke liye alfaaz
  </footer>

</div>

<div class="toast" id="toast"></div>

<script>
  let selectedMood = 'ishq';
  let selectedStyle = 'ghazal';

  function selectMood(btn, mood) {
    document.querySelectorAll('.mood-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    selectedMood = mood;
  }

  function selectStyle(btn, style) {
    document.querySelectorAll('.style-pill').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    selectedStyle = style;
  }

  async function generateShayari() {
    const name = document.getElementById('nameInput').value.trim();
    const theme = document.getElementById('themeInput').value.trim();
    const genBtn = document.getElementById('genBtn');
    const loader = document.getElementById('loader');
    const resultCard = document.getElementById('resultCard');
    const errorMsg = document.getElementById('errorMsg');

    genBtn.disabled = true;
    loader.classList.add('show');
    resultCard.classList.remove('show');
    errorMsg.classList.remove('show');

    const moodMap = {
      ishq: 'romantic love and longing',
      dard: 'heartbreak and pain',
      dosti: 'friendship and loyalty',
      mazaah: 'humor and wit',
      judai: 'separation and distance',
      khushi: 'joy and celebration'
    };

    const styleMap = {
      ghazal: 'ghazal (with matla, maqta, and radif)',
      nazm: 'nazm (free verse poem)',
      rubai: 'rubai (4-line quatrain)',
      doha: 'doha (couplet)',
      modern: 'modern contemporary style'
    };

    const nameNote = name ? `The shayari is dedicated to or about someone named "${name}".` : '';
    const themeNote = theme ? `Include this theme or imagery: "${theme}".` : '';

    const prompt = `You are a master Urdu poet. Write a beautiful ${styleMap[selectedStyle]} about ${moodMap[selectedMood]}. ${nameNote} ${themeNote}

Rules:
1. Write the shayari FIRST in Urdu script (nastaliq)
2. Then write the Roman Urdu transliteration
3. Keep it 4-8 lines, authentic and poetic
4. Format your response EXACTLY like this:

URDU:
[Urdu script shayari here]

ROMAN:
[Roman Urdu transliteration here]

Make it deeply emotional, use classical Urdu imagery (chaand, aankhein, dil, intezaar, shama, parwana, etc.). Make it feel genuine, not generic.`;

    try {
      const response = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 1000,
          messages: [{ role: "user", content: prompt }]
        })
      });

      const data = await response.json();
      const text = data.content[0].text;

      const urduMatch = text.match(/URDU:\n([\s\S]*?)(?=\nROMAN:|$)/);
      const romanMatch = text.match(/ROMAN:\n([\s\S]*?)$/);

      const urduText = urduMatch ? urduMatch[1].trim() : text;
      const romanText = romanMatch ? romanMatch[1].trim() : '';

      document.getElementById('shayariUrdu').textContent = urduText;
      document.getElementById('shayariRoman').textContent = romanText;

      resultCard.classList.add('show');
    } catch (err) {
      errorMsg.classList.add('show');
    } finally {
      genBtn.disabled = false;
      loader.classList.remove('show');
    }
  }

  function copyShayari() {
    const urdu = document.getElementById('shayariUrdu').textContent;
    const roman = document.getElementById('shayariRoman').textContent;
    navigator.clipboard.writeText(urdu + '\n\n' + roman).then(() => showToast('✅ Copy ho gaya!'));
  }

  function shareWhatsApp() {
    const urdu = document.getElementById('shayariUrdu').textContent;
    const roman = document.getElementById('shayariRoman').textContent;
    const text = encodeURIComponent(`✨ AI Shayari ✨\n\n${urdu}\n\n${roman}\n\n— AI Shayari Generator`);
    window.open(`https://wa.me/?text=${text}`, '_blank');
  }

  function showToast(msg) {
    const toast = document.getElementById('toast');
    toast.textContent = msg;
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 2500);
  }
</script>

</body>
</html>
