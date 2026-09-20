<!DOCTYPE html>
<html lang="or">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For Miss ❤️</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@600&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  
  <style>
    :root {
      --bg-color: #fff5f7;
      --card-bg: #ffffff;
      --accent: #e85a71;
      --text-dark: #3a2e39;
      --gold-frame: #d4af37;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fdfbfb 0%, #ebedee 100%);
      background-color: var(--bg-color);
      color: var(--text-dark);
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* Initial Entrance Popup Overlay */
    #welcomeOverlay {
      position: fixed;
      inset: 0;
      background: radial-gradient(circle at center, #ffebee, #f8bbd0);
      z-index: 9999;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
      transition: opacity 0.8s ease, visibility 0.8s ease;
    }

    .open-btn {
      margin-top: 25px;
      padding: 16px 42px;
      font-size: 1.2rem;
      font-weight: 600;
      color: white;
      background: linear-gradient(45deg, #ff416c, #ff4b2b);
      border: none;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 10px 25px rgba(255, 65, 108, 0.4);
      transition: all 0.3s ease;
      animation: pulse 2s infinite;
    }

    .open-btn:hover {
      transform: scale(1.06);
      box-shadow: 0 12px 30px rgba(255, 65, 108, 0.6);
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }

    /* Main Container */
    #mainContent {
      display: none;
      opacity: 0;
      transition: opacity 1s ease;
      max-width: 900px;
      margin: 0 auto;
      padding: 40px 20px 80px;
    }

    /* Main Story Letter Box */
    .story-card {
      background: var(--card-bg);
      border-radius: 20px;
      padding: 35px 30px;
      box-shadow: 0 15px 35px rgba(214, 158, 175, 0.2);
      border: 1px solid #ffd8e4;
      line-height: 1.9;
      font-size: 1.05rem;
      color: #4a3e47;
      text-align: justify;
      position: relative;
      margin-bottom: 50px;
    }

    .story-card::before {
      content: "💌";
      font-size: 2.2rem;
      position: absolute;
      top: -24px;
      left: 50%;
      transform: translateX(-50%);
      background: #fff;
      padding: 0 10px;
      border-radius: 50%;
    }

    /* Art Gallery */
    .gallery-title {
      text-align: center;
      font-family: 'Caveat', cursive;
      font-size: 2.8rem;
      color: var(--accent);
      margin-bottom: 35px;
    }

    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 30px;
      margin-bottom: 55px;
    }

    .art-frame {
      background: #ffffff;
      padding: 14px 14px 25px 14px;
      border-radius: 6px;
      box-shadow: 0 12px 28px rgba(0, 0, 0, 0.12);
      position: relative;
      border: 1px solid #eee;
      transition: transform 0.4s ease, box-shadow 0.4s ease;
    }

    .art-frame:hover {
      transform: translateY(-8px) rotate(0.5deg);
      box-shadow: 0 20px 35px rgba(232, 90, 113, 0.25);
    }

    /* Ribbon Bow on top of each frame */
    .art-frame::before {
      content: "🎀";
      font-size: 1.9rem;
      position: absolute;
      top: -16px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 2;
      filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.15));
    }

    .art-frame img {
      width: 100%;
      height: 330px;
      object-fit: cover;
      border-radius: 4px;
      display: block;
    }

    /* Special Gift Heart Button */
    .gift-container {
      text-align: center;
      margin: 40px 0;
    }

    .gift-btn {
      font-size: 3.5rem;
      background: none;
      border: none;
      cursor: pointer;
      display: inline-block;
      transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      animation: heartbeat 1.5s infinite;
    }

    .gift-label {
      font-size: 1.25rem;
      color: #c2185b;
      font-weight: 600;
      margin-top: 10px;
      cursor: pointer;
    }

    @keyframes heartbeat {
      0%, 100% { transform: scale(1); }
      14% { transform: scale(1.15); }
      28% { transform: scale(1); }
      42% { transform: scale(1.15); }
      70% { transform: scale(1); }
    }

    /* Confession Popup Modal */
    .modal-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.55);
      backdrop-filter: blur(4px);
      z-index: 10000;
      display: none;
      justify-content: center;
      align-items: center;
      padding: 20px;
      opacity: 0;
      transition: opacity 0.4s ease;
    }

    .modal-box {
      background: #ffffff;
      max-width: 580px;
      width: 100%;
      border-radius: 24px;
      padding: 35px 30px;
      text-align: center;
      position: relative;
      box-shadow: 0 25px 50px rgba(0, 0, 0, 0.25);
      transform: translateY(20px);
      transition: transform 0.4s ease;
    }

    .modal-title {
      font-size: 1.6rem;
      color: #d81b60;
      font-weight: 600;
      margin-bottom: 20px;
    }

    .modal-content {
      font-size: 1.05rem;
      line-height: 1.8;
      color: #333;
      margin-bottom: 25px;
      text-align: justify;
    }

    .close-modal-btn {
      background: linear-gradient(45deg, #ff416c, #ff4b2b);
      color: white;
      border: none;
      padding: 10px 28px;
      border-radius: 30px;
      font-size: 0.95rem;
      cursor: pointer;
      font-weight: 500;
    }

    /* Last Message Card */
    .last-message-card {
      background: linear-gradient(135deg, #fff0f3, #ffe3e8);
      border-left: 6px solid #e85a71;
      border-radius: 14px;
      padding: 24px 28px;
      font-size: 1.1rem;
      line-height: 1.8;
      color: #4a2d38;
      margin: 45px 0;
      text-align: center;
      box-shadow: 0 10px 25px rgba(232, 90, 113, 0.1);
    }

    /* Final Proposal Section */
    .proposal-box {
      background: #ffffff;
      border-radius: 20px;
      padding: 40px 25px;
      text-align: center;
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.08);
      border: 2px dashed #f8bbd0;
    }

    .proposal-question {
      font-size: 1.45rem;
      font-weight: 600;
      color: #2c252a;
      margin-bottom: 30px;
    }

    .options-group {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 25px;
      flex-wrap: wrap;
    }

    .opt-btn {
      padding: 14px 40px;
      font-size: 1.15rem;
      border-radius: 40px;
      cursor: pointer;
      font-weight: 600;
      transition: all 0.3s ease;
      min-width: 140px;
      border: none;
    }

    .btn-yes {
      background: linear-gradient(45deg, #11998e, #38ef7d);
      color: white;
      box-shadow: 0 8px 20px rgba(56, 239, 125, 0.35);
    }

    .btn-yes:hover {
      transform: scale(1.1);
      box-shadow: 0 12px 25px rgba(56, 239, 125, 0.5);
    }

    .btn-no {
      background: #f1f3f5;
      color: #6c757d;
      border: 1px solid #ced4da;
    }

    #responseSuccess {
      display: none;
      margin-top: 25px;
      font-size: 1.5rem;
      font-weight: 600;
      color: #e85a71;
      animation: fadeIn 0.8s ease forwards;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <!-- 1. Open Screen Popup Overlay -->
  <div id="welcomeOverlay">
    <h1 style="font-family: 'Caveat', cursive; font-size: 3.5rem; color: #d81b60; margin-bottom: 10px;">For Miss ✨</h1>
    <p style="font-size: 1.15rem; color: #555;">There is something special waiting for you inside...</p>
    <button class="open-btn" id="openBtn" onclick="openWebsite()">Open 💖</button>
  </div>

  <!-- Main Website Content -->
  <main id="mainContent">
    
    <!-- 2. Message For Her -->
    <section class="story-card">
      mu jani ni tame mo katha re biswas Kari ba ki nahi,mu gote pila jiye love at first sight upare kebe biswas kare ni . Mu bahut logically bhabe au bahut chin ta kari katha kuhey huye ta sei thi pai mu bahut hin boring chua te boli sabu mate kuhan ti . Mate chua belu hin khali kama Kari baku hin sikha hela jaha jogu mu emotion kn kiye kn feel karu chi kebe bhi feel kari pare ni .kahi baku gale mu manisha na re robot gote. hele jebe pratham thara pai tama ra pai tamara se sadhi pindha photo ti dekhi thili sebe 9 February  chocolate day . Mu ta kebe bhalapai ba re biswas kare ni. mu mo favourite chocolate pai ki bhi khusi nathi li kn pai mu jani ni.Hele se dina 12:30 pakha pakhi tame mate cross kari ki gala au kichi time pare mu tama photo dekhi li seta gote coincident hei pare sata. Hele  mu life re first time pai emi ti kichi feel kali.Mo ye beranga dunia re jemi ti ki colour bhari hei gala . Mo Hrudaya tama ra se photo sahi ta hin tamara hei jai thila.Jiye bhala paiba ku kahu thila ki kebala film re huye  taku love at first sight hei thila.......Sata kahu chi sei dina hin mu bhabi nei thi li ki yei Jhia ra sinthi re mu hin sindura pindhei bi au kebala ya pai hin mu banchi bi au yiye hin mo stree haba boli.
    </section>

    <!-- 3. Art Gallery with Ribbon Bow Frames -->
    <h2 class="gallery-title">Our Art Gallery</h2>
    <section class="gallery-grid">
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260914-WA0073.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260608-WA0022.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260414-WA0014.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\.trashed-1792243535-IMG-20260901-WA0005.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\.trashed-1792243565-IMG-20260810-WA0008.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260608-WA0013.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260414-WA0016.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260706-WA0012.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260914-WA0053.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
      <div class="art-frame">
        <img src="E:\Arajeet\arajeet\pictur\IMG-20260914-WA0030.jpg" alt="Art Frame Photo" loading="lazy" />
      </div>
    </section>

    <!-- 4. Special Gift Trigger Button -->
    <section class="gift-container">
      <button class="gift-btn" onclick="openConfessionModal()" title="Open your special gift">💝</button>
      <div class="gift-label" onclick="openConfessionModal()">special gift for you</div>
    </section>

    <!-- 5. Complete Last Message -->
    <section class="last-message-card">
      mu jani ni ki  aga ku kn haba ki kn nahi hele yeti ki sure ji tama saha sabu kichi possible 🫂 i love you dhana 💗🤧🫂
    </section>

    <!-- 6. Proposal Question Section -->
    <section class="proposal-box">
      <div class="proposal-question">Are u sure about to live the rest of your life with me ?</div>
      <div class="options-group">
        <button class="opt-btn btn-yes" onclick="handleYes()">a. Yes</button>
        <button class="opt-btn btn-no" id="noBtn" onmouseover="dodgeNo()" onclick="dodgeNo()">b. No</button>
      </div>
      <div id="responseSuccess">Forever & Always! ❤️💍✨</div>
    </section>

  </main>

  <!-- Confession Pop-up Modal -->
  <div class="modal-overlay" id="confessionModal" onclick="handleOverlayClick(event)">
    <div class="modal-box" id="modalBox">
      <div class="modal-title">confession 👉👈</div>
      <div class="modal-content">
        mu jebe first time pai tama ku dekhi li mu pura tumara hei sari chi kebala tumara . Mate tumaku chadi dele au sabu fika fika lagu chi .emi ti lagu chi tame acha ta sabu achi tame nahan ta kichi nahi .I LOVE YOU MISS ❤️ i only love 🫵 kebala tume.tume hin mo pai mo stree mo sanga mo jebana sathi mo sabu kichi 🫂🫂. I love you dhana 💗🤧
      </div>
      <button class="close-modal-btn" onclick="closeConfessionModal()">Close 🌸</button>
    </div>
  </div>

  <script>
    // 1. Open Website Transition
    function openWebsite() {
      const overlay = document.getElementById('welcomeOverlay');
      const mainContent = document.getElementById('mainContent');

      overlay.style.opacity = '0';
      setTimeout(() => {
        overlay.style.display = 'none';
        mainContent.style.display = 'block';
        setTimeout(() => {
          mainContent.style.opacity = '1';
        }, 50);
      }, 700);
    }

    // 4. Confession Modal functions
    function openConfessionModal() {
      const modal = document.getElementById('confessionModal');
      const box = document.getElementById('modalBox');
      modal.style.display = 'flex';
      setTimeout(() => {
        modal.style.opacity = '1';
        box.style.transform = 'translateY(0)';
      }, 20);
    }

    function closeConfessionModal() {
      const modal = document.getElementById('confessionModal');
      const box = document.getElementById('modalBox');
      modal.style.opacity = '0';
      box.style.transform = 'translateY(20px)';
      setTimeout(() => {
        modal.style.display = 'none';
      }, 350);
    }

    function handleOverlayClick(event) {
      if (event.target.id === 'confessionModal') {
        closeConfessionModal();
      }
    }

    // 6. Interactive No button behavior & Yes reaction
    function handleYes() {
      const response = document.getElementById('responseSuccess');
      response.style.display = 'block';
      
      // Floating heart burst effect
      for (let i = 0; i < 25; i++) {
        createFloatingHeart();
      }
    }

    function dodgeNo() {
      const noBtn = document.getElementById('noBtn');
      const x = (Math.random() - 0.5) * 260;
      const y = (Math.random() - 0.5) * 180;
      noBtn.style.transform = `translate(${x}px, ${y}px)`;
    }

    function createFloatingHeart() {
      const heart = document.createElement('div');
      heart.innerHTML = '💖';
      heart.style.position = 'fixed';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.bottom = '-20px';
      heart.style.fontSize = (Math.random() * 20 + 20) + 'px';
      heart.style.zIndex = '99999';
      heart.style.pointerEvents = 'none';
      heart.style.transition = 'transform 3s ease-out, opacity 3s ease-out';
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.style.transform = `translateY(-${window.innerHeight + 100}px) rotate(${Math.random() * 360}deg)`;
        heart.style.opacity = '0';
      }, 50);

      setTimeout(() => {
        heart.remove();
      }, 3200);
    }
  </script>
</body>
</html>
