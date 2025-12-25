
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debeatzgh Developer Hub – Widgets & Tools</title>
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@3.4.1/dist/tailwind.min.css" rel="stylesheet">

<style>
/* Carousel */
.carousel-container {
  display: flex;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  gap: 20px;
  padding: 20px;
}
.carousel-card {
  min-width: 320px;
  max-width: 320px;
  background: white;
  border-radius: 16px;
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
  scroll-snap-align: center;
  overflow: hidden;
  transition: transform 0.3s;
  position: relative;
}
.carousel-card:hover { transform: translateY(-5px); }

/* Badges */
.badge {
  position: absolute;
  top: 12px;
  left: 12px;
  padding: 4px 10px;
  font-size: 11px;
  font-weight: 700;
  border-radius: 999px;
  color: white;
  text-transform: uppercase;
  box-shadow: 0 4px 10px rgba(0,0,0,0.25);
}
.badge-new { background:#22c55e; }
.badge-popular { background:#ef4444; }
.badge-featured { background:#3b82f6; }

/* Modal */
.modal-bg {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.7);
  backdrop-filter: blur(6px);
  justify-content: center;
  align-items: center;
  z-index: 9999;
}
.modal-box {
  width: 92%;
  height: 92%;
  background: white;
  border-radius: 16px;
  overflow: hidden;
  position: relative;
}

/* iframe */
iframe {
  width: 100%;
  height: 100%;
  border: none;
}

/* Modal Controls */
.modal-controls {
  position: absolute;
  top: 10px;
  left: 10px;
  display: flex;
  gap: 8px;
  z-index: 10;
}
.ctrl-btn {
  background: rgba(0,0,0,0.7);
  color: white;
  padding: 6px 10px;
  border-radius: 8px;
  font-size: 12px;
  font-weight: bold;
  cursor: pointer;
}
.ctrl-btn:hover { opacity: 0.85; }

/* Floating Button */
.floating-bar {
  position: fixed;
  bottom: 18px;
  right: 18px;
  z-index: 99999;
}
.float-btn {
  background:#f97316;
  color:white;
  padding:10px 14px;
  border-radius:999px;
  font-size:14px;
  font-weight:600;
  cursor:pointer;
  box-shadow:0 5px 15px rgba(0,0,0,0.25);
}
.float-btn:hover { opacity:0.9; }
</style>
</head>

<body class="bg-gray-100">

<header class="text-center py-8">
  <h1 class="text-3xl font-bold text-gray-800">🚀 Debeatzgh Developer Hub</h1>
  <p class="text-lg text-gray-600 mt-3">
    Widgets, tools, templates, and creative resources for Bloggers, Creators & Developers.
  </p>
</header>

<!-- CAROUSEL -->
<div class="carousel-container">
  <div id="carousel"></div>
</div>

<script>
const projects = [
  {
    repo:"Ai-quiz",
    title:"AI Quiz Widget",
    thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251115-064239_16091878416894258095.png",
    badge:"new"
  },
  {
    repo:"curly-chainsaw",
    title:"HTML Script Preview Editor",
    thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251117-062730_12400543406935180859.png",
    badge:"popular"
  },
  {
    repo:"debeatzgh",
    title:"Personal Dev Portfolio Widget",
    thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/1763148379311_1619032177476517720.jpg",
    badge:"featured"
  }
];

const container = document.getElementById("carousel");

projects.forEach(p => {
  container.innerHTML += `
    <div class="carousel-card">
      ${p.badge ? `<span class="badge badge-${p.badge}">${p.badge}</span>` : ""}

      <img src="${p.thumb}" class="w-full h-40 object-cover">

      <div class="p-5">
        <h3 class="text-xl font-bold text-gray-800 mb-2">${p.title}</h3>
        <p class="text-gray-600 text-sm mb-4">
          Explore modern widgets, tools, templates, and utilities.
        </p>

        <div class="flex gap-3">
          <button onclick="openPreview('https://debeatzgh1.github.io/${p.repo}/')"
            class="px-4 py-2 w-1/2 rounded-lg text-white font-bold"
            style="background:#10B981;">
            Preview
          </button>

          <a href="https://github.com/debeatzgh1/${p.repo}" target="_blank"
            class="px-4 py-2 w-1/2 rounded-lg text-center text-white font-bold"
            style="background:#DC2626;">
            Repo
          </a>
        </div>
      </div>
    </div>
  `;
});
</script>

<!-- FLOATING MILKSHAKE BUTTON -->
<div class="floating-bar">
  <div class="float-btn" onclick="openMilkshake()">🌐 My Links</div>
</div>

<!-- PREVIEW MODAL -->
<div class="modal-bg" id="previewModal">
  <div class="modal-box" id="previewBox">
    <div class="modal-controls">
      <div class="ctrl-btn" onclick="toggleFullscreen()">⛶ Fullscreen</div>
      <div class="ctrl-btn" onclick="closePreview()">✕ Close</div>
    </div>
    <iframe id="previewFrame"></iframe>
  </div>
</div>

<!-- MILKSHAKE MODAL -->
<div class="modal-bg" id="milkshakeModal">
  <div class="modal-box" id="milkshakeBox">
    <div class="modal-controls">
      <div class="ctrl-btn" onclick="toggleFullscreenMilkshake()">⛶ Fullscreen</div>
      <div class="ctrl-btn" onclick="closeMilkshake()">✕ Close</div>
    </div>
    <iframe src="https://msha.ke/debeatzgh"></iframe>
  </div>
</div>

<script>
function openPreview(url){
  previewFrame.src = url;
  previewModal.style.display = "flex";
}

function closePreview(){
  previewModal.style.display = "none";
  previewFrame.src = "";
  exitFullscreen();
}

function openMilkshake(){
  milkshakeModal.style.display = "flex";
}

function closeMilkshake(){
  milkshakeModal.style.display = "none";
  exitFullscreen();
}

function toggleFullscreen(){
  const el = document.getElementById("previewBox");
  fullscreen(el);
}

function toggleFullscreenMilkshake(){
  const el = document.getElementById("milkshakeBox");
  fullscreen(el);
}

function fullscreen(el){
  if (!document.fullscreenElement) {
    el.requestFullscreen();
  } else {
    document.exitFullscreen();
  }
}

function exitFullscreen(){
  if (document.fullscreenElement) {
    document.exitFullscreen();
  }
}
</script>

</body>
</html>
