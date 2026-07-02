<!-- 

<!-- ===============================
 FLOATING WIDGET
================================ -->
<div class="dbz-hustle-widget">

  <div class="dbz-mini-card" onclick="openDbzHub()">

    <div class="dbz-content">

      <div class="dbz-icon-wrap">
        <svg viewBox="0 0 24 24">
          <path d="M12 2L2 7v10l10 5 10-5V7L12 2zm0 2.2l7.5 3.8L12 11.8 4.5 8 12 4.2z"/>
        </svg>
      </div>

      <div class="dbz-text-area">

        <div class="dbz-badge">
          <span class="dbz-live-dot"></span>
          LIVE PLATFORM
        </div>

        <div class="dbz-slide active">
          <h3>Side Hustle Starter Kits</h3>
          <p>Launch modern digital businesses with AI tools & resources.</p>
        </div>

        <div class="dbz-slide">
          <h3>Premium GitHub Interfaces</h3>
          <p>Reusable widgets, templates & modern UI systems.</p>
        </div>

        <div class="dbz-slide">
          <h3>AI Productivity Hub</h3>
          <p>Discover tools for creators, bloggers & entrepreneurs.</p>
        </div>

      </div>

      <div class="dbz-arrow">›</div>

    </div>

  </div>

  <div class="dbz-quick-actions">
    <button class="dbz-action-btn dbz-open" onclick="openDbzHub()">
      Open Preview
    </button>

    <button class="dbz-action-btn dbz-visit" onclick="window.open('https://debeatzgh1.github.io/Home-/', '_blank')">
      Visit Homepage
    </button>
  </div>

</div>

<!-- ===============================
 OVERLAY FRAME
================================ -->
<div id="dbzOverlay">

  <div class="dbz-frame-shell">

    <div class="dbz-topbar">

      <div class="dbz-brand">
        <div class="dbz-brand-icon">D</div>

        <div>
          <h2>DeBeatzGH Digital Hub</h2>
          <p>Professional GitHub Pages Workspace</p>
        </div>
      </div>

      <div class="dbz-controls">

        <button class="dbz-control-btn dbz-fullscreen" onclick="toggleFullscreen()">
          Fullscreen
        </button>

        <button class="dbz-control-btn dbz-external"
          onclick="window.open('https://msha.ke/debeatzgh','_blank')">
          Open External
        </button>

        <button class="dbz-control-btn dbz-close" onclick="closeDbzHub()">
          Close
        </button>

      </div>

    </div>

    <div class="dbz-frame-wrap">

      <div class="dbz-loader" id="dbzLoader">
        <div class="dbz-loader-ring"></div>
        <p>Loading GitHub workspace interface...</p>
      </div>

      <!-- Lazy Loaded -->
      <iframe
        id="dbzIframe"
        loading="lazy"
        title="DeBeatzGH Workspace">
      </iframe>

    </div>

  </div>

</div>

<script>
/* ===============================
 AUTO TEXT ROTATOR
================================ */
const dbzSlides = document.querySelectorAll('.dbz-slide');
let dbzCurrent = 0;

setInterval(() => {
  dbzSlides[dbzCurrent].classList.remove('active');
  dbzCurrent = (dbzCurrent + 1) % dbzSlides.length;
  dbzSlides[dbzCurrent].classList.add('active');
}, 3500);

/* ===============================
 OPEN HUB (LAZY LOAD)
================================ */
function openDbzHub(){

  const overlay = document.getElementById('dbzOverlay');
  const iframe = document.getElementById('dbzIframe');
  const loader = document.getElementById('dbzLoader');

  overlay.classList.add('active');
  document.body.style.overflow = 'hidden';

  // Lazy Load
  if(!iframe.src){
    iframe.src = "https://msha.ke/debeatzgh";

    iframe.onload = () => {
      loader.style.display = 'none';
      iframe.style.opacity = '1';
      showDbzToast();
    };
  }else{
    loader.style.display = 'none';
    iframe.style.opacity = '1';
  }
}

/* ===============================
 CLOSE HUB
================================ */
function closeDbzHub(){
  document.getElementById('dbzOverlay').classList.remove('active');
  document.body.style.overflow = 'auto';
}

/* ===============================
 FULLSCREEN
================================ */
function toggleFullscreen(){

  const shell = document.querySelector('.dbz-frame-shell');

  if (!document.fullscreenElement) {
    shell.requestFullscreen().catch(err => {
      console.log(err);
    });
  } else {
    document.exitFullscreen();
  }
}

/* ===============================
 ESC CLOSE
================================ */
document.addEventListener('keydown', (e)=>{
  if(e.key === 'Escape'){
    closeDbzHub();
  }
});

/* ===============================
 CLICK OUTSIDE CLOSE
================================ */
document.getElementById('dbzOverlay')
.addEventListener('click', (e)=>{
  if(e.target.id === 'dbzOverlay'){
    closeDbzHub();
  }
});

/* ===============================
 PREMIUM TOAST
================================ */
function showDbzToast(){

  if(document.querySelector('.dbz-toast')) return;

  const toast = document.createElement('div');

  toast.className = 'dbz-toast';

  toast.innerHTML = `
    <div style="font-size:1.3rem">🚀</div>
    <div>
      <strong>Workspace Ready</strong>
      <span>GitHub Pages interface loaded successfully.</span>
    </div>
  `;

  document.body.appendChild(toast);

  setTimeout(()=>{
    toast.remove();
  },4000);
}
</script>
            



