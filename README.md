<!-- ===============================
 DeBeatzGH Premium Floating Banner
 GitHub Pages / Blogger Compatible
 Modern Interactive Top Banner
================================ -->

<style>
:root{
    --dbz-bg:#0d1117;
    --dbz-card:#161b22;
    --dbz-border:#30363d;
    --dbz-accent:#238636;
    --dbz-accent-2:#58a6ff;
    --dbz-text:#f0f6fc;
    --dbz-muted:#8b949e;
    --dbz-shadow:0 10px 35px rgba(0,0,0,.45);
}

/* GLOBAL RESET */
.dbz-banner-wrap *{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

/* MAIN FLOATING BANNER */
.dbz-banner-wrap{
    position:fixed;
    top:14px;
    left:50%;
    transform:translateX(-50%);
    width:92%;
    max-width:520px;
    z-index:999999;
    animation:dbzEntry .8s cubic-bezier(.175,.885,.32,1.2);
    font-family:Inter,Segoe UI,Roboto,sans-serif;
}

@keyframes dbzEntry{
    from{
        opacity:0;
        transform:translateX(-50%) translateY(-50px);
    }
    to{
        opacity:1;
        transform:translateX(-50%) translateY(0);
    }
}

.dbz-banner{
    position:relative;
    overflow:hidden;
    display:flex;
    align-items:center;
    gap:14px;
    padding:14px 16px;
    border-radius:20px;
    background:rgba(13,17,23,.88);
    backdrop-filter:blur(18px);
    border:1px solid rgba(255,255,255,.08);
    box-shadow:var(--dbz-shadow);
    cursor:pointer;
    transition:.35s ease;
}

.dbz-banner:hover{
    transform:translateY(-2px) scale(1.01);
    border-color:rgba(88,166,255,.45);
    box-shadow:0 18px 40px rgba(0,0,0,.55);
}

/* Animated glow */
.dbz-banner::before{
    content:"";
    position:absolute;
    inset:-2px;
    background:linear-gradient(
        90deg,
        transparent,
        rgba(88,166,255,.15),
        rgba(35,134,54,.18),
        transparent
    );
    animation:dbzGlow 5s linear infinite;
}

@keyframes dbzGlow{
    0%{transform:translateX(-100%);}
    100%{transform:translateX(100%);}
}

/* ICON */
.dbz-icon{
    position:relative;
    width:48px;
    height:48px;
    border-radius:14px;
    background:linear-gradient(135deg,var(--dbz-accent),var(--dbz-accent-2));
    display:flex;
    align-items:center;
    justify-content:center;
    flex-shrink:0;
    z-index:2;
    box-shadow:0 10px 20px rgba(35,134,54,.35);
}

.dbz-icon svg{
    width:22px;
    height:22px;
    fill:#fff;
}

/* TEXT SLIDER */
.dbz-content{
    flex:1;
    overflow:hidden;
    position:relative;
    z-index:2;
}

.dbz-slide{
    display:none;
    animation:dbzFade .5s ease;
}

.dbz-slide.active{
    display:block;
}

@keyframes dbzFade{
    from{
        opacity:0;
        transform:translateY(8px);
    }
    to{
        opacity:1;
        transform:translateY(0);
    }
}

.dbz-title{
    font-size:.92rem;
    font-weight:800;
    color:var(--dbz-text);
    letter-spacing:.2px;
}

.dbz-desc{
    margin-top:4px;
    color:var(--dbz-muted);
    font-size:.76rem;
    line-height:1.4;
}

/* LIVE BADGE */
.dbz-badge{
    display:flex;
    align-items:center;
    gap:6px;
    background:rgba(35,134,54,.15);
    border:1px solid rgba(35,134,54,.25);
    padding:5px 10px;
    border-radius:999px;
    color:#7ee787;
    font-size:.66rem;
    font-weight:800;
    text-transform:uppercase;
    letter-spacing:.8px;
    flex-shrink:0;
    z-index:2;
}

.dbz-pulse{
    width:7px;
    height:7px;
    border-radius:50%;
    background:#7ee787;
    animation:dbzPulse 1.5s infinite;
}

@keyframes dbzPulse{
    0%{
        transform:scale(1);
        opacity:1;
    }
    50%{
        transform:scale(1.6);
        opacity:.4;
    }
    100%{
        transform:scale(1);
        opacity:1;
    }
}

/* QUICK ACTION BUTTONS */
.dbz-quick-links{
    margin-top:10px;
    display:flex;
    gap:10px;
    overflow-x:auto;
    scrollbar-width:none;
}

.dbz-quick-links::-webkit-scrollbar{
    display:none;
}

.dbz-link{
    white-space:nowrap;
    text-decoration:none;
    background:rgba(255,255,255,.05);
    border:1px solid rgba(255,255,255,.06);
    color:var(--dbz-text);
    font-size:.74rem;
    padding:9px 14px;
    border-radius:999px;
    transition:.25s ease;
    display:flex;
    align-items:center;
    gap:6px;
}

.dbz-link:hover{
    background:var(--dbz-accent-2);
    color:#fff;
    transform:translateY(-2px);
}

/* MINI NOTIFICATION */
.dbz-popup{
    position:fixed;
    right:18px;
    bottom:20px;
    background:rgba(13,17,23,.94);
    border:1px solid rgba(88,166,255,.22);
    color:var(--dbz-text);
    padding:14px 16px;
    border-radius:16px;
    width:280px;
    z-index:99999;
    backdrop-filter:blur(12px);
    box-shadow:var(--dbz-shadow);
    animation:dbzPopup 1s ease;
}

@keyframes dbzPopup{
    from{
        opacity:0;
        transform:translateY(30px);
    }
    to{
        opacity:1;
        transform:translateY(0);
    }
}

.dbz-popup h4{
    font-size:.9rem;
    margin-bottom:6px;
}

.dbz-popup p{
    font-size:.76rem;
    color:var(--dbz-muted);
    line-height:1.5;
}

.dbz-popup button{
    margin-top:12px;
    border:none;
    background:var(--dbz-accent);
    color:#fff;
    padding:8px 12px;
    border-radius:10px;
    cursor:pointer;
    font-size:.74rem;
    font-weight:700;
}

/* MOBILE */
@media(max-width:640px){

    .dbz-banner{
        padding:12px;
        gap:10px;
    }

    .dbz-icon{
        width:42px;
        height:42px;
    }

    .dbz-title{
        font-size:.82rem;
    }

    .dbz-desc{
        font-size:.7rem;
    }

    .dbz-popup{
        width:90%;
        right:5%;
    }
}
</style>

<!-- ===============================
 MAIN BANNER
================================ -->

<div class="dbz-banner-wrap">

    <div class="dbz-banner" onclick="dbzOpenMainLink()">

        <div class="dbz-icon">
            <svg viewBox="0 0 24 24">
                <path d="M4 4h7v7H4zm9 0h7v7h-7zM4 13h7v7H4zm9 3h7v4h-7z"/>
            </svg>
        </div>

        <div class="dbz-content">

            <div class="dbz-slide active">
                <div class="dbz-title">
                    DeBeatzGH Digital Creator Hub
                </div>
                <div class="dbz-desc">
                    Launch online businesses, AI tools, side hustles & premium digital resources.
                </div>
            </div>

            <div class="dbz-slide">
                <div class="dbz-title">
                    Professional GitHub Pages UI
                </div>
                <div class="dbz-desc">
                    Explore reusable widgets, premium interfaces and startup resources.
                </div>
            </div>

            <div class="dbz-slide">
                <div class="dbz-title">
                    AI & Online Business Starter Kits
                </div>
                <div class="dbz-desc">
                    Smart tools and guides designed for creators, freelancers and entrepreneurs.
                </div>
            </div>

        </div>

        <div class="dbz-badge">
            <span class="dbz-pulse"></span>
            LIVE
        </div>

    </div>

    <!-- QUICK LINKS -->
    <div class="dbz-quick-links">

        <a class="dbz-link"
           href="https://debeatzgh1.github.io/Home-/"
           target="_blank">
           🏠 Home
        </a>

        <a class="dbz-link"
           href="https://debeatzgh1.github.io/Pages-/"
           target="_blank">
           📄 Pages
        </a>

        <a class="dbz-link"
           href="https://debeatzgh1.github.io/The-Ultimate-Guide-to-Side-Hustle/"
           target="_blank">
           🚀 Starter Kits
        </a>

        <a class="dbz-link"
           href="https://beatzde4.blogspot.com/"
           target="_blank">
           ✍️ Blog
        </a>

    </div>

</div>

<!-- SMART POPUP -->
<div class="dbz-popup" id="dbzPopup">
    <h4>✨ Welcome to DeBeatzGH</h4>
    <p>
        Discover premium AI resources, side hustle starter kits, blogging tools,
        GitHub page templates and modern creator solutions.
    </p>

    <button onclick="window.open('https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/','_blank')">
        Explore Resources
    </button>
</div>

<script>
/* ===============================
   MAIN URL OPEN
================================ */
function dbzOpenMainLink(){
    window.open(
        "https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/",
        "_blank"
    );
}

/* ===============================
   AUTO TEXT SLIDER
================================ */
const dbzSlides = document.querySelectorAll('.dbz-slide');
let dbzCurrent = 0;

function dbzRotateSlides(){

    dbzSlides[dbzCurrent].classList.remove('active');

    dbzCurrent = (dbzCurrent + 1) % dbzSlides.length;

    dbzSlides[dbzCurrent].classList.add('active');
}

setInterval(dbzRotateSlides, 3500);

/* ===============================
   AUTO POPUP CLOSE
================================ */
setTimeout(() => {
    const popup = document.getElementById('dbzPopup');

    if(popup){
        popup.style.transition = ".5s ease";
        popup.style.opacity = "0";
        popup.style.transform = "translateY(20px)";

        setTimeout(() => {
            popup.remove();
        }, 500);
    }

}, 14000);

/* ===============================
   LAZY ENGAGEMENT EFFECT
================================ */
window.addEventListener('scroll', () => {
    const banner = document.querySelector('.dbz-banner');

    if(window.scrollY > 100){
        banner.style.backdropFilter = "blur(24px)";
        banner.style.borderColor = "rgba(88,166,255,.28)";
    } else {
        banner.style.borderColor = "rgba(255,255,255,.08)";
    }
});
</script>


<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Premium Workspace Embed UI</title>

<style>
/* =========================
   GLOBAL
========================= */
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  background:#0b1120;
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
  padding:20px;
  color:#fff;
}

/* =========================
   MAIN WRAPPER
========================= */
#dbz-workspace-embed{
  --dbz-bg:#ffffff;
  --dbz-border:#e2e8f0;
  --dbz-text:#0f172a;
  --dbz-muted:#64748b;
  --dbz-primary:#2563eb;
  --dbz-primary-light:#eff6ff;
  --dbz-shadow:0 15px 50px rgba(0,0,0,.15);

  width:100%;
  max-width:1200px;
  margin:auto;
  border-radius:24px;
  overflow:hidden;
  background:var(--dbz-bg);
  border:1px solid var(--dbz-border);
  box-shadow:var(--dbz-shadow);
  position:relative;
}

/* =========================
   HEADER
========================= */
.dbz-topbar{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:20px;
  flex-wrap:wrap;
  padding:16px 20px;
  background:#f8fafc;
  border-bottom:1px solid var(--dbz-border);
}

.dbz-left{
  display:flex;
  align-items:center;
  gap:12px;
  flex-wrap:wrap;
}

.dbz-dots{
  display:flex;
  gap:7px;
}

.dbz-dot{
  width:12px;
  height:12px;
  border-radius:50%;
}

.dbz-red{
  background:#ef4444;
}

.dbz-yellow{
  background:#facc15;
}

.dbz-green{
  background:#22c55e;
}

.dbz-title{
  color:var(--dbz-text);
  font-size:15px;
  font-weight:700;
}

.dbz-subtitle{
  color:var(--dbz-muted);
  font-size:12px;
  margin-top:3px;
}

/* =========================
   BUTTONS
========================= */
.dbz-actions{
  display:flex;
  gap:12px;
  flex-wrap:wrap;
}

.dbz-btn{
  text-decoration:none;
  border:none;
  cursor:pointer;
  padding:12px 18px;
  border-radius:14px;
  font-size:13px;
  font-weight:700;
  transition:.3s ease;
  display:inline-flex;
  align-items:center;
  justify-content:center;
  gap:8px;
}

.dbz-btn-primary{
  background:linear-gradient(135deg,#2563eb,#4f46e5);
  color:#fff;
}

.dbz-btn-primary:hover{
  transform:translateY(-2px);
}

.dbz-btn-light{
  background:#eff6ff;
  color:#2563eb;
}

.dbz-btn-light:hover{
  background:#dbeafe;
}

/* =========================
   FRAME AREA
========================= */
.dbz-frame-wrap{
  position:relative;
  width:100%;
  height:780px;
  background:#f1f5f9;
}

.dbz-frame{
  width:100%;
  height:100%;
  border:none;
  background:#fff;
  opacity:0;
  transition:opacity .4s ease;
}

/* =========================
   LOADER
========================= */
.dbz-loader{
  position:absolute;
  inset:0;
  background:#fff;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  z-index:5;
}

.dbz-spinner{
  width:52px;
  height:52px;
  border-radius:50%;
  border:4px solid #dbeafe;
  border-top-color:#2563eb;
  animation:dbzSpin .8s linear infinite;
}

@keyframes dbzSpin{
  to{
    transform:rotate(360deg);
  }
}

.dbz-loader p{
  margin-top:16px;
  color:#64748b;
  font-size:14px;
  font-weight:600;
}

/* =========================
   URL BAR
========================= */
.dbz-urlbar{
  padding:16px 18px;
  border-top:1px solid var(--dbz-border);
  background:#fff;
  display:flex;
  gap:12px;
  flex-wrap:wrap;
}

.dbz-urlbar input{
  flex:1;
  min-width:220px;
  border:1px solid #cbd5e1;
  border-radius:14px;
  padding:14px;
  font-size:14px;
  outline:none;
  background:#f8fafc;
  color:#0f172a;
}

.dbz-urlbar input:focus{
  border-color:#2563eb;
  background:#fff;
}

/* =========================
   MOBILE
========================= */
@media(max-width:768px){

  body{
    padding:12px;
  }

  .dbz-topbar{
    flex-direction:column;
    align-items:flex-start;
  }

  .dbz-actions{
    width:100%;
  }

  .dbz-btn{
    flex:1;
  }

  .dbz-frame-wrap{
    height:620px;
  }

  .dbz-urlbar{
    flex-direction:column;
  }

}
</style>
</head>

<body>

<div id="dbz-workspace-embed">

  <!-- HEADER -->
  <div class="dbz-topbar">

    <div class="dbz-left">

      <div class="dbz-dots">
        <span class="dbz-dot dbz-red"></span>
        <span class="dbz-dot dbz-yellow"></span>
        <span class="dbz-dot dbz-green"></span>
      </div>

      <div>
        <div class="dbz-title">
          Workspace Viewport
        </div>

        <div class="dbz-subtitle">
          Docs • Blogger • GitHub Pages • WordPress Compatible
        </div>
      </div>

    </div>

    <div class="dbz-actions">

      <a class="dbz-btn dbz-btn-light"
         href="https://appdategh1.blogspot.com/2024/05/tech-business-tools-and-ideas-for.html"
         target="_blank">
         Templates ↗
      </a>

      <a class="dbz-btn dbz-btn-primary"
         id="dbzExternalBtn"
         href="https://mailchi.mp/0a569aa1173e/ai-decoder"
         target="_blank">
         Open External ↗
      </a>

    </div>

  </div>

  <!-- FRAME -->
  <div class="dbz-frame-wrap">

    <!-- LOADER -->
    <div class="dbz-loader" id="dbzLoader">
      <div class="dbz-spinner"></div>

      <p>
        Establishing secure workspace connection...
      </p>
    </div>

    <!-- IFRAME -->
    <iframe
      id="dbzFrame"
      class="dbz-frame"
      src="https://mailchi.mp/0a569aa1173e/ai-decoder"
      loading="lazy"
      allowfullscreen
      referrerpolicy="strict-origin-when-cross-origin"
      sandbox="allow-scripts allow-same-origin allow-popups allow-forms allow-modals allow-downloads"
      onload="dbzFrameLoaded()">
    </iframe>

  </div>

  <!-- URL TOOL -->
  <div class="dbz-urlbar">

    <input
      type="text"
      id="dbzUrlInput"
      placeholder="Paste GitHub Pages, Blogger, Docs, or WordPress URL..."
    >

    <button
      class="dbz-btn dbz-btn-primary"
      onclick="dbzLoadURL()">
      Preview URL
    </button>

  </div>

</div>

<script>
(function(){

  const frame = document.getElementById("dbzFrame");
  const loader = document.getElementById("dbzLoader");
  const input = document.getElementById("dbzUrlInput");
  const externalBtn = document.getElementById("dbzExternalBtn");

  // FRAME LOAD
  window.dbzFrameLoaded = function(){

    loader.style.display = "none";
    frame.style.opacity = "1";

  };

  // LOAD NEW URL
  window.dbzLoadURL = function(){

    let url = input.value.trim();

    if(!url){
      alert("Please enter a valid URL.");
      return;
    }

    // Convert Google Docs edit → preview
    if(url.includes("docs.google.com/document") && url.includes("/edit")){
      url = url.replace("/edit", "/preview");
    }

    // Show loader
    loader.style.display = "flex";
    frame.style.opacity = "0";

    // Load iframe
    frame.src = https://mailchi.mp/0a569aa1173e/ai-decoder;

    // Update external button
    externalBtn.href = url;

  };

})();
</script>
