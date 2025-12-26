<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <title>FDZ Anime & Movie & Series</title>
    <meta name="description" content="FDZ Anime & Movie & Series - แหล่งรวมอนิเมะ ซีรีส์ และเดอะมูฟวี่ ดูออนไลน์ฟรี อัปเดตล่าสุด">
    <meta name="keywords" content="ดูอนิเมะ, อนิเมะซับไทย, FDZ Anime, ดูการ์ตูน">
    <meta property="og:title" content="FDZ Anime & Movie & Series">
    <meta property="og:description" content="แหล่งรวมความบันเทิงอนิเมะและซีรีส์">
    <meta property="og:image" content="https://i.ibb.co/v6W8Xm8/rimuru-icon.jpg">
    <meta http-equiv="Content-Security-Policy" content="default-src 'self' https: 'unsafe-inline' 'unsafe-eval'; img-src 'self' https: data: blob: *; frame-src *; connect-src 'self' https://api.jikan.moe https://translate.googleapis.com https://nekos.best https://api.mangadex.org https://anime-d7d4e-default-rtdb.firebaseio.com;">
    
    <link rel="icon" type="image/jpeg" href="https://i.ibb.co/v6W8Xm8/rimuru-icon.jpg">
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;500;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary: #00fbff; --accent: #ff00ea; --text: #ffffff;
            --card-bg: rgba(15, 23, 42, 0.9); --fav-color: #ff4757;
            --top-rated: #f1c40f;
            --update-color: #2ecc71;
            --upcoming-color: #9b59b6;
            --sub-color: #3498db;
            --dub-color: #e67e22;
        }
        body {
            font-family: 'Kanit', sans-serif; margin: 0; padding: 10px; color: var(--text);
            min-height: 100vh; 
            background-color: #050810;
            background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.7)), 
                              url('https://images.wallpapersden.com/image/download/anime-girl-scenery-evening_bWhtZWyUmZqaraWkpJRmbmdlrWZlbWU.jpg');
            background-size: cover; background-position: center center; background-attachment: fixed; background-repeat: no-repeat;
        }
        header { text-align: center; margin-bottom: 20px; background: rgba(0, 0, 0, 0.75); backdrop-filter: blur(15px); padding: 15px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.2); position: relative; z-index: 100; }
        h1 { font-size: 1.8rem; margin: 0 0 15px 0; font-weight: 800; background: linear-gradient(to right, #00fbff, #ff00ea); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        
        .controls { display: flex; justify-content: center; gap: 8px; flex-wrap: wrap; margin-bottom: 10px; }
        select, button, input { padding: 8px 12px; border-radius: 10px; border: 1px solid var(--primary); background: rgba(0, 0, 0, 0.8); color: white; cursor: pointer; font-family: 'Kanit'; font-size: 11px; transition: 0.2s; }
        button:hover { filter: brightness(1.2); transform: scale(1.05); }
        
        .anime-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 15px; padding-bottom: 20px; }
        
        .anime-card { background: var(--card-bg); border-radius: 15px; overflow: hidden; border: 1px solid rgba(255,255,255,0.1); position: relative; transition: transform 0.2s; cursor: pointer; contain: layout; }
        .anime-card:hover { transform: translateY(-5px); border-color: var(--primary); }
        .image-container { position: relative; width: 100%; height: 210px; background: #1a1a1a; overflow: hidden; }
        .image-container img { width: 100%; height: 100%; object-fit: cover; }
        .score-badge { position: absolute; top: 8px; left: 8px; background: rgba(0,0,0,0.8); color: #ffcc00; padding: 2px 6px; border-radius: 5px; font-size: 10px; font-weight: bold; z-index: 2; }
        .completed-badge { position: absolute; top: 8px; left: 50px; background: #2ecc71; color: #fff; padding: 2px 6px; border-radius: 5px; font-size: 10px; font-weight: bold; z-index: 2; border: 1px solid #fff; }

        .fav-btn { position: absolute; top: 8px; right: 8px; background: rgba(0,0,0,0.7); border: none; color: #ccc; font-size: 18px; padding: 5px; border-radius: 50%; z-index: 5; transition: 0.3s; }
        .fav-btn.active { color: var(--fav-color); text-shadow: 0 0 10px var(--fav-color); }
        
        .anime-info { padding: 8px; }
        .title-th { color: var(--primary); display: block; font-size: 13px; font-weight: 500; line-height: 1.2; min-height: 1.2em; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
        .title-en { color: #aaa; font-size: 9px; font-style: italic; display: block; margin-bottom: 5px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }

        .episode-container { display: flex; flex-direction: column; gap: 8px; margin-top: 10px; padding: 10px; background: rgba(0,0,0,0.5); border-radius: 10px; }
        .ep-row { display: flex; align-items: center; gap: 5px; width: 100%; }
        .btn-ep { flex-grow: 1; background: #4834d4; color: white; border: none; padding: 8px; border-radius: 5px; font-size: 12px; cursor: pointer; text-align: left; }
        .btn-del-ep { background: #eb4d4b; color: white; border: none; padding: 8px; border-radius: 5px; cursor: pointer; font-size: 12px; }

        .btn-video-db { display: block; width: 100%; text-align: center; background: #ff9f43; color: black; border: none; padding: 8px; border-radius: 8px; font-size: 10px; font-weight: bold; margin-top: 5px; text-decoration: none; pointer-events: none; }
        .admin-upload-section { margin-top: 15px; padding: 10px; border-top: 1px dashed #333; background: rgba(255,255,255,0.05); border-radius: 10px; }
        .admin-upload-section input, .admin-upload-section select { width: 100%; margin-bottom: 5px; background: #000; color: white; border: 1px solid var(--primary); padding: 5px; box-sizing: border-box; }

        .modal { display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); backdrop-filter: blur(10px); justify-content: center; align-items: center; }
        .modal-content { background: #0f172a; border: 1px solid var(--primary); width: 95%; max-width: 500px; border-radius: 20px; position: relative; max-height: 90vh; overflow-y: auto; padding: 15px; }
        
        #videoPlayerModal { display: none; position: fixed; z-index: 2000; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); backdrop-filter: blur(5px); align-items: center; justify-content: center; padding: 10px; box-sizing: border-box; }
        .video-box { width: 100%; max-width: 900px; background: #000; border-radius: 15px; overflow: hidden; box-shadow: 0 0 30px rgba(0, 251, 255, 0.3); border: 1px solid var(--primary); display: flex; flex-direction: column; max-height: 90vh; }
        #videoPlayerContainer { width: 100%; flex-grow: 1; aspect-ratio: 16/9; background: #000; display: flex; align-items: center; justify-content: center; overflow: hidden; }
        #videoPlayerContainer iframe { width: 100%; height: 100%; border: none; }

        .modal-synopsis { font-size: 13px; line-height: 1.6; color: #ddd; background: rgba(0,0,0,0.3); padding: 10px; border-radius: 10px; margin: 10px 0; max-height: 200px; overflow-y: auto; }
        .air-date { font-size: 10px; color: #00fbff; margin-top: 5px; font-weight: bold; }
        
        #sentinel { height: 150px; width: 100%; clear: both; }

        .admin-type-controls { display: flex; gap: 5px; margin-bottom: 8px; }
        .admin-type-controls button { flex: 1; font-size: 10px; padding: 5px; border: 1px solid var(--primary); }
    </style>
</head>
<body>

<header>
    <h1>💎 FDZ Anime & Movie & Series</h1>
    <div class="controls">
        <select id="yearSelect" onchange="startSearch()"><option value="all">ทุกปี</option></select>
        <button onclick="fetchSeries()" style="background:#4834d4;">📺 ซีรีส์อนิเมะ</button>
        <button onclick="fetchMovies()" style="background:var(--accent);">🎬 เดอะมูฟวี่</button>
        <button onclick="fetchTopRated()" style="background:var(--top-rated); color:#000;">⭐ รีวิวสูงสุด</button>
        <button onclick="showFavorites()" style="background:var(--fav-color);">❤️ รายการโปรด</button>
        <button onclick="showUpdatedOnly()" style="background:var(--update-color); color:#000;">🎬 อัปเดตล่าสุด</button>
        <button onclick="fetchUpcoming()" style="background:var(--upcoming-color); color:#fff;">🚀 ยังไม่ฉาย</button>
        <button onclick="filterByType('ซับไทย')" style="background:var(--sub-color);">🔵 ซับไทย</button>
        <button onclick="filterByType('พากย์ไทย')" style="background:var(--dub-color);">🟠 พากย์ไทย</button>
    </div>
    <div class="controls">
        <select id="genreSelect" onchange="startSearch()">
            <option value="all">ทุกหมวดหมู่</option>
            <option value="1">แอคชั่น (Action)</option>
            <option value="2">ผจญภัย (Adventure)</option>
            <option value="4">ตลก (Comedy)</option>
            <option value="10">แฟนตาซี (Fantasy)</option>
            <option value="22">โรแมนติก (Romance)</option>
        </select>
        <button onclick="fetchMangaData('manga')" style="background:#6ab04c;">📖 มังงะญี่ปุ่น</button>
        <button onclick="fetchMangaData('manhwa')" style="background:#f0932b;">🇰🇷 มังฮวาเกาหลี</button>
        <button onclick="fetchMangaData('manhua')" style="background:#eb4d4b;">🇨🇳 มังงะจีน</button>
    </div>
    <div class="controls">
        <input type="text" id="keywordSearch" placeholder="🔍 ค้นชื่ออนิเมะที่ต้องการ..." oninput="handleSearchInput()">
    </div>
</header>

<main class="anime-grid" id="animeList"></main>
<div id="sentinel"></div> 
<div id="loading" style="display:none; text-align:center; color:var(--primary); padding:20px;">⚡ กำลังโหลดข้อมูล...</div>

<div class="modal" id="animeModal" onclick="if(event.target===this) closeModal()">
    <div class="modal-content">
        <div id="modalBody"></div>
        <button onclick="closeModal()" style="width:100%; margin-top:15px; background:#eb4d4b;">❌ ปิดหน้าต่าง</button>
    </div>
</div>

<div id="videoPlayerModal">
    <div class="video-box">
        <div style="padding:10px; display:flex; justify-content:space-between; align-items:center; background:#111;">
            <span id="videoTitle" style="font-size:14px; color:var(--primary);"></span>
            <button onclick="closeVideo()" style="background:#ff4757; padding:5px 15px;">❌ ปิด</button>
        </div>
        <div id="videoPlayerContainer"></div>
    </div>
</div>

<script src="https://www.gstatic.com/firebasejs/9.22.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.1/firebase-database-compat.js"></script>

<script>
    const firebaseConfig = { databaseURL: "https://anime-d7d4e-default-rtdb.firebaseio.com/" };
    if (!firebase.apps.length) firebase.initializeApp(firebaseConfig);
    const db = firebase.database();

    let favorites = JSON.parse(localStorage.getItem('anime_favs')) || [];
    let translationCache = JSON.parse(localStorage.getItem('translation_cache')) || {};
    let currentPage = 1, currentCategory = 'anime', currentType = '', isFetching = false, searchTimeout;
    let hasMore = true;

    function manageCache() {
        if (Object.keys(translationCache).length > 800) {
            translationCache = {};
            localStorage.removeItem('translation_cache');
        }
    }

    const sleep = ms => new Promise(res => setTimeout(res, ms));

    function formatThaiDate(dateStr) {
        if (!dateStr) return "";
        const thaiMonths = {
            'January': 'มกราคม', 'February': 'กุมภาพันธ์', 'March': 'มีนาคม', 'April': 'เมษายน',
            'May': 'พฤษภาคม', 'June': 'มิถุนายน', 'July': 'กรกฎาคม', 'August': 'สิงหาคม',
            'September': 'กันยายน', 'October': 'ตุลาคม', 'November': 'พฤศจิกายน', 'December': 'ธันวาคม',
            'Jan': 'ม.ค.', 'Feb': 'ก.พ.', 'Mar': 'มี.ค.', 'Apr': 'เม.ย.', 'May': 'พ.ค.', 'Jun': 'มิ.ย.',
            'Jul': 'ก.ค.', 'Aug': 'ส.ค.', 'Sep': 'ก.ย.', 'Oct': 'ต.ค.', 'Nov': 'พ.ย.', 'Dec': 'ธ.ค.'
        };
        let formatted = dateStr;
        Object.entries(thaiMonths).forEach(([en, th]) => {
            formatted = formatted.replace(new RegExp(en, 'gi'), th);
        });
        return formatted.replace(/\bto\b/gi, 'ถึง');
    }

    async function fetchAnime(keyword = '', reset = false) {
        if (isFetching || (!hasMore && !reset)) return;
        if (reset) {
            currentPage = 1; hasMore = true;
            document.getElementById('animeList').innerHTML = '';
        }

        isFetching = true;
        document.getElementById('loading').style.display = 'block';
        
        const year = document.getElementById('yearSelect').value;
        const genre = document.getElementById('genreSelect').value;
        let k = keyword ? await translateKeyword(keyword) : '';
        
        let url = `https://api.jikan.moe/v4/${currentCategory}?page=${currentPage}&q=${encodeURIComponent(k)}&limit=24`;
        if (currentType) url += `&type=${currentType}`;
        if (year !== 'all') url += `&start_date=${year}-01-01`;
        if (genre !== 'all') url += `&genres=${genre}`;
        if (!k) url += `&order_by=popularity`;

        try {
            const res = await fetch(url);
            if (res.status === 429) {
                await sleep(2000);
                isFetching = false;
                return fetchAnime(keyword);
            }
            const result = await res.json();
            if (result.data && result.data.length > 0) {
                render(result.data);
                currentPage++;
                hasMore = result.pagination?.has_next_page || false;
            } else if (reset) {
                document.getElementById('animeList').innerHTML = '<div style="grid-column:1/-1; text-align:center; padding:50px;">ไม่พบข้อมูล</div>';
                hasMore = false;
            }
        } catch (e) { 
            console.error("Fetch error:", e);
        } finally {
            document.getElementById('loading').style.display = 'none';
            isFetching = false;
        }
    }

    function toggleFavorite(id, btn) {
        const animeId = parseInt(id);
        const idx = favorites.indexOf(animeId);
        if (idx !== -1) { favorites.splice(idx, 1); btn.classList.remove('active'); }
        else { favorites.push(animeId); btn.classList.add('active'); }
        localStorage.setItem('anime_favs', JSON.stringify(favorites));
    }

    async function showFavorites() {
        if (favorites.length === 0) return alert("ยังไม่มีรายการโปรด");
        document.getElementById('animeList').innerHTML = '';
        document.getElementById('loading').style.display = 'block';
        hasMore = false;
        for (const id of favorites) {
            try {
                await sleep(400);
                const r = await fetch(`https://api.jikan.moe/v4/anime/${id}`);
                const res = await r.json();
                if(res.data) render([res.data]);
            } catch(e) {}
        }
        document.getElementById('loading').style.display = 'none';
    }

    function showUpdatedOnly() {
        document.getElementById('animeList').innerHTML = '';
        document.getElementById('loading').style.display = 'block';
        hasMore = false;
        db.ref('episodes').limitToLast(20).once('value', async snap => {
            const data = snap.val();
            if (!data) {
                document.getElementById('loading').style.display = 'none';
                return;
            }
            const updatedIds = Object.keys(data).reverse();
            for (const id of updatedIds) {
                try {
                    await sleep(400);
                    const res = await fetch(`https://api.jikan.moe/v4/anime/${id}`);
                    const result = await res.json();
                    if(result.data) render([result.data]);
                } catch(e) {}
            }
            document.getElementById('loading').style.display = 'none';
        });
    }

    async function fetchUpcoming() {
        currentCategory = 'anime'; currentType = ''; hasMore = true;
        document.getElementById('animeList').innerHTML = ''; currentPage = 1;
        document.getElementById('loading').style.display = 'block';
        try {
            const res = await fetch(`https://api.jikan.moe/v4/anime?status=upcoming&order_by=popularity&sort=asc&page=1&limit=24`);
            const result = await res.json();
            if(result.data) { render(result.data, true); currentPage++; }
        } catch(e) {}
        document.getElementById('loading').style.display = 'none';
    }

    async function fetchTopRated() {
        document.getElementById('animeList').innerHTML = ''; currentPage = 1; hasMore = true;
        document.getElementById('loading').style.display = 'block';
        try {
            const res = await fetch(`https://api.jikan.moe/v4/top/${currentCategory}?page=1&limit=24`);
            const result = await res.json();
            if(result.data) { render(result.data); currentPage++; }
        } catch(e) {}
        document.getElementById('loading').style.display = 'none';
    }

    function filterByType(typeName) {
        document.getElementById('animeList').innerHTML = '';
        document.getElementById('loading').style.display = 'block';
        hasMore = false;
        
        db.ref('episodes').once('value', async snap => {
            const allData = snap.val();
            if (!allData) {
                document.getElementById('loading').style.display = 'none';
                alert(`ไม่พบข้อมูล${typeName}`);
                return;
            }

            const matchedIds = [];
            Object.entries(allData).forEach(([malId, episodes]) => {
                const hasType = Object.values(episodes).some(ep => ep.name && ep.name.includes(typeName));
                if (hasType) matchedIds.push(malId);
            });

            if (matchedIds.length === 0) {
                document.getElementById('loading').style.display = 'none';
                alert(`ไม่พบเรื่องที่เป็น ${typeName}`);
                return;
            }

            for (const id of matchedIds.reverse()) {
                try {
                    await sleep(400);
                    const res = await fetch(`https://api.jikan.moe/v4/anime/${id}`);
                    const result = await res.json();
                    if(result.data) render([result.data]);
                } catch(e) {}
            }
            document.getElementById('loading').style.display = 'none';
        });
    }

    function render(dataList, isUpcoming = false) {
        const container = document.getElementById('animeList');
        const fragment = document.createDocumentFragment();
        dataList.forEach(item => {
            if (!item || !item.mal_id) return;
            const isFav = favorites.includes(parseInt(item.mal_id));
            const card = document.createElement('div');
            card.className = 'anime-card';
            card.onclick = () => openModal(item);
            
            let airDateHtml = (isUpcoming && item.aired?.string) ? `<div class="air-date">📅 เริ่ม: <span id="date-${item.mal_id}">${formatThaiDate(item.aired.string)}</span></div>` : '';
            
            card.innerHTML = `
                <div class="image-container">
                    <button class="fav-btn ${isFav ? 'active' : ''}" onclick="event.stopPropagation(); toggleFavorite(${item.mal_id}, this)">❤</button>
                    <div class="score-badge">⭐ ${item.score || 'N/A'}</div>
                    <div id="comp-${item.mal_id}"></div> 
                    <img src="${item.images?.jpg?.large_image_url || ''}" loading="lazy" alt="${item.title}" onerror="this.src='https://via.placeholder.com/225x315?text=No+Image'">
                </div>
                <div class="anime-info">
                    <span class="title-th" id="th-${item.mal_id}">...</span>
                    <span class="title-en">${item.title}</span>
                    ${airDateHtml}
                    <div id="vbox-${item.mal_id}"></div>
                </div>
            `;
            fragment.appendChild(card);
            
            setTimeout(() => {
                translateText(item.title, `th-${item.mal_id}`);
                checkVideoQuickLink(item.mal_id, `vbox-${item.mal_id}`, item.episodes, `comp-${item.mal_id}`);
                if (isUpcoming && item.aired?.string) {
                    const el = document.getElementById(`date-${item.mal_id}`);
                    if (el && !/[ก-ฮ]/.test(el.innerText)) translateText(item.aired.string, `date-${item.mal_id}`);
                }
            }, 100);
        });
        container.appendChild(fragment);
    }

    function checkVideoQuickLink(malId, containerId, totalEpisodes, badgeContainerId) {
        db.ref('episodes/' + malId).once('value', snap => {
            const target = document.getElementById(containerId);
            const badgeTarget = document.getElementById(badgeContainerId);
            if (snap.exists()) {
                if (target) target.innerHTML = `<button class="btn-video-db">📺 มีวิดีโอพร้อมดู</button>`;
                if (totalEpisodes && snap.numChildren() >= totalEpisodes) {
                    if (badgeTarget) badgeTarget.innerHTML = `<div class="completed-badge">จบแล้ว</div>`;
                }
            }
        });
    }

    function saveEpisode(malId) {
        const url = document.getElementById(`url-${malId}`).value.trim();
        const epSelect = document.getElementById(`epnum-${malId}`);
        const epNameInput = document.getElementById(`epname-${malId}`).value.trim();
        const epName = epNameInput || (epSelect ? "ตอนที่ " + epSelect.value : "ตอนที่ 1");
        const pass = document.getElementById(`pass-${malId}`).value.trim();
        
        if (pass !== "755902") return alert("รหัสผ่านไม่ถูกต้อง!");
        if (!url) return alert("กรุณาใส่ลิงก์วิดีโอ");
        
        db.ref('episodes/' + malId).push({ name: epName, videoUrl: url, time: Date.now() })
        .then(() => { alert("บันทึกสำเร็จ!"); refreshEpisodeList(malId); });
    }

    function deleteEpisode(malId, epKey) {
        const pass = prompt("ใส่รหัสผ่านเพื่อลบ:");
        if (pass === "755902") {
            db.ref(`episodes/${malId}/${epKey}`).remove().then(() => { alert("ลบสำเร็จ!"); refreshEpisodeList(malId); });
        }
    }

    function refreshEpisodeList(malId) {
        const container = document.getElementById(`eplist-${malId}`);
        if(!container) return;
        db.ref('episodes/' + malId).once('value', snap => {
            container.innerHTML = '';
            const data = snap.val();
            if (data) {
                const episodesArray = Object.entries(data).map(([key, value]) => ({ key, ...value }));
                episodesArray.sort((a, b) => {
                    const numA = parseInt(a.name.match(/\d+/)) || 0;
                    const numB = parseInt(b.name.match(/\d+/)) || 0;
                    return numA - numB;
                });

                episodesArray.forEach((ep) => {
                    const row = document.createElement('div');
                    row.className = 'ep-row';
                    row.innerHTML = `<button class="btn-ep" onclick="playVideo('${ep.videoUrl}', '${ep.name}')">▶ ${ep.name}</button>
                                     <button class="btn-del-ep" onclick="deleteEpisode('${malId}', '${ep.key}')">🗑️</button>`;
                    container.appendChild(row);
                });
            } else { container.innerHTML = '<span style="font-size:11px;">ยังไม่มีวิดีโอ</span>'; }
        });
    }

    function setEpType(malId, type) {
        const nameInput = document.getElementById(`epname-${malId}`);
        const epSelect = document.getElementById(`epnum-${malId}`);
        let baseName = "ตอนที่ " + epSelect.value;
        nameInput.value = `${baseName} (${type})`;
    }

    function openModal(item) {
        const modal = document.getElementById('animeModal');
        const body = document.getElementById('modalBody');
        
        let epOptions = '';
        const totalEp = item.episodes || 24; 
        for(let i=1; i<=totalEp; i++) {
            epOptions += `<option value="${i}">ตอนที่ ${i}</option>`;
        }

        let trailerHtml = '';
        if (item.trailer && item.trailer.embed_url) {
            trailerHtml = `
                <div style="margin-top: 15px;">
                    <p style="color:var(--primary); font-size:12px; margin-bottom:5px;">📺 ตัวอย่างอนิเมะ (Trailer):</p>
                    <div style="width:100%; aspect-ratio:16/9; background:#000; border-radius:10px; overflow:hidden; border:1px solid rgba(255,255,255,0.1);">
                        <iframe src="${item.trailer.embed_url}" style="width:100%; height:100%; border:none;" allowfullscreen></iframe>
                    </div>
                </div>
            `;
        }

        body.innerHTML = `
            <img src="${item.images?.jpg?.large_image_url || ''}" style="width:100%; border-radius:10px;" onerror="this.src='https://via.placeholder.com/225x315?text=No+Image'">
            <h3 style="color:var(--primary); margin:10px 0 0 0;">${item.title}</h3>
            <div class="modal-synopsis" id="synp-${item.mal_id}">กำลังแปลเรื่องย่อ...</div>
            
            ${trailerHtml}

            <div style="margin-top:15px; border-top:1px solid #333; padding-top:10px;">
                <p style="color:var(--update-color); font-size:12px;">🎬 รายชื่อตอนที่พร้อมดู:</p>
                <div class="episode-container" id="eplist-${item.mal_id}"></div>
            </div>

            <div class="admin-upload-section">
                <p style="color:#aaa; font-size:10px; margin-bottom:5px;">🛠️ ส่วนจัดการ (Admin Only):</p>
                
                <div class="admin-type-controls">
                    <button type="button" onclick="setEpType('${item.mal_id}', 'ซับไทย')" style="background:#3498db;">🔵 ซับไทย</button>
                    <button type="button" onclick="setEpType('${item.mal_id}', 'พากย์ไทย')" style="background:#e67e22;">🟠 พากย์ไทย</button>
                </div>

                <select id="epnum-${item.mal_id}" onchange="document.getElementById('epname-${item.mal_id}').value = 'ตอนที่ ' + this.value">
                    ${epOptions}
                </select>
                <input type="text" id="epname-${item.mal_id}" placeholder="ชื่อตอน (หรือแก้ไขจากที่เลือก)" value="ตอนที่ 1">
                <input type="text" id="url-${item.mal_id}" placeholder="ลิงก์ Google Drive หรือ Ok.ru">
                <input type="password" id="pass-${item.mal_id}" placeholder="Password">
                <button onclick="saveEpisode('${item.mal_id}')">บันทึกตอน</button>
            </div>
        `;
        modal.style.display = 'flex';
        document.body.style.overflow = 'hidden';
        if(item.synopsis) translateText(item.synopsis, `synp-${item.mal_id}`);
        refreshEpisodeList(item.mal_id);
    }

    async function translateText(t, id) {
        if(!t || !document.getElementById(id)) return;
        const cacheKey = btoa(unescape(encodeURIComponent(t.substring(0, 60))));
        if(translationCache[cacheKey]) { 
            document.getElementById(id).innerText = translationCache[cacheKey]; 
            return; 
        }
        try {
            const res = await fetch(`https://translate.googleapis.com/translate_a/single?client=gtx&sl=auto&tl=th&dt=t&q=${encodeURIComponent(t)}`);
            const d = await res.json();
            let fullText = d[0].map(p => p[0] || "").join("");
            if(document.getElementById(id)) { 
                document.getElementById(id).innerText = fullText; 
                translationCache[cacheKey] = fullText; 
                localStorage.setItem('translation_cache', JSON.stringify(translationCache)); 
            }
        } catch(e) { 
            if(document.getElementById(id)) document.getElementById(id).innerText = t; 
        }
    }

    async function translateKeyword(t) {
        if(!/[ก-ฮ]/.test(t)) return t;
        try {
            const res = await fetch(`https://translate.googleapis.com/translate_a/single?client=gtx&sl=th&tl=en&dt=t&q=${encodeURIComponent(t)}`);
            const d = await res.json(); return d[0][0][0];
        } catch(e) { return t; }
    }

    function playVideo(url, title) {
        const modal = document.getElementById('videoPlayerModal');
        const titleEl = document.getElementById('videoTitle');
        const videoContainer = document.getElementById('videoPlayerContainer');
        titleEl.innerText = title;
        
        let embedUrl = url;
        
        if (url.includes('drive.google.com')) {
            const driveMatch = url.match(/\/file\/d\/(.+?)(\/|$|\?)/) || url.match(/id=(.+?)(&|$)/);
            if (driveMatch) embedUrl = `https://drive.google.com/file/d/${driveMatch[1]}/preview`;
        } 
        else if (url.includes('ok.ru')) {
            const okMatch = url.match(/video\/(\d+)/);
            if (okMatch) embedUrl = `https://ok.ru/videoembed/${okMatch[1]}`;
        }

        videoContainer.innerHTML = `
            <iframe 
                src="${embedUrl}" 
                allow="autoplay; fullscreen; picture-in-picture; xr-spatial-tracking; clipboard-write; encrypted-media; gyroscope; accelerometer" 
                allowfullscreen="true"
                webkitallowfullscreen="true"
                mozallowfullscreen="true">
            </iframe>`;
        
        modal.style.display = 'flex';
        document.body.style.overflow = 'hidden';
    }

    function closeVideo() { 
        document.getElementById('videoPlayerContainer').innerHTML = ''; 
        document.getElementById('videoPlayerModal').style.display = 'none'; 
        document.body.style.overflow = 'auto';
    }

    function closeModal() { document.getElementById('animeModal').style.display = 'none'; document.body.style.overflow = 'auto'; }
    function startSearch() { fetchAnime(document.getElementById('keywordSearch').value, true); }
    function handleSearchInput() { clearTimeout(searchTimeout); searchTimeout = setTimeout(startSearch, 700); }
    function fetchSeries() { currentCategory = 'anime'; currentType = 'tv'; startSearch(); }
    function fetchMovies() { currentCategory = 'anime'; currentType = 'movie'; startSearch(); }
    function fetchMangaData(type) { currentCategory = 'manga'; currentType = type; startSearch(); }

    const ys = document.getElementById('yearSelect');
    const currentYear = new Date().getFullYear();
    for (let y = currentYear; y >= 1990; y--) { 
        let opt = document.createElement('option'); opt.value = y; opt.innerText = `ปี ${y}`; ys.appendChild(opt); 
    }

    const observer = new IntersectionObserver(e => { 
        if (e[0].isIntersecting && !isFetching && hasMore) {
            fetchAnime(document.getElementById('keywordSearch').value); 
        }
    }, { 
        rootMargin: '300px', 
        threshold: 0.01 
    });

    window.onload = () => { 
        manageCache();
        startSearch(); 
        observer.observe(document.getElementById('sentinel')); 
    };
</script>

<script>
    (function() {
        var meta = document.createElement('meta');
        meta.name = "google-site-verification";
        // เมื่อคุณได้รหัสจาก Google Search Console ให้นำมาใส่แทนข้อความด้านล่างนี้
        meta.content = "ใส่รหัสยืนยันจากGoogleของคุณที่นี่"; 
        document.getElementsByTagName('head')[0].appendChild(meta);
    })();
</script>

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "FDZ Anime & Movie & Series",
  "url": "https://your-website-url.com/",
  "description": "แหล่งรวมอนิเมะ ซีรีส์ และเดอะมูฟวี่ ดูออนไลน์ฟรี อัปเดตล่าสุด",
  "potentialAction": {
    "@type": "SearchAction",
    "target": "https://your-website-url.com/?q={search_term_string}",
    "query-input": "required name=search_term_string"
  }
}
</script>

</body>
</html>
