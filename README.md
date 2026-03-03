
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title> Developer Hub – Widgets & Tools</title>

<link href="https://cdn.jsdelivr.net/npm/tailwindcss@3.4.1/dist/tailwind.min.css" rel="stylesheet">

<style>
.carousel-container{
  display:flex; overflow-x:auto; scroll-snap-type:x mandatory;
  gap:20px; padding:20px;
}
.carousel-card{
  min-width:320px; max-width:320px;
  background:#fff; border-radius:16px;
  box-shadow:0 8px 25px rgba(0,0,0,.15);
  scroll-snap-align:center;
  transition:.3s; position:relative;
}
.carousel-card:hover{transform:translateY(-5px)}

.badge{
  position:absolute; top:12px; left:12px;
  padding:4px 10px; font-size:11px; font-weight:700;
  border-radius:999px; color:#fff; text-transform:uppercase;
}
.badge-new{background:#22c55e}
.badge-popular{background:#ef4444}
.badge-featured{background:#3b82f6}

/* MODALS */
.modal-bg{
  display:none; position:fixed; inset:0;
  background:rgba(0,0,0,.7);
  backdrop-filter:blur(6px);
  justify-content:center; align-items:center;
  z-index:9999;
}
.modal-box{
  width:92%; height:92%;
  background:#fff; border-radius:16px;
  overflow:hidden; position:relative;
}
iframe{width:100%; height:100%; border:none}

.modal-controls{
  position:absolute; top:10px; left:10px;
  display:flex; gap:8px; z-index:10;
}
.ctrl-btn{
  background:rgba(0,0,0,.75);
  color:#fff; padding:6px 10px;
  border-radius:8px; font-size:12px;
  font-weight:700; cursor:pointer;
}

/* MINI LAUNCHER */
#mini-launcher{
  position:fixed;
  right:16px;
  bottom:50%;
  transform:translateY(-50%);
  width:40px;height:40px;
  background:#16a34a;
  color:#fff;
  border-radius:50%;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:20px;
  cursor:pointer;
  z-index:99999;
}
#mini-panel{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.7);
  z-index:99998;
}
#mini-box{
  position:absolute;
  inset:14px;
  background:#fff;
  border-radius:16px;
  display:flex;
  flex-direction:column;
  overflow:hidden;
}
#mini-tabs{
  display:flex;
  gap:8px;
  padding:8px;
  background:#f1f5f9;
}
#mini-tabs button{
  padding:6px 12px;
  border:none;
  border-radius:999px;
  font-size:12px;
  background:#e5e7eb;
  cursor:pointer;
}
#mini-tabs button.active{
  background:#16a34a;
  color:#fff;
}
</style>
</head>

<body class="bg-gray-100">

<header class="text-center py-8">
  <h1 class="text-3xl font-bold">🚀 Developer Hub</h1>
  <p class="text-gray-600 mt-2">
    Widgets, tools, templates & creative resources for Bloggers, Creators & Developers
  </p>
</header>

<div class="carousel-container">
  <div id="carousel"></div>
</div>

<script>
const projects=[
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

<!-- MINI MULTI-TAB LAUNCHER -->
<div id="mini-launcher">☰</div>

<div id="mini-panel">
  <div id="mini-box">
    <div class="modal-controls">
      <div class="ctrl-btn" onclick="miniBack()">⟵</div>
      <div class="ctrl-btn" onclick="miniForward()">⟶</div>
      <div class="ctrl-btn" onclick="toggleFS('mini-box')">⛶</div>
      <div class="ctrl-btn" onclick="closeMini()">✕</div>
    </div>
    <div id="mini-tabs">
      <button onclick="openMini(0)" class="active">Home</button>
      <button onclick="openMini(1)">Docs</button>
    </div>
    <iframe id="miniFrame"></iframe>
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

/* MINI LAUNCHER LOGIC */
const miniUrls=[
 "https://form.svhrt.com/60f4a0aeedc1993c8c7b3989",
 "https://docs.google.com/document/d/1OfyxaiFRlRhu736Ayr8NZ_ieaNZoS5nNrhHggO63Ixg/edit?usp=drivesdk"
];

const miniPanel=document.getElementById("mini-panel");
const miniFrame=document.getElementById("miniFrame");
const miniTabs=document.querySelectorAll("#mini-tabs button");

document.getElementById("mini-launcher").onclick=()=>{
 miniPanel.style.display="block";
 openMini(0);
};

function openMini(i){
 miniFrame.src=miniUrls[i];
 miniTabs.forEach(b=>b.classList.remove("active"));
 miniTabs[i].classList.add("active");
}
function closeMini(){
 miniPanel.style.display="none";
 miniFrame.src="";
}
function miniBack(){ try{miniFrame.contentWindow.history.back()}catch(e){} }
function miniForward(){ try{miniFrame.contentWindow.history.forward()}catch(e){} }

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
