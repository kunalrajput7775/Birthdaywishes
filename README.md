# Birthdaywishes
A simple thank a note
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🎉 Happy Birthday!</title>
  <style>
    :root{
      --bg1:#0f1020; --bg2:#1b1740; --accent:#ff73c6; --accent2:#7cf0ff; --gold:#ffd166;
      --card:#121225cc; --white:#ffffff; --muted:#cbd5e1;
    }
    *{box-sizing:border-box}
    html,body{height:100%;}
    body{
      margin:0; font-family:system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Helvetica,Arial,sans-serif;
      color:var(--white); background: radial-gradient(1200px 800px at 20% -10%, #2e1b74 0%, transparent 60%),
                          radial-gradient(1000px 700px at 110% 10%, #1a5b7a 0%, transparent 60%),
                          linear-gradient(160deg, var(--bg1), var(--bg2));
      overflow:hidden;
    }

    .stars{position:fixed; inset:0; background:transparent; pointer-events:none;}
    .stars::before,.stars::after{
      content:""; position:absolute; inset:0; background-repeat:repeat; opacity:.4; filter:drop-shadow(0 0 2px #fff);
    }
    .stars::before{background-image:radial-gradient(#fff 1px, transparent 1px); background-size:3px 3px; animation: twinkle 6s linear infinite;}
    .stars::after{background-image:radial-gradient(#fff 1px, transparent 1px); background-size:5px 5px; animation: twinkle 9s linear infinite reverse;}
    @keyframes twinkle{from{transform:translateY(0)} to{transform:translateY(5px)}}

    .wrap{position:relative; min-height:100%; display:grid; place-items:center; padding:24px}

    .card{
      width:min(720px, 92vw); border-radius:24px; background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02));
      border:1px solid rgba(255,255,255,.15); box-shadow:0 15px 40px rgba(0,0,0,.45);
      padding:28px 28px 22px; backdrop-filter: blur(8px);
    }

    .eyebrow{font-size:.9rem; letter-spacing:.2em; text-transform:uppercase; color:var(--muted)}
    h1{margin:.25rem 0 0; font-size:clamp(2rem, 4.5vw, 3.25rem); line-height:1.1}
    h1 .gradient{background:linear-gradient(90deg, var(--gold), var(--accent), var(--accent2)); -webkit-background-clip:text; background-clip:text; color:transparent}
    p.lede{margin:.75rem 0 1.25rem; color:#e2e8f0; font-size:clamp(1rem, 2.2vw, 1.2rem)}

    .btns{display:flex; flex-wrap:wrap; gap:10px; align-items:center}
    button,.linklike{
      appearance:none; border:none; cursor:pointer; border-radius:999px; padding:10px 16px; font-weight:600; font-size:15px;
      background:linear-gradient(180deg, rgba(255,255,255,.15), rgba(255,255,255,.05)); color:#fff;
      border:1px solid rgba(255,255,255,.2); box-shadow:0 6px 16px rgba(0,0,0,.35);
      transition: transform .06s ease, box-shadow .2s ease, background .2s ease;
    }
    button:hover{transform:translateY(-1px);}
    button.primary{background:linear-gradient(90deg, var(--accent), var(--accent2)); color:#0b1020}
    .linklike{background:transparent; border-color:transparent; padding:0 10px; text-decoration:underline;}

    .wish-box{margin:14px 0 16px; background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.12);
      border-radius:16px; padding:14px}
    .wish{white-space:pre-wrap; font-size:1.05rem; line-height:1.55}

    .footer{display:flex; justify-content:space-between; align-items:center; gap:10px; color:var(--muted); font-size:.95rem; margin-top:12px}

    .balloon{position:fixed; bottom:-140px; width:60px; height:80px; border-radius:50% 50% 47% 53% / 63% 63% 37% 37%; opacity:.85; filter:drop-shadow(0 8px 12px rgba(0,0,0,.35));}
    .balloon:after{content:""; position:absolute; bottom:-18px; left:50%; width:2px; height:90px; background:rgba(255,255,255,.35)}
    .balloon:nth-child(1){left:8%; background:#ff7ac3; animation:float 13s linear infinite;}
    .balloon:nth-child(2){left:22%; background:#7af0ff; animation:float 16s linear infinite 1s;}
    .balloon:nth-child(3){left:42%; background:#ffd166; animation:float 14s linear infinite .5s;}
    .balloon:nth-child(4){left:66%; background:#b4f46c; animation:float 15s linear infinite 1.3s;}
    .balloon:nth-child(5){left:84%; background:#caa8ff; animation:float 12s linear infinite .8s;}
    @keyframes float{0%{transform:translateY(0) rotate(-4deg)} 50%{transform:translateY(-60vh) rotate(4deg)} 100%{transform:translateY(-120vh) rotate(-3deg)}}

    canvas#confetti{position:fixed; inset:0; pointer-events:none}

    .row{display:flex; gap:8px; align-items:center; flex-wrap:wrap}
    input[type="text"]{flex:1; min-width:140px; border-radius:10px; background:#0f1427; border:1px solid rgba(255,255,255,.2); color:#fff; padding:10px 12px}
  </style>
</head>
<body>
  <div class="stars"></div>
  <canvas id="confetti"></canvas>
  <div class="balloon"></div>
  <div class="balloon"></div>
  <div class="balloon"></div>
  <div class="balloon"></div>
  <div class="balloon"></div>

  <main class="wrap">
    <section class="card" role="region" aria-label="Birthday card">
      <div class="eyebrow">It's your day 🎂</div>
      <h1>Happy Birthday, <span id="name" class="gradient">Anshu</span>!</h1>
      <p class="lede">Wishing you laughter, love, and a year sprinkled with adventures, cozy moments, and sweet surprises.</p>

      <div class="wish-box">
        <div id="wish" class="wish" contenteditable>
🎉 Dear Anshu —
May your day be filled with bright smiles, warm hugs, and a mountain of cake.
✨ Keep shining, keep dreaming, and may this year bring you wonderful new adventures.
— With love,
<span id="sender">Kunal</span>
        </div>
      </div>

      <div class="row" style="margin:10px 0 14px">
        <input id="nameInput" type="text" placeholder="Recipient name (e.g., Anshu)" value="Anshu" />
        <input id="fromInput" type="text" placeholder="Your name (e.g., Kunal)" value="Kunal" />
      </div>

      <div class="btns">
        <button class="primary" id="celebrateBtn">Celebrate 🎊</button>
        <button id="copyBtn">Copy Wish</button>
        <button id="shareBtn">Share…</button>
        <button id="downloadBtn">Save as Image</button>
        <span class="linklike" id="resetBtn" title="Reset">Reset</span>
      </div>

      <div class="footer">
        <span>Tip: Edit the message above directly. It’s live!</span>
        <span><a href="#" id="linkOut" style="color:var(--gold); text-decoration:none">Create a shareable link</a></span>
      </div>
    </section>
  </main>

  <script>
    const $ = (s, p=document) => p.querySelector(s);
    const nameEl = $('#name');
    const wishEl = $('#wish');
    const senderEl = $('#sender');
    const nameInput = $('#nameInput');
    const fromInput = $('#fromInput');

    const params = new URLSearchParams(location.search);
    if (params.get('name')) { setName(params.get('name')); nameInput.value = params.get('name'); }
    if (params.get('from')) { senderEl.textContent = params.get('from'); fromInput.value = params.get('from'); }
    if (params.get('msg')) { wishEl.innerText = decodeURIComponent(params.get('msg')); }

    function setName(n){ nameEl.textContent = (n||'Anshu'); document.title = `🎉 Happy Birthday, ${nameEl.textContent}!`; }

    nameInput.addEventListener('input', e => setName(e.target.value));
    fromInput.addEventListener('input', e => senderEl.textContent = e.target.value || 'Kunal');

    $('#resetBtn').addEventListener('click', () => {
      nameInput.value = 'Anshu';
      fromInput.value = 'Kunal';
      setName('Anshu');
      senderEl.textContent = 'Kunal';
      wishEl.innerText = `🎉 Dear Anshu —\nMay your day be filled with bright smiles, warm hugs, and a mountain of cake.\n✨ Keep shining, keep dreaming, and may this year bring you wonderful new adventures.\n— With love,\nKunal`;
      fire(140);
      history.replaceState({}, '', location.pathname);
    });

    $('#copyBtn').addEventListener('click', async() => {
      try{
        await navigator.clipboard.writeText(wishEl.innerText);
        flash('Copied!');
      }catch{ alert('Copy failed — you can select the text and copy manually.'); }
    });

    $('#shareBtn').addEventListener('click', async() => {
      const title = `Happy Birthday, ${nameEl.textContent}!`;
      const text = wishEl.innerText;
      const url = makeShareURL();
      if (navigator.share){
        try{ await navigator.share({title, text, url}); }catch{}
      } else {
        await navigator.clipboard.writeText(`${title}\n\n${text}\n\n${url}`);
        flash('Share link copied!');
      }
    });

    $('#linkOut').addEventListener('click', (e) => {
      e.preventDefault();
      const url = makeShareURL();
      navigator.clipboard.writeText(url).then(()=>flash('Link copied!'));
    });

    function makeShareURL(){
      const q = new URLSearchParams({
        name: nameEl.textContent,
        from: senderEl.textContent,
        msg: wishEl.innerText.trim()
      });
      const url = `${location.origin}${location.pathname}?${q.toString()}`;
      return url;
    }

    $('#downloadBtn').addEventListener('click', async () => {
      const node = document.querySelector('.card');
      const {width, height} = node.getBoundingClientRect();
      const s = new XMLSerializer().serializeToString(elToSVG(node, width, height));
      const svgBlob = new Blob([s], {type: 'image/svg+xml;charset=utf-8'});
      const url = URL.createObjectURL(svgBlob);
      const img = new Image();
      img.onload = () => {
        const canvas = document.createElement('canvas');
        canvas.width = Math.ceil(width*2); canvas.height = Math.ceil(height*2);
        const ctx = canvas.getContext('2d');
        ctx.scale(2,2); ctx.drawImage(img, 0, 0);
        URL.revokeObjectURL(url);
        const a = document.createElement('a');
        a.download = `Happy-Birthday-${nameEl.textContent}.png`;
        a.href = canvas.toDataURL('image/png');
        a.click();
      };
      img.src = url;
      flash('Generating image…');
    });

    function elToSVG(el, w, h){
      const clone = el.cloneNode(true);
      clone.style.margin = '0';
      const xmlns = 'http://www.w3.org/2000/svg';
      const svg = document.createElementNS(xmlns, 'svg');
      svg.setAttribute('xmlns', xmlns);
      svg.setAttribute('width', w);
      svg.setAttribute('height', h);
      const fo = document.createElementNS(xmlns, 'foreignObject');
      fo.setAttribute('width', '100%');
      fo.setAttribute('height', '100%');
      fo.appendChild(clone);
      svg.appendChild(fo);
      return svg;
    }

    $('#celebrateBtn').addEventListener('click', () => fire(200));

    const confetti = document.getElementById('confetti');
    const ctx = confetti.getContext('2d');
    let pieces = [], lastT = 0;

    function resize(){ confetti.width = innerWidth; confetti.height = innerHeight; }
    addEventListener('resize', resize); resize();

    function fire(n=150){
      for(let i=0;i<n;i++){
        pieces.push({
          x: Math.random()*confetti.width,
          y: -20,
          w: 6+Math.random()*6,
          h: 8+Math.random()*10,
          vy: 2+Math.random()*3.5,
          vx: -1.5+Math.random()*3,
          rot: Math.random()*Math.PI,
          vr: -0.25+Math.random()*0.5,
          hue: Math.floor(Math.random()*360),
          alpha: 1
        });
      }
    }

    function tick(t){
      const dt = Math.min(32, t - (lastT||t)); lastT = t;
      ctx.clearRect(0,0,confetti.width, confetti.height);
      pieces = pieces.filter(p => p.alpha>0 && p.y<confetti.height+40);
      for(const p of pieces){
        p.vy += 0.006*dt;
        p.x += p.vx * (dt/16);
        p.y += p.vy * (dt/16);
        p.rot += p.vr * (dt/16);
        p.alpha -= 0.002 * (dt/16);
        ctx.save();
        ctx.globalAlpha = Math.max(0, p.alpha);
        ctx.translate(p.x, p.y);
        ctx.rotate(p.rot);
        ctx.fillStyle = `hsl(${p.hue} 90% 60%)`;
        ctx.fillRect(-p.w/2, -p.h/2, p.w, p.h);
        ctx.restore();
      }
      requestAnimationFrame(tick);
    }
    requestAnimationFrame(tick);
    fire(140);

    function flash(msg){
      const n = document.createElement('div');
      n.textContent = msg; n.style.position='fixed'; n.style.bottom='18px'; n.style.left='50%'; n.style.transform='translateX(-50%)';
      n.style.background='rgba(0,0,0,.7)'; n.style.color='#fff'; n.style.padding='10px 14px'; n.style.borderRadius='999px'; n.style.boxShadow='0 6px 18px rgba(0,0,0,.4)';
      n.style.zIndex='9999'; document.body.appendChild(n); setTimeout(()=>n.remove(), 1400);
    }
  </script>
</body>
</html>
