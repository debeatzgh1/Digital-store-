
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Content Hub</title>

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
  min-width:340px;
  background:#fff;
  border-radius:18px;
  box-shadow:0 10px 30px rgba(0,0,0,.12);
  scroll-snap-align:center;
  overflow:hidden;
  position:relative;
  transition:.3s;
}
.carousel-card:hover{transform:translateY(-6px)}

.badge{
  position:absolute;
  top:12px;left:12px;
  padding:4px 12px;
  font-size:11px;
  font-weight:700;
  border-radius:999px;
  color:#fff;
}
.badge-featured{background:#2563eb}
.badge-popular{background:#16a34a}

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
  width:94%;
  height:92%;
  background:#fff;
  border-radius:18px;
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
  background:rgba(0,0,0,.75);
  color:#fff;
  padding:6px 10px;
  border-radius:8px;
  font-size:12px;
  font-weight:700;
  cursor:pointer;
}

/* Floating Milkshake Button */
.floating-btn{
  position:fixed;
  bottom:18px;
  right:18px;
  background:#f97316;
  color:#fff;
  padding:12px 18px;
  border-radius:999px;
  font-weight:700;
  font-size:14px;
  box-shadow:0 10px 25px rgba(0,0,0,.25);
  cursor:pointer;
  z-index:99999;
}
</style>
</head>

<body class="bg-gray-100">

<header class="text-center py-10">
  <h1 class="text-3xl font-bold">AI & Knowledge Hub</h1>
  <p class="text-gray-600 mt-2 max-w-xl mx-auto">
    Explore AI insights, tutorials, and creator resources in a focused,
    distraction-free reading experience.
  </p>
</header>

<!-- CONTENT CARDS -->
<div class="carousel-container">

  <!-- WORDPRESS -->
  <div class="carousel-card">
    <span class="badge badge-featured">Featured</span>
    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticcatalogcoverthumbnailfeaturingagridoffloatingbrowserwindowsandappcardseachwithsmalliconslikebloggergithubshoppingcartchatbubbleandnewsletterenvelope6320208726725.jpg"
         class="w-full h-44 object-cover">
    <div class="p-6">
      <h3 class="text-xl font-bold mb-2">Build With AI (WordPress)</h3>
      <p class="text-sm text-gray-600 mb-4">
        Deep-dive AI articles, real-world use cases, and step-by-step learning
        resources.
      </p>
      <button onclick="openPreview('https://debeatzgh.wordpress.com/build-with-ai-2/')"
        class="w-full px-4 py-3 rounded-xl text-white font-bold bg-blue-600">
        Open Articles
      </button>
    </div>
  </div>

  <!-- BLOGGER -->
  <div class="carousel-card">
    <span class="badge badge-popular">Popular</span>
    <img src="https://images.unsplash.com/photo-1677442136019-21780ecad995"
         class="w-full h-44 object-cover">
    <div class="p-6">
      <h3 class="text-xl font-bold mb-2">AI Knowledge Blog (Blogger)</h3>
      <p class="text-sm text-gray-600 mb-4">
        Beginner-friendly explanations, decoding AI concepts for creators,
        students, and entrepreneurs.
      </p>
      <button onclick="openPreview('https://debeatzgh2.blogspot.com/p/blog-page_9.html')"
        class="w-full px-4 py-3 rounded-xl text-white font-bold bg-emerald-600">
        Read Blog
      </button>
    </div>
  </div>

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

<!-- FLOATING MILKSHAKE -->
<div class="floating-btn" onclick="openPreview('https://msha.ke/debeatzgh')">
  🌐 My Links
</div>

<script>
const previewModal=document.getElementById("previewModal");
const previewFrame=document.getElementById("previewFrame");

function openPreview(url){
  previewFrame.src=url;
  previewModal.style.display="flex";
}

function closePreview(){
  previewModal.style.display="none";
  previewFrame.src="";
  if(document.fullscreenElement){document.exitFullscreen();}
}

function toggleFS(id){
  const el=document.getElementById(id);
  if(!document.fullscreenElement){el.requestFullscreen();}
  else{document.exitFullscreen();}
}

/* 🔍 Auto-detect ads & external links */
previewFrame.addEventListener("load", ()=>{
  try{
    const doc=previewFrame.contentDocument;
    const links=doc.querySelectorAll("a[href]");
    links.forEach(a=>{
      const href=a.href;
      if(
        !href.includes("debeatzgh.wordpress.com") &&
        !href.includes("debeatzgh2.blogspot.com") &&
        !href.includes("msha.ke")
      ){
        a.setAttribute("target","_blank");
        a.setAttribute("rel","noopener");
      }
    });
  }catch(e){
    console.warn("Cross-domain content: ad handling limited");
  }
});
</script>

</body>
</html>
