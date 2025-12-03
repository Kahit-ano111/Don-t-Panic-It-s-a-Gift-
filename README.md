<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Collage UI — Alt</title>
    <style>
      :root {
        --pink: #ffc1d9;
        --paper: #ffffff;
        --paper2: #f8f1ea;
        --shadow: 0 20px 50px rgba(0,0,0,0.18);
        --muted: #6b7280;
        --ink: #111827;
        --accent: #e91e63;
        --green: #73d719;
        --duration: 300ms;
        --easing: ease;
      }
      @media (prefers-reduced-motion: reduce) { :root { --duration: 0ms; } }
      *, *::before, *::after { box-sizing: border-box; }
      html, body { height: 100%; }
      body { margin: 0; background: var(--pink); font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial; color: var(--ink); }
      .scene { min-height: 100vh; display: grid; place-items: center; padding: 32px; }
      .board { position: relative; width: min(1100px, 94vw); height: 620px; }
      .phone { position: absolute; left: 6%; top: 10%; width: 380px; border-radius: 30px; background: #fff; box-shadow: var(--shadow); transform: rotate(-10deg); overflow: hidden; }
      .bar { display: flex; align-items: center; justify-content: space-between; padding: 14px 16px; font-weight: 700; }
      .bar .brand { display: inline-flex; align-items: center; gap: 10px; color: var(--ink); }
      .icons { display: inline-flex; align-items: center; gap: 12px; color: var(--ink); }
      .i { width: 22px; height: 22px; }
      .media { width: 100%; aspect-ratio: 1 / 1; display: grid; place-items: center; background: var(--green); position: relative; overflow: hidden; }
      .controls { display: flex; align-items: center; justify-content: space-between; padding: 14px 16px; }
      .meta { display: flex; align-items: center; gap: 10px; padding: 0 16px 16px; color: var(--muted); }
      .pad { position: absolute; right: 0; top: -4%; width: 640px; transform: rotate(7deg); }
      .sheet { position: relative; border-radius: 18px; box-shadow: var(--shadow); background: var(--paper); height: 100%; }
      .sheet::after { content: ""; position: absolute; inset: 0; border-radius: 18px; background-image: repeating-linear-gradient(0deg, transparent 0 24px, #eef1f5 25px 25px), repeating-linear-gradient(90deg, transparent 0 24px, #eef1f5 25px 25px); mix-blend-mode: multiply; opacity: 0.65; }
      .under { position: absolute; inset: 18px 18px auto auto; width: 92%; height: 92%; border-radius: 16px; transform: rotate(-4deg); background: var(--paper2); box-shadow: 0 10px 28px rgba(0,0,0,0.14); }
      .tear { position: absolute; right: 16px; bottom: -10px; width: 220px; height: 90px; background: var(--paper2); border-radius: 10px; transform: rotate(3deg); box-shadow: 0 8px 24px rgba(0,0,0,0.12); }
      .letter { position: absolute; inset: 24px; padding: 24px 30px; color: var(--ink); }
      .letter h2 { margin: 0 0 12px; font-size: 1.6rem; letter-spacing: 0.01em; }
      .letter p { margin: 0 0 12px; line-height: 1.75; font-size: 1rem; color: var(--ink); }
      @media (max-width: 720px) {
        .board { height: 520px; }
        .phone { width: 300px; left: 4%; transform: rotate(-8deg); }
        .pad { width: 440px; transform: rotate(6deg); }
      }
      .fade-enter { opacity: 0; transform: translateY(14px) scale(0.98); transition: opacity var(--duration) var(--easing), transform var(--duration) var(--easing); }
      .fade-enter.show { opacity: 1; transform: translateY(0) scale(1); }
      .control { display: flex; align-items: center; gap: 10px; justify-content: center; padding: 16px; }
      .control input[type="url"] { width: 100%; max-width: 420px; padding: 10px 12px; border-radius: 10px; border: 1px solid rgba(0,0,0,0.15); }
      .control button { appearance: none; border: 0; border-radius: 9999px; padding: 10px 14px; background: #fff; box-shadow: 0 6px 16px rgba(0,0,0,0.12); cursor: pointer; font-weight: 600; }
    </style>
  </head>
  <body>
    <section class="scene">
      <div class="board">
        <div class="phone fade-enter show">
          <div class="bar">
            <div class="brand">
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><circle cx="12" cy="12" r="10" fill="currentColor" opacity="0.15"/><circle cx="12" cy="12" r="3" fill="currentColor"/></svg>
              <span>❤️ Happy Valentines</span>
            </div>
            <div class="icons">
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M21 15a2 2 0 0 1-2 2H8l-5 5V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2v10z"/></svg>
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M3 20l18-8-18-8v6l12 2-12 2v6z"/></svg>
            </div>
          </div>
          <div class="media"><img id="mediaImg" alt="Selected image" style="display:none;width:100%;height:100%;object-fit:cover"/></div>
          <div class="controls">
            <div class="icons">
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M12 21s-8-4.438-8-10a5 5 0 0 1 9-3 5 5 0 0 1 9 3c0 5.562-8 10-8 10z"/></svg>
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M21 15a2 2 0 0 1-2 2H8l-5 5V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2v10z"/></svg>
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M12 5v14M5 12h14"/></svg>
              <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><circle cx="12" cy="8" r="4" fill="currentColor"/><path fill="currentColor" d="M4 20c0-4 4-6 8-6s8 2 8 6"/></svg>
            </div>
            <svg class="i" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M6 21l6-4 6 4V3H6z"/></svg>
          </div>
          <div class="meta"><span>❤️ 987</span><span>•</span><span>We Fall inn love in October</span></div>
        </div>
        <div class="pad fade-enter show" style="height: 520px;">
          <div class="under"></div>
          <div class="sheet">
            <div class="letter">
              <h2>My Love,</h2>
              <p>From the moment you came into my life, everything felt a little brighter, a little softer, and a lot more meaningful. I never thought someone could make even the smallest moments feel unforgettable, but you do—just by being you.</p>
              <p>I love the way you listen, the way you laugh, and the way you make ordinary days feel like something worth writing about. You have become my favorite thought, my safest place, and the reason I look forward to tomorrow. With you, I’ve learned that love isn’t always grand gestures—it’s the quiet assurance that someone truly cares.</p>
              <p>Thank you for loving me in ways I never knew I needed. I promise to hold your heart gently, to support your dreams as if they were my own, and to choose you every single day.</p>
            </div>
          </div>
          <div class="tear"></div>
        </div>
      </div>
    </section>
    <script>
      (function () {
        var media = document.querySelector('.media');
        var img = document.getElementById('mediaImg');
        var urlInput = document.getElementById('imgUrl');
        var urlSetBtn = document.getElementById('urlSet');
        function show(src) { img.src = src; img.style.display = 'block'; }
        function setUrl(url) { if (!url) return; var v = url.trim(); show(v); }
        var params = new URLSearchParams(location.search);
        var q = params.get('img');
        if (q) { setUrl(q); } else { img.src = 'pic2.jfif'; img.style.display = 'block'; }
        urlSetBtn.addEventListener('click', function () { setUrl(urlInput.value); });
      })();
    </script>
  </body>
  </html>
