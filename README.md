<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Abdelrahman Nasser — Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&display=swap" rel="stylesheet">
<style>
/* ===== RESET & ROOT ===== */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --indigo:#3730A3;--indigo-light:#6366F1;
  --pink:#EC4899;--pink-light:#F472B6;
  --cyan:#06B6D4;--cyan-light:#67E8F9;
  --amber:#F59E0B;--amber-light:#FCD34D;
  --bg:#080B18;--bg2:#0D1025;--bg3:#111527;
  --surface:#151929;--surface2:#1A1F35;
  --text:#E8ECF4;--text2:#9BA3BE;--text3:#5C6480;
  --font-head:'Syne',sans-serif;--font-body:'DM Sans',sans-serif;
  --radius:12px;--radius-lg:20px;
  --glow-pink:0 0 30px rgba(236,72,153,0.35);
  --glow-cyan:0 0 30px rgba(6,182,212,0.35);
  --glow-indigo:0 0 30px rgba(99,102,241,0.35);
  --glow-amber:0 0 30px rgba(245,158,11,0.35);
}
html{scroll-behavior:smooth;scrollbar-width:thin;scrollbar-color:var(--indigo-light) var(--bg2)}
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:var(--bg2)}
::-webkit-scrollbar-thumb{background:var(--indigo-light);border-radius:3px}
body{background:var(--bg);color:var(--text);font-family:var(--font-body);font-size:15px;line-height:1.65;overflow-x:hidden;cursor:none}
a{color:inherit;text-decoration:none}
img{max-width:100%}

/* ===== NOISE OVERLAY ===== */
body::before{
  content:'';position:fixed;inset:0;z-index:0;pointer-events:none;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  opacity:.4;mix-blend-mode:overlay;
}

/* ===== CUSTOM CURSOR ===== */
#cursor-dot{position:fixed;width:8px;height:8px;background:var(--cyan);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:background .2s;box-shadow:0 0 12px var(--cyan),0 0 24px rgba(6,182,212,.5)}
#cursor-ring{position:fixed;width:36px;height:36px;border:1.5px solid rgba(99,102,241,.7);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:transform .12s ease,width .2s,height .2s,opacity .2s;box-shadow:0 0 12px rgba(99,102,241,.3)}

/* ===== LOADING SCREEN ===== */
#loader{position:fixed;inset:0;z-index:99999;background:var(--bg);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:28px;transition:opacity .6s ease,visibility .6s ease}
#loader.hide{opacity:0;visibility:hidden}
.loader-initials{font-family:var(--font-head);font-size:clamp(60px,12vw,120px);font-weight:800;background:linear-gradient(135deg,var(--indigo-light),var(--pink),var(--cyan),var(--amber));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:pulse-scale 1s ease-in-out infinite alternate}
.loader-bar-wrap{width:220px;height:3px;background:rgba(255,255,255,.1);border-radius:3px;overflow:hidden}
.loader-bar{height:100%;width:0%;background:linear-gradient(90deg,var(--indigo-light),var(--pink),var(--cyan),var(--amber));border-radius:3px;animation:load-fill 2s ease forwards}
.loader-text{font-family:var(--font-head);font-size:13px;letter-spacing:.25em;color:var(--text2);text-transform:uppercase}
@keyframes load-fill{0%{width:0%}100%{width:100%}}
@keyframes pulse-scale{from{transform:scale(1)}to{transform:scale(1.05)}}

/* ===== CANVAS ===== */
#bg-canvas{position:fixed;inset:0;z-index:1;pointer-events:none}

/* ===== NAVBAR ===== */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:0 5%;height:68px;display:flex;align-items:center;justify-content:space-between;backdrop-filter:blur(18px) saturate(140%);-webkit-backdrop-filter:blur(18px) saturate(140%);background:rgba(8,11,24,.72);border-bottom:1px solid rgba(99,102,241,.12);transform:translateY(-100%);transition:transform .7s cubic-bezier(.4,0,.2,1)}
nav.visible{transform:translateY(0)}
.nav-logo{font-family:var(--font-head);font-weight:800;font-size:18px;letter-spacing:-.02em;background:linear-gradient(90deg,var(--indigo-light),var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.nav-links{display:flex;gap:32px;list-style:none}
.nav-links a{font-family:var(--font-head);font-size:13px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--text2);position:relative;padding-bottom:4px;transition:color .2s}
.nav-links a::after{content:'';position:absolute;bottom:0;left:0;width:0;height:1.5px;background:linear-gradient(90deg,var(--pink),var(--cyan));transition:width .3s ease}
.nav-links a:hover{color:var(--text)}
.nav-links a:hover::after{width:100%}
.nav-toggle{display:none;flex-direction:column;gap:5px;cursor:pointer;padding:4px}
.nav-toggle span{display:block;width:22px;height:2px;background:var(--text);border-radius:2px;transition:.3s}
@media(max-width:700px){
  .nav-links{display:none;position:absolute;top:68px;left:0;right:0;flex-direction:column;background:rgba(8,11,24,.96);backdrop-filter:blur(20px);padding:20px 5%;gap:16px;border-bottom:1px solid rgba(99,102,241,.12)}
  .nav-links.open{display:flex}
  .nav-toggle{display:flex}
}

/* ===== SECTIONS GENERAL ===== */
section{position:relative;z-index:2;padding:100px 5%}
.section-label{font-family:var(--font-head);font-size:11px;font-weight:700;letter-spacing:.3em;text-transform:uppercase;color:var(--pink);margin-bottom:12px}
.section-title{font-family:var(--font-head);font-size:clamp(28px,4vw,42px);font-weight:800;line-height:1.1;margin-bottom:48px}
.gradient-text{background:linear-gradient(135deg,var(--indigo-light),var(--pink),var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}

/* ===== REVEAL ANIMATIONS ===== */
.reveal{opacity:0;transition:opacity .7s ease,transform .7s cubic-bezier(.4,0,.2,1)}
.reveal.fade-up{transform:translateY(40px)}
.reveal.fade-left{transform:translateX(-40px)}
.reveal.fade-right{transform:translateX(40px)}
.reveal.visible{opacity:1;transform:none}

/* ===== HERO ===== */
#hero{min-height:100vh;display:flex;align-items:center;padding-top:120px;padding-bottom:60px}
.hero-inner{display:grid;grid-template-columns:1fr 420px;gap:60px;align-items:center;width:100%;max-width:1200px;margin:0 auto}
.avail-tag{display:inline-flex;align-items:center;gap:8px;background:rgba(6,182,212,.1);border:1px solid rgba(6,182,212,.25);border-radius:99px;padding:5px 14px;font-size:12px;font-weight:600;color:var(--cyan-light);letter-spacing:.04em;margin-bottom:22px}
.avail-dot{width:7px;height:7px;border-radius:50%;background:var(--cyan);animation:blink 1.5s ease-in-out infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}
.hero-name{font-family:var(--font-head);font-size:clamp(38px,6vw,76px);font-weight:800;line-height:1.0;letter-spacing:-.03em;margin-bottom:16px;background:linear-gradient(135deg,#fff 0%,rgba(255,255,255,.9) 30%,var(--pink-light) 50%,var(--cyan-light) 70%,#fff 100%);background-size:300% 300%;-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:shimmer 4s linear infinite}
@keyframes shimmer{0%{background-position:0% 50%}50%{background-position:100% 50%}100%{background-position:0% 50%}}
.hero-subtitle{font-size:clamp(16px,2vw,20px);color:var(--text2);margin-bottom:32px;font-weight:300}
.hero-subtitle span{color:var(--amber-light);font-weight:500}
.hero-ctas{display:flex;gap:14px;flex-wrap:wrap}
.btn{display:inline-flex;align-items:center;gap:8px;padding:12px 28px;border-radius:99px;font-family:var(--font-head);font-weight:600;font-size:14px;letter-spacing:.04em;cursor:none;transition:all .3s ease;border:none;outline:none}
.btn-primary{background:linear-gradient(135deg,var(--indigo-light),var(--pink));color:#fff;box-shadow:0 0 0 0 rgba(236,72,153,0)}
.btn-primary:hover{box-shadow:var(--glow-pink),0 8px 24px rgba(236,72,153,.3);transform:translateY(-2px)}
.btn-outline{background:transparent;color:var(--text);border:1.5px solid rgba(99,102,241,.4)}
.btn-outline:hover{border-color:var(--cyan);color:var(--cyan);box-shadow:var(--glow-cyan);transform:translateY(-2px)}

/* ===== HERO CARD ===== */
.hero-card-wrap{position:relative;display:flex;align-items:center;justify-content:center}
.hero-orb{position:absolute;width:320px;height:320px;border-radius:50%;background:radial-gradient(circle,rgba(99,102,241,.22) 0%,rgba(236,72,153,.1) 50%,transparent 70%);filter:blur(40px);animation:orb-pulse 4s ease-in-out infinite alternate}
@keyframes orb-pulse{from{transform:scale(1)}to{transform:scale(1.15)}}
.hero-ring{position:absolute;width:290px;height:290px;border-radius:50%;border:2px dashed rgba(99,102,241,.3);animation:spin-slow 12s linear infinite}
@keyframes spin-slow{from{transform:rotate(0)}to{transform:rotate(360deg)}}
.hero-ring-2{position:absolute;width:310px;height:310px;border-radius:50%;border:1px dashed rgba(236,72,153,.2);animation:spin-slow 20s linear infinite reverse}
.hero-card{position:relative;z-index:2;background:linear-gradient(145deg,rgba(26,31,53,.95),rgba(17,21,39,.9));border:1px solid rgba(99,102,241,.2);border-radius:var(--radius-lg);padding:36px 32px;text-align:center;width:280px;backdrop-filter:blur(20px);animation:float-card 4s ease-in-out infinite alternate;box-shadow:0 20px 60px rgba(0,0,0,.4),var(--glow-indigo)}
@keyframes float-card{from{transform:translateY(0) rotateY(-3deg) rotateX(2deg)}to{transform:translateY(-14px) rotateY(3deg) rotateX(-2deg)}}
.card-avatar{width:80px;height:80px;border-radius:50%;background:linear-gradient(135deg,var(--indigo-light),var(--pink));display:flex;align-items:center;justify-content:center;font-family:var(--font-head);font-size:26px;font-weight:800;color:#fff;margin:0 auto 16px;box-shadow:var(--glow-indigo)}
.card-name{font-family:var(--font-head);font-weight:700;font-size:17px;margin-bottom:4px}
.card-role{font-size:12px;color:var(--text2);margin-bottom:20px}
.card-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.stat-box{background:rgba(99,102,241,.1);border:1px solid rgba(99,102,241,.15);border-radius:10px;padding:10px 6px}
.stat-num{font-family:var(--font-head);font-size:20px;font-weight:800;background:linear-gradient(135deg,var(--cyan),var(--indigo-light));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.stat-lbl{font-size:10px;color:var(--text3);margin-top:2px;line-height:1.3}

@media(max-width:900px){
  .hero-inner{grid-template-columns:1fr}
  .hero-card-wrap{justify-content:flex-start}
  .hero-card{width:100%;max-width:340px}
  .hero-orb,.hero-ring,.hero-ring-2{display:none}
}

/* ===== MARQUEE ===== */
.marquee-section{z-index:2;position:relative;padding:20px 0;overflow:hidden;border-top:1px solid rgba(255,255,255,.05);border-bottom:1px solid rgba(255,255,255,.05);background:rgba(13,16,37,.6)}
.marquee-track{display:flex;gap:0;white-space:nowrap;animation:marquee 22s linear infinite}
.marquee-track:hover{animation-play-state:paused}
.marquee-item{display:inline-flex;align-items:center;gap:14px;padding:0 32px;font-family:var(--font-head);font-size:13px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--text3)}
.marquee-item::after{content:'✦';color:var(--pink);font-size:9px}
@keyframes marquee{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ===== SKILLS ===== */
#skills{background:var(--bg2)}
.skills-grid{display:grid;grid-template-columns:1fr 1fr;gap:48px}
.skill-bars{display:flex;flex-direction:column;gap:20px}
.skill-item{}
.skill-meta{display:flex;justify-content:space-between;margin-bottom:8px}
.skill-name{font-size:13px;font-weight:600;font-family:var(--font-head)}
.skill-pct{font-size:12px;color:var(--text2)}
.skill-track{height:6px;background:rgba(255,255,255,.07);border-radius:6px;overflow:hidden}
.skill-fill{height:100%;width:0%;border-radius:6px;transition:width 1.2s cubic-bezier(.4,0,.2,1);position:relative;overflow:hidden}
.skill-fill::after{content:'';position:absolute;inset:0;background:linear-gradient(90deg,transparent 0%,rgba(255,255,255,.4) 50%,transparent 100%);transform:translateX(-100%)}
.skill-fill.animated::after{animation:shimmer-sweep 1.2s .8s forwards}
@keyframes shimmer-sweep{from{transform:translateX(-100%)}to{transform:translateX(200%)}}
.skill-fill.c1{background:linear-gradient(90deg,var(--indigo),var(--indigo-light))}
.skill-fill.c2{background:linear-gradient(90deg,var(--pink),var(--pink-light))}
.skill-fill.c3{background:linear-gradient(90deg,var(--cyan),var(--cyan-light))}
.skill-fill.c4{background:linear-gradient(90deg,var(--amber),var(--amber-light))}
.chip-cloud{display:flex;flex-wrap:wrap;gap:10px;align-content:flex-start}
.chip{display:inline-block;padding:6px 14px;border-radius:99px;font-size:12px;font-weight:600;border:1px solid;cursor:none;transition:transform .25s ease,box-shadow .25s ease}
.chip:hover{transform:translateY(-4px)}
.chip.indigo{background:rgba(99,102,241,.12);border-color:rgba(99,102,241,.3);color:var(--indigo-light)}
.chip.pink{background:rgba(236,72,153,.1);border-color:rgba(236,72,153,.3);color:var(--pink-light)}
.chip.cyan{background:rgba(6,182,212,.1);border-color:rgba(6,182,212,.3);color:var(--cyan-light)}
.chip.amber{background:rgba(245,158,11,.1);border-color:rgba(245,158,11,.3);color:var(--amber-light)}
@media(max-width:800px){.skills-grid{grid-template-columns:1fr}}

/* ===== EXPERIENCE ===== */
#experience{background:var(--bg)}
.timeline{position:relative;padding-left:32px}
.timeline::before{content:'';position:absolute;left:0;top:0;bottom:0;width:2px;background:linear-gradient(180deg,var(--indigo-light),var(--pink),var(--cyan),var(--amber));border-radius:2px}
.exp-card{position:relative;margin-bottom:36px;padding:28px 28px 28px 28px;background:var(--surface);border:1px solid rgba(255,255,255,.06);border-radius:var(--radius-lg);transition:transform .3s ease,box-shadow .3s ease;cursor:default}
.exp-card::before{content:'';position:absolute;left:-37px;top:32px;width:11px;height:11px;border-radius:50%;background:var(--indigo-light);border:2px solid var(--bg);box-shadow:0 0 10px var(--indigo-light)}
.exp-card:hover{transform:translateX(8px);box-shadow:var(--glow-indigo)}
.exp-header{display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:12px;margin-bottom:12px}
.exp-title{font-family:var(--font-head);font-size:17px;font-weight:700;margin-bottom:3px}
.exp-company{font-size:13px;color:var(--cyan-light);font-weight:600}
.exp-meta{text-align:right}
.exp-date{font-size:12px;color:var(--text2);background:rgba(99,102,241,.1);border:1px solid rgba(99,102,241,.2);border-radius:6px;padding:3px 10px;display:inline-block}
.exp-desc{font-size:14px;color:var(--text2);line-height:1.7;margin-bottom:16px}
.exp-badges{display:flex;flex-wrap:wrap;gap:8px}
.badge{font-size:11px;font-weight:600;padding:3px 10px;border-radius:6px;letter-spacing:.03em}
.badge-pink{background:rgba(236,72,153,.12);color:var(--pink-light);border:1px solid rgba(236,72,153,.2)}
.badge-cyan{background:rgba(6,182,212,.12);color:var(--cyan-light);border:1px solid rgba(6,182,212,.2)}
.badge-amber{background:rgba(245,158,11,.12);color:var(--amber-light);border:1px solid rgba(245,158,11,.2)}
.badge-indigo{background:rgba(99,102,241,.12);color:var(--indigo-light);border:1px solid rgba(99,102,241,.2)}

/* ===== PROJECTS ===== */
#projects{background:var(--bg2)}
.projects-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:24px}
.proj-card{background:var(--surface);border:1px solid rgba(255,255,255,.06);border-radius:var(--radius-lg);padding:28px;transition:transform .3s ease,box-shadow .3s ease;position:relative;overflow:hidden;cursor:default}
.proj-card::before{content:'';position:absolute;top:0;left:-100%;right:0;height:2px;background:linear-gradient(90deg,var(--indigo-light),var(--pink),var(--cyan));transition:left .4s ease}
.proj-card:hover::before{left:0}
.proj-card:hover{transform:translateY(-6px);box-shadow:0 20px 48px rgba(0,0,0,.4)}
.proj-emoji{font-size:32px;margin-bottom:16px;display:block}
.proj-name{font-family:var(--font-head);font-size:16px;font-weight:700;margin-bottom:8px}
.proj-desc{font-size:13px;color:var(--text2);line-height:1.65;margin-bottom:16px}
.proj-tags{display:flex;flex-wrap:wrap;gap:6px}
.proj-tag{font-size:11px;padding:3px 9px;border-radius:6px;background:rgba(99,102,241,.1);border:1px solid rgba(99,102,241,.2);color:var(--indigo-light);font-weight:500}
@media(max-width:900px){.projects-grid{grid-template-columns:1fr 1fr}}
@media(max-width:600px){.projects-grid{grid-template-columns:1fr}}

/* ===== EDUCATION & LANGUAGES ===== */
#education{background:var(--bg)}
.edu-lang-grid{display:grid;grid-template-columns:1fr 1fr;gap:48px}
.edu-cards{display:flex;flex-direction:column;gap:20px}
.edu-card{background:var(--surface);border:1px solid rgba(255,255,255,.06);border-radius:var(--radius);padding:24px}
.edu-degree{font-family:var(--font-head);font-size:16px;font-weight:700;margin-bottom:4px}
.edu-school{font-size:14px;color:var(--cyan-light);font-weight:600;margin-bottom:8px}
.edu-detail{font-size:13px;color:var(--text2)}
.lang-wrap{display:flex;flex-direction:column;gap:16px}
.lang-card{background:var(--surface);border:1px solid rgba(255,255,255,.06);border-radius:var(--radius);padding:20px;display:flex;align-items:center;gap:16px}
.lang-flag{font-size:28px}
.lang-name{font-family:var(--font-head);font-weight:700;font-size:15px;margin-bottom:4px}
.lang-badge{display:inline-block;font-size:11px;font-weight:700;padding:2px 10px;border-radius:99px;letter-spacing:.05em;animation:badge-pulse 3s ease-in-out infinite}
.native-badge{background:linear-gradient(135deg,var(--indigo-light),var(--pink));color:#fff}
.fluent-badge{background:linear-gradient(135deg,var(--cyan),var(--indigo-light));color:#fff}
@keyframes badge-pulse{0%,100%{box-shadow:0 0 0 0 rgba(99,102,241,.4)}50%{box-shadow:0 0 0 6px rgba(99,102,241,0)}}
.cert-cards{display:flex;flex-direction:column;gap:12px;margin-top:24px}
.cert-card{background:rgba(245,158,11,.06);border:1px solid rgba(245,158,11,.15);border-radius:var(--radius);padding:14px 18px;display:flex;align-items:center;gap:12px;font-size:13px;font-weight:500}
.cert-icon{color:var(--amber-light);font-size:16px}
@media(max-width:800px){.edu-lang-grid{grid-template-columns:1fr}}

/* ===== CONTACT ===== */
#contact{background:var(--bg2);padding-bottom:80px}
.contact-inner{display:grid;grid-template-columns:1fr auto;gap:60px;align-items:start}
.contact-cards{display:flex;flex-direction:column;gap:16px}
.contact-card{background:var(--surface);border:1px solid rgba(255,255,255,.06);border-radius:var(--radius);padding:18px 22px;display:flex;align-items:center;gap:16px;transition:transform .25s ease,box-shadow .25s ease;cursor:default}
.contact-card:hover{transform:translateX(8px);box-shadow:var(--glow-cyan)}
.contact-icon{width:42px;height:42px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0}
.ci-email{background:rgba(99,102,241,.15);border:1px solid rgba(99,102,241,.2)}
.ci-phone{background:rgba(6,182,212,.15);border:1px solid rgba(6,182,212,.2)}
.ci-loc{background:rgba(245,158,11,.15);border:1px solid rgba(245,158,11,.2)}
.ci-avail{background:rgba(236,72,153,.15);border:1px solid rgba(236,72,153,.2)}
.contact-label{font-size:11px;color:var(--text3);text-transform:uppercase;letter-spacing:.08em;margin-bottom:2px}
.contact-value{font-size:14px;font-weight:600;color:var(--text)}
.contact-avatar-wrap{position:relative;display:flex;align-items:center;justify-content:center;width:200px;height:200px}
.ripple{position:absolute;border-radius:50%;border:2px solid;animation:ripple-out 3s ease-out infinite}
.ripple-1{width:100px;height:100px;border-color:rgba(99,102,241,.6);animation-delay:0s}
.ripple-2{width:140px;height:140px;border-color:rgba(99,102,241,.35);animation-delay:.7s}
.ripple-3{width:180px;height:180px;border-color:rgba(99,102,241,.15);animation-delay:1.4s}
@keyframes ripple-out{0%{transform:scale(.6);opacity:1}100%{transform:scale(1.1);opacity:0}}
.contact-avatar{position:relative;z-index:2;width:80px;height:80px;border-radius:50%;background:linear-gradient(135deg,var(--indigo-light),var(--pink));display:flex;align-items:center;justify-content:center;font-family:var(--font-head);font-size:24px;font-weight:800;color:#fff;box-shadow:var(--glow-indigo),var(--glow-pink)}
@media(max-width:700px){.contact-inner{grid-template-columns:1fr}.contact-avatar-wrap{display:none}}

/* ===== FOOTER ===== */
footer{position:relative;z-index:2;text-align:center;padding:32px 5%;border-top:1px solid rgba(255,255,255,.05);color:var(--text3);font-size:13px}
footer span{color:var(--pink-light)}

/* ===== REDUCED MOTION ===== */
@media(prefers-reduced-motion:reduce){
  *{animation-duration:.01ms!important;animation-iteration-count:1!important;transition-duration:.01ms!important}
}
</style>
</head>
<body>

<!-- CURSOR -->
<div id="cursor-dot"></div>
<div id="cursor-ring"></div>

<!-- LOADER -->
<div id="loader">
  <div class="loader-initials">AN</div>
  <div class="loader-bar-wrap"><div class="loader-bar"></div></div>
  <div class="loader-text">Loading Portfolio</div>
</div>

<!-- PARTICLE CANVAS -->
<canvas id="bg-canvas"></canvas>

<!-- NAV -->
<nav id="navbar">
  <a href="#hero" class="nav-logo">Abdelrahman Nasser</a>
  <div class="nav-toggle" id="navToggle" onclick="document.querySelector('.nav-links').classList.toggle('open')">
    <span></span><span></span><span></span>
  </div>
  <ul class="nav-links">
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-inner">
    <div class="hero-left reveal fade-up">
      <div class="avail-tag"><span class="avail-dot"></span>Open to Opportunities</div>
      <h1 class="hero-name">Abdelrahman<br>Nasser</h1>
      <p class="hero-subtitle">PR Specialist · Film Director · <span>Multi-Industry Professional</span></p>
      <div class="hero-ctas">
        <a href="#contact" class="btn btn-primary">Get in Touch →</a>
        <a href="#experience" class="btn btn-outline">View Experience</a>
      </div>
    </div>
    <div class="hero-card-wrap reveal fade-left">
      <div class="hero-orb"></div>
      <div class="hero-ring"></div>
      <div class="hero-ring-2"></div>
      <div class="hero-card">
        <div class="card-avatar">AN</div>
        <div class="card-name">Abdelrahman Nasser</div>
        <div class="card-role">PR · Film · Corporate · Marketing</div>
        <div class="card-stats">
          <div class="stat-box"><div class="stat-num">8+</div><div class="stat-lbl">Roles Held</div></div>
          <div class="stat-box"><div class="stat-num">6+</div><div class="stat-lbl">Film Credits</div></div>
          <div class="stat-box"><div class="stat-num">3</div><div class="stat-lbl">Sectors</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-section">
  <div class="marquee-track" id="marqueeTrack">
    <span class="marquee-item">Jazeera Airways</span>
    <span class="marquee-item">Cairo Airport Travel</span>
    <span class="marquee-item">National Bank of Egypt</span>
    <span class="marquee-item">Vodafone</span>
    <span class="marquee-item">Property Hills</span>
    <span class="marquee-item">Raya Customer Experience</span>
    <span class="marquee-item">Guy Ritchie</span>
    <span class="marquee-item">Marwan Hamed</span>
    <span class="marquee-item">Helwan University</span>
    <span class="marquee-item">Mohamed Kotb</span>
    <span class="marquee-item">Jazeera Airways</span>
    <span class="marquee-item">Cairo Airport Travel</span>
    <span class="marquee-item">National Bank of Egypt</span>
    <span class="marquee-item">Vodafone</span>
    <span class="marquee-item">Property Hills</span>
    <span class="marquee-item">Raya Customer Experience</span>
    <span class="marquee-item">Guy Ritchie</span>
    <span class="marquee-item">Marwan Hamed</span>
    <span class="marquee-item">Helwan University</span>
    <span class="marquee-item">Mohamed Kotb</span>
  </div>
</div>

<!-- SKILLS -->
<section id="skills">
  <div style="max-width:1100px;margin:0 auto">
    <p class="section-label">What I Bring</p>
    <h2 class="section-title">Skills & <span class="gradient-text">Expertise</span></h2>
    <div class="skills-grid">
      <div class="skill-bars reveal fade-left" id="skillBars">
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Public Relations & Communications</span><span class="skill-pct">95%</span></div>
          <div class="skill-track"><div class="skill-fill c1" data-pct="95"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Crisis Management</span><span class="skill-pct">90%</span></div>
          <div class="skill-track"><div class="skill-fill c2" data-pct="90"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Film Production & 1st AD Operations</span><span class="skill-pct">90%</span></div>
          <div class="skill-track"><div class="skill-fill c3" data-pct="90"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Customer Service & CRM</span><span class="skill-pct">95%</span></div>
          <div class="skill-track"><div class="skill-fill c4" data-pct="95"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Marketing & Media Buying</span><span class="skill-pct">80%</span></div>
          <div class="skill-track"><div class="skill-fill c1" data-pct="80"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Real Estate Sales & Market Analysis</span><span class="skill-pct">82%</span></div>
          <div class="skill-track"><div class="skill-fill c2" data-pct="82"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Team Leadership</span><span class="skill-pct">88%</span></div>
          <div class="skill-track"><div class="skill-fill c3" data-pct="88"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-meta"><span class="skill-name">Production Logistics & Coordination</span><span class="skill-pct">85%</span></div>
          <div class="skill-track"><div class="skill-fill c4" data-pct="85"></div></div>
        </div>
      </div>
      <div class="chip-cloud reveal fade-right" id="chipCloud">
        <span class="chip indigo">PR Strategy</span>
        <span class="chip pink">Media Relations</span>
        <span class="chip cyan">Film Set Operations</span>
        <span class="chip amber">1st AD</span>
        <span class="chip indigo">Press Releases</span>
        <span class="chip pink">Crisis Comms</span>
        <span class="chip cyan">Media Buying</span>
        <span class="chip amber">CRM Systems</span>
        <span class="chip indigo">Airport Operations</span>
        <span class="chip pink">Event Management</span>
        <span class="chip cyan">Travel Consulting</span>
        <span class="chip amber">Market Analysis (CMA)</span>
        <span class="chip indigo">Team Leadership</span>
        <span class="chip pink">Customer Retention</span>
        <span class="chip cyan">Storyboarding</span>
        <span class="chip amber">Sales Strategy</span>
        <span class="chip indigo">Production Coordination</span>
        <span class="chip pink">Call Center Ops</span>
        <span class="chip cyan">Government Liaison</span>
        <span class="chip amber">ICDL</span>
        <span class="chip indigo">Arabic</span>
        <span class="chip pink">English</span>
        <span class="chip cyan">Styling & Wardrobe</span>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div style="max-width:900px;margin:0 auto">
    <p class="section-label">Work History</p>
    <h2 class="section-title">Professional <span class="gradient-text">Experience</span></h2>
    <div class="timeline">

      <div class="exp-card reveal fade-up">
        <div class="exp-header">
          <div><div class="exp-title">PR Specialist</div><div class="exp-company">Jazeera Airways</div></div>
          <div class="exp-meta"><span class="exp-date">Aviation</span></div>
        </div>
        <p class="exp-desc">Official company representative at the airport maintaining high brand standards. Liaised with airport authorities and government entities. Managed media relations and passenger communications during flight updates. Developed and executed crisis communication strategies and drafted official press releases. Led press events and high-profile airport visits.</p>
        <div class="exp-badges">
          <span class="badge badge-pink">Media Relations</span>
          <span class="badge badge-cyan">Crisis Comms</span>
          <span class="badge badge-amber">Press Releases</span>
          <span class="badge badge-indigo">Government Liaison</span>
        </div>
      </div>

      <div class="exp-card reveal fade-up">
        <div class="exp-header">
          <div><div class="exp-title">Travel Advisor</div><div class="exp-company">Cairo Airport Travel</div></div>
          <div class="exp-meta"><span class="exp-date">Travel & Tourism</span></div>
        </div>
        <p class="exp-desc">Orchestrated comprehensive domestic and international travel itineraries for high-volume clientele. Managed full-cycle booking, invoicing, and vendor communications. Rapidly resolved travel-related disruptions to minimize client impact.</p>
        <div class="exp-badges">
          <span class="badge badge-cyan">Travel Planning</span>
          <span class="badge badge-amber">Vendor Management</span>
          <span class="badge badge-indigo">Client Relations</span>
        </div>
      </div>

      <div class="exp-card reveal fade-up">
        <div class="exp-header">
          <div><div class="exp-title">Real Estate Agent</div><div class="exp-company">Property Hills</div></div>
          <div class="exp-meta"><span class="exp-date">Real Estate</span></div>
        </div>
        <p class="exp-desc">Executed high-value sales strategies through targeted advertisements, open houses, and professional listing services. Conducted deep-dive financial assessments to match clients with optimal real estate solutions. Utilized comparative market analysis (CMA) to estimate property values and investment potential. Managed end-to-end property auctions and exchanges.</p>
        <div class="exp-badges">
          <span class="badge badge-pink">Sales Strategy</span>
          <span class="badge badge-cyan">CMA Analysis</span>
          <span class="badge badge-amber">Property Auctions</span>
        </div>
      </div>

      <div class="exp-card reveal fade-up">
        <div class="exp-header">
          <div><div class="exp-title">Customer Service Agent</div><div class="exp-company">National Bank of Egypt</div></div>
          <div class="exp-meta"><span class="exp-date">Banking</span></div>
        </div>
        <p class="exp-desc">Managed complex banking inquiries and resolved high-priority complaints with absolute professionalism. Collaborated with internal departments to streamline issue escalation and resolution processes. Ensured consistent client satisfaction through proactive problem-solving and follow-up.</p>
        <div class="exp-badges">
          <span class="badge badge-indigo">Banking Ops</span>
          <span class="badge badge-pink">Complaint Resolution</span>
          <span class="badge badge-cyan">Client Satisfaction</span>
        </div>
      </div>

      <div class="exp-card reveal fade-up">
        <div class="exp-header">
          <div><div class="exp-title">Call Center Agent — Team Leader</div><div class="exp-company">Vodafone</div></div>
          <div class="exp-meta"><span class="exp-date">Telecom</span></div>
        </div>
        <p class="exp-desc">Led a team in providing rapid solutions for customer concerns, directly impacting retention rates. Maintained peak performance and emotional control during high-pressure, difficult customer interactions.</p>
        <div class="exp-badges">
          <span class="badge badge-pink">Team Leadership</span>
          <span class="badge badge-amber">Customer Retention</span>
          <span class="badge badge-indigo">Call Center Ops</span>
        </div>
      </div>

      <div class="exp-card reveal fade-up">
        <div class="exp-header">
          <div><div class="exp-title">Customer Service Agent</div><div class="exp-company">Raya Customer Experience (Justlife UAE)</div></div>
          <div class="exp-meta"><span class="exp-date">CX / UAE</span></div>
        </div>
        <p class="exp-desc">Managed intricate booking and reservation logistics through advanced CRM systems. Coordinated with operations teams to ensure seamless service delivery for international clients.</p>
        <div class="exp-badges">
          <span class="badge badge-cyan">CRM Systems</span>
          <span class="badge badge-amber">International Clients</span>
          <span class="badge badge-indigo">Reservations</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div style="max-width:1100px;margin:0 auto">
    <p class="section-label">Selected Work</p>
    <h2 class="section-title">Film & <span class="gradient-text">Production Credits</span></h2>
    <div class="projects-grid">

      <div class="proj-card reveal fade-up">
        <span class="proj-emoji">🎬</span>
        <div class="proj-name">Fountain of Youth Film</div>
        <div class="proj-desc">Production Assistant on the Egypt shoot of Guy Ritchie's feature film. Supported on-set operations and international crew coordination in Cairo.</div>
        <div class="proj-tags"><span class="proj-tag">Guy Ritchie</span><span class="proj-tag">Feature Film</span><span class="proj-tag">Egypt</span></div>
      </div>

      <div class="proj-card reveal fade-up">
        <span class="proj-emoji">🏗️</span>
        <div class="proj-name">Beta Compound Commercial</div>
        <div class="proj-desc">Served as 2nd Assistant Director on a real estate commercial directed by acclaimed Egyptian director Marwan Hamed, managing talent and set flow.</div>
        <div class="proj-tags"><span class="proj-tag">Marwan Hamed</span><span class="proj-tag">2nd AD</span><span class="proj-tag">Commercial</span></div>
      </div>

      <div class="proj-card reveal fade-up">
        <span class="proj-emoji">🏙️</span>
        <div class="proj-name">Vivenda Real Estate Commercial</div>
        <div class="proj-desc">1st Assistant Director on a high-end real estate commercial, co-directed by Omar Salem and Hassan El Menshawy. Full production logistics and crew management.</div>
        <div class="proj-tags"><span class="proj-tag">Omar Salem</span><span class="proj-tag">1st AD</span><span class="proj-tag">Real Estate</span></div>
      </div>

      <div class="proj-card reveal fade-up">
        <span class="proj-emoji">🏦</span>
        <div class="proj-name">Bank El Shifa Commercial</div>
        <div class="proj-desc">1st AD on the Bank El Shifa brand commercial under Director Hassan El Menshawy. Oversaw scheduling, script breakdown, and on-set direction support.</div>
        <div class="proj-tags"><span class="proj-tag">Hassan El Menshawy</span><span class="proj-tag">1st AD</span><span class="proj-tag">Banking</span></div>
      </div>

      <div class="proj-card reveal fade-up">
        <span class="proj-emoji">🎭</span>
        <div class="proj-name">Launch Box TV Series</div>
        <div class="proj-desc">Acted in a sales-focused role within this Egyptian television series directed by Hesham El Rashidy, showcasing on-screen presence and product storytelling.</div>
        <div class="proj-tags"><span class="proj-tag">Actor</span><span class="proj-tag">TV Series</span><span class="proj-tag">Hesham El Rashidy</span></div>
      </div>

      <div class="proj-card reveal fade-up">
        <span class="proj-emoji">🎪</span>
        <div class="proj-name">Events & Live Shows</div>
        <div class="proj-desc">Assistant Director and Stylist across various live events and stage productions, handling talent direction, wardrobe coordination, and show flow management.</div>
        <div class="proj-tags"><span class="proj-tag">AD</span><span class="proj-tag">Stylist</span><span class="proj-tag">Live Events</span></div>
      </div>

    </div>
  </div>
</section>

<!-- EDUCATION -->
<section id="education">
  <div style="max-width:1100px;margin:0 auto">
    <p class="section-label">Background</p>
    <h2 class="section-title">Education & <span class="gradient-text">Languages</span></h2>
    <div class="edu-lang-grid">
      <div>
        <div class="edu-cards reveal fade-left">
          <div class="edu-card">
            <div class="edu-degree">Bachelor of Arts — History</div>
            <div class="edu-school">Helwan University, Cairo</div>
            <div class="edu-detail">Strong foundation in research, analytical thinking, and cultural context — skills that transfer directly to storytelling, PR, and client communication.</div>
          </div>
        </div>
        <div class="cert-cards reveal fade-left">
          <div class="cert-card"><span class="cert-icon">📊</span>Marketing & Media Buying — Mohamed Kotb</div>
          <div class="cert-card"><span class="cert-icon">💻</span>ICDL — Computer Literacy</div>
          <div class="cert-card"><span class="cert-icon">📣</span>Public Relations Training</div>
          <div class="cert-card"><span class="cert-icon">🗣️</span>Advanced Communication Skills</div>
        </div>
      </div>
      <div class="lang-wrap reveal fade-right">
        <div class="lang-card">
          <span class="lang-flag">🇪🇬</span>
          <div>
            <div class="lang-name">Arabic</div>
            <span class="lang-badge native-badge">Native Speaker</span>
          </div>
        </div>
        <div class="lang-card">
          <span class="lang-flag">🇬🇧</span>
          <div>
            <div class="lang-name">English</div>
            <span class="lang-badge fluent-badge">Excellent Proficiency</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div style="max-width:900px;margin:0 auto">
    <p class="section-label">Let's Connect</p>
    <h2 class="section-title">Get In <span class="gradient-text">Touch</span></h2>
    <div class="contact-inner">
      <div class="contact-cards">
        <div class="contact-card reveal fade-left">
          <div class="contact-icon ci-email">📧</div>
          <div><div class="contact-label">Email</div><div class="contact-value">abdelrhmannasser720@gmail.com</div></div>
        </div>
        <div class="contact-card reveal fade-left">
          <div class="contact-icon ci-phone">📱</div>
          <div><div class="contact-label">Phone</div><div class="contact-value">+20 115 099 0182</div></div>
        </div>
        <div class="contact-card reveal fade-left">
          <div class="contact-icon ci-loc">📍</div>
          <div><div class="contact-label">Location</div><div class="contact-value">Cairo, Egypt</div></div>
        </div>
        <div class="contact-card reveal fade-left">
          <div class="contact-icon ci-avail">✅</div>
          <div><div class="contact-label">Status</div><div class="contact-value">Open to New Opportunities</div></div>
        </div>
        <div class="contact-card reveal fade-left">
          <div class="contact-icon ci-email" style="background:rgba(6,182,212,.15);border-color:rgba(6,182,212,.2)">🔗</div>
          <div><div class="contact-label">LinkedIn</div><div class="contact-value">abdelrhman-nasser-566439223</div></div>
        </div>
      </div>
      <div class="contact-avatar-wrap reveal fade-right">
        <div class="ripple ripple-1"></div>
        <div class="ripple ripple-2"></div>
        <div class="ripple ripple-3"></div>
        <div class="contact-avatar">AN</div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p>Built with <span>♥</span> · Abdelrahman Nasser © 2025 · Cairo, Egypt</p>
</footer>

<script>
/* ===== LOADER ===== */
window.addEventListener('load',()=>{
  setTimeout(()=>{
    document.getElementById('loader').classList.add('hide');
    document.getElementById('navbar').classList.add('visible');
  },2200);
});

/* ===== CUSTOM CURSOR ===== */
const dot=document.getElementById('cursor-dot');
const ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;dot.style.left=mx+'px';dot.style.top=my+'px'});
(function animRing(){rx+=(mx-rx)*.12;ry+=(my-ry)*.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animRing)})();
document.querySelectorAll('a,button,.btn,.proj-card,.exp-card,.contact-card').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ring.style.width='56px';ring.style.height='56px';ring.style.borderColor='rgba(236,72,153,.8)'});
  el.addEventListener('mouseleave',()=>{ring.style.width='36px';ring.style.height='36px';ring.style.borderColor='rgba(99,102,241,.7)'});
});

/* ===== PARTICLE CANVAS ===== */
const canvas=document.getElementById('bg-canvas');
const ctx=canvas.getContext('2d');
let W,H,particles=[];
const COLORS=['rgba(99,102,241,','rgba(236,72,153,','rgba(6,182,212,','rgba(245,158,11,'];
function resize(){W=canvas.width=window.innerWidth;H=canvas.height=window.innerHeight}
window.addEventListener('resize',()=>{resize();initParticles()});
resize();
function Particle(){
  this.x=Math.random()*W;this.y=Math.random()*H;
  this.vx=(Math.random()-.5)*.4;this.vy=(Math.random()-.5)*.4;
  this.r=Math.random()*2+1;
  this.color=COLORS[Math.floor(Math.random()*COLORS.length)];
  this.alpha=Math.random()*.6+.2;
}
function initParticles(){
  const n=Math.min(80,Math.floor(W*H/14000));
  particles=Array.from({length:n},()=>new Particle());
}
initParticles();
function drawParticles(){
  ctx.clearRect(0,0,W,H);
  particles.forEach((p,i)=>{
    p.x+=p.vx;p.y+=p.vy;
    if(p.x<0||p.x>W)p.vx*=-1;
    if(p.y<0||p.y>H)p.vy*=-1;
    ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
    ctx.fillStyle=p.color+p.alpha+')';ctx.fill();
    for(let j=i+1;j<particles.length;j++){
      const q=particles[j];
      const dx=p.x-q.x,dy=p.y-q.y,dist=Math.sqrt(dx*dx+dy*dy);
      if(dist<140){
        const a=(1-dist/140)*0.25;
        ctx.beginPath();ctx.moveTo(p.x,p.y);ctx.lineTo(q.x,q.y);
        ctx.strokeStyle=p.color+a+')';ctx.lineWidth=1;ctx.stroke();
      }
    }
  });
  requestAnimationFrame(drawParticles);
}
drawParticles();

/* ===== SCROLL REVEAL ===== */
const observer=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('visible');observer.unobserve(e.target)}});
},{threshold:.12,rootMargin:'0px 0px -40px 0px'});
document.querySelectorAll('.reveal').forEach(el=>observer.observe(el));

/* ===== SKILL BARS ===== */
const skillObserver=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.querySelectorAll('.skill-fill').forEach(bar=>{
        const pct=bar.dataset.pct;
        setTimeout(()=>{bar.style.width=pct+'%';bar.classList.add('animated')},200);
      });
      skillObserver.unobserve(e.target);
    }
  });
},{threshold:.2});
const skillSection=document.getElementById('skillBars');
if(skillSection)skillObserver.observe(skillSection);

/* ===== SMOOTH SCROLL + NAV CLOSE ===== */
document.querySelectorAll('a[href^="#"]').forEach(a=>{
  a.addEventListener('click',e=>{
    e.preventDefault();
    const t=document.querySelector(a.getAttribute('href'));
    if(t)t.scrollIntoView({behavior:'smooth'});
    document.querySelector('.nav-links').classList.remove('open');
  });
});
</script>
</body>
</html>
