<!DOCTYPE html>
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
}
.carousel-card:hover { transform: translateY(-5px); }

/* Modal */
.modal-bg {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.65);
  backdrop-filter: blur(6px);
  justify-content: center;
  align-items: center;
  z-index: 9999;
}
.modal-box {
  width: 90%; height: 90%;
  background: white;
  border-radius: 16px;
  overflow: hidden;
}
iframe { width: 100%; height: 100%; border: none; }

/* Close button */
.close-btn {
  background: red;
  color: white;
  font-weight: bold;
  padding: 10px;
  width: 100%;
  cursor: pointer;
}

/* Floating Buttons */
.floating-bar {
  position: fixed;
  bottom: 20px;
  right: 20px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  z-index: 99999;
}
.float-btn {
  background: #2563eb;
  color: white;
  padding: 14px 20px;
  border-radius: 50px;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 5px 20px rgba(0,0,0,0.25);
}
.float-btn:hover { opacity: 0.85; }
</style>
</head>

<body class="bg-gray-100">

<header class="text-center py-8">
  <h1 class="text-3xl font-bold text-gray-800">🚀 Debeatzgh Developer Hub</h1>
  <p class="text-lg text-gray-600 mt-3">A collection of powerful widgets, templates, tools, and creative resources for Bloggers, Creators, and Developers.</p>
</header>

<!-- CAROUSEL -->
<div class="carousel-container">

<script>
const projects = [
  {repo:"Ai-quiz", title:"AI Quiz Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251115-064239_16091878416894258095.png"},
  {repo:"curly-chainsaw", title:"HTML Script Preview Editor", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251117-062730_12400543406935180859.png"},
  {repo:"debeatzgh", title:"Personal Dev Portfolio Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/1763148379311_1619032177476517720.jpg"},
  {repo:"-Interactive-Knowledge-Quizzes", title:"Knowledge Quiz System", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251121-103715_12380909417515729112.png"},
  {repo:"menu-widget-", title:"Menu Floating Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/screenshot_20251130-1208252190938125820625163.png"},
  {repo:"Decode-AI-starter-kit-", title:"Decode AI Starter Kit", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/screenshot_20251206-065712_18880183932568216810.png"},
  {repo:"-My-Brand-Online-Digital-Products-Affiliate-Shop", title:"Affiliate Digital Shop", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/imagine_15372372473219325794330965895770459.jpg"},
  {repo:"Digital-Creator-s-Essential-Guides-Tools", title:"Digital Creator Guides", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernminimallayoutwithafloatingdockofcolorfulroundicons28patreonbloggergithub29ontherightsideofacleanwebpagemockup6676994054500999142.jpg"},
  {repo:"Docs-Carousel-for-Blogger", title:"Documentation Carousel", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticcatalogcoverthumbnailfeaturingagridoffloatingbrowserwindowsandappcardseachwithsmalliconslikebloggergithubshoppingcartchatbubbleandnewsletterenvelope6320208726725.jpg"},
  {repo:"-Floating-Dock-Smart-Iframe-Modal", title:"Floating Iframe Dock", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg"},
  {repo:"Sliding-Newsletter-Signup-Widget-with-Pulse-Animation", title:"Newsletter Slider", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/minimalistbusinessiconthemealaptopwithdollarsignsorgrowtharrows4197483127374475983.jpg"},
  {repo:"PowerPoint-carousel-widget", title:"PowerPoint Carousel Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createacleanandmodernflat-stylethumbnailforaweb-basedtoolcalledhtmlpagegeneratorforblogger322282329178022614.jpg"},
  {repo:"Blogger-iframe-embed-generator", title:"Iframe Embed Generator", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createavibranteye-catchingyoutubeblogthumbnailfeaturingafloatingquizpop-upicononadigitalblogpage5084708667809205788.jpg"},
  {repo:"firebase-front-end-components", title:"Firebase Components", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createatoolthatgeneratesiframeorcard-styleembedsforindividualbloggerpostscompletewiththumbnailtitleandreadmorebuttonforcross-blogpromotion754077096311972631.jpg"},
  {repo:"Custom-Blogger-Theme-for-with-Dynamic-Post-Loading-and-Logo-", title:"Custom Blogger Theme", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg"}
];
</script>

<div id="carousel"></div>

<script>
const container = document.getElementById("carousel");

projects.forEach(p => {
  container.innerHTML += `
    <div class="carousel-card">
      <img src="${p.thumb}" class="w-full h-40 object-cover"/>
      <div class="p-5">
        <h3 class="text-xl font-bold text-gray-800 mb-2">${p.title}</h3>
        <p class="text-gray-600 text-sm mb-4">Explore modern widgets, tools, templates, and developer utilities.</p>

        <div class="flex gap-3 mt-3">
          
          <!-- GREEN PREVIEW BUTTON -->
          <button onclick="openPreview('https://debeatzgh1.github.io/${p.repo}/')" 
            class="px-4 py-2 rounded-lg w-1/2 text-white font-bold"
            style="background:#10B981;">
            Preview
          </button>

          <!-- RED COLLABORATE BUTTON -->
          <a href="https://github.com/debeatzgh1/${p.repo}" target="_blank"
            class="px-4 py-2 rounded-lg w-1/2 text-center text-white font-bold"
            style="background:#DC2626;">
            Repo
          </a>
        </div>
      </div>
    </div>
  `;
});
</script>

</div>

<!-- FLOATING ACTION BUTTONS -->
<div class="floating-bar">
  <a href="https://github.com/apps/dkonsult" target="_blank" class="float-btn bg-purple-600">⭐ Sign Up on GitHub</a>

  <div class="float-btn bg-orange-600" onclick="openForm()">📨 Suggestions Form</div>
</div>

<!-- PREVIEW MODAL -->
<div class="modal-bg" id="previewModal">
  <div class="modal-box">
    <iframe id="previewFrame"></iframe>
    <button class="close-btn" onclick="closePreview()">Close</button>
  </div>
</div>

<!-- SUGGESTION FORM MODAL -->
<div class="modal-bg" id="formModal">
  <div class="modal-box">
    <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform?embedded=true"></iframe>
    <button class="close-btn" onclick="closeForm()">Close</button>
  </div>
</div>

<script>
function openPreview(url){
  document.getElementById("previewFrame").src = url;
  document.getElementById("previewModal").style.display = "flex";
}
function closePreview(){
  document.getElementById("previewModal").style.display = "none";
  document.getElementById("previewFrame").src = "";
}

function openForm(){
  document.getElementById("formModal").style.display = "flex";
}
function closeForm(){
  document.getElementById("formModal").style.display = "none";
}
</script>

</body>
</html>
