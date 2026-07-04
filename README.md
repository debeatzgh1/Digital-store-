
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
         href="https://docs.google.com/document/d/1jDfbRKcmrtGnWRMPQnp8WqCZ-1y5waoI/preview"
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
      src="https://docs.google.com/document/d/1jDfbRKcmrtGnWRMPQnp8WqCZ-1y5waoI/preview"
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
    frame.src = url;

    // Update external button
    externalBtn.href = url;

  };

})();
</script>
