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
            






<!-- Live Workspace Embed Component -->
<div class="dbz-embed-container" style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; margin: 20px auto; max-width: 1000px; border-radius: 16px; overflow: hidden; box-shadow: 0 10px 30px rgba(0,0,0,0.08); border: 1px solid #e2e8f0; background: #ffffff;">
    
    <!-- Control Header -->
    <div style="background: #f8fafc; padding: 12px 20px; border-b: 1px solid #e2e8f0; display: flex; justify-content: space-between; items-center: center; flex-wrap: wrap; gap: 10px;">
        <div style="display: flex; items-center: center; gap: 8px;">
            <span style="width: 10px; height: 10px; border-radius: 50%; background: #ef4444; display: inline-block;"></span>
            <span style="width: 10px; height: 10px; border-radius: 50%; background: #eab308; display: inline-block;"></span>
            <span style="width: 10px; height: 10px; border-radius: 50%; background: #22c55e; display: inline-block;"></span>
            <span style="font-size: 13px; font-weight: 600; color: #475569; margin-left: 10px;">A central collaboration platform for code, resources, ideas, and projects in music technology, digital entrepreneurship, and online business. This repo is designed for contributors to work together, launch new initiatives, and support each other’s creative and professional growth. All creators, developers, and digital hustle </span>
        </div>
        <div>
            <a href="https://debeatzgh1.github.io/1/" target="_blank" style="font-size: 12px; font-weight: 600; color: #2563eb; text-decoration: none; padding: 6px 12px; border-radius: 6px; background: #eff6ff; transition: all 0.2s;" onmouseover="this.style.background='#dbeafe'" onmouseout="this.style.background='#eff6ff'">
                View templates & edit <span style="font-size: 10px; margin-left: 2px;">↗</span>
            </a>
        </div>
    </div>

    <!-- Active Sandbox Viewport -->
    <div style="position: relative; width: 100%; height: 750px; background: #f1f5f9;">
        <!-- CSS-Only Spinner (Hidden automatically once iframe mounts content threads) -->
        <div id="dbz-embed-loader" style="position: absolute; inset: 0; display: flex; flex-direction: column; align-items: center; justify-content: center; background: #ffffff; z-index: 5;">
            <div style="width: 40px; height: 40px; border: 3px solid #cbd5e1; border-top-color: #2563eb; border-radius: 50%; animation: dbz-spin 0.8s linear infinite;"></div>
            <p style="margin-top: 12px; font-size: 13px; color: #64748b; font-weight: 500;">Establishing portal attachment...</p>
        </div>

        <!-- Embedded Frame Target Node -->
        <iframe 
            src="https://debeatzgh1.github.io/Pages-/" 
            style="width: 100%; height: 80%; border: none; opacity: 0; transition: opacity 0.3s ease;" 
            allow="geolocation; microphone; camera; midi; encrypted-media;"
            sandbox="allow-forms allow-modals allow-popups allow-scripts allow-same-origin allow-top-navigation-by-user-activation"
            onload="document.getElementById('dbz-embed-loader').style.display='none'; this.style.opacity='1';">
        </iframe>
    </div>
</div>

<!-- Essential Animation Styles Definition -->
<style>
    @keyframes dbz-spin {
        to { transform: rotate(360deg); }
    }
</style>


