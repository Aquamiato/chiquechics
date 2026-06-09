<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ChiqueChics</title>
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'><rect width='32' height='32' rx='6' fill='%23050a0f'/><text x='4' y='23' font-size='17' font-family='Georgia,serif' font-style='italic' fill='%2300d4ff'>CC</text></svg>">
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600&family=Raleway:wght@200;300;400&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}

body{
  background:#050a0f;
  color:#e8f4f8;
  font-family:'Raleway',sans-serif;
  font-weight:300;
  overflow-x:hidden;
}

/* NEON GLOW KEYFRAMES */
@keyframes pulseGlow{
  0%,100%{box-shadow:0 0 18px #00d4ff55,0 0 40px #00d4ff22}
  50%{box-shadow:0 0 28px #00d4ff99,0 0 70px #00d4ff44}
}
@keyframes fadeUp{
  from{opacity:0;transform:translateY(28px)}
  to{opacity:1;transform:translateY(0)}
}
@keyframes shimmer{
  0%{background-position:-200% center}
  100%{background-position:200% center}
}
@keyframes ticker{
  from{transform:translateX(0)}
  to{transform:translateX(-50%)}
}
@keyframes floatY{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-10px)}
}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;z-index:999;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 40px;height:66px;
  background:rgba(5,10,15,0.92);
  border-bottom:1px solid rgba(0,212,255,0.15);
  backdrop-filter:blur(20px);
}
.nav-logo{
  font-family:'Cinzel',serif;
  font-size:20px;letter-spacing:3px;
  color:#fff;text-decoration:none;
  text-shadow:0 0 20px rgba(0,212,255,0.5);
}
.nav-logo span{color:#00d4ff}
.nav-links{display:flex;align-items:center;gap:8px}
.nav-a{
  padding:8px 18px;
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(200,230,240,0.6);text-decoration:none;
  transition:color .2s;
}
.nav-a:hover{color:#00d4ff}
.nav-cta{
  padding:11px 28px;
  background:linear-gradient(135deg,#0088aa,#00d4ff);
  color:#050a0f;
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  font-weight:600;text-decoration:none;
  animation:pulseGlow 3s ease-in-out infinite;
  transition:transform .2s;
}
.nav-cta:hover{transform:translateY(-2px)}

/* HERO */
.hero{
  min-height:100vh;
  position:relative;
  display:flex;align-items:center;justify-content:center;
  text-align:center;
  overflow:hidden;
  padding:80px 24px 60px;
}
.hero-bg{
  position:absolute;inset:0;z-index:0;
}
.hero-bg img{
  width:100%;height:100%;
  object-fit:cover;object-position:center top;
  filter:brightness(.35) saturate(.7);
}
/* Multi-layer ocean overlay */
.hero-bg::after{
  content:'';
  position:absolute;inset:0;
  background:
    linear-gradient(to bottom,rgba(5,10,15,.5) 0%,rgba(5,10,15,.1) 40%,rgba(5,10,15,.85) 100%),
    radial-gradient(ellipse 80% 60% at 50% 50%,rgba(0,100,140,.25) 0%,transparent 70%);
}
/* Animated neon horizon line */
.hero-line{
  position:absolute;bottom:30%;left:0;right:0;height:1px;
  background:linear-gradient(to right,transparent,rgba(0,212,255,.3),rgba(0,212,255,.6),rgba(0,212,255,.3),transparent);
  pointer-events:none;z-index:1;
}

.hero-inner{position:relative;z-index:2;max-width:800px}

.hero-badge{
  display:inline-flex;align-items:center;gap:12px;
  font-size:9px;letter-spacing:5px;text-transform:uppercase;
  color:#00d4ff;margin-bottom:32px;
  opacity:0;animation:fadeUp .8s ease .2s forwards;
}
.hero-badge::before,.hero-badge::after{
  content:'';display:block;
  width:32px;height:1px;background:rgba(0,212,255,.4);
}

.hero-title{
  font-family:'Cinzel',serif;
  font-size:clamp(56px,12vw,120px);
  font-weight:600;line-height:.9;letter-spacing:4px;
  color:#fff;
  text-shadow:0 0 60px rgba(0,212,255,.25);
  opacity:0;animation:fadeUp .9s ease .4s forwards;
}
.hero-title .neon{
  display:block;
  background:linear-gradient(90deg,#7ff0ff,#00d4ff,#0088aa,#00d4ff,#7ff0ff);
  background-size:200% auto;
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  animation:shimmer 4s linear infinite;
}

.hero-sub{
  font-size:clamp(14px,2.5vw,18px);
  color:rgba(200,230,240,.65);
  line-height:1.75;
  margin:28px 0 48px;
  opacity:0;animation:fadeUp .9s ease .6s forwards;
}

.hero-btns{
  display:flex;flex-wrap:wrap;gap:14px;justify-content:center;
  opacity:0;animation:fadeUp .9s ease .8s forwards;
}

/* BUTTONS */
.btn{
  display:inline-block;text-decoration:none;
  font-family:'Raleway',sans-serif;
  font-size:10px;letter-spacing:3px;text-transform:uppercase;
  font-weight:400;
  transition:all .3s ease;
  white-space:nowrap;
}
.btn-neon{
  padding:17px 48px;
  background:linear-gradient(135deg,#006688,#00d4ff);
  color:#050a0f;font-weight:600;
  animation:pulseGlow 3s ease-in-out infinite;
}
.btn-neon:hover{transform:translateY(-3px);filter:brightness(1.15)}

.btn-border{
  padding:16px 44px;
  border:1px solid rgba(0,212,255,.5);
  color:#00d4ff;
  background:rgba(0,212,255,.05);
}
.btn-border:hover{
  background:rgba(0,212,255,.12);
  border-color:#00d4ff;
  transform:translateY(-2px);
  box-shadow:0 0 20px rgba(0,212,255,.2);
}
.btn-dim{
  padding:16px 36px;
  border:1px solid rgba(200,230,240,.12);
  color:rgba(200,230,240,.5);
  background:transparent;
}
.btn-dim:hover{border-color:rgba(0,212,255,.3);color:#00d4ff}

/* TRUST PILLS */
.trust-row{
  display:flex;flex-wrap:wrap;gap:12px;justify-content:center;
  margin-top:36px;
  opacity:0;animation:fadeUp .9s ease 1s forwards;
}
.trust-pill{
  display:flex;align-items:center;gap:8px;
  padding:8px 18px;
  border:1px solid rgba(0,212,255,.15);
  background:rgba(0,212,255,.05);
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(200,230,240,.55);
}
.trust-pill i{color:#00d4ff;font-style:normal}

/* TICKER */
.ticker-bar{
  background:#030709;
  border-top:1px solid rgba(0,212,255,.12);
  border-bottom:1px solid rgba(0,212,255,.12);
  overflow:hidden;height:42px;display:flex;align-items:center;
}
.ticker-track{
  display:flex;
  animation:ticker 20s linear infinite;
  white-space:nowrap;
}
.tick{
  display:inline-flex;align-items:center;gap:10px;
  padding:0 40px;
  font-size:9px;letter-spacing:3px;text-transform:uppercase;
  color:rgba(180,220,230,.4);
}
.tick-dot{color:#00d4ff;font-size:12px}

/* SECTION COMMONS */
.s-inner{max-width:960px;margin:0 auto}
.s-label{
  font-size:9px;letter-spacing:5px;text-transform:uppercase;
  color:#00d4ff;text-align:center;margin-bottom:10px;
}
.s-title{
  font-family:'Cinzel',serif;
  font-size:clamp(30px,5.5vw,52px);
  text-align:center;line-height:1.1;margin-bottom:54px;
  color:#fff;
}
.s-title em{font-style:italic;color:#00d4ff}

/* PHOTO GRID SECTION */
.grid-sec{padding:100px 24px;background:#050a0f}

.photo-grid{
  display:grid;
  grid-template-columns:1.15fr 1fr 1fr;
  grid-template-rows:320px 260px;
  gap:6px;
}
@media(max-width:680px){
  .photo-grid{grid-template-columns:1fr 1fr;grid-template-rows:auto}
  .p-tall{grid-row:span 1}
}
@media(max-width:420px){.photo-grid{grid-template-columns:1fr}}

.p-card{
  position:relative;overflow:hidden;
  text-decoration:none;display:block;
  background:#0a1520;
}
.p-card.p-tall{grid-row:span 2}
.p-card.p-wide{grid-column:span 2}

.p-card img{
  width:100%;height:100%;
  object-fit:cover;object-position:center top;
  display:block;
  transition:transform .7s ease,filter .4s;
  filter:brightness(.6) saturate(.75);
}
.p-card:hover img{transform:scale(1.07);filter:brightness(.45) saturate(1)}

/* neon top border reveal */
.p-card::before{
  content:'';
  position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(to right,transparent,#00d4ff,transparent);
  transform:scaleX(0);transition:transform .4s ease;z-index:3;
}
.p-card:hover::before{transform:scaleX(1)}

.p-overlay{
  position:absolute;inset:0;
  background:linear-gradient(to top,rgba(5,10,15,.92) 0%,transparent 55%);
  display:flex;flex-direction:column;
  justify-content:flex-end;padding:22px 20px;
}
.p-tag{font-size:8px;letter-spacing:3px;text-transform:uppercase;color:#00d4ff;margin-bottom:5px}
.p-name{
  font-family:'Cinzel',serif;
  font-size:18px;color:#fff;margin-bottom:14px;
  text-shadow:0 0 20px rgba(0,212,255,.3);
}
.p-btn{
  display:inline-block;padding:9px 20px;
  background:rgba(0,212,255,.9);color:#050a0f;
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  font-weight:600;text-decoration:none;
  width:fit-content;
  opacity:0;transform:translateY(8px);
  transition:opacity .3s,transform .3s;
}
.p-card:hover .p-btn{opacity:1;transform:translateY(0)}

.grid-cta{display:flex;flex-wrap:wrap;gap:12px;justify-content:center;margin-top:44px}

/* VIDEO SECTION */
.vid-sec{
  padding:100px 24px;
  background:#030709;
  position:relative;overflow:hidden;
}
.vid-sec::before{
  content:'';
  position:absolute;
  width:700px;height:700px;border-radius:50%;
  background:radial-gradient(circle,rgba(0,212,255,.06) 0%,transparent 70%);
  top:50%;left:50%;transform:translate(-50%,-50%);
  pointer-events:none;
}
.vid-layout{
  max-width:960px;margin:0 auto;
  display:grid;grid-template-columns:1fr 1fr;
  gap:64px;align-items:center;
  position:relative;z-index:1;
}
@media(max-width:740px){.vid-layout{grid-template-columns:1fr;gap:40px}}

.vid-copy .s-label,.vid-copy .s-title{text-align:left}
.vid-copy .s-title{margin-bottom:18px}
.vid-copy p{
  font-size:16px;line-height:1.8;
  color:rgba(180,220,230,.55);
  margin-bottom:36px;
  font-style:italic;
}
.vid-btns{display:flex;flex-wrap:wrap;gap:10px}

.vid-frame{
  position:relative;
  border:1px solid rgba(0,212,255,.15);
  overflow:hidden;
  box-shadow:0 0 60px rgba(0,212,255,.08),inset 0 0 40px rgba(0,0,0,.4);
}
.vid-frame video{
  width:100%;display:block;
  aspect-ratio:4/5;object-fit:cover;
  filter:brightness(.75) saturate(.85);
}
.vid-over{
  position:absolute;inset:0;
  display:flex;align-items:center;justify-content:center;
  background:rgba(5,10,15,.15);
  text-decoration:none;
  transition:background .3s;
}
.vid-over:hover{background:rgba(5,10,15,.05)}
.play-ring{
  width:68px;height:68px;border-radius:50%;
  border:1.5px solid #00d4ff;
  display:flex;align-items:center;justify-content:center;
  color:#00d4ff;font-size:22px;
  background:rgba(0,212,255,.08);
  transition:all .3s;
  animation:pulseGlow 3s ease-in-out infinite;
}
.vid-over:hover .play-ring{background:rgba(0,212,255,.2);transform:scale(1.1)}

/* LOOKBOOK */
.lookbook-sec{padding:100px 24px;background:#050a0f}

.look-grid{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:6px;margin-top:54px;
}
@media(max-width:720px){.look-grid{grid-template-columns:repeat(2,1fr)}}

.look-card{
  position:relative;overflow:hidden;
  text-decoration:none;display:block;
  aspect-ratio:2/3;background:#0a1520;
}
.look-card img{
  width:100%;height:100%;
  object-fit:cover;object-position:center top;
  transition:transform .6s,filter .4s;
  filter:brightness(.6) saturate(.7);
}
.look-card:hover img{transform:scale(1.08);filter:brightness(.45) saturate(1)}

.look-card::after{
  content:'';
  position:absolute;bottom:0;left:0;right:0;height:2px;
  background:#00d4ff;
  transform:scaleX(0);transform-origin:left;
  transition:transform .4s ease;
}
.look-card:hover::after{transform:scaleX(1)}

.look-info{
  position:absolute;bottom:0;left:0;right:0;
  padding:18px 14px 14px;
  background:linear-gradient(to top,rgba(5,10,15,.9),transparent);
  display:flex;justify-content:space-between;align-items:flex-end;
}
.look-lbl{font-size:9px;letter-spacing:2px;text-transform:uppercase;color:#00d4ff}
.look-arr{
  font-size:16px;color:rgba(0,212,255,.5);
  transform:translateX(-6px);opacity:0;
  transition:all .3s;
}
.look-card:hover .look-arr{opacity:1;transform:translateX(0)}

.look-cta{display:flex;flex-wrap:wrap;gap:12px;justify-content:center;margin-top:44px}

/* QUOTE */
.quote-sec{
  padding:100px 24px;
  background:#030709;
  text-align:center;position:relative;overflow:hidden;
}
.quote-sec::before{
  content:'"';
  position:absolute;
  font-family:'Cinzel',serif;font-size:380px;
  color:rgba(0,212,255,.03);
  top:-40px;left:50%;transform:translateX(-50%);
  pointer-events:none;line-height:1;
}
.q-inner{max-width:580px;margin:0 auto;position:relative;z-index:1}
.q-stars{font-size:18px;letter-spacing:5px;color:#00d4ff;margin-bottom:24px}
.q-text{
  font-family:'Cinzel',serif;
  font-size:clamp(20px,3.5vw,30px);
  line-height:1.55;color:#fff;margin-bottom:18px;
  text-shadow:0 0 40px rgba(0,212,255,.1);
}
.q-author{
  font-size:9px;letter-spacing:3px;text-transform:uppercase;
  color:rgba(180,220,230,.4);margin-bottom:44px;
}
.q-btns{display:flex;flex-wrap:wrap;gap:12px;justify-content:center}

/* FINAL */
.final-sec{
  padding:120px 24px;
  background:#050a0f;
  text-align:center;position:relative;overflow:hidden;
}
.final-sec::before{
  content:'';
  position:absolute;bottom:-80px;left:50%;transform:translateX(-50%);
  width:900px;height:400px;border-radius:50%;
  background:radial-gradient(ellipse,rgba(0,212,255,.1) 0%,transparent 65%);
  pointer-events:none;
}
.f-inner{position:relative;z-index:1;max-width:620px;margin:0 auto}
.f-label{
  font-size:9px;letter-spacing:5px;text-transform:uppercase;
  color:#00d4ff;margin-bottom:24px;display:block;
}
.f-title{
  font-family:'Cinzel',serif;
  font-size:clamp(42px,9vw,88px);
  line-height:.9;color:#fff;margin-bottom:12px;
  text-shadow:0 0 80px rgba(0,212,255,.2);
}
.f-title .neon{
  display:block;
  background:linear-gradient(90deg,#7ff0ff,#00d4ff,#0088aa,#00d4ff,#7ff0ff);
  background-size:200% auto;
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  animation:shimmer 4s linear infinite;
}
.f-sub{
  font-size:11px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(180,220,230,.35);margin-bottom:48px;
}
.f-btns{display:flex;flex-wrap:wrap;gap:12px;justify-content:center;margin-bottom:28px}
.f-note{font-size:10px;letter-spacing:1px;color:rgba(180,220,230,.2)}

/* FOOTER */
footer{
  padding:30px 40px;
  background:#030709;
  border-top:1px solid rgba(0,212,255,.1);
  display:flex;flex-wrap:wrap;
  align-items:center;justify-content:space-between;gap:16px;
}
.f-logo{
  font-family:'Cinzel',serif;font-size:16px;
  color:rgba(0,212,255,.6);text-decoration:none;letter-spacing:2px;
}
.f-logo:hover{color:#00d4ff}
footer small{font-size:9px;letter-spacing:2px;text-transform:uppercase;color:rgba(180,220,230,.2)}
.f-links{display:flex;gap:20px}
.f-links a{
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(180,220,230,.25);text-decoration:none;transition:color .2s;
}
.f-links a:hover{color:#00d4ff}

/* REVEAL */
.reveal{opacity:0;transform:translateY(26px);transition:opacity .8s ease,transform .8s ease}
.reveal.on{opacity:1;transform:translateY(0)}
.d1{transition-delay:.07s}.d2{transition-delay:.14s}
.d3{transition-delay:.21s}.d4{transition-delay:.28s}
.d5{transition-delay:.35s}.d6{transition-delay:.42s}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="https://aquamiato.com" class="nav-logo">Chique<span>Chics</span></a>
  <div class="nav-links">
    <a href="https://aquamiato.com/collections/all" class="nav-a">Shop</a>
    <a href="https://aquamiato.com/collections" class="nav-a">Collections</a>
    <a href="https://aquamiato.com" class="nav-cta">Shop Now →</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg">
    <img
      src="https://images.pexels.com/photos/1032110/pexels-photo-1032110.jpeg?auto=compress&cs=tinysrgb&w=1600"
      alt="Luxury swimwear"
      loading="eager"
    >
  </div>
  <div class="hero-line"></div>

  <div class="hero-inner">
    <div class="hero-badge">Summer Collection 2025</div>
    <h1 class="hero-title">
      CHIQUE<span class="neon">CHICS</span>
    </h1>
    <p class="hero-sub">
      Luxury swimwear crafted for women who command every shore.<br>
      Mediterranean soul. Uncompromising craft. Free worldwide shipping.
    </p>
    <div class="hero-btns">
      <a href="https://aquamiato.com/collections/all" class="btn btn-neon">Shop the Collection →</a>
      <a href="https://aquamiato.com/collections" class="btn btn-border">Browse Lookbook</a>
      <a href="https://aquamiato.com" class="btn btn-dim">Aquamiato.com ↗</a>
    </div>
    <div class="trust-row">
      <div class="trust-pill"><i>✦</i> Free Worldwide Shipping</div>
      <div class="trust-pill"><i>✦</i> Easy Returns</div>
      <div class="trust-pill"><i>✦</i> New Arrivals Weekly</div>
      <div class="trust-pill"><i>✦</i> Premium Fabric</div>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker-bar">
  <div class="ticker-track">
    <span class="tick"><span class="tick-dot">✦</span> Free Worldwide Shipping</span>
    <span class="tick"><span class="tick-dot">✦</span> New Arrivals Every Week</span>
    <span class="tick"><span class="tick-dot">✦</span> Easy Returns</span>
    <span class="tick"><span class="tick-dot">✦</span> Chlorine Resistant</span>
    <span class="tick"><span class="tick-dot">✦</span> 60+ Countries Delivered</span>
    <span class="tick"><span class="tick-dot">✦</span> Mediterranean Design</span>
    <span class="tick"><span class="tick-dot">✦</span> Free Worldwide Shipping</span>
    <span class="tick"><span class="tick-dot">✦</span> New Arrivals Every Week</span>
    <span class="tick"><span class="tick-dot">✦</span> Easy Returns</span>
    <span class="tick"><span class="tick-dot">✦</span> Chlorine Resistant</span>
    <span class="tick"><span class="tick-dot">✦</span> 60+ Countries Delivered</span>
    <span class="tick"><span class="tick-dot">✦</span> Mediterranean Design</span>
  </div>
</div>

<!-- PHOTO GRID -->
<section class="grid-sec">
  <div class="s-inner">
    <p class="s-label reveal">Shop by Style</p>
    <h2 class="s-title reveal">Find your <em>perfect piece</em></h2>
    <div class="photo-grid">
      <a href="https://aquamiato.com/collections/all" class="p-card p-tall reveal d1">
        <img src="https://images.pexels.com/photos/1082528/pexels-photo-1082528.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Bikini Sets" loading="lazy">
        <div class="p-overlay">
          <div class="p-tag">Bestseller</div>
          <div class="p-name">Bikini Sets</div>
          <span class="p-btn">Shop Now →</span>
        </div>
      </a>
      <a href="https://aquamiato.com/collections/all" class="p-card reveal d2">
        <img src="https://images.pexels.com/photos/1536619/pexels-photo-1536619.jpeg?auto=compress&cs=tinysrgb&w=800" alt="One-Pieces" loading="lazy">
        <div class="p-overlay">
          <div class="p-tag">Trending</div>
          <div class="p-name">One-Pieces</div>
          <span class="p-btn">Shop Now →</span>
        </div>
      </a>
      <a href="https://aquamiato.com/collections/all" class="p-card reveal d3">
        <img src="https://images.pexels.com/photos/1055691/pexels-photo-1055691.jpeg?auto=compress&cs=tinysrgb&w=800" alt="Beach Fashion" loading="lazy">
        <div class="p-overlay">
          <div class="p-tag">New In</div>
          <div class="p-name">Beach Fashion</div>
          <span class="p-btn">Shop Now →</span>
        </div>
      </a>
      <a href="https://aquamiato.com/collections/all" class="p-card p-wide reveal d4">
        <img src="https://images.pexels.com/photos/1021293/pexels-photo-1021293.jpeg?auto=compress&cs=tinysrgb&w=1200" alt="Summer 2025" loading="lazy" style="min-height:260px">
        <div class="p-overlay">
          <div class="p-tag">Full Collection</div>
          <div class="p-name">Summer 2025</div>
          <span class="p-btn">Explore All →</span>
        </div>
      </a>
    </div>
    <div class="grid-cta reveal">
      <a href="https://aquamiato.com/collections/all" class="btn btn-neon">View All Products →</a>
      <a href="https://aquamiato.com" class="btn btn-border">Visit Aquamiato.com</a>
      <a href="https://aquamiato.com/collections" class="btn btn-dim">All Collections</a>
    </div>
  </div>
</section>

<!-- VIDEO -->
<section class="vid-sec">
  <div class="vid-layout">
    <div class="vid-copy">
      <p class="s-label reveal">The Aquamiato World</p>
      <h2 class="s-title reveal">Wear the <em>Ocean.</em></h2>
      <p class="reveal">Crafted for women who live in the water. Every piece carries the spirit of Positano, Santorini, and Ibiza.</p>
      <div class="vid-btns reveal">
        <a href="https://aquamiato.com/collections/all" class="btn btn-neon">Shop the Look →</a>
        <a href="https://aquamiato.com" class="btn btn-border">Discover More</a>
      </div>
    </div>
    <div class="vid-frame reveal">
      <video autoplay muted loop playsinline
        poster="https://images.pexels.com/photos/1174732/pexels-photo-1174732.jpeg?auto=compress&cs=tinysrgb&w=800">
        <source src="https://www.pexels.com/download/video/4069530/?fps=25.0&h=1080&w=1920" type="video/mp4">
      </video>
      <a href="https://aquamiato.com" class="vid-over">
        <div class="play-ring">▶</div>
      </a>
    </div>
  </div>
</section>

<!-- LOOKBOOK -->
<section class="lookbook-sec">
  <div class="s-inner">
    <p class="s-label reveal">Lookbook 2025</p>
    <h2 class="s-title reveal">Dressed for <em>the shore</em></h2>
    <div class="look-grid">
      <a href="https://aquamiato.com/collections/all" class="look-card reveal d1">
        <img src="https://images.pexels.com/photos/1174732/pexels-photo-1174732.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Look 1" loading="lazy">
        <div class="look-info"><span class="look-lbl">Bikini Sets</span><span class="look-arr">→</span></div>
      </a>
      <a href="https://aquamiato.com/collections/all" class="look-card reveal d2">
        <img src="https://images.pexels.com/photos/1337436/pexels-photo-1337436.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Look 2" loading="lazy">
        <div class="look-info"><span class="look-lbl">One-Pieces</span><span class="look-arr">→</span></div>
      </a>
      <a href="https://aquamiato.com/collections/all" class="look-card reveal d3">
        <img src="https://images.pexels.com/photos/457701/pexels-photo-457701.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Look 3" loading="lazy">
        <div class="look-info"><span class="look-lbl">Beach Wear</span><span class="look-arr">→</span></div>
      </a>
      <a href="https://aquamiato.com/collections/all" class="look-card reveal d4">
        <img src="https://images.pexels.com/photos/1139793/pexels-photo-1139793.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Look 4" loading="lazy">
        <div class="look-info"><span class="look-lbl">New Arrivals</span><span class="look-arr">→</span></div>
      </a>
    </div>
    <div class="look-cta reveal">
      <a href="https://aquamiato.com/collections/all" class="btn btn-neon">Shop Full Lookbook →</a>
      <a href="https://aquamiato.com" class="btn btn-border">Aquamiato.com</a>
      <a href="https://aquamiato.com/collections" class="btn btn-dim">All Collections</a>
    </div>
  </div>
</section>

<!-- QUOTE -->
<section class="quote-sec">
  <div class="q-inner">
    <div class="q-stars reveal">★★★★★</div>
    <p class="q-text reveal">"I've never felt so effortlessly beautiful. The fabric, the fit, the way it moves — pure luxury."</p>
    <p class="q-author reveal">— Verified Customer, Italy</p>
    <div class="q-btns reveal">
      <a href="https://aquamiato.com/collections/all" class="btn btn-neon">Shop Now →</a>
      <a href="https://aquamiato.com" class="btn btn-border">Visit the Store</a>
      <a href="https://aquamiato.com/collections" class="btn btn-dim">Browse Collections</a>
    </div>
  </div>
</section>

<!-- FINAL CTA -->
<section class="final-sec">
  <div class="f-inner">
    <span class="f-label reveal">✦ Free worldwide shipping on every order</span>
    <h2 class="f-title reveal">
      THIS SUMMER<span class="neon">BE CHIC.</span>
    </h2>
    <p class="f-sub reveal">New collection — available now</p>
    <div class="f-btns reveal">
      <a href="https://aquamiato.com/collections/all" class="btn btn-neon">Shop All Collections →</a>
      <a href="https://aquamiato.com" class="btn btn-border">Visit Aquamiato.com</a>
      <a href="https://aquamiato.com/collections" class="btn btn-dim">Browse Lookbook</a>
    </div>
    <p class="f-note reveal">Free shipping · Easy returns · New arrivals every week</p>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <a href="https://aquamiato.com" class="f-logo">ChiqueChics</a>
  <small>© 2025 ChiqueChics — Powered by Aquamiato</small>
  <div class="f-links">
    <a href="https://aquamiato.com/collections/all">Shop</a>
    <a href="https://aquamiato.com/collections">Collections</a>
    <a href="https://aquamiato.com/pages/contact">Contact</a>
  </div>
</footer>

<script>
  const els = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('on'); });
  }, {threshold: 0.08});
  els.forEach(el => io.observe(el));
</script>
</body>
</html>
