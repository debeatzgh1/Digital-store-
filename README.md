
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
