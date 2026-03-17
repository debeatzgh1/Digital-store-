
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Premium Resource Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap');

        :root {
            --accent: #FF1493;
            --glass: rgba(15, 15, 20, 0.85);
            --border: rgba(255, 255, 255, 0.1);
        }

        body {
            background-color: #050505;
            color: #fff;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
        }

        /* --- 1. TOP FLOATING BANNER --- */
        .top-banner {
            position: fixed; top: 15px; left: 50%; transform: translateX(-50%);
            width: 320px; height: 48px; background: var(--glass);
            backdrop-filter: blur(12px); border: 1px solid var(--border);
            border-radius: 50px; display: flex; align-items: center;
            padding: 0 6px 0 16px; z-index: 10000;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .banner-slider { flex: 1; height: 18px; overflow: hidden; }
        .slide-text { display: flex; flex-direction: column; animation: slideUp 8s infinite; }
        .slide-text span { height: 18px; font-size: 0.65rem; font-weight: 800; display: flex; align-items: center; gap: 6px; text-transform: uppercase; letter-spacing: 1px; }

        @keyframes slideUp {
            0%, 25% { transform: translateY(0); }
            33%, 58% { transform: translateY(-18px); }
            66%, 91% { transform: translateY(-36px); }
            100% { transform: translateY(0); }
        }

        /* --- 2. AUTO-SLIDE CAROUSEL --- */
        .carousel-wrapper {
            width: 100%; overflow: hidden; padding: 100px 0 50px;
        }

        .carousel-track {
            display: flex; gap: 25px; width: calc(300px * 10); /* Adjust based on card count */
            animation: scrollTrack 40s linear infinite;
        }

        .carousel-track:hover { animation-play-state: paused; }

        @keyframes scrollTrack {
            0% { transform: translateX(0); }
            100% { transform: translateX(calc(-300px * 5)); }
        }

        .project-card {
            min-width: 300px; height: 400px;
            background: linear-gradient(145deg, #111, #080808);
            border: 1px solid var(--border); border-radius: 24px;
            padding: 24px; display: flex; flex-direction: column;
            justify-content: space-between; transition: 0.4s;
            position: relative; overflow: hidden;
        }

        .project-card:hover {
            border-color: var(--accent);
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(255, 20, 147, 0.15);
        }

        .card-glow {
            position: absolute; top: -50%; left: -50%; width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,20,147,0.05) 0%, transparent 70%);
            pointer-events: none;
        }

        .launch-btn {
            background: var(--accent); color: white;
            padding: 12px; border-radius: 14px;
            font-weight: 800; font-size: 0.75rem;
            text-align: center; text-transform: uppercase;
            letter-spacing: 1px; transition: 0.3s;
        }
        .launch-btn:hover { background: #ff4da6; box-shadow: 0 0 20px rgba(255,20,147,0.4); }

    </style>
</head>
<body>

    <div class="top-banner">
        <div class="banner-slider">
            <div class="slide-text">
                <span><i class="fas fa-bolt text-pink-500"></i> New AI Tools Live</span>
                <span><i class="fas fa-code text-blue-400"></i> Dev Portfolio Updated</span>
                <span><i class="fas fa-rocket text-green-400"></i> Scale Your Side Hustle</span>
            </div>
        </div>
        <a href="https://debeatzgh1.github.io/Home-/" target="_blank" class="bg-pink-600 text-[10px] font-black px-4 py-2 rounded-full hover:scale-105 transition">OPEN HUB</a>
    </div>

    <section class="max-w-7xl mx-auto px-6 pt-32">
        <h2 class="text-5xl font-black tracking-tighter mb-4">The <span class="text-pink-600">Ecosystem.</span></h2>
        <p class="text-gray-500 max-w-xl mb-12">Professional resources, AI widgets, and creative tools tailored for the modern digital strategist.</p>
    </section>

    <div class="carousel-wrapper">
        <div class="carousel-track" id="carouselTrack">
            </div>
    </div>

    <script>
        const projects = [
            { title: "Home Hub", url: "https://debeatzgh1.github.io/Home-/", icon: "fa-house", desc: "The central gateway to all DeBeatzGH platforms." },
            { title: "E-Hub", url: "https://debeatzgh1.github.io/E-Hub-/", icon: "fa-play", desc: "Entertainment and media streaming interface." },
            { title: "Personal Dev", url: "https://debeatzgh1.github.io/me-/", icon: "fa-user-tie", desc: "Professional developer portfolio and CV." },
            { title: "AI Quiz", url: "https://debeatzgh1.github.io/Ai-quiz/", icon: "fa-brain", desc: "Interactive AI-powered knowledge testing." },
            { title: "Pages Hub", url: "https://debeatzgh1.github.io/Pages-/", icon: "fa-layer-group", desc: "Curated collection of landing pages." }
        ];

        const track = document.getElementById('carouselTrack');

        // Create cards and clone them for seamless infinite loop
        function createCards(data) {
            return data.map(p => `
                <div class="project-card">
                    <div class="card-glow"></div>
                    <div>
                        <div class="w-12 h-12 bg-white/5 rounded-2xl flex items-center justify-center mb-6 border border-white/10">
                            <i class="fas ${p.icon} text-xl text-pink-500"></i>
                        </div>
                        <h3 class="text-xl font-black mb-3">${p.title}</h3>
                        <p class="text-gray-500 text-xs leading-relaxed">${p.desc}</p>
                    </div>
                    <a href="${p.url}" target="_blank" class="launch-btn">Launch Resource</a>
                </div>
            `).join('');
        }

        // Initialize with original + clone
        track.innerHTML = createCards(projects) + createCards(projects);
    </script>
</body>
</html>




    <iframe
      id="JotFormIFrame-241335470278053"
      title="Welcome to — Your Hub for AI Tools, Side Hustles & Digital Growth"
      onload="window.parent.scrollTo(0,0)"
      allowtransparency="true"
      allow="geolocation; microphone; camera; fullscreen; payment"
      src="https://form.jotform.com/241335470278053"
      frameborder="0"
      style="min-width:100%;max-width:100%;height:539px;border:none;"
      scrolling="no"
    >
    </iframe>
    <script src='https://cdn.jotfor.ms/s/umd/latest/for-form-embed-handler.js'></script>
    <script>window.jotformEmbedHandler("iframe[id='JotFormIFrame-241335470278053']", "https://form.jotform.com/")</script>
    





<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Premium Saved Resources</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <style>
        :root {
            --accent: #3b82f6;
            --heart-red: #ff2e63;
            --glass: rgba(15, 23, 42, 0.95);
            --border: rgba(255, 255, 255, 0.1);
        }

        body { background: #0f172a; color: #f1f5f9; font-family: 'Inter', sans-serif; padding-top: 60px; }

        /* --- FAVORITES BAR --- */
        .fav-bar {
            position: fixed; top: 45px; left: 0; width: 100%; height: 40px;
            background: rgba(59, 130, 246, 0.1); border-bottom: 1px solid var(--border);
            display: flex; align-items: center; padding: 0 20px; z-index: 1000;
            font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 1px;
        }

        /* --- CARDS & HEART --- */
        .card {
            min-width: 280px; background: rgba(30, 41, 59, 0.5);
            border: 1px solid var(--border); border-radius: 20px;
            position: relative; transition: 0.3s;
        }
        
        .bookmark-btn {
            position: absolute; top: 15px; right: 15px;
            width: 35px; height: 35px; background: rgba(0,0,0,0.5);
            backdrop-filter: blur(5px); border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; z-index: 20; transition: 0.3s;
        }

        .bookmark-btn.saved { color: var(--heart-red); background: #fff; }

        /* --- MODAL --- */
        .modal-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.9);
            display: none; z-index: 100000;
        }
    </style>
</head>
<body>

    <header class="fixed top-0 left-0 w-full h-[45px] bg-[#0f172a] border-b border-white/10 flex items-center px-6 z-[10001]">
        <span class="text-blue-500 font-black">DEBEATZGH HUB</span>
        <div class="ml-auto flex gap-4 text-[10px] font-bold">
            <span id="fav-count" class="bg-blue-600 px-2 py-0.5 rounded-full">0 SAVED</span>
        </div>
    </header>

    <div class="fav-bar">
        <i class="fas fa-bookmark mr-2 text-blue-500"></i> Local Storage Engine Active
    </div>

    <main class="max-w-7xl mx-auto p-8 mt-10">
        <h2 class="text-3xl font-black mb-8">Featured <span class="text-blue-500">Widgets</span></h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" id="widget-grid">
            </div>
    </main>

    <div class="modal-overlay" id="globalModal">
        <div class="relative w-[95%] h-[90%] bg-white m-auto mt-[2%] rounded-3xl overflow-hidden shadow-2xl">
            <div class="absolute top-4 left-4 flex gap-2 z-50">
                <button onclick="closeModal()" class="bg-black/80 text-white px-4 py-2 rounded-xl text-xs font-bold">✕ CLOSE</button>
            </div>
            <iframe id="modalFrame" class="w-full h-full border-none"></iframe>
        </div>
    </div>

    <script>
        const widgets = [
            {id: "Ai-quiz", name: "AI Quiz Widget", desc: "Interactive AI testing tool."},
            {id: "curly-chainsaw", name: "Script Previewer", desc: "Live HTML/CSS editor."},
            {id: "debeatzgh", name: "Portfolio Pro", desc: "Developer profile widget."},
            {id: "Decode-AI-starter-kit-", name: "AI Starter Kit", desc: "The ultimate AI foundation."},
            {id: "menu-widget-", name: "Smart Dock", desc: "Floating navigation menu."},
            {id: "Blogger-iframe-embed-generator", name: "Iframe Gen", desc: "Embed tool for bloggers."}
        ];

        let savedItems = JSON.parse(localStorage.getItem('dbgh_favorites')) || [];

        function renderWidgets() {
            const grid = document.getElementById('widget-grid');
            grid.innerHTML = widgets.map(w => {
                const isSaved = savedItems.includes(w.id);
                return `
                    <div class="card p-6">
                        <div class="bookmark-btn ${isSaved ? 'saved' : ''}" onclick="toggleSave('${w.id}')">
                            <i class="${isSaved ? 'fas' : 'far'} fa-heart"></i>
                        </div>
                        <div class="w-12 h-12 bg-blue-600/20 rounded-xl flex items-center justify-center mb-4">
                            <i class="fas fa-code text-blue-500"></i>
                        </div>
                        <h3 class="font-bold text-lg">${w.name}</h3>
                        <p class="text-slate-400 text-xs mt-2 mb-6">${w.desc}</p>
                        <button onclick="openModal('https://debeatzgh1.github.io/${w.id}/')" 
                                class="w-full py-3 bg-white/5 hover:bg-blue-600 rounded-xl text-xs font-bold transition">
                            PREVIEW WIDGET
                        </button>
                    </div>
                `;
            }).join('');
            updateCounter();
        }

        function toggleSave(id) {
            if (savedItems.includes(id)) {
                savedItems = savedItems.filter(item => item !== id);
            } else {
                savedItems.push(id);
            }
            localStorage.setItem('dbgh_favorites', JSON.stringify(savedItems));
            renderWidgets();
        }

        function updateCounter() {
            document.getElementById('fav-count').innerText = `${savedItems.length} SAVED`;
        }

        function openModal(url) {
            document.getElementById('modalFrame').src = url;
            document.getElementById('globalModal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('globalModal').style.display = 'none';
            document.getElementById('modalFrame').src = '';
        }

        // Init
        renderWidgets();
    </script>
</body>
</html>




<iframe src="https://form.svhrt.com/60f4a0aeedc1993c8c7b3989"></iframe>


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH Premium | Dev Ecosystem</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <style>
        :root {
            --accent: #3b82f6;
            --glass: rgba(15, 23, 42, 0.9);
            --border: rgba(255, 255, 255, 0.1);
            --bg-dark: #0f172a;
        }

        body {
            background-color: var(--bg-dark);
            color: #f1f5f9;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            padding-top: 45px;
        }

        /* --- 1. PREMIUM AUTO-SCROLL BANNER --- */
        .top-banner {
            position: fixed; top: 0; left: 0; width: 100%; height: 35px;
            background: var(--glass); backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border);
            display: flex; align-items: center; z-index: 10005; padding: 0 20px;
        }

        .scroll-container { flex: 1; overflow: hidden; white-space: nowrap; margin: 0 30px; }
        .scroll-track { display: inline-block; animation: scrollText 25s linear infinite; }
        .scroll-item { display: inline-block; font-size: 0.75rem; font-weight: 600; padding-right: 60px; color: #94a3b8; }

        @keyframes scrollText { from { transform: translateX(0); } to { transform: translateX(-50%); } }

        /* --- 2. CAROUSEL & LAZY LOADING --- */
        .carousel-container {
            display: flex; overflow-x: auto; scroll-snap-type: x mandatory;
            gap: 20px; padding: 40px 20px; scrollbar-width: none;
        }
        .carousel-container::-webkit-scrollbar { display: none; }

        .card {
            min-width: 300px; background: rgba(30, 41, 59, 0.5);
            border: 1px solid var(--border); border-radius: 20px;
            overflow: hidden; scroll-snap-align: start; transition: 0.4s;
        }
        .card:hover { transform: translateY(-10px); border-color: var(--accent); box-shadow: 0 20px 40px rgba(0,0,0,0.4); }

        /* Lazy Load Placeholder Style */
        .lazy-img { background: #1e293b; height: 160px; width: 100%; object-fit: cover; transition: opacity 0.5s; }

        /* --- 3. PREMIUM IFRAME MODAL --- */
        .modal-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.85);
            backdrop-filter: blur(8px); display: none; justify-content: center; align-items: center;
            z-index: 100000; animation: fadeIn 0.3s ease;
        }

        .modal-window {
            width: 95%; height: 100%; background: #fff; border-radius: 24px;
            overflow: hidden; position: relative; transform: scale(0.95); transition: 0.3s;
        }

        .modal-active .modal-window { transform: scale(1); }

        .modal-bar {
            position: absolute; top: 15px; left: 15px; display: flex; gap: 10px; z-index: 10;
        }

        .btn-ui {
            background: rgba(0,0,0,0.8); color: #fff; padding: 8px 15px;
            border-radius: 12px; font-size: 11px; font-weight: 700; cursor: pointer;
        }

        /* --- 4. AUTO POPUP NOTIFICATION --- */
        #auto-popup {
            position: fixed; bottom: -100px; left: 20px; 
            background: var(--accent); color: white; padding: 15px 25px;
            border-radius: 15px; box-shadow: 0 10px 30px rgba(59, 130, 246, 0.4);
            z-index: 99999; transition: 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            display: flex; align-items: center; gap: 15px;
        }

        #auto-popup.show { bottom: 20px; }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    </style>
</head>
<body>

    <header class="top-banner">
        <span class="text-blue-500 font-black text-xl">D.</span>
        <div class="scroll-container">
            <div class="scroll-track" id="banner-track">
                </div>
        </div>
        <button onclick="launchModal('https://msha.ke/debeatzgh#quest-post')" class="text-[10px] font-bold border border-white/20 px-3 py-1 rounded-full hover:bg-white/10">Open site</button>
    </header>

    <div class="max-w-6xl mx-auto mt-10 px-6">
        <h1 class="text-4xl font-black tracking-tighter">Developer Hub <span class="text-blue-500">.</span></h1>
        <p class="text-slate-400 mt-2">Premium widgets and creative resources.</p>
    </div>

    <div class="carousel-container" id="main-grid">
        </div>

    <div class="modal-overlay" id="globalModal">
        <div class="modal-window">
            <div class="modal-bar">
                <div class="btn-ui" onclick="closeModal()">✕ CLOSE</div>
                <div class="btn-ui" onclick="toggleFull()">⛶ FULLSCREEN</div>
            </div>
            <iframe id="modalFrame" class="w-full h-full border-none"></iframe>
        </div>
    </div>

    <div id="auto-popup">
        <i class="fas fa-rocket text-xl"></i>
        <div>
            <p class="text-[10px] uppercase font-black opacity-80">New Resource Available</p>
            <p class="text-sm font-bold">Check out the Decode AI Starter Kit!</p>
        </div>
        <button onclick="document.getElementById('auto-popup').classList.remove('show')" class="ml-4 opacity-50 hover:opacity-100">✕</button>
    </div>

    <script>
        const repos = [
            {id: "Ai-quiz", name: "AI Quiz Widget"},
            {id: "curly-chainsaw", name: "HTML Editor"},
            {id: "debeatzgh", name: "Dev Portfolio"},
            {id: "menu-widget-", name: "Floating Menu"},
            {id: "Decode-AI-starter-kit-", name: "AI Starter Kit"},
            {id: "-Floating-Dock-Smart-Iframe-Modal", name: "Smart Iframe Dock"}
        ];

        // 1. Populate Banner
        const track = document.getElementById('banner-track');
        const content = "Widgets, tools, templates & creative resources for Bloggers, Creators & Developers • ";
        track.innerHTML = `<span class="scroll-item">${content.repeat(10)}</span>`;

        // 2. Populate Carousel with Lazy Loading
        const grid = document.getElementById('main-grid');
        repos.forEach(repo => {
            grid.innerHTML += `
                <div class="card">
                    <img data-src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticcatalogcoverthumbnailfeaturingagridoffloatingbrowserwindowsandappcardseachwithsmalliconslikebloggergithubshoppingcartchatbubbleandnewsletterenvelope6320208726725.jpg" 
                         src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAQAAAC1HAwCAAAAC0lEQVR42mNkYAAAAAYAAjCB0C8AAAAASUVORK5CYII=" 
                         class="lazy-img shadow-xl">
                    <div class="p-6">
                        <h3 class="font-bold text-lg">${repo.name}</h3>
                        <p class="text-slate-500 text-xs mt-2 mb-5">Professional GitHub resource for modern web apps.</p>
                        <button onclick="launchModal('https://debeatzgh1.github.io/${repo.id}/')" 
                                class="w-full bg-blue-600 hover:bg-blue-500 text-white font-bold py-3 rounded-xl text-xs transition">
                            LIVE PREVIEW
                        </button>
                    </div>
                </div>
            `;
        });

        // 3. Lazy Load Logic
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if(entry.isIntersecting) {
                    const img = entry.target;
                    img.src = img.dataset.src;
                    img.classList.remove('lazy-img');
                    observer.unobserve(img);
                }
            });
        });
        document.querySelectorAll('img[data-src]').forEach(img => observer.observe(img));

        // 4. Modal Engine
        function launchModal(url) {
            const modal = document.getElementById('globalModal');
            document.getElementById('modalFrame').src = url;
            modal.style.display = 'flex';
            setTimeout(() => modal.classList.add('modal-active'), 10);
            document.body.style.overflow = 'hidden';
        }

        function closeModal() {
            const modal = document.getElementById('globalModal');
            modal.classList.remove('modal-active');
            setTimeout(() => {
                modal.style.display = 'none';
                document.getElementById('modalFrame').src = '';
            }, 300);
            document.body.style.overflow = 'auto';
        }

        function toggleFull() {
            const frame = document.getElementById('modalFrame');
            if (frame.requestFullscreen) frame.requestFullscreen();
        }

        // 5. Auto Popup Logic (Triggers after 5 seconds)
        setTimeout(() => {
            document.getElementById('auto-popup').classList.add('show');
        }, 5000);
    </script>
</body>
</html>
