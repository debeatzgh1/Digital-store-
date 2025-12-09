<!-- 🌟 Floating Launcher Button (Left Middle) -->
<style>
  .launcher-btn {
      position: fixed;
      left: 10px;
      top: 50%;
      transform: translateY(-50%);
      z-index: 99999;
      background: #2563eb;
      color: #fff;
      padding: 6px 10px;
      font-size: 11px;
      font-weight: 700;
      border-radius: 6px;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0,0,0,0.25);
      animation: pulse 2.2s infinite ease-in-out;
  }

  @keyframes pulse {
    0% { transform: translateY(-50%) scale(1); }
    50% { transform: translateY(-50%) scale(1.06); }
    100% { transform: translateY(-50%) scale(1); }
  }

  /* Modal Backdrop */
  #iframe-modal {
      display: none;
      position: fixed;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      z-index: 99998;
      backdrop-filter: blur(4px);
  }

  /* Modal Window */
  .modal-box {
      position: relative;
      width: 90%;
      height: 88%;
      background: #fff;
      margin: 3% auto;
      border-radius: 14px;
      overflow: hidden;
      box-shadow: 0 8px 25px rgba(0,0,0,0.35);
      animation: fadeIn 0.4s ease-out;
  }

  @keyframes fadeIn {
      0% {opacity:0; transform: translateY(30px);}
      100% {opacity:1; transform: translateY(0);}
  }

  .close-modal {
      position: absolute;
      top: 10px;
      right: 15px;
      font-size: 28px;
      font-weight: bold;
      color: #333;
      cursor: pointer;
      z-index: 200;
  }

  .close-modal:hover { color: red; }

  #modal-iframe {
      width: 100%;
      height: 100%;
      border: none;
  }
</style>

<!-- Floating Button -->
<div class="launcher-btn" id="openLauncher">Menu</div>

<!-- Modal -->
<div id="iframe-modal">
  <div class="modal-box">
      <span class="close-modal" id="closeModal">&times;</span>
      <iframe id="modal-iframe"></iframe>
  </div>
</div>

<script>
document.getElementById("openLauncher").addEventListener("click", function() {
    document.getElementById("iframe-modal").style.display = "block";
    document.getElementById("modal-iframe").src = "#carousel";
});

document.getElementById("closeModal").addEventListener("click", function() {
    document.getElementById("iframe-modal").style.display = "none";
    document.getElementById("modal-iframe").src = "";
});

document.getElementById("iframe-modal").addEventListener("click", function(e) {
    if (e.target.id === "iframe-modal") {
        document.getElementById("iframe-modal").style.display = "none";
        document.getElementById("modal-iframe").src = "";
    }
});
</script>
