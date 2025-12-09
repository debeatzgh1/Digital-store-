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

<!-- TEMPLATE FOR EACH CARD -->
<script>
const projects = [
  {repo:"Ai-quiz", title:"AI Quiz Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251115-064239_16091878416894258095.png"},
  {repo:"curly-chainsaw", title:"HTML Script Preview Editor", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251117-062730_12400543406935180859.png"},
  {repo:"debeatzgh", title:"Personal Dev Portfolio Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/1763148379311_1619032177476517720.jpg"},
  {repo:"-Interactive-Knowledge-Quizzes", title:"Knowledge Quiz System", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251121-103715_12380909417515729112.png"},
  {repo:"menu-widget-", title:"Menu Floating Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/screenshot_20251130-1208252190938125820625163.png"},
  {repo:"Decode-AI-starter-kit-", title:"Decode AI Starter Kit", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/screenshot_20251206-065712_18880183932568216810.png"},
  {repo:"-My-Brand-Online-Digital-Products-Affiliate-Shop", title:"Digital Products Affiliate Shop", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/imagine_15372372473219325794330965895770459.jpg"},
  {repo:"Digital-Creator-s-Essential-Guides-Tools", title:"Digital Creator Essential Guides", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernminimallayoutwithafloatingdockofcolorfulroundicons28patreonbloggergithub29ontherightsideofacleanwebpagemockup6676994054500999142.jpg"},
  {repo:"Docs-Carousel-for-Blogger", title:"Documentation Carousel", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticcatalogcoverthumbnailfeaturingagridoffloatingbrowserwindowsandappcardseachwithsmalliconslikebloggergithubshoppingcartchatbubbleandnewsletterenvelope6320208726725.jpg"},
  {repo:"-Floating-Dock-Smart-Iframe-Modal", title:"Smart Floating Iframe Dock", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg"},
  {repo:"Sliding-Newsletter-Signup-Widget-with-Pulse-Animation", title:"Newsletter Slider Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/minimalistbusinessiconthemealaptopwithdollarsignsorgrowtharrows4197483127374475983.jpg"},
  {repo:"PowerPoint-carousel-widget", title:"PowerPoint Carousel Widget", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createacleanandmodernflat-stylethumbnailforaweb-basedtoolcalledhtmlpagegeneratorforblogger322282329178022614.jpg"},
  {repo:"Blogger-iframe-embed-generator", title:"Blogger Iframe Embed Generator", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createavibranteye-catchingyoutubeblogthumbnailfeaturingafloatingquizpop-upicononadigitalblogpage5084708667809205788.jpg"},
  {repo:"firebase-front-end-components", title:"Firebase Front-End UI Components", thumb:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createatoolthatgeneratesiframeorcard-styleembedsforindividualbloggerpostscompletewiththumbnailtitleandreadmorebuttonforcross-blogpromotion754077096311972631.jpg"},
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
        <p class="text-gray-600 text-sm mb-4">A modern widget/tool built for creators, bloggers, and developers. Explore, preview, and collaborate on GitHub.</p>

        <div class="flex gap-3 mt-3">
          <button onclick="openPreview('https://debeatzgh1.github.io/${p.repo}/')" class="bg-emerald-600 text-white px-4 py-2 rounded-lg w-1/2">Preview</button>

          <a href="https://github.com/debeatzgh1/${p.repo}" target="_blank" class="bg-blue-600 text-white px-4 py-2 rounded-lg w-1/2 text-center">Collaborate</a>
        </div>
      </div>
    </div>
  `;
});
</script>

</div>

<!-- GLOBAL ACTION BUTTONS -->
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


<style>
  /* 🌟 Fade Slide Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateY(20px); }
    100% { opacity: 1; transform: translateY(0); }
  }

  /* ❤️ Heartbeat Animation */
  @keyframes heartbeat {
    0% { transform: scale(1); }
    25% { transform: scale(1.05); }
    50% { transform: scale(1); }
    75% { transform: scale(1.05); }
    100% { transform: scale(1); }
  }

  /* Iframe Modal Styles */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Create Floating Button Group
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    top: "50%",
    right: "12px",
    transform: "translateY(-50%)",
    zIndex: "9999",
    animation: "heartbeat 2.5s infinite ease-in-out, fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // ⭐ Updated Button — "Build"
  // -------------------------------------------------------
  const button = document.createElement("a");
  button.href = "#";
  button.innerText = "Build";
  Object.assign(button.style, {
    background: "#2563eb",
    color: "#fff",
    padding: "8px 14px",
    borderRadius: "12px",
    textDecoration: "none",
    fontSize: "13px",
    fontWeight: "700",
    boxShadow: "0 3px 8px rgba(0,0,0,0.25)",
    whiteSpace: "nowrap",
  });

  // 🔹 Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;

  document.body.appendChild(modal);

  // 🔹 Button Click → Opens your GitHub Affiliate Shop
  button.addEventListener("click", function (e) {
    e.preventDefault();
    document.getElementById("modal-iframe").src = "https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/";
    document.getElementById("iframe-modal").style.display = "block";
  });

  btnGroup.appendChild(button);
  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in new tab safely
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh1.github.io")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>



<style>
  /* 🌟 Fade Slide Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateY(0) translateX(20px); }
    100% { opacity: 1; transform: translateY(0) translateX(0); }
  }

  /* ❤️ Heartbeat Animation */
  @keyframes heartbeat {
    0% { transform: scale(1); }
    25% { transform: scale(1.08); }
    50% { transform: scale(1); }
    75% { transform: scale(1.08); }
    100% { transform: scale(1); }
  }

  .floating-btn-group {
    animation: fadeSlideUp 0.6s ease-out;
  }

  /* Iframe Modal Styles */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Floating Button at TOP-LEFT
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    top: "20px",          // Top-left positioning
    left: "20px",
    zIndex: "9999",
    animation: "heartbeat 2.5s infinite ease-in-out, fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // 📌 Updates Button
  // -------------------------------------------------------
  const button = document.createElement("a");
  button.href = "#";
  button.innerText = "📌 Updates";
  Object.assign(button.style, {
    background: "#16a34a",
    color: "#fff",
    padding: "12px 24px",
    borderRadius: "30px",
    textDecoration: "none",
    fontSize: "15px",
    fontWeight: "700",
    boxShadow: "0 4px 10px rgba(0,0,0,0.25)",
    whiteSpace: "nowrap",
  });

  // 🔹 Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;

  document.body.appendChild(modal);

  // 🔹 Open Iframe on click
  button.addEventListener("click", function (e) {
    e.preventDefault();
    document.getElementById("modal-iframe").src = "https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/";
    modal.style.display = "block";
  });

  btnGroup.appendChild(button);
  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in a new tab
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh.wordpress.com")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>


<!doctype html>


<style>
  /* 🌟 Floating Button Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateX(-50%) translateY(20px); }
    100% { opacity: 1; transform: translateX(-50%) translateY(0); }
  }

  .floating-btn-group {
    animation: fadeSlideUp 0.6s ease-out;
  }

  .floating-btn-group a:hover {
    transform: scale(1.05);
    transition: transform 0.3s ease;
  }

  /* 🌟 Iframe Modal */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Create Floating Button Group
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    bottom: "16px",
    left: "50%",
    transform: "translateX(-50%)",
    display: "flex",
    gap: "10px",
    zIndex: "9999",
    background: "rgba(0,0,0,0.1)",
    padding: "6px 10px",
    borderRadius: "10px",
    boxShadow: "0 4px 8px rgba(0,0,0,0.2)",
    opacity: "0",
    animation: "fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // ✅ BUTTONS INCLUDING NEW “IDEAS” BUTTON
  // -------------------------------------------------------
  const buttons = [
    {
      text: "🔥 Blog",
      bg: "#1e90ff",
      url: "https://beatzde4.blogspot.com/"
    },
    {
      text: "📌 Feed",
      bg: "#16a34a",
      url: "https://debeatzgh.wordpress.com/"
    },
    {
      text: "💡 Ideas",
      bg: "#c026d3",
      url: "https://msha.ke/debeatzgh"
    }
  ];

  // 🔹 Create Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;
  document.body.appendChild(modal);

  // 🔹 Add Buttons to Page
  buttons.forEach(function (btn) {
    const a = document.createElement("a");
    a.href = "#";
    a.innerText = btn.text;
    Object.assign(a.style, {
      background: btn.bg,
      color: "#fff",
      padding: "8px 14px",
      borderRadius: "20px",
      textDecoration: "none",
      fontSize: "13px",
      fontWeight: "600",
      whiteSpace: "nowrap",
      boxShadow: "0 2px 6px rgba(0, 0, 0, 0.2)",
      transition: "opacity 0.3s ease, transform 0.3s ease"
    });

    a.addEventListener("click", function (e) {
      e.preventDefault();
      document.getElementById("modal-iframe").src = btn.url;
      document.getElementById("iframe-modal").style.display = "block";
    });

    btnGroup.appendChild(a);
  });

  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in new tab safely
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh.wordpress.com")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>
# 🌐 Debeatzgh Projects & Tools Hub

Welcome to my collection of **modern digital projects, AI-powered tools, and Blogger widgets**.
This hub is designed to help creators, entrepreneurs, and tech enthusiasts **explore, build, and scale** their digital presence with professional tools.

---

## 📚 Featured Projects

### 1. 📝 Docs Carousel for Blogger

![Docs Carousel](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticcatalogcoverthumbnailfeaturingagridoffloatingbrowserwindowsandappcardseachwithsmalliconslikebloggergithubshoppingcartchatbubbleandnewsletterenvelope6320208726725.jpg)
A responsive and elegant carousel widget to showcase your documents in Blogger.
🔗 [Explore Project](https://github.com/debeatzgh1/Docs-Carousel-for-Blogger)

---

### 2. 🤖 AI Tech Mastery Hub

![AI Hub](https://debeatzgh.wordpress.com/wp-content/uploads/2025/09/asleekandmoderngoogleclassroombannerfortechaihubfeaturingfuturisticdigitalelements261807892942313727.jpg)
A curated hub of **AI resources, tools, and strategies** to master digital innovation.
🔗 [Explore Project](https://github.com/debeatzgh1/AI-Tech-Mastery-Hub-)

---

### 3. 🌍 Tech and AI Hub

![Tech Hub](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/wp-17550753518668254821238386385497.jpg)
A modern knowledge space offering guides, tutorials, and resources on AI and technology.
🔗 [Explore Project](https://github.com/debeatzgh1/Tech-and-AI-Hub-)

---

### 4. 🏠 Home Project

![Home UI](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg)
Clean, responsive homepage template for Blogger and web creators.
🔗 [Explore Project](https://github.com/debeatzgh1/Home-)

---

### 5. 🛒 My Brand Online – Affiliate Shop

![Affiliate Shop](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg)
A professional **digital products shop** for affiliate marketing & online income.
🔗 [Explore Project](https://github.com/debeatzgh1/-My-Brand-Online-Digital-Products-Affiliate-Shop)

---

### 6. ✉️ Sliding Newsletter Widget (Pulse Animation)

![Newsletter](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernuidashboardonalaptopscreenshowingastylishfloatinggreenbuttonlabeledaddservicecard8118683982414859133.jpg)
Capture emails in style with this animated **sliding newsletter signup widget**.
🔗 [Explore Project](https://github.com/debeatzgh1/Sliding-Newsletter-Signup-Widget-with-Pulse-Animation)

---

### 7. 💼 The Ultimate Guide to Side Hustle

![Side Hustle](https://debeatzgh.wordpress.com/wp-content/uploads/2025/09/facebookposttemplateprompt-digitalmarketingthumbnailidea28attachimage29acleanmoderngraphicwithtextoverlaymasterdigitalmarketingiconsofinstagramanalyticstargetwebsiteemail2812944137932373.jpg)
A **comprehensive digital guide** packed with strategies for launching and growing your side hustle.
🔗 [Explore Project](https://github.com/debeatzgh1/The-Ultimate-Guide-to-Side-Hustle)

---

### 8. 🎨 Personal Portfolio Site

![Portfolio](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/adarkthemepreviewofapersonalportfoliowebsitewithglowingblueaccentsprojectshowcasecardsandamodernnavigationbar8701627220551173592.jpg)
A sleek, modern **personal portfolio website** template for professionals & freelancers.
🔗 [Explore Project](https://github.com/debeatzgh1/Personal-Portfolio-site-)

---

### 9. 📖 Floating Flashcards Widget

![Flashcards](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/wp-17550753129553143934409952739598.jpg)
Interactive flashcards for Blogger – perfect for **study, tutorials, and knowledge sharing.**
🔗 [Explore Project](https://github.com/debeatzgh1/Floating-Flashcards-Widget)

---

### 10. 🚀 Floating Dock Smart Iframe Modal

![Dock](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernminimallayoutwithafloatingdockofcolorfulroundicons28patreonbloggergithub29ontherightsideofacleanwebpagemockup6676994054500999142.jpg)
A minimal floating dock + iframe modal to **embed external content seamlessly.**
🔗 [Explore Project](https://github.com/debeatzgh1/-Floating-Dock-Smart-Iframe-Modal)

---

### 11. 🖥 Blogger iFrame Embed Generator

![Embed Tool](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createacleanandmodernflat-stylethumbnailforaweb-basedtoolcalledhtmlpagegeneratorforblogger322282329178022614.jpg)
Generate clean **iframe embed codes** for your Blogger site easily.
🔗 [Explore Project](https://github.com/debeatzgh1/Blogger-iframe-embed-generator)

---

### 12. 🎠 Carousel for Blogger

![Carousel](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designacleanmodernthumbnailforabloggerproductscarouseltool1711994558720457535.jpg)
A modern carousel widget for showcasing products or posts on Blogger.
🔗 [Explore Project](https://github.com/debeatzgh1/Carousel-for-blogger-)

---

### 13. ⏱ Improve Productivity with AI

![Productivity](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designacleanflat-layofalaptopshowingcodeoraidiagramspairedwithanotebookandcoffee-capturingproductivityanddigitalcreativity3607438369271002624.jpg)
An AI-powered web app project to **boost personal productivity and creativity.**
🔗 [Explore Project](https://github.com/debeatzgh1/Improve-productivity-with-AI-Web-App-project-)

---

### 14. 🧩 TechAdapt – Strategies for Startups & Individuals

![TechAdapt](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amoderndigitalbloggersittingatasleekdeskwithaglowinglaptopsurroundedbyiconslikewordpresspendollarsignandgrowthchart2305198289795713004.jpg)
Smart **digital adaptation strategies** for startups, businesses, and individuals.
🔗 [Explore Project](https://github.com/debeatzgh1/TechAdapt-Solutions-Strategies-for-Modern-Startups-and-Individuals)

---

### 15. 🛍 Blogger Product Carousel + WhatsApp Button

![Product Carousel](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticlogoforadigitaltoolcalledall-in-onefloatinginfomenuforblogger5444122951694103302.jpg)
Showcase your products in a sleek carousel with a **WhatsApp floating button** for instant engagement.
🔗 [Explore Project](https://github.com/debeatzgh1/Blogger-Product-Carousel-with-WhatsApp-Floating-Button)

---

## 📌 Final Note

These projects are created to empower **bloggers, creators, and digital entrepreneurs** with easy-to-use, professional, and modern tools.

💡 Feel free to fork, contribute, or share feedback on any project.
📩 For collaboration, reach out anytime!

---

✨ **Which project do you find most useful for your own work?** Drop your feedback—it helps shape future tools.

# [Portfolio](https://debeatzgh1.github.io/Personal-Portfolio-site-/)
