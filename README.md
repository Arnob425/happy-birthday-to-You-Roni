<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>My Video — Full Page Player</title>
  <meta name="description" content="A clean, responsive, full-page HTML5 video player website." />
  <style>
    :root{
      --bg:#0b0d10;--fg:#e8edf2;--muted:#9aa7b2;--accent:#71c7ec;--card:#14181d;--ring:rgba(113,199,236,.35)
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0;font-family:ui-sans-serif,system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif;background:linear-gradient(180deg,#0a0c10 0%,#0f141a 100%);color:var(--fg);display:flex;flex-direction:column}
    header{position:sticky;top:0;backdrop-filter:saturate(140%) blur(6px);background:rgba(10,14,18,.6);border-bottom:1px solid rgba(255,255,255,.06);z-index:20}
    .nav{max-width:1100px;margin:auto;padding:14px 18px;display:flex;align-items:center;gap:14px}
    .brand{font-weight:800;letter-spacing:.3px}
    .spacer{flex:1}
    a,button{color:var(--fg)}
    main{flex:1;display:grid;grid-template-rows:1fr auto;}

    /* Card */
    .wrap{max-width:1100px;margin:22px auto;padding:0 18px;width:100%}
    .card{background:linear-gradient(180deg,rgba(255,255,255,.06),rgba(255,255,255,.02));border:1px solid rgba(255,255,255,.08);box-shadow:0 10px 30px rgba(0,0,0,.35);border-radius:20px;overflow:hidden}

    /* Video area */
    .player{position:relative;background:#000}
    video{width:100%;height:70vh;max-height:76vh;display:block;background:#000}
    .badge{position:absolute;top:12px;left:12px;background:rgba(0,0,0,.5);backdrop-filter:blur(4px);border:1px solid rgba(255,255,255,.15);padding:6px 10px;border-radius:999px;font-size:12px;color:#dce7f3}

    /* Controls Row */
    .controls{display:flex;flex-wrap:wrap;gap:10px;align-items:center;padding:14px;background:var(--card)}
    .btn{appearance:none;border:none;outline:none;background:#171c22;border:1px solid rgba(255,255,255,.1);padding:10px 14px;border-radius:12px;cursor:pointer;transition:.2s;display:inline-flex;align-items:center;gap:8px}
    .btn:hover{transform:translateY(-1px);box-shadow:0 8px 24px rgba(0,0,0,.25)}
    .btn:focus{box-shadow:0 0 0 6px var(--ring)}
    .btn.alt{background:#0f1318}
    .row-spacer{flex:1}
    .time{font-variant-numeric:tabular-nums;color:var(--muted)}
    input[type="range"]{accent-color:var(--accent)}

    /* Footer */
    footer{border-top:1px solid rgba(255,255,255,.06);color:var(--muted)}
    .foot{max-width:1100px;margin:auto;padding:16px 18px;font-size:14px;display:flex;gap:10px;align-items:center;flex-wrap:wrap}

    /* Responsive tweaks */
    @media (max-width:640px){
      video{height:54vh}
      .controls{padding:10px}
      .btn{padding:9px 12px}
    }
  </style>
</head>
<body>
  <header>
    <div class="nav">
      <div class="brand">🎬 My Video Site</div>
      <div class="spacer"></div>
      <a href="#" id="openLocal" class="btn" style="text-decoration:none">Open File</a>
      <a href="#" id="muteToggle" class="btn alt" style="text-decoration:none">Mute</a>
    </div>
  </header>

  <main>
    <div class="wrap">
      <div class="card">
        <div class="player">
          <!-- Put your video file in the same folder as this HTML and keep the filename the same -->
          <video id="vid" playsinline controls preload="metadata" poster="">
            <source src="WhatsApp Video 2025-08-22 at 01.26.34_7aaac6ef.mp4" type="video/mp4" />
            <!-- You can add more formats for wider support
            <source src="movie.webm" type="video/webm" />
            -->
            Your browser does not support HTML5 video.
          </video>
          <div class="badge" id="status">Ready</div>
        </div>
        <div class="controls">
          <button class="btn" id="playBtn">▶️ Play</button>
          <button class="btn" id="pauseBtn">⏸️ Pause</button>
          <button class="btn" id="replayBtn">⟲ Replay</button>
          <button class="btn" id="pipBtn">🗔 Picture‑in‑Picture</button>
          <button class="btn" id="fsBtn">⛶ Fullscreen</button>

          <div class="row-spacer"></div>
          <span class="time" id="timeTxt">00:00 / 00:00</span>
          <input id="seek" type="range" min="0" max="100" step="0.1" value="0" style="width:220px" />
          <input id="vol" type="range" min="0" max="1" step="0.02" value="1" title="Volume" style="width:110px" />
          <a class="btn alt" id="downloadBtn" download
             href="WhatsApp Video 2025-08-22 at 01.26.34_7aaac6ef.mp4">⬇️ Download</a>
        </div>
      </div>
    </div>

    <section class="wrap" style="opacity:.9">
      <div class="card" style="padding:18px 18px 22px 18px">
        <h2 style="margin:6px 0 12px 0">How to use</h2>
        <ol style="margin:0 0 10px 18px;line-height:1.7">
          <li>Keep your video file named exactly <code>WhatsApp Video 2025-08-22 at 01.26.34_7aaac6ef.mp4</code> in the <em>same folder</em> as this HTML file. Or click <strong>Open File</strong> to load any local video without renaming.</li>
          <li>Open this page in any modern browser (Chrome, Edge, Firefox, Safari).</li>
          <li>Hit <strong>Play</strong>, use the seekbar, and toggle <strong>Fullscreen</strong> for an immersive view.</li>
        </ol>
        <p style="color:var(--muted);margin-top:8px">Tip: This player remembers your last watched position per browser. Next time you open, it resumes automatically.</p>
      </div>
    </section>
  </main>

  <footer>
    <div class="foot">© <span id="yr"></span> My Video Site • HTML5 Player</div>
  </footer>

  <input id="filePicker" type="file" accept="video/*" hidden />

  <script>
    const $ = s=>document.querySelector(s);
    const vid = $('#vid');
    const playBtn=$('#playBtn'), pauseBtn=$('#pauseBtn'), fsBtn=$('#fsBtn'), pipBtn=$('#pipBtn'), replayBtn=$('#replayBtn');
    const seek=$('#seek'), vol=$('#vol'), status=$('#status'), timeTxt=$('#timeTxt');
    const downloadBtn=$('#downloadBtn');
    const openLocal=$('#openLocal');
    const picker=$('#filePicker');
    const KEY='player:lastTime:'+ (vid.currentSrc||'default');

    // Update footer year
    $('#yr').textContent = new Date().getFullYear();

    function fmt(t){ if(!isFinite(t)) return '00:00'; const m=Math.floor(t/60).toString().padStart(2,'0'); const s=Math.floor(t%60).toString().padStart(2,'0'); return `${m}:${s}` }

    function setStatus(t){ status.textContent=t }

    // Restore last time
    vid.addEventListener('loadedmetadata',()=>{
      try{
        const k='player:lastTime:'+ (vid.currentSrc||'default');
        const last=+localStorage.getItem(k)||0;
        if(last>0 && last<vid.duration-2){ vid.currentTime=last }
      }catch(err){}
      seek.max=vid.duration||100;
      updateTime();
    });

    // Save time periodically
    setInterval(()=>{
      try{
        const k='player:lastTime:'+ (vid.currentSrc||'default');
        localStorage.setItem(k, String(vid.currentTime||0));
      }catch(err){}
    }, 1000);

    // Buttons
    playBtn.onclick=()=>{ vid.play(); };
    pauseBtn.onclick=()=>{ vid.pause(); };
    replayBtn.onclick=()=>{ vid.currentTime=0; vid.play(); };
    fsBtn.onclick=()=>{ if(document.fullscreenElement){ document.exitFullscreen(); } else { vid.requestFullscreen().catch(()=>{}); } };
    pipBtn.onclick=async()=>{ try{ if(document.pictureInPictureElement){ document.exitPictureInPicture(); } else if(document.pictureInPictureEnabled){ await vid.requestPictureInPicture(); } }catch(e){} };

    // Seek & volume
    seek.oninput=()=>{ vid.currentTime=+seek.value };
    vol.oninput=()=>{ vid.volume=+vol.value };

    function updateTime(){ timeTxt.textContent = `${fmt(vid.currentTime)} / ${fmt(vid.duration)}`; seek.value = vid.currentTime||0 }
    vid.addEventListener('timeupdate', updateTime);
    vid.addEventListener('play',()=>setStatus('Playing'));
    vid.addEventListener('pause',()=>setStatus('Paused'));
    vid.addEventListener('ended',()=>setStatus('Ended'));

    // Open local file
    openLocal.addEventListener('click', (e)=>{ e.preventDefault(); picker.click(); });
    picker.addEventListener('change', ()=>{
      const f=picker.files?.[0]; if(!f) return;
      const url=URL.createObjectURL(f);
      vid.src=url;
      downloadBtn.removeAttribute('download');
      downloadBtn.href=url; // download blob
      setStatus('Loaded local file');
      vid.play();
    });

    // Mute toggle in header
    const muteToggle=document.getElementById('muteToggle');
    function updateMuteBtn(){ muteToggle.textContent = vid.muted? 'Unmute' : 'Mute'; }
    muteToggle.addEventListener('click', (e)=>{ e.preventDefault(); vid.muted=!vid.muted; updateMuteBtn(); });
    vid.addEventListener('volumechange', updateMuteBtn);
    updateMuteBtn();
  </script>
</body>
</html>
