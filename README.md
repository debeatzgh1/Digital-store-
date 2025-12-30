
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debeatzgh Developer Hub – Widgets & Tools</title>
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@3.4.1/dist/tailwind.min.css" rel="stylesheet">

<style>
.carousel-container{
  display:flex;
  overflow-x:auto;
  scroll-snap-type:x mandatory;
  gap:20px;
  padding:20px;
}
.carousel-card{
  min-width:320px;
  max-width:320px;
  background:#fff;
  border-radius:16px;
  box-shadow:0 8px 25px rgba(0,0,0,.15);
  scroll-snap-align:center;
  overflow:hidden;
  position:relative;
  transition:.3s;
}
.carousel-card:hover{transform:translateY(-5px)}

.badge{
  position:absolute;
  top:12px;left:12px;
  padding:4px 10px;
  font-size:11px;
  font-weight:700;
  border-radius:999px;
  color:#fff;
  text-transform:uppercase;
}
.badge-new{background:#22c55e}
.badge-popular{background:#ef4444}
.badge-featured{background:#3b82f6}

.modal-bg{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.7);
  backdrop-filter:blur(6px);
  justify-content:center;
  align-items:center;
  z-index:9999;
}
.modal-box{
  width:92%;
  height:92%;
  background:#fff;
  border-radius:16px;
  overflow:hidden;
  position:relative;
}
iframe{width:100%;height:100%;border:none}

.modal-controls{
  position:absolute;
  top:10px;left:10px;
  display:flex;
  gap:8px;
  z-index:10;
}
.ctrl-btn{
  background:rgba(0,0,0,.7);
  color:#fff;
  padding:6px 10px;
  border-radius:8px;
  font-size:12px;
  font-weight:700;
  cursor:pointer;
}

.floating-bar{
  position:fixed;
  bottom:18px;
  right:18px;
  z-index:99999;
}
.float-btn{
  background:#f97316;
  color:#fff;
  padding:10px 14px;
  border-radius:999px;
  font-size:14px;
  font-weight:600;
  cursor:pointer;
}
</style>
</head>

<body class="bg-gray-100">

<header class="text-center py-8">
  <h1 class="text-3xl font-bold">🚀 Debeatzgh Developer Hub</h1>
  <p class="text-gray-600 mt-2">
    Widgets, tools, templates & creative resources for Bloggers, Creators & Developers
  </p>
</header>

<div class="carousel-container">
  <div id="carousel"></div>
</div>

<script>
const projects = [
 {repo:"Ai-quiz",title:"AI Quiz Widget",badge:"new"},
 {repo:"curly-chainsaw",title:"HTML Script Preview Editor",badge:"popular"},
 {repo:"debeatzgh",title:"Personal Dev Portfolio Widget",badge:"featured"},
 {repo:"-Interactive-Knowledge-Quizzes",title:"Knowledge Quiz System",badge:"popular"},
 {repo:"menu-widget-",title:"Menu Floating Widget",badge:"featured"},
 {repo:"Decode-AI-starter-kit-",title:"Decode AI Starter Kit",badge:"new"},
 {repo:"-My-Brand-Online-Digital-Products-Affiliate-Shop",title:"Affiliate Digital Shop",badge:"featured"},
 {repo:"Digital-Creator-s-Essential-Guides-Tools",title:"Digital Creator Guides",badge:"popular"},
 {repo:"Docs-Carousel-for-Blogger",title:"Documentation Carousel",badge:"new"},
 {repo:"-Floating-Dock-Smart-Iframe-Modal",title:"Floating Iframe Dock",badge:"featured"},
 {repo:"Sliding-Newsletter-Signup-Widget-with-Pulse-Animation",title:"Newsletter Slider"},
 {repo:"PowerPoint-carousel-widget",title:"PowerPoint Carousel Widget"},
 {repo:"Blogger-iframe-embed-generator",title:"Iframe Embed Generator"},
 {repo:"firebase-front-end-components",title:"Firebase Components"},
 {repo:"Custom-Blogger-Theme-for-with-Dynamic-Post-Loading-and-Logo-",title:"Custom Blogger Theme"}
];

const container=document.getElementById("carousel");

projects.forEach(p=>{
 container.innerHTML+=`
  <div class="carousel-card">
    ${p.badge?`<span class="badge badge-${p.badge}">${p.badge}</span>`:""}
    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticcatalogcoverthumbnailfeaturingagridoffloatingbrowserwindowsandappcardseachwithsmalliconslikebloggergithubshoppingcartchatbubbleandnewsletterenvelope6320208726725.jpg"
         class="w-full h-40 object-cover">
    <div class="p-5">
      <h3 class="text-xl font-bold mb-2">${p.title}</h3>
      <p class="text-sm text-gray-600 mb-4">
        Explore modern widgets, tools & templates.
      </p>
      <div class="flex gap-3">
        <button onclick="openPreview('https://debeatzgh1.github.io/${p.repo}/')"
          class="w-1/2 px-4 py-2 rounded-lg text-white font-bold bg-emerald-500">
          Preview
        </button>
        <a href="https://github.com/debeatzgh1/${p.repo}" target="_blank"
          class="w-1/2 px-4 py-2 rounded-lg text-white font-bold bg-red-600 text-center">
          Repo
        </a>
      </div>
    </div>
  </div>`;
});
</script>

<!-- FLOATING MILKSHAKE -->
<div class="floating-bar">
  <div class="float-btn" onclick="openMilkshake()">🌐</div>
</div>

<!-- PREVIEW MODAL -->
<div class="modal-bg" id="previewModal">
  <div class="modal-box" id="previewBox">
    <div class="modal-controls">
      <div class="ctrl-btn" onclick="toggleFS('previewBox')">⛶ Fullscreen</div>
      <div class="ctrl-btn" onclick="closePreview()">✕ Close</div>
    </div>
    <iframe id="previewFrame"></iframe>
  </div>
</div>

<!-- MILKSHAKE MODAL -->
<div class="modal-bg" id="milkshakeModal">
  <div class="modal-box" id="milkshakeBox">
    <div class="modal-controls">
      <div class="ctrl-btn" onclick="toggleFS('milkshakeBox')">⛶ Fullscreen</div>
      <div class="ctrl-btn" onclick="closeMilkshake()">✕ Close</div>
    </div>
    <iframe src="https://debeatzgh1.github.io/Home-/"></iframe>
  </div>
</div>

<script>
function openPreview(url){
 previewFrame.src=url;
 previewModal.style.display="flex";
}
function closePreview(){
 previewModal.style.display="none";
 previewFrame.src="";
 exitFS();
}
function openMilkshake(){
 milkshakeModal.style.display="flex";
}
function closeMilkshake(){
 milkshakeModal.style.display="none";
 exitFS();
}
function toggleFS(id){
 const el=document.getElementById(id);
 if(!document.fullscreenElement){el.requestFullscreen();}
 else{document.exitFullscreen();}
}
function exitFS(){
 if(document.fullscreenElement){document.exitFullscreen();}
}
</script>

</body>
</html>
