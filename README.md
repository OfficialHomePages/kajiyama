<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>梶山秀一 | HIDEO KAJIYAMA</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+JP:wght@300;400;700&family=Bebas+Neue&family=Noto+Sans+JP:wght@300;400&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #0a0a0a;
    --white: #f5f0e8;
    --accent: #c8a96e;
    --accent2: #8b5e3c;
    --glass: rgba(245,240,232,0.04);
    --border: rgba(200,169,110,0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'Noto Sans JP', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease, width 0.3s, height 0.3s, background 0.3s;
    transform: translate(-50%, -50%);
  }
  .cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1px solid rgba(200,169,110,0.5);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: left 0.08s ease, top 0.08s ease, width 0.3s, height 0.3s;
  }
  body:hover .cursor { opacity: 1; }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9990;
    opacity: 0.4;
  }

  /* ====== HERO ====== */
  #hero {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse 70% 60% at 50% 40%, rgba(139,94,60,0.18) 0%, transparent 70%);
    animation: pulse-bg 6s ease-in-out infinite alternate;
  }

  @keyframes pulse-bg {
    from { opacity: 0.6; transform: scale(1); }
    to   { opacity: 1;   transform: scale(1.08); }
  }

  .hero-lines {
    position: absolute;
    inset: 0;
    overflow: hidden;
  }
  .hero-lines span {
    position: absolute;
    left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    animation: line-slide 8s linear infinite;
    opacity: 0;
  }
  .hero-lines span:nth-child(1) { top: 20%; animation-delay: 0s; }
  .hero-lines span:nth-child(2) { top: 50%; animation-delay: 2.5s; }
  .hero-lines span:nth-child(3) { top: 80%; animation-delay: 5s; }

  @keyframes line-slide {
    0%   { opacity: 0; transform: scaleX(0); transform-origin: left; }
    20%  { opacity: 1; }
    80%  { opacity: 1; }
    100% { opacity: 0; transform: scaleX(1); transform-origin: left; }
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(5rem, 15vw, 14rem);
    letter-spacing: 0.06em;
    line-height: 0.85;
    text-align: center;
    position: relative;
    z-index: 2;
    animation: fade-up 1.2s cubic-bezier(.16,1,.3,1) both;
  }

  .hero-name .en {
    display: block;
    background: linear-gradient(135deg, var(--white) 30%, var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-name .jp {
    display: block;
    font-family: 'Noto Serif JP', serif;
    font-size: clamp(1.2rem, 3vw, 2.8rem);
    font-weight: 300;
    letter-spacing: 0.4em;
    -webkit-text-fill-color: var(--accent);
    margin-top: 0.5rem;
  }

  @keyframes fade-up {
    from { opacity: 0; transform: translateY(40px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .hero-tagline {
    font-size: clamp(0.7rem, 1.2vw, 0.95rem);
    letter-spacing: 0.3em;
    color: rgba(245,240,232,0.4);
    margin-top: 2.5rem;
    position: relative; z-index: 2;
    animation: fade-up 1.4s 0.3s cubic-bezier(.16,1,.3,1) both;
  }

  .scroll-indicator {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    opacity: 0.5;
    animation: fade-up 1.6s 0.6s both;
  }
  .scroll-indicator span {
    font-size: 0.65rem;
    letter-spacing: 0.3em;
    color: var(--accent);
  }
  .scroll-line {
    width: 1px;
    height: 50px;
    background: linear-gradient(to bottom, var(--accent), transparent);
    animation: scroll-anim 2s ease-in-out infinite;
  }
  @keyframes scroll-anim {
    0%,100% { transform: scaleY(1); opacity: 0.5; }
    50%      { transform: scaleY(0.3); opacity: 1; }
  }

  /* ====== NAV ====== */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    padding: 1.5rem 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    backdrop-filter: blur(12px);
    background: rgba(10,10,10,0.6);
    border-bottom: 1px solid var(--border);
    transition: padding 0.3s;
  }
  nav .logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem;
    letter-spacing: 0.1em;
    color: var(--accent);
    text-decoration: none;
  }
  nav ul {
    list-style: none;
    display: flex;
    gap: 2.5rem;
  }
  nav a {
    color: rgba(245,240,232,0.6);
    text-decoration: none;
    font-size: 0.75rem;
    letter-spacing: 0.2em;
    transition: color 0.3s;
  }
  nav a:hover { color: var(--accent); }

  /* ====== SECTIONS ====== */
  section {
    padding: 7rem 5vw;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-label {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 0.75rem;
    letter-spacing: 0.4em;
    color: var(--accent);
    margin-bottom: 0.8rem;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.8s ease;
  }
  .section-title {
    font-family: 'Noto Serif JP', serif;
    font-size: clamp(2rem, 5vw, 4rem);
    font-weight: 300;
    line-height: 1.2;
    margin-bottom: 3rem;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.8s 0.1s ease;
  }
  .visible .section-label,
  .visible .section-title { opacity: 1; transform: translateY(0); }

  /* ====== SOCIAL ====== */
  #social .cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }

  .social-card {
    border: 1px solid var(--border);
    background: var(--glass);
    backdrop-filter: blur(8px);
    padding: 2.5rem;
    border-radius: 2px;
    text-decoration: none;
    color: var(--white);
    display: flex;
    flex-direction: column;
    gap: 1rem;
    position: relative;
    overflow: hidden;
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease, border-color 0.3s, background 0.3s;
  }
  .visible .social-card { opacity: 1; transform: translateY(0); }
  .visible .social-card:nth-child(2) { transition-delay: 0.15s; }

  .social-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(200,169,110,0.06), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }
  .social-card:hover { border-color: var(--accent); background: rgba(200,169,110,0.05); }
  .social-card:hover::before { opacity: 1; }

  .social-icon {
    font-size: 2rem;
    line-height: 1;
  }
  .social-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.8rem;
    letter-spacing: 0.1em;
    color: var(--accent);
  }
  .social-desc {
    font-size: 0.8rem;
    letter-spacing: 0.1em;
    color: rgba(245,240,232,0.5);
  }
  .social-arrow {
    position: absolute;
    bottom: 1.5rem; right: 1.5rem;
    font-size: 1.2rem;
    color: var(--accent);
    opacity: 0;
    transform: translate(-6px, 6px);
    transition: all 0.3s;
  }
  .social-card:hover .social-arrow { opacity: 1; transform: translate(0, 0); }

  /* Divider */
  .divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 0 5vw;
    max-width: 1200px;
  }

  /* ====== BLOG ====== */
  #blog .blog-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    margin-bottom: 3rem;
  }

  .admin-badge {
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    color: var(--accent);
    border: 1px solid var(--border);
    padding: 0.4rem 0.8rem;
    border-radius: 2px;
    background: rgba(200,169,110,0.05);
  }

  .blog-new {
    margin-bottom: 2rem;
    display: none;
  }
  .blog-new.active { display: block; }
  .blog-new textarea,
  .blog-new input {
    width: 100%;
    background: var(--glass);
    border: 1px solid var(--border);
    color: var(--white);
    padding: 1rem;
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 0.9rem;
    border-radius: 2px;
    margin-bottom: 0.8rem;
    resize: vertical;
    outline: none;
    transition: border-color 0.3s;
  }
  .blog-new textarea:focus,
  .blog-new input:focus { border-color: var(--accent); }
  .blog-new textarea { min-height: 120px; }

  .btn {
    background: var(--accent);
    color: var(--black);
    border: none;
    padding: 0.8rem 2rem;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1rem;
    letter-spacing: 0.15em;
    cursor: none;
    border-radius: 2px;
    transition: background 0.3s, transform 0.2s;
  }
  .btn:hover { background: var(--white); transform: translateY(-2px); }
  .btn-sm {
    padding: 0.5rem 1.2rem;
    font-size: 0.85rem;
  }
  .btn-outline {
    background: transparent;
    border: 1px solid var(--accent);
    color: var(--accent);
  }
  .btn-outline:hover { background: var(--accent); color: var(--black); }

  .blog-posts { display: flex; flex-direction: column; gap: 1px; }

  .post-item {
    border-bottom: 1px solid var(--border);
    padding: 2rem 0;
    display: grid;
    grid-template-columns: 100px 1fr auto;
    gap: 2rem;
    align-items: start;
    opacity: 0;
    transform: translateX(-20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
    cursor: none;
  }
  .visible .post-item { opacity: 1; transform: translateX(0); }
  .visible .post-item:nth-child(2) { transition-delay: 0.1s; }
  .visible .post-item:nth-child(3) { transition-delay: 0.2s; }

  .post-date {
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    color: var(--accent);
    font-family: 'Bebas Neue', sans-serif;
    padding-top: 0.2rem;
  }
  .post-title {
    font-family: 'Noto Serif JP', serif;
    font-size: 1.1rem;
    font-weight: 400;
    margin-bottom: 0.5rem;
    transition: color 0.3s;
  }
  .post-item:hover .post-title { color: var(--accent); }
  .post-body {
    font-size: 0.82rem;
    color: rgba(245,240,232,0.5);
    line-height: 1.8;
  }
  .post-tag {
    font-size: 0.6rem;
    letter-spacing: 0.2em;
    border: 1px solid var(--border);
    padding: 0.2rem 0.6rem;
    color: rgba(245,240,232,0.4);
    border-radius: 2px;
    white-space: nowrap;
    margin-top: 0.3rem;
    display: inline-block;
  }
  .post-expand { display: none; margin-top: 1rem; font-size: 0.85rem; line-height: 1.8; color: rgba(245,240,232,0.7); }
  .post-expand.active { display: block; animation: fade-up 0.4s ease; }

  /* ====== COMMENTS ====== */
  #comments {
    background: rgba(245,240,232,0.02);
    max-width: 100%;
    padding: 7rem 5vw;
  }
  #comments > * { max-width: 1200px; margin-left: auto; margin-right: auto; }

  .comment-form {
    border: 1px solid var(--border);
    background: var(--glass);
    padding: 2.5rem;
    border-radius: 2px;
    margin-bottom: 3rem;
  }
  .comment-form h3 {
    font-family: 'Noto Serif JP', serif;
    font-size: 1rem;
    font-weight: 400;
    margin-bottom: 1.5rem;
    color: var(--accent);
    letter-spacing: 0.1em;
  }
  .input-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-bottom: 1rem; }
  .comment-form input,
  .comment-form textarea {
    width: 100%;
    background: rgba(245,240,232,0.03);
    border: 1px solid var(--border);
    color: var(--white);
    padding: 0.9rem 1rem;
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 0.85rem;
    border-radius: 2px;
    outline: none;
    transition: border-color 0.3s;
  }
  .comment-form input:focus,
  .comment-form textarea:focus { border-color: var(--accent); }
  .comment-form textarea { min-height: 100px; resize: vertical; margin-bottom: 1rem; }

  .comments-list { display: flex; flex-direction: column; gap: 1px; }

  .comment-item {
    padding: 1.8rem 0;
    border-bottom: 1px solid rgba(200,169,110,0.1);
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 1.5rem;
    opacity: 0;
    animation: fade-up 0.5s ease forwards;
  }

  .comment-avatar {
    width: 44px; height: 44px;
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.1rem;
    color: var(--black);
    flex-shrink: 0;
  }
  .comment-meta {
    display: flex;
    gap: 1rem;
    align-items: center;
    margin-bottom: 0.5rem;
  }
  .comment-id {
    font-family: 'Bebas Neue', sans-serif;
    letter-spacing: 0.1em;
    color: var(--accent);
    font-size: 0.95rem;
  }
  .comment-time {
    font-size: 0.65rem;
    color: rgba(245,240,232,0.3);
    letter-spacing: 0.1em;
  }
  .comment-text {
    font-size: 0.88rem;
    line-height: 1.9;
    color: rgba(245,240,232,0.7);
  }

  /* ====== FOOTER ====== */
  footer {
    text-align: center;
    padding: 4rem 2rem;
    border-top: 1px solid var(--border);
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    color: rgba(245,240,232,0.25);
  }
  footer .footer-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2rem;
    letter-spacing: 0.15em;
    color: rgba(200,169,110,0.3);
    display: block;
    margin-bottom: 1rem;
  }

  /* Password modal */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(10,10,10,0.85);
    backdrop-filter: blur(8px);
    z-index: 2000;
    display: none;
    align-items: center;
    justify-content: center;
  }
  .modal-overlay.active { display: flex; }
  .modal {
    border: 1px solid var(--border);
    background: #111;
    padding: 3rem;
    border-radius: 2px;
    width: min(400px, 90vw);
    animation: fade-up 0.4s ease;
  }
  .modal h2 {
    font-family: 'Noto Serif JP', serif;
    font-weight: 300;
    font-size: 1.3rem;
    margin-bottom: 0.5rem;
    color: var(--accent);
  }
  .modal p { font-size: 0.8rem; color: rgba(245,240,232,0.4); margin-bottom: 1.5rem; letter-spacing: 0.05em; }
  .modal input {
    width: 100%;
    background: var(--glass);
    border: 1px solid var(--border);
    color: var(--white);
    padding: 0.9rem 1rem;
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 0.9rem;
    border-radius: 2px;
    outline: none;
    margin-bottom: 1rem;
    transition: border-color 0.3s;
  }
  .modal input:focus { border-color: var(--accent); }
  .modal-btns { display: flex; gap: 1rem; }
  .modal-error { font-size: 0.75rem; color: #e06060; margin-top: 0.5rem; display: none; }

  @media (max-width: 700px) {
    nav { padding: 1rem 1.5rem; }
    nav ul { gap: 1.2rem; }
    #social .cards { grid-template-columns: 1fr; }
    .post-item { grid-template-columns: 1fr; }
    .post-date { margin-bottom: -1rem; }
    .input-row { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Password Modal -->
<div class="modal-overlay" id="modal">
  <div class="modal">
    <h2>管理者ログイン</h2>
    <p>梶山秀一専用 — ブログ投稿パスワードを入力してください</p>
    <input type="password" id="adminPw" placeholder="パスワード">
    <div class="modal-error" id="pwError">パスワードが違います</div>
    <div class="modal-btns">
      <button class="btn" onclick="checkPassword()">ログイン</button>
      <button class="btn btn-outline" onclick="closeModal()">キャンセル</button>
    </div>
  </div>
</div>

<!-- NAV -->
<nav>
  <a class="logo" href="#hero">梶山秀一HP</a>
  <ul>
    <li><a href="#social">SNS</a></li>
    <li><a href="#blog">ブログ</a></li>
    <li><a href="#comments">掲示板</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="hero">
  <div class="hero-bg"></div>
  <div class="hero-lines">
    <span></span><span></span><span></span>
  </div>
  <h1 class="hero-name">
    <span class="en">HIDEO<br>KAJIYAMA</span>
    <span class="jp">梶山 秀一</span>
  </h1>
  <p class="hero-tagline">CREATOR / THINKER / EXPLORER</p>
  <div class="scroll-indicator">
    <span>SCROLL</span>
    <div class="scroll-line"></div>
  </div>
</div>

<!-- SOCIAL -->
<section id="social">
  <div class="reveal-block">
    <div class="section-label">— CONNECT</div>
    <div class="section-title">ソーシャル</div>
  </div>
  <div class="cards reveal-block">
    <a class="social-card" href="https://youtube.com/channel/UC2sHMxsa1o0hJ3Sp-kg4Psg?si=9cELgzJLiZtLvY-7" target="_blank">
      <div class="social-icon">▶</div>
      <div class="social-name">YouTube</div>
      <div class="social-desc">YouTube</div>
      <div class="social-arrow">↗</div>
    </a>
    <a class="social-card" href="https://x.com/hideo_exp" target="_blank">
      <div class="social-icon">🐦</div>
      <div class="social-name">Twitter</div>
      <div class="social-desc">@hideo_exp </div>
      <div class="social-arrow">↗</div>
    </a>
  </div>
</section>

<div class="divider"></div>

<!-- BLOG -->
<section id="blog">
  <div class="reveal-block">
    <div class="blog-header">
      <div>
        <div class="section-label">— JOURNAL</div>
        <div class="section-title" style="margin-bottom:0;">ブログ</div>
      </div>
      <div style="display:flex;gap:1rem;align-items:center">
        <span class="admin-badge">ADMIN ONLY</span>
        <button class="btn btn-sm" onclick="openModal()">＋ 投稿</button>
      </div>
    </div>
  </div>

  <div class="blog-new" id="blogNew">
    <input type="text" id="postTitle" placeholder="タイトル">
    <input type="text" id="postTag" placeholder="タグ（例: 日常 / 旅 / 考察）">
    <textarea id="postBody" placeholder="本文を入力..."></textarea>
    <button class="btn" onclick="addPost()">投稿する</button>
    <button class="btn btn-outline" style="margin-left:0.8rem" onclick="cancelPost()">キャンセル</button>
  </div>

  <div class="blog-posts reveal-block" id="blogPosts"></div>
</section>

<div class="divider"></div>

<!-- COMMENTS -->
<div id="comments">
  <div class="reveal-block" style="max-width:1200px;margin:0 auto 3rem">
    <div class="section-label">— COMMUNITY</div>
    <div class="section-title">コメント掲示板</div>
  </div>

  <div class="comment-form reveal-block" style="max-width:1200px;margin:0 auto 3rem">
    <h3>投稿する</h3>
    <div class="input-row">
      <input type="text" id="commentId" placeholder="ID（ハンドルネーム）*" maxlength="20">
    </div>
    <textarea id="commentText" placeholder="コメントを入力..."></textarea>
    <button class="btn" onclick="addComment()">送信する</button>
  </div>

  <div class="comments-list" id="commentsList" style="max-width:1200px;margin:0 auto"></div>
</div>

<!-- FOOTER -->
<footer>
  <span class="footer-name">HIDEO KAJIYAMA</span>
  © 2026 梶山秀一. All rights reserved.
</footer>

<script>
// Cursor
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.left = mx + 'px';
  cursor.style.top  = my + 'px';
});
(function animRing() {
  rx += (mx - rx) * 0.12;
  ry += (my - ry) *.12;
  ring.style.left = rx + 'px';
  ring.style.top  = ry + 'px';
  requestAnimationFrame(animRing);
})();
document.querySelectorAll('a,button,.post-item').forEach(el => {
  el.addEventListener('mouseenter', () => {
    cursor.style.transform = 'translate(-50%,-50%) scale(2.5)';
    cursor.style.background = 'rgba(200,169,110,0.5)';
  });
  el.addEventListener('mouseleave', () => {
    cursor.style.transform = 'translate(-50%,-50%) scale(1)';
    cursor.style.background = 'var(--accent)';
  });
});

// Scroll reveal
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal-block').forEach(el => observer.observe(el));

// Admin
const ADMIN_PW = 'hideo2025';
let isAdmin = false;

function openModal() { document.getElementById('modal').classList.add('active'); document.getElementById('adminPw').focus(); }
function closeModal() { document.getElementById('modal').classList.remove('active'); document.getElementById('pwError').style.display='none'; }
function checkPassword() {
  const pw = document.getElementById('adminPw').value;
  if (pw === ADMIN_PW) {
    isAdmin = true;
    closeModal();
    document.getElementById('blogNew').classList.add('active');
    document.getElementById('adminPw').value = '';
  } else {
    document.getElementById('pwError').style.display = 'block';
  }
}
document.getElementById('adminPw').addEventListener('keydown', e => { if (e.key === 'Enter') checkPassword(); });
document.getElementById('modal').addEventListener('click', e => { if (e.target === document.getElementById('modal')) closeModal(); });
function cancelPost() { document.getElementById('blogNew').classList.remove('active'); isAdmin = false; }


function renderPosts() {
  const container = document.getElementById('blogPosts');
  container.innerHTML = '';
  posts.forEach((p, i) => {
    const div = document.createElement('div');
    div.className = 'post-item';
    div.style.transitionDelay = (i * 0.08) + 's';
    div.innerHTML = `
    div style="margin-top:0.8rem;display:flex;gap:0.8rem;align-items:center">
          <span class="post-tag">${p.tag}</span>
          <button class="btn btn-sm btn-outline" onclick="togglePost(${i})" style="cursor:none;font-size:0.7rem;padding:0.3rem 0.8rem;margin-top:0.3rem">続きを読む</button>
        </div>
      </div>
    `;
    container.appendChild(div);
  });
  observer.observe(container);
  setTimeout(() => container.classList.add('visible'), 50);
}

function togglePost(i) {
  const el = document.getElementById('expand-' + i);
  el.classList.toggle('active');
  el.previousElementSibling.querySelector('button').textContent = el.classList.contains('active') ? '閉じる' : '続きを読む';
}

function addPost() {
  const title = document.getElementById('postTitle').value.trim();
  const body  = document.getElementById('postBody').value.trim();
  const tag   = document.getElementById('postTag').value.trim() || '日記';
  if (!title || !body) return;
  const now = new Date();
  const date = `${now.getFullYear()}.${String(now.getMonth()+1).padStart(2,'0')}.${String(now.getDate()).padStart(2,'0')}`;
  posts.unshift({ date, title, body, tag, full: '' });
  renderPosts();
  document.getElementById('postTitle').value = '';
  document.getElementById('postBody').value  = '';
  document.getElementById('postTag').value   = '';
  document.getElementById('blogNew').classList.remove('active');
  isAdmin = false;
}

// 

function getInitial(id) { return id.charAt(0).toUpperCase(); }

function renderComments() {
  const list = document.getElementById('commentsList');
  list.innerHTML = '';
  comments.forEach((c, i) => {
    const div = document.createElement('div');
    div.className = 'comment-item';
    div.style.animationDelay = (i * 0.06) + 's';
    div.innerHTML = `
      <div class="comment-avatar">${getInitial(c.id)}</div>
      <div>
        <div class="comment-meta">
          <span class="comment-id">${c.id}</span>
          <span class="comment-time">${c.time}</span>
        </div>
        <div class="comment-text">${c.text}</div>
      </div>
    `;
    list.appendChild(div);
  });
}

function addComment() {
  const id   = document.getElementById('commentId').value.trim();
  const text = document.getElementById('commentText').value.trim();
  if (!id || !text) { alert('IDとコメントを入力してください'); return; }
  const now = new Date();
  const time = `${now.getFullYear()}.${String(now.getMonth()+1).padStart(2,'0')}.${String(now.getDate()).padStart(2,'0')} ${String(now.getHours()).padStart(2,'0')}:${String(now.getMinutes()).padStart(2,'0')}`;
  comments.unshift({ id, text, time });
  renderComments();
  document.getElementById('commentId').value   = '';
  document.getElementById('commentText').value = '';
  document.getElementById('commentEmail').value = '';
}

// Init
renderPosts();
renderComments();
</script>
</body>
</html>
