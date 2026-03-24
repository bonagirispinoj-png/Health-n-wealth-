<!DOCTYPE html>
<!--
╔══════════════════════════════════════════════════════════════════════╗
║           HEALTH CONSCIOUS BOOK — FIREBASE HOSTING GUIDE            ║
╠══════════════════════════════════════════════════════════════════════╣
║  STEP 1: Rename this file to  index.html                            ║
║  STEP 2: Create firebase.json in same folder:                       ║
║                                                                      ║
║  {                                                                   ║
║    "hosting": {                                                      ║
║      "public": ".",                                                  ║
║      "ignore": ["firebase.json"],                                    ║
║      "headers": [{                                                   ║
║        "source": "**",                                               ║
║        "headers": [                                                  ║
║          {"key":"Cache-Control","value":"no-cache"},                 ║
║          {"key":"X-Frame-Options","value":"SAMEORIGIN"},             ║
║          {"key":"X-Content-Type-Options","value":"nosniff"}          ║
║        ]                                                             ║
║      }]                                                              ║
║    }                                                                 ║
║  }                                                                   ║
║                                                                      ║
║  STEP 3: Open terminal in that folder and run:                       ║
║    npm install -g firebase-tools                                     ║
║    firebase login                                                    ║
║    firebase deploy --only hosting                                    ║
║                                                                      ║
║  LIVE URL: https://neurocoin-ntc.web.app                             ║
║                                                                      ║
║  AUTHORIZE DOMAIN (IMPORTANT after deploy):                          ║
║    Firebase Console → Authentication → Settings                      ║
║    → Authorized domains → Add: neurocoin-ntc.web.app                ║
║    (Already added: neurocoin-ntc.firebaseapp.com)                    ║
╚══════════════════════════════════════════════════════════════════════╝
-->
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0"/>
<meta name="theme-color" content="#1a3a2a"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<!-- Hosting optimizations for Firebase / Cloudflare Pages -->
<meta http-equiv="X-Content-Type-Options" content="nosniff"/>
<meta http-equiv="X-XSS-Protection" content="1; mode=block"/>
<meta http-equiv="Referrer-Policy" content="strict-origin-when-cross-origin"/>
<meta name="robots" content="noindex,nofollow"/>
<!-- PWA Manifest (inline) -->
<link rel="manifest" href="data:application/manifest+json,{
  %22name%22:%22HealthConscious Book%22,
  %22short_name%22:%22HealthBook%22,
  %22start_url%22:%22/%22,
  %22display%22:%22standalone%22,
  %22background_color%22:%22%230a1f14%22,
  %22theme_color%22:%22%231a3a2a%22,
  %22description%22:%22Complete Guide to Healthy Eating%22
}"/>
<title>HealthConscious Book — Complete Guide to Healthy Eating</title>
<!-- Firebase/Cloudflare Hosting Optimizations -->
<meta http-equiv="X-Content-Type-Options" content="nosniff"/>
<meta http-equiv="X-XSS-Protection" content="1; mode=block"/>
<meta http-equiv="Referrer-Policy" content="strict-origin-when-cross-origin"/>
<meta name="robots" content="noindex,nofollow"/>
<meta name="mobile-web-app-capable" content="yes"/>
<meta property="og:title" content="HealthConscious Book"/>
<meta property="og:description" content="Complete Guide to Healthy Eating — Birth to Old Age"/>
<!-- PWA Manifest (inline for single-file deployment) -->
<link rel="manifest" href='data:application/manifest+json,{"name":"HealthConscious Book","short_name":"HealthBook","start_url":"/","display":"standalone","background_color":"%230a1f14","theme_color":"%231a3a2a","description":"Complete Guide to Healthy Eating"}'/>

<!-- Premium fonts -->
<!-- Firebase Hosting Performance Optimizations -->
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link rel="preconnect" href="https://www.gstatic.com"/>
<link rel="preconnect" href="https://firebasestorage.googleapis.com"/>
<link rel="dns-prefetch" href="https://neurocoin-ntc-default-rtdb.firebaseio.com"/>
<link rel="dns-prefetch" href="https://firestore.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;0,900;1,400;1,600&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>

<!-- Firebase -->
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore-compat.js"></script>

<style>
/* ═══════════════════════════════════════════════════════════
   HEALTHCONSCIOUS — Premium Wellness Brand
   Luxury forest green · Warm gold · Cream white
   Playfair Display + DM Sans typography
   ═══════════════════════════════════════════════════════════ */
:root{
  /* Brand colors */
  --forest:  #1a3a2a;
  --forest2: #243d30;
  --forest3: #0f2419;
  --sage:    #3d6b4f;
  --sage-l:  #5a9970;
  --mint:    #e8f5ee;
  --mint2:   #d4ebde;

  /* Gold accent */
  --gold:    #c9963a;
  --gold2:   #e8b86d;
  --gold3:   #f5d49a;
  --gold-dk: #8a5e1a;

  /* Neutrals */
  --cream:   #faf7f2;
  --warm:    #f5f0e8;
  --parch:   #ede5d5;
  --ink:     #1c1c1c;
  --charcoal:#2d2d2d;
  --stone:   #6b7280;
  --border:  #e5e0d8;
  --white:   #ffffff;

  /* Status */
  --success: #2d6a4f;
  --success-l:#d8f3dc;
  --danger:  #b91c1c;
  --danger-l:#fee2e2;
  --warn:    #92400e;
  --warn-l:  #fef3c7;
  --info:    #1e3a5f;
  --info-l:  #dbeafe;

  /* Shadows */
  --shadow-sm: 0 1px 3px rgba(26,58,42,.08), 0 1px 2px rgba(26,58,42,.06);
  --shadow:    0 4px 16px rgba(26,58,42,.1), 0 2px 6px rgba(26,58,42,.06);
  --shadow-lg: 0 10px 40px rgba(26,58,42,.15), 0 4px 12px rgba(26,58,42,.08);
  --shadow-xl: 0 20px 60px rgba(0,0,0,.2);

  /* Transitions */
  --ease: cubic-bezier(.4,0,.2,1);
}

/* ── RESET & BASE ── */
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent;}
html{height:100%;scroll-behavior:smooth;}
body{
  font-family:'DM Sans',system-ui,sans-serif;
  background:var(--cream);color:var(--ink);
  min-height:100vh;font-size:15px;line-height:1.6;
  -webkit-font-smoothing:antialiased;
}

/* ── TYPOGRAPHY ── */
.serif{font-family:'Playfair Display',Georgia,serif;}
h1,h2,h3{font-family:'Playfair Display',serif;line-height:1.25;}

/* ── SCROLLBAR ── */
::-webkit-scrollbar{width:5px;height:5px;}
::-webkit-scrollbar-track{background:var(--cream);}
::-webkit-scrollbar-thumb{background:var(--parch);border-radius:3px;}

/* ═══ SCREENS & TRANSITIONS ═══ */
.screen{
  position:fixed;inset:0;z-index:10;
  display:flex;flex-direction:column;
  opacity:0;transform:translateY(12px);
  pointer-events:none;transition:opacity .35s var(--ease),transform .35s var(--ease);
  overflow:hidden;
}
.screen.active{
  opacity:1;transform:translateY(0);pointer-events:all;
}

/* ═══ SPLASH SCREEN ═══ */
#splash{
  background:var(--forest3);
  align-items:center;justify-content:center;z-index:100;
}
.splash-logo{text-align:center;}
.splash-leaf{
  width:72px;height:72px;margin:0 auto 20px;
  animation:leafPulse 2s var(--ease) infinite;
}
@keyframes leafPulse{
  0%,100%{transform:scale(1);filter:drop-shadow(0 0 12px rgba(201,150,58,.4));}
  50%{transform:scale(1.06);filter:drop-shadow(0 0 24px rgba(201,150,58,.7));}
}
.splash-name{
  font-family:'Playfair Display',serif;font-size:1.9rem;
  font-weight:900;color:var(--white);letter-spacing:.5px;
}
.splash-name span{color:var(--gold2);}
.splash-tag{color:rgba(255,255,255,.5);font-size:.82rem;
  letter-spacing:2px;margin-top:6px;text-transform:uppercase;}
.splash-bar{
  width:140px;height:2px;background:rgba(255,255,255,.1);
  border-radius:1px;margin:28px auto 0;overflow:hidden;
}
.splash-bar-fill{
  height:100%;background:linear-gradient(90deg,var(--gold),var(--gold2));
  border-radius:1px;animation:splashLoad 2.2s var(--ease) forwards;
}
@keyframes splashLoad{from{width:0%;}to{width:100%;}}

/* ═══ AUTH SCREEN ═══ */
#authScreen{
  background:var(--forest3);overflow-y:auto;
  align-items:center;justify-content:flex-start;padding:0;
}
.auth-hero{
  width:100%;
  background:linear-gradient(160deg,var(--forest3) 0%,var(--forest) 60%,#1f4530 100%);
  padding:52px 24px 40px;text-align:center;position:relative;overflow:hidden;
  flex-shrink:0;
}
.auth-hero::before{
  content:'';position:absolute;inset:0;
  background:url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none'%3E%3Cg fill='%23ffffff' fill-opacity='0.025'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
}
.auth-brand{
  display:inline-flex;align-items:center;gap:12px;margin-bottom:20px;
  position:relative;
}
.auth-brand-logo{width:44px;height:44px;}
.auth-brand-name{
  font-family:'Playfair Display',serif;font-size:1.6rem;
  font-weight:900;color:var(--white);letter-spacing:.3px;
}
.auth-brand-name em{color:var(--gold2);font-style:normal;}
.auth-tagline{
  color:rgba(255,255,255,.65);font-size:.82rem;
  letter-spacing:.5px;margin-bottom:24px;font-weight:300;
}
.auth-pills{display:flex;justify-content:center;gap:7px;flex-wrap:wrap;}
.auth-pill{
  background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);
  color:rgba(255,255,255,.85);padding:5px 12px;border-radius:20px;
  font-size:.72rem;font-weight:500;letter-spacing:.3px;
}

.auth-form-wrap{
  width:100%;max-width:420px;margin:0 auto;
  padding:28px 20px 40px;flex-shrink:0;
}
.auth-card{
  background:var(--white);border-radius:20px;
  padding:28px 24px;box-shadow:var(--shadow-xl);
  border:1px solid rgba(255,255,255,.2);
}
.auth-tabs{
  display:flex;background:var(--warm);
  border-radius:12px;padding:4px;margin-bottom:22px;gap:4px;
}
.auth-tab{
  flex:1;padding:9px;border:none;border-radius:9px;cursor:pointer;
  font-family:'DM Sans',sans-serif;font-size:.84rem;font-weight:600;
  transition:.2s var(--ease);background:transparent;color:var(--stone);
}
.auth-tab.on{
  background:var(--forest);color:var(--white);
  box-shadow:0 2px 8px rgba(26,58,42,.25);
}

.inp-group{margin-bottom:14px;}
.inp-label{
  display:block;font-size:.76rem;font-weight:600;
  color:var(--charcoal);margin-bottom:6px;letter-spacing:.3px;
}
.inp-field{
  width:100%;padding:12px 14px;
  border:1.5px solid var(--border);border-radius:10px;
  font-family:'DM Sans',sans-serif;font-size:.92rem;
  color:var(--ink);background:var(--cream);
  outline:none;transition:.2s var(--ease);
}
.inp-field:focus{
  border-color:var(--sage);background:var(--white);
  box-shadow:0 0 0 3px rgba(61,107,79,.1);
}
.inp-field::placeholder{color:#b0a898;}
.inp-hint{font-size:.7rem;color:var(--stone);margin-top:4px;}

.cta-btn{
  width:100%;padding:14px;border:none;border-radius:12px;cursor:pointer;
  font-family:'DM Sans',sans-serif;font-size:.92rem;font-weight:700;
  letter-spacing:.3px;transition:.2s var(--ease);
  background:linear-gradient(135deg,var(--forest),var(--sage));
  color:var(--white);box-shadow:0 4px 16px rgba(26,58,42,.3);
  position:relative;overflow:hidden;
}
.cta-btn::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,transparent,rgba(255,255,255,.08));
}
.cta-btn:hover{transform:translateY(-1px);box-shadow:0 6px 22px rgba(26,58,42,.4);}
.cta-btn:active{transform:translateY(0);}
.cta-btn:disabled{opacity:.6;cursor:not-allowed;transform:none;}
.cta-btn.loading::before{
  content:'';display:inline-block;width:14px;height:14px;
  border:2px solid rgba(255,255,255,.3);border-top-color:#fff;
  border-radius:50%;animation:spin .7s linear infinite;
  margin-right:8px;vertical-align:middle;
}

.auth-err{
  font-size:.78rem;color:var(--danger);text-align:center;
  min-height:18px;margin-top:8px;font-weight:500;
}
.auth-ok{color:var(--success);font-weight:600;}

/* ═══ MAIN APP LAYOUT ═══ */
#appScreen{
  background:var(--cream);
  justify-content:flex-start;
}

/* ── HEADER ── */
.app-header{
  background:var(--white);border-bottom:1px solid var(--border);
  padding:0 18px;height:58px;
  display:flex;align-items:center;justify-content:space-between;
  flex-shrink:0;z-index:50;position:sticky;top:0;
  box-shadow:var(--shadow-sm);
}
.header-brand{display:flex;align-items:center;gap:10px;}
.header-logo{width:32px;height:32px;}
.header-name{
  font-family:'Playfair Display',serif;font-size:1rem;
  font-weight:700;color:var(--forest);
}
.header-name em{color:var(--gold);font-style:normal;}
.header-right{display:flex;align-items:center;gap:8px;}
.wallet-chip{
  display:flex;align-items:center;gap:5px;
  background:var(--mint);border:1px solid var(--mint2);
  padding:5px 11px;border-radius:20px;
  font-size:.78rem;font-weight:700;color:var(--forest);
}
.logout-btn{
  width:32px;height:32px;border-radius:8px;
  background:var(--warm);border:1px solid var(--border);
  display:flex;align-items:center;justify-content:center;
  cursor:pointer;font-size:.8rem;transition:.2s;color:var(--stone);
}
.logout-btn:hover{background:var(--danger-l);color:var(--danger);border-color:var(--danger);}

/* ── BOTTOM NAV ── */
.bottom-nav{
  position:fixed;bottom:0;left:0;right:0;z-index:50;
  background:var(--white);border-top:1px solid var(--border);
  display:flex;height:64px;
  box-shadow:0 -4px 20px rgba(0,0,0,.06);
  padding-bottom:env(safe-area-inset-bottom);
}
.nav-item{
  flex:1;display:flex;flex-direction:column;align-items:center;
  justify-content:center;gap:3px;cursor:pointer;
  border:none;background:none;font-family:'DM Sans',sans-serif;
  transition:.2s var(--ease);padding:8px 4px;
  position:relative;
}
.nav-item.active{color:var(--forest);}
.nav-item:not(.active){color:var(--stone);}
.nav-ico{font-size:1.25rem;line-height:1;}
.nav-lbl{font-size:.62rem;font-weight:600;letter-spacing:.3px;}
.nav-item.active .nav-ico{transform:translateY(-2px);}
.nav-item.active::after{
  content:'';position:absolute;bottom:0;left:50%;
  transform:translateX(-50%);
  width:28px;height:3px;background:var(--forest);border-radius:2px 2px 0 0;
}
.nav-admin{background:var(--forest3)!important;}
.nav-admin .nav-ico,.nav-admin .nav-lbl{color:var(--gold)!important;}

/* ── PAGE CONTAINER ── */
.pages{flex:1;overflow-y:auto;padding-bottom:80px;}
.pages::-webkit-scrollbar{width:0;}
.pg{display:none;animation:pgIn .3s var(--ease) both;}
.pg.active{display:block;}
@keyframes pgIn{from{opacity:0;transform:translateY(8px);}to{opacity:1;transform:none;}}

/* ── SECTION CONTAINER ── */
.wrap{max-width:680px;margin:0 auto;padding:20px 16px;}

/* ── CARDS ── */
.card{
  background:var(--white);border-radius:16px;
  padding:20px;margin-bottom:16px;
  border:1px solid var(--border);
  box-shadow:var(--shadow-sm);
  transition:.2s var(--ease);
}
.card:hover{box-shadow:var(--shadow);}
.card-title{
  font-family:'Playfair Display',serif;
  font-size:1rem;font-weight:700;color:var(--forest);
  margin-bottom:14px;padding-bottom:10px;
  border-bottom:1px solid var(--border);
  display:flex;align-items:center;gap:8px;
}
.card-title .ct-ico{font-size:1.1rem;}

/* ── ALERTS ── */
.alert{
  padding:11px 14px;border-radius:10px;margin:10px 0;
  font-size:.84rem;line-height:1.6;display:flex;gap:8px;align-items:flex-start;
}
.alert .ai{flex-shrink:0;margin-top:1px;}
.alert-s{background:var(--success-l);color:var(--success);border-left:3px solid var(--success);}
.alert-e{background:var(--danger-l);color:var(--danger);border-left:3px solid var(--danger);}
.alert-w{background:var(--warn-l);color:var(--warn);border-left:3px solid #d97706;}
.alert-i{background:var(--info-l);color:var(--info);border-left:3px solid #2563eb;}

/* ── STAT GRID ── */
.stat-grid{
  display:grid;grid-template-columns:repeat(auto-fit,minmax(100px,1fr));
  gap:10px;margin-bottom:18px;
}
.stat-card{
  background:var(--white);border:1px solid var(--border);
  border-radius:14px;padding:14px 12px;text-align:center;
  box-shadow:var(--shadow-sm);transition:.2s;
  position:relative;overflow:hidden;
}
.stat-card::before{
  content:'';position:absolute;top:0;left:0;right:0;
  height:3px;background:linear-gradient(90deg,var(--forest),var(--sage));
}
.stat-card.gold::before{background:linear-gradient(90deg,var(--gold-dk),var(--gold));}
.stat-card.warm::before{background:linear-gradient(90deg,#c2410c,#ea580c);}
.stat-v{
  font-family:'Playfair Display',serif;
  font-size:1.35rem;font-weight:700;color:var(--forest);
}
.stat-card.gold .stat-v{color:var(--gold-dk);}
.stat-card.warm .stat-v{color:#c2410c;}
.stat-l{font-size:.68rem;font-weight:600;color:var(--stone);
  margin-top:2px;letter-spacing:.3px;text-transform:uppercase;}

/* ── BUTTONS ── */
.btn{
  display:inline-flex;align-items:center;justify-content:center;gap:6px;
  padding:10px 18px;border:none;border-radius:10px;cursor:pointer;
  font-family:'DM Sans',sans-serif;font-weight:600;font-size:.85rem;
  transition:.2s var(--ease);letter-spacing:.2px;
}
.btn-primary{
  background:linear-gradient(135deg,var(--forest),var(--sage));
  color:var(--white);box-shadow:0 3px 12px rgba(26,58,42,.25);
}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 5px 18px rgba(26,58,42,.35);}
.btn-gold{
  background:linear-gradient(135deg,var(--gold-dk),var(--gold));
  color:var(--white);box-shadow:0 3px 12px rgba(139,94,26,.25);
}
.btn-gold:hover{transform:translateY(-1px);}
.btn-outline{
  background:transparent;border:1.5px solid var(--forest);color:var(--forest);
}
.btn-outline:hover{background:var(--mint);}
.btn-danger{background:var(--danger);color:var(--white);}
.btn-sm{padding:6px 12px;font-size:.76rem;}
.btn-full{width:100%;display:flex;}
.btn:active{transform:scale(.98);}
.btn:disabled{opacity:.5;cursor:not-allowed;transform:none!important;}

/* ── COMMISSION GRID ── */
.comm-grid{
  display:grid;grid-template-columns:repeat(5,1fr);gap:8px;margin:14px 0;
}
.comm-box{
  border-radius:12px;padding:12px 6px;text-align:center;
  border:1px solid;transition:.2s;
}
.comm-box:hover{transform:translateY(-2px);box-shadow:var(--shadow);}
.comm-l{font-size:.72rem;font-weight:700;margin-bottom:2px;}
.comm-v{font-size:1rem;font-weight:800;margin-bottom:2px;}
.comm-d{font-size:.62rem;color:var(--stone);}
.cb1{background:#f0fdf4;border-color:#86efac;}.cb1 .comm-l,.cb1 .comm-v{color:#166534;}
.cb2{background:#eff6ff;border-color:#93c5fd;}.cb2 .comm-l,.cb2 .comm-v{color:#1e3a8a;}
.cb3{background:#fff7ed;border-color:#fdba74;}.cb3 .comm-l,.cb3 .comm-v{color:#9a3412;}
.cb4{background:#fdf4ff;border-color:#d8b4fe;}.cb4 .comm-l,.cb4 .comm-v{color:#6b21a8;}
.cb5{background:#f0fdf4;border-color:#6ee7b7;}.cb5 .comm-l,.cb5 .comm-v{color:#065f46;}

/* ── HOW-IT-WORKS ── */
.flow-steps{display:flex;flex-direction:column;gap:0;}
.flow-step{
  display:flex;gap:14px;align-items:flex-start;
  padding:12px 0;position:relative;
}
.flow-step:not(:last-child)::after{
  content:'';position:absolute;left:17px;top:44px;
  width:2px;height:calc(100% - 20px);
  background:linear-gradient(180deg,var(--mint2),transparent);
}
.flow-num{
  width:34px;height:34px;border-radius:50%;flex-shrink:0;
  background:linear-gradient(135deg,var(--forest),var(--sage));
  color:var(--white);font-weight:700;font-size:.82rem;
  display:flex;align-items:center;justify-content:center;
  box-shadow:0 3px 10px rgba(26,58,42,.25);
}
.flow-content h4{font-size:.9rem;color:var(--forest);margin-bottom:2px;font-weight:600;}
.flow-content p{font-size:.8rem;color:var(--stone);}

/* ── PDF UNLOCK ── */
.pdf-hero{
  background:linear-gradient(135deg,var(--forest3) 0%,var(--forest) 100%);
  border-radius:16px;padding:32px 20px;text-align:center;
  position:relative;overflow:hidden;margin-bottom:16px;
}
.pdf-hero::before{
  content:'';position:absolute;inset:0;
  background:url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23ffffff' fill-opacity='0.03'%3E%3Ccircle cx='40' cy='40' r='30'/%3E%3Ccircle cx='40' cy='40' r='20'/%3E%3C/g%3E%3C/svg%3E") center/cover;
}
.pdf-lock-ico{font-size:3rem;margin-bottom:12px;position:relative;}
.pdf-hero h2{
  font-family:'Playfair Display',serif;font-size:1.4rem;
  color:var(--white);margin-bottom:8px;position:relative;
}
.pdf-price{
  font-family:'Playfair Display',serif;font-size:2rem;
  font-weight:900;color:var(--gold2);margin:10px 0;
  position:relative;
}
.pdf-hero p{color:rgba(255,255,255,.65);font-size:.82rem;margin-bottom:18px;position:relative;}
.pay-btn{
  display:inline-flex;align-items:center;gap:8px;
  padding:14px 28px;border:none;border-radius:12px;cursor:pointer;
  background:linear-gradient(135deg,var(--gold-dk),var(--gold),var(--gold2));
  color:var(--white);font-family:'DM Sans',sans-serif;
  font-weight:700;font-size:.95rem;letter-spacing:.3px;
  box-shadow:0 6px 24px rgba(201,150,58,.45);
  transition:.2s var(--ease);position:relative;
}
.pay-btn:hover{transform:translateY(-2px);box-shadow:0 10px 32px rgba(201,150,58,.55);}
.pay-btn:active{transform:scale(.98);}

.pdf-open-hero{
  background:linear-gradient(135deg,#f0fdf4,#dcfce7);
  border:2px solid #86efac;border-radius:16px;
  padding:28px 20px;text-align:center;margin-bottom:16px;
}

/* ── REFERRAL ── */
.ref-code-card{
  background:linear-gradient(135deg,var(--forest3),var(--forest));
  border-radius:14px;padding:18px 20px;margin-bottom:12px;
  display:flex;align-items:center;gap:14px;
}
.ref-code-display{
  font-family:'Playfair Display',serif;font-size:1.5rem;
  font-weight:900;color:var(--gold2);letter-spacing:4px;flex:1;
}
.ref-link-card{
  background:var(--warm);border:1.5px dashed var(--parch);
  border-radius:12px;padding:13px 15px;cursor:pointer;
  transition:.2s;margin-bottom:12px;
}
.ref-link-card:hover{background:var(--mint);border-color:var(--sage);}
.ref-link-label{
  font-size:.68rem;font-weight:700;color:var(--stone);
  letter-spacing:1px;text-transform:uppercase;margin-bottom:5px;
}
.ref-link-url{
  font-family:'DM Sans',monospace;font-size:.75rem;
  color:var(--forest);word-break:break-all;line-height:1.5;
}
.copy-flash{
  font-size:.76rem;font-weight:600;color:var(--success);
  display:none;margin-top:4px;
}
.share-row{display:flex;gap:8px;flex-wrap:wrap;}
.share-btn{
  flex:1;min-width:90px;padding:10px 12px;border:none;
  border-radius:10px;cursor:pointer;font-family:'DM Sans',sans-serif;
  font-size:.78rem;font-weight:600;transition:.2s;
  display:flex;align-items:center;justify-content:center;gap:5px;
}
.wa-btn{background:#25d366;color:#fff;}
.wa-btn:hover{background:#1ebe5b;}
.tg-btn{background:#0088cc;color:#fff;}
.tg-btn:hover{background:#0077b5;}
.cp-btn{background:var(--forest);color:#fff;}
.cp-btn:hover{background:var(--sage);}

/* ── RECRUIT TABLE ── */
.recruit-row{
  display:flex;align-items:center;gap:12px;
  padding:11px 0;border-bottom:1px solid var(--border);
}
.recruit-row:last-child{border-bottom:none;}
.recruit-avatar{
  width:36px;height:36px;border-radius:50%;
  background:linear-gradient(135deg,var(--forest),var(--sage));
  display:flex;align-items:center;justify-content:center;
  color:var(--white);font-weight:700;font-size:.88rem;flex-shrink:0;
}
.recruit-name{flex:1;font-weight:600;font-size:.88rem;}
.recruit-sub{font-size:.72rem;color:var(--stone);}
.badge{
  display:inline-block;padding:3px 8px;border-radius:8px;
  font-size:.68rem;font-weight:700;letter-spacing:.3px;
}
.badge-s{background:var(--success-l);color:var(--success);}
.badge-w{background:var(--warn-l);color:var(--warn);}
.badge-n{background:var(--warm);color:var(--stone);}

/* ── EARNINGS BREAKDOWN ── */
.earn-row{
  display:flex;align-items:center;gap:10px;
  padding:9px 12px;border-radius:10px;margin-bottom:6px;
}
.er-level{
  width:32px;height:32px;border-radius:8px;flex-shrink:0;
  display:flex;align-items:center;justify-content:center;
  font-weight:800;font-size:.78rem;
}
.er-name{flex:1;font-size:.84rem;font-weight:500;}
.er-rate{font-size:.78rem;color:var(--stone);}
.er-total{font-weight:700;font-size:.9rem;}
.er-l1{background:#f0fdf4;}.er-l1 .er-level{background:#86efac;color:#166534;}
.er-l2{background:#eff6ff;}.er-l2 .er-level{background:#93c5fd;color:#1e3a8a;}
.er-l3{background:#fff7ed;}.er-l3 .er-level{background:#fdba74;color:#9a3412;}
.er-l4{background:#fdf4ff;}.er-l4 .er-level{background:#d8b4fe;color:#6b21a8;}
.er-l5{background:#f0fdf4;}.er-l5 .er-level{background:#6ee7b7;color:#065f46;}
.er-tot{background:var(--warn-l);}.er-tot .er-level{background:var(--gold);color:#fff;}

/* ── WALLET ── */
.wallet-hero{
  background:linear-gradient(135deg,var(--forest3),var(--forest));
  border-radius:16px;padding:24px 20px;margin-bottom:16px;
  text-align:center;
}
.wallet-balance-label{
  color:rgba(255,255,255,.55);font-size:.75rem;
  letter-spacing:1.5px;text-transform:uppercase;margin-bottom:8px;
}
.wallet-balance{
  font-family:'Playfair Display',serif;font-size:2.4rem;
  font-weight:900;color:var(--gold2);
}
.wallet-sub{color:rgba(255,255,255,.4);font-size:.76rem;margin-top:4px;}

.form-group{margin-bottom:14px;}
.form-label{
  display:block;font-size:.76rem;font-weight:600;
  color:var(--charcoal);margin-bottom:6px;letter-spacing:.3px;
}
.form-input{
  width:100%;padding:11px 14px;
  border:1.5px solid var(--border);border-radius:10px;
  font-family:'DM Sans',sans-serif;font-size:.9rem;
  color:var(--ink);background:var(--cream);outline:none;
  transition:.2s var(--ease);
}
.form-input:focus{border-color:var(--sage);background:var(--white);}

/* ── TX LIST ── */
.tx-row{
  display:flex;align-items:center;gap:12px;
  padding:11px 0;border-bottom:1px solid var(--border);
}
.tx-row:last-child{border-bottom:none;}
.tx-ico{
  width:36px;height:36px;border-radius:10px;flex-shrink:0;
  display:flex;align-items:center;justify-content:center;font-size:1rem;
}
.tx-ico.credit{background:var(--success-l);}
.tx-ico.debit{background:var(--danger-l);}
.tx-info{flex:1;}
.tx-title{font-size:.85rem;font-weight:600;}
.tx-sub{font-size:.72rem;color:var(--stone);}
.tx-amount{font-weight:700;font-size:.92rem;}
.tx-amount.credit{color:var(--success);}
.tx-amount.debit{color:var(--danger);}

/* ── UPI MODAL ── */
.modal-backdrop{
  display:none;position:fixed;inset:0;
  background:rgba(15,36,25,.85);backdrop-filter:blur(6px);
  z-index:200;align-items:flex-end;justify-content:center;
  padding:0 0 env(safe-area-inset-bottom);
}
.modal-backdrop.open{display:flex;}
.modal-sheet{
  background:var(--white);border-radius:24px 24px 0 0;
  width:100%;max-width:500px;
  max-height:90vh;overflow-y:auto;
  animation:sheetUp .35s var(--ease) both;
}
@keyframes sheetUp{from{transform:translateY(100%);}to{transform:translateY(0);}}
.modal-drag{
  width:40px;height:4px;background:var(--parch);
  border-radius:2px;margin:12px auto 0;
}
.modal-head{
  padding:16px 20px 14px;border-bottom:1px solid var(--border);
}
.modal-head h3{
  font-family:'Playfair Display',serif;font-size:1.05rem;
  font-weight:700;color:var(--forest);margin-bottom:2px;
}
.modal-head p{font-size:.78rem;color:var(--stone);}
.modal-body{padding:18px 20px 24px;}

.upi-dest-card{
  background:var(--mint);border:1.5px solid var(--mint2);
  border-radius:14px;padding:16px;text-align:center;margin-bottom:16px;
}
.upi-id{
  font-family:'DM Sans',monospace;font-size:.92rem;
  font-weight:700;color:var(--forest);margin-bottom:4px;
}
.upi-amount{
  font-family:'Playfair Display',serif;font-size:1.8rem;
  font-weight:900;color:var(--gold-dk);
}
.upi-note{font-size:.72rem;color:var(--stone);margin-top:4px;}

.upi-apps-grid{
  display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:16px;
}
.upi-app-btn{
  background:var(--white);border:1.5px solid var(--border);
  border-radius:12px;padding:10px 6px;text-align:center;
  text-decoration:none;display:block;transition:.2s;cursor:pointer;
}
.upi-app-btn:hover{border-color:var(--sage);background:var(--mint);}
.upi-app-btn.any{
  background:var(--forest);border-color:var(--forest);
}
.upi-app-ico{font-size:1.3rem;margin-bottom:3px;}
.upi-app-name{font-size:.65rem;font-weight:600;color:var(--charcoal);}
.upi-app-btn.any .upi-app-name{color:var(--gold2);}

.txn-section{
  background:var(--warm);border-radius:12px;
  padding:14px;margin-bottom:14px;
  border:1px solid var(--parch);
}
.txn-section p{
  font-size:.78rem;font-weight:600;color:var(--warn);margin-bottom:8px;
}
.txn-input{
  width:100%;padding:11px 13px;border:1.5px solid var(--parch);
  border-radius:9px;font-family:'DM Sans',monospace;font-size:.88rem;
  color:var(--ink);background:var(--white);outline:none;
  transition:.2s var(--ease);
}
.txn-input:focus{border-color:var(--sage);}
.txn-hint{font-size:.68rem;color:var(--stone);margin-top:5px;}

/* ── SUCCESS MODAL ── */
.success-backdrop{
  display:none;position:fixed;inset:0;background:rgba(0,0,0,.7);
  backdrop-filter:blur(8px);z-index:300;
  align-items:center;justify-content:center;padding:20px;
}
.success-backdrop.open{display:flex;}
.success-card{
  background:var(--white);border-radius:24px;
  max-width:360px;width:100%;padding:32px 24px;
  text-align:center;box-shadow:var(--shadow-xl);
  animation:successPop .4s var(--ease) both;
}
@keyframes successPop{
  from{opacity:0;transform:scale(.85);}
  to{opacity:1;transform:scale(1);}
}
.success-ring{
  width:72px;height:72px;border-radius:50%;margin:0 auto 18px;
  background:linear-gradient(135deg,var(--success-l),#bbf7d0);
  display:flex;align-items:center;justify-content:center;
  font-size:2rem;
  box-shadow:0 0 0 8px rgba(45,106,79,.08),0 0 0 16px rgba(45,106,79,.04);
  animation:successRing 1s var(--ease) .3s both;
}
@keyframes successRing{
  from{transform:scale(.8);}to{transform:scale(1);}
}
.success-title{
  font-family:'Playfair Display',serif;font-size:1.3rem;
  font-weight:700;color:var(--success);margin-bottom:8px;
}
.success-msg{color:var(--stone);font-size:.86rem;line-height:1.7;margin-bottom:16px;}
.txn-display{
  background:var(--mint);border-radius:10px;
  padding:10px 14px;margin-bottom:18px;
}
.txn-display .td-label{font-size:.68rem;color:var(--stone);font-weight:600;letter-spacing:.5px;}
.txn-display .td-value{
  font-family:'DM Sans',monospace;font-size:.82rem;
  color:var(--forest);font-weight:700;word-break:break-all;margin-top:2px;
}

/* ── ADMIN ── */
.admin-table-wrap{overflow-x:auto;border-radius:12px;border:1px solid var(--border);}
.admin-table{width:100%;border-collapse:collapse;font-size:.8rem;}
.admin-table th{
  background:var(--forest);color:var(--white);
  padding:10px 12px;text-align:left;font-weight:600;
  font-size:.72rem;letter-spacing:.5px;text-transform:uppercase;
}
.admin-table td{padding:9px 12px;border-bottom:1px solid var(--border);}
.admin-table tr:nth-child(even) td{background:var(--cream);}
.admin-table tr:hover td{background:var(--mint);}

/* ── PLAN PAGE ── */
.income-row{
  display:grid;grid-template-columns:56px 1fr 72px 90px;
  gap:6px;padding:8px 10px;border-radius:10px;
  margin-bottom:5px;align-items:center;font-size:.8rem;
}
.ir-head{background:var(--forest);color:var(--white);font-weight:700;}
.ir1{background:#f0fdf4;}.ir2{background:#eff6ff;}
.ir3{background:#fff7ed;}.ir4{background:#fdf4ff;}
.ir5{background:#ecfdf5;}
.ir-tot{
  background:var(--warn-l);font-weight:800;
  border:1.5px solid #fbbf24;
}

/* ── TOAST ── */
#toast{
  position:fixed;top:70px;left:50%;
  transform:translateX(-50%) translateY(-20px);
  background:var(--forest);color:var(--white);
  padding:9px 20px;border-radius:20px;
  font-family:'DM Sans',sans-serif;font-size:.8rem;font-weight:600;
  letter-spacing:.3px;z-index:500;opacity:0;
  transition:opacity .3s,transform .3s;pointer-events:none;
  white-space:nowrap;box-shadow:var(--shadow-lg);
}
#toast.show{opacity:1;transform:translateX(-50%) translateY(0);}

/* ── SECURITY INDICATOR ── */
.sec-badge{
  display:inline-flex;align-items:center;gap:5px;
  background:var(--success-l);border:1px solid #86efac;
  padding:4px 10px;border-radius:20px;
  font-size:.68rem;font-weight:600;color:var(--success);
  letter-spacing:.3px;
}

/* ── MOBILE TWEAKS ── */
@media(max-width:380px){
  .comm-grid{grid-template-columns:repeat(3,1fr);}
  .upi-apps-grid{grid-template-columns:repeat(4,1fr);}
}

/* ── CUSTOM CURSOR ── */
@media(pointer:fine){
  *{cursor:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='18' height='18' viewBox='0 0 18 18'%3E%3Ccircle cx='9' cy='9' r='4' fill='%231a3a2a' fill-opacity='0.5'/%3E%3C/svg%3E") 9 9, auto;}
  button,a,[onclick]{cursor:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='18' height='18' viewBox='0 0 18 18'%3E%3Ccircle cx='9' cy='9' r='6' fill='%231a3a2a'/%3E%3C/svg%3E") 9 9, pointer;}
}

/* Bottom Navigation */
.bnav{display:flex;}
.bnav-item{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:3px;padding:8px 4px;background:none;border:none;cursor:pointer;font-family:inherit;transition:.2s;}
.bnav-item.on{color:var(--forest);}
.bnav-item:not(.on){color:var(--stone);}
.bnav-ico{font-size:1.2rem;line-height:1;}
.bnav-lbl{font-size:.58rem;font-weight:700;letter-spacing:.3px;text-transform:uppercase;}
.bnav-item.on .bnav-ico{transform:translateY(-2px);}
@media(min-width:769px){#bnavEl{display:none!important;}}
</style>
</head>
<body>
<script>
// Register inline service worker for offline caching (Firebase/Cloudflare hosting)
if('serviceWorker' in navigator){
  const SW_CODE=`
    self.addEventListener('install',e=>self.skipWaiting());
    self.addEventListener('activate',e=>e.waitUntil(self.clients.claim()));
    self.addEventListener('fetch',e=>{
      if(e.request.method!=='GET')return;
      e.respondWith(
        caches.open('hcbook-v1').then(cache=>
          cache.match(e.request).then(cached=>{
            const fresh=fetch(e.request).then(r=>{
              if(r.ok&&e.request.url.includes('firebasejs'))cache.put(e.request,r.clone());
              return r;
            }).catch(()=>cached);
            return cached||fresh;
          })
        )
      );
    });
  `;
  const blob=new Blob([SW_CODE],{type:'application/javascript'});
  navigator.serviceWorker.register(URL.createObjectURL(blob)).catch(()=>{});
}
</script>

<div id="toast"></div>

<!-- ════════════════ SVG LOGO DEFINITION ════════════════ -->
<svg style="display:none;">
  <defs>
    <symbol id="hc-logo" viewBox="0 0 48 48">
      <!-- Custom HealthConscious logo: stylized leaf with book pages -->
      <circle cx="24" cy="24" r="22" fill="#1a3a2a"/>
      <path d="M24 8 C14 12 10 20 12 30 C16 38 24 40 24 40 C24 40 32 38 36 30 C38 20 34 12 24 8Z"
        fill="#3d6b4f" opacity=".8"/>
      <path d="M24 10 C16 15 13 22 14 30 C17 37 24 39 24 39"
        fill="#5a9970" opacity=".9"/>
      <!-- Book spine line -->
      <line x1="24" y1="14" x2="24" y2="36" stroke="#c9963a" stroke-width="1.5" stroke-linecap="round"/>
      <!-- Book pages -->
      <path d="M24 18 C21 17 18 18 17 20 C16 23 17 27 18 29 C20 31 22 32 24 32"
        fill="none" stroke="#e8b86d" stroke-width="1.2" stroke-linecap="round"/>
      <path d="M24 18 C27 17 30 18 31 20 C32 23 31 27 30 29 C28 31 26 32 24 32"
        fill="none" stroke="#f5d49a" stroke-width="1.2" stroke-linecap="round"/>
    </symbol>
    <symbol id="hc-logo-sm" viewBox="0 0 32 32">
      <circle cx="16" cy="16" r="15" fill="#1a3a2a"/>
      <path d="M16 5 C10 8 7 14 8 21 C11 27 16 28 16 28 C16 28 21 27 24 21 C25 14 22 8 16 5Z" fill="#3d6b4f"/>
      <path d="M16 7 C11 10 9 15 10 21 C12 26 16 27 16 27" fill="#5a9970" opacity=".7"/>
      <line x1="16" y1="10" x2="16" y2="24" stroke="#c9963a" stroke-width="1.2" stroke-linecap="round"/>
      <path d="M16 13 C14 12 12 13 11 15 C11 17 12 19 13 21 C14 22 15 22 16 22" fill="none" stroke="#e8b86d" stroke-width="1" stroke-linecap="round"/>
      <path d="M16 13 C18 12 20 13 21 15 C21 17 20 19 19 21 C18 22 17 22 16 22" fill="none" stroke="#f5d49a" stroke-width="1" stroke-linecap="round"/>
    </symbol>
  </defs>
</svg>

<!-- ════════════════ SPLASH SCREEN ════════════════ -->
<div class="screen active" id="splash">
  <div class="splash-logo">
    <svg class="splash-leaf" viewBox="0 0 48 48">
      <use href="#hc-logo"/>
    </svg>
    <div class="splash-name">Health<em>Conscious</em></div>
    <div class="splash-tag">Complete Guide to Healthy Eating</div>
    <div class="splash-bar"><div class="splash-bar-fill"></div></div>
  </div>
</div>

<!-- ════════════════ AUTH SCREEN ════════════════ -->
<div class="screen" id="authScreen">
  <div class="auth-hero">
    <div class="auth-brand">
      <svg class="auth-brand-logo" viewBox="0 0 48 48"><use href="#hc-logo"/></svg>
      <div class="auth-brand-name">Health<em>Conscious</em></div>
    </div>
    <div class="auth-tagline">Science-based nutrition for every stage of life</div>
    <div class="auth-pills">
      <span class="auth-pill">📚 15 Chapters</span>
      <span class="auth-pill">🌍 3 Languages</span>
      <span class="auth-pill">💰 Earn ₹300/Referral</span>
      <span class="auth-pill">⚡ Instant PDF</span>
    </div>
  </div>
  <div class="auth-form-wrap">
    <div class="auth-card">
      <div class="auth-tabs">
        <button class="auth-tab on" id="regTab" onclick="switchAuth('reg')">Register</button>
        <button class="auth-tab" id="logTab" onclick="switchAuth('log')">Login</button>
      </div>
      <div id="authErr" class="auth-err"></div>
      <div id="regForm">
        <div class="inp-group">
          <label class="inp-label">Full Name</label>
          <input class="inp-field" id="rName" placeholder="Your full name" autocomplete="name"/>
        </div>
        <div class="inp-group">
          <label class="inp-label">Email Address</label>
          <input class="inp-field" id="rEmail" type="email" placeholder="your@email.com" autocomplete="email"/>
        </div>
        <div class="inp-group">
          <label class="inp-label">Password</label>
          <input class="inp-field" id="rPass" type="password" placeholder="Min 6 characters"/>
        </div>
        <div class="inp-group">
          <label class="inp-label">Referral Code <span style="color:var(--stone);font-weight:400;">(optional)</span></label>
          <input class="inp-field" id="rRef" placeholder="Enter if someone referred you"/>
          <div class="inp-hint">Leave empty if no one referred you</div>
        </div>
        <button class="cta-btn" id="regSubmitBtn" onclick="doRegister()">Create Account</button>
      </div>
      <div id="logForm" style="display:none;">
        <div class="inp-group">
          <label class="inp-label">Email Address</label>
          <input class="inp-field" id="lEmail" type="email" placeholder="your@email.com" autocomplete="email"/>
        </div>
        <div class="inp-group">
          <label class="inp-label">Password</label>
          <input class="inp-field" id="lPass" type="password" placeholder="Your password" autocomplete="current-password"/>
        </div>
        <button class="cta-btn" id="logSubmitBtn" onclick="doLogin()">Login</button>
      </div>
      <div style="text-align:center;margin-top:14px;">
        <span class="sec-badge">🔒 Secured by Firebase · SSL Encrypted</span>
      </div>
    </div>
  </div>
</div>

<!-- ════════════════ MAIN APP ════════════════ -->
<div class="screen" id="appScreen">

  <!-- Header -->
  <div class="app-header">
    <div class="header-brand">
      <svg class="header-logo" viewBox="0 0 32 32"><use href="#hc-logo-sm"/></svg>
      <div class="header-name">Health<em>Conscious</em></div>
    </div>
    <div class="header-right">
      <div class="wallet-chip">
        <span>₹</span><span id="headerWallet">0</span>
      </div>
      <div class="logout-btn" onclick="doLogout()" title="Logout">⏻</div>
    </div>
  </div>

  <!-- Pages -->
  <div class="pages" id="pages">

    <!-- ═══ HOME ═══ -->
    <div class="pg active" id="pg-home">
      <div class="wrap">
        <div class="stat-grid" id="homeStats">
          <div class="stat-card">
            <div class="stat-v" id="hWallet">₹0</div>
            <div class="stat-l">Wallet</div>
          </div>
          <div class="stat-card gold">
            <div class="stat-v" id="hEarned">₹0</div>
            <div class="stat-l">Earned</div>
          </div>
          <div class="stat-card">
            <div class="stat-v" id="hRefs">0</div>
            <div class="stat-l">Recruits</div>
          </div>
          <div class="stat-card warm">
            <div class="stat-v" id="hPDF">🔒</div>
            <div class="stat-l">PDF</div>
          </div>
        </div>

        <div class="card" id="welcomeCard">
          <div class="card-title">
            <span class="ct-ico">👋</span>
            Welcome, <span id="hName" style="color:var(--gold-dk);"></span>
          </div>
          <p style="color:var(--stone);font-size:.86rem;margin-bottom:16px;">
            Earn ₹300 for every person you refer. Their network earns you ₹200→₹25 across 5 levels — automatically, forever.
          </p>
          <div style="display:flex;gap:8px;flex-wrap:wrap;">
            <button class="btn btn-gold" onclick="navTo('book')">📚 Get PDF ₹1,999</button>
            <button class="btn btn-primary" onclick="navTo('earn')">💰 My Referral Link</button>
          </div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">💰</span>How You Earn</div>
          <div class="flow-steps">
            <div class="flow-step">
              <div class="flow-num">1</div>
              <div class="flow-content">
                <h4>You recruit A, B, C, D, E</h4>
                <p>You earn <b style="color:var(--forest);">₹300 direct bonus</b> for each person</p>
              </div>
            </div>
            <div class="flow-step">
              <div class="flow-num">2</div>
              <div class="flow-content">
                <h4>A recruits F, G, H, I, J</h4>
                <p>A earns ₹300 each. <b style="color:var(--forest);">You earn ₹200 each (L2)</b></p>
              </div>
            </div>
            <div class="flow-step">
              <div class="flow-num">3</div>
              <div class="flow-content">
                <h4>F recruits K, L, M, N, O</h4>
                <p>F ₹300 · A ₹200 · <b style="color:var(--forest);">You earn ₹100 each (L3)</b></p>
              </div>
            </div>
            <div class="flow-step">
              <div class="flow-num">4</div>
              <div class="flow-content">
                <h4>Network grows to L4 &amp; L5</h4>
                <p>You earn <b style="color:var(--forest);">₹50 (L4) and ₹25 (L5)</b> automatically</p>
              </div>
            </div>
            <div class="flow-step">
              <div class="flow-num">∞</div>
              <div class="flow-content">
                <h4>Recruit new people anytime</h4>
                <p><b style="color:var(--gold-dk);">₹300 direct bonus every time — no cap, no limit, forever</b></p>
              </div>
            </div>
          </div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">📊</span>Commission Rates</div>
          <div class="comm-grid">
            <div class="comm-box cb1">
              <div class="comm-l">L1</div>
              <div class="comm-v">₹300</div>
              <div class="comm-d">Direct</div>
            </div>
            <div class="comm-box cb2">
              <div class="comm-l">L2</div>
              <div class="comm-v">₹200</div>
              <div class="comm-d">Via L1</div>
            </div>
            <div class="comm-box cb3">
              <div class="comm-l">L3</div>
              <div class="comm-v">₹100</div>
              <div class="comm-d">Via L2</div>
            </div>
            <div class="comm-box cb4">
              <div class="comm-l">L4</div>
              <div class="comm-v">₹50</div>
              <div class="comm-d">Via L3</div>
            </div>
            <div class="comm-box cb5">
              <div class="comm-l">L5</div>
              <div class="comm-v">₹25</div>
              <div class="comm-d">Via L4</div>
            </div>
          </div>
          <div class="alert alert-s" style="margin-top:10px;font-size:.78rem;">
            <span class="ai">✅</span>
            <span>No cap · No expiry · No blocking · Earn forever · Min withdrawal ₹500</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ BOOK ═══ -->
    <div class="pg" id="pg-book">
      <div class="wrap">
        <div id="bookLocked">
          <div class="pdf-hero">
            <div class="pdf-lock-ico">📗</div>
            <h2>Health Conscious Book</h2>
            <p>Complete Guide to Healthy Eating from Birth to Old Age<br/>15 Chapters · English · Telugu · Hindi</p>
            <div class="pdf-price">₹1,999</div>
            <p style="font-size:.75rem;opacity:.5;margin-bottom:20px;">One-time payment · Instant PDF · Lifetime access</p>
            <button class="pay-btn" onclick="doBuy()">💳 Pay ₹1,999 &amp; Unlock PDF</button>
          </div>
          <div class="card">
            <div class="card-title"><span class="ct-ico">📚</span>What You Get</div>
            <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:10px;">
              <div style="background:var(--mint);border-radius:12px;padding:14px;text-align:center;">
                <div style="font-size:1.6rem;margin-bottom:6px;">📚</div>
                <div style="font-weight:700;color:var(--forest);font-size:.85rem;">15 Chapters</div>
                <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">Birth to 100+ years</div>
              </div>
              <div style="background:var(--warm);border-radius:12px;padding:14px;text-align:center;">
                <div style="font-size:1.6rem;margin-bottom:6px;">🌍</div>
                <div style="font-weight:700;color:var(--forest);font-size:.85rem;">3 Languages</div>
                <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">English · Telugu · Hindi</div>
              </div>
              <div style="background:#fef9ee;border-radius:12px;padding:14px;text-align:center;">
                <div style="font-size:1.6rem;margin-bottom:6px;">💰</div>
                <div style="font-weight:700;color:var(--gold-dk);font-size:.85rem;">Earn ₹300</div>
                <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">Per direct referral</div>
              </div>
              <div style="background:var(--info-l);border-radius:12px;padding:14px;text-align:center;">
                <div style="font-size:1.6rem;margin-bottom:6px;">⚡</div>
                <div style="font-weight:700;color:var(--info);font-size:.85rem;">Instant PDF</div>
                <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">Download immediately</div>
              </div>
            </div>
          </div>
        </div>
        <div id="bookOpen" style="display:none;">
          <div class="pdf-open-hero">
            <div style="font-size:2.5rem;margin-bottom:12px;">✅</div>
            <h2 style="font-family:'Playfair Display',serif;color:var(--success);font-size:1.3rem;margin-bottom:8px;">PDF Unlocked!</h2>
            <p style="color:var(--stone);margin-bottom:20px;font-size:.86rem;">
              Your Health Conscious Book is ready to download.</p>
            <button class="btn btn-primary btn-full" style="justify-content:center;font-size:.95rem;padding:14px;" onclick="doDownload()">
              ⬇ Download Health Conscious Book PDF
            </button>
            <p style="font-size:.72rem;color:var(--stone);margin-top:10px;">
              15 Chapters · English, Telugu &amp; Hindi · Lifetime access</p>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ EARN ═══ -->
    <div class="pg" id="pg-earn">
      <div class="wrap">
        <div id="earnLocked" style="display:none;">
          <div class="alert alert-w">
            <span class="ai">🔒</span>
            <span><b>Purchase the book (₹1,999)</b> first to activate your referral link and start earning.</span>
          </div>
          <button class="btn btn-gold btn-full" onclick="navTo('book')" style="justify-content:center;">
            💳 Buy Book to Activate
          </button>
        </div>
        <div id="earnActive" style="display:none;">
          <div class="card">
            <div class="card-title">
              <span class="ct-ico">🔗</span>Your Referral Link
              <span id="earnStatus" class="badge badge-s" style="margin-left:auto;">✅ Active</span>
            </div>
            <p style="color:var(--stone);font-size:.83rem;margin-bottom:14px;">
              Every person who buys through your link gives you <b style="color:var(--forest);">₹300 direct bonus</b>.
              Their recruits earn you ₹200 → ₹25 across 5 levels — no cap, forever.
            </p>
            <div class="ref-code-card">
              <div>
                <div style="font-size:.68rem;color:rgba(255,255,255,.5);letter-spacing:1px;text-transform:uppercase;margin-bottom:6px;">YOUR CODE</div>
                <div class="ref-code-display" id="myCode">------</div>
              </div>
              <button class="btn btn-gold btn-sm" onclick="copyCode()">📋 Copy</button>
            </div>
            <div class="ref-link-card" onclick="copyLink()">
              <div class="ref-link-label">Tap to Copy Your Referral Link</div>
              <div class="ref-link-url" id="refLinkDisplay">Loading your link...</div>
              <div class="copy-flash" id="copyFlash">✓ Link copied to clipboard!</div>
            </div>
            <div class="share-row">
              <button class="share-btn wa-btn" onclick="shareWA()">📱 WhatsApp</button>
              <button class="share-btn tg-btn" onclick="shareTG()">✈ Telegram</button>
              <button class="share-btn cp-btn" onclick="copyLink()">🔗 Copy</button>
            </div>
            <div style="margin-top:10px;font-size:.74rem;color:var(--stone);" id="earnMeta"></div>
          </div>

          <div class="card">
            <div class="card-title"><span class="ct-ico">👥</span>My Direct Recruits (L1)</div>
            <div id="recruitList"><p style="color:var(--stone);font-size:.82rem;">Loading...</p></div>
          </div>

          <div class="card">
            <div class="card-title"><span class="ct-ico">📊</span>Earnings by Level</div>
            <div id="earnBreakdown"><p style="color:var(--stone);font-size:.82rem;">Loading...</p></div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ WALLET ═══ -->
    <div class="pg" id="pg-wallet">
      <div class="wrap">
        <div class="wallet-hero">
          <div class="wallet-balance-label">Available Balance</div>
          <div class="wallet-balance" id="wBalance">₹0</div>
          <div class="wallet-sub">Total earned: <span id="wTotalEarned">₹0</span> · Withdrawn: <span id="wWithdrawn">₹0</span></div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">💸</span>Request Withdrawal</div>
          <div class="alert alert-i" style="margin-bottom:14px;">
            <span class="ai">ℹ️</span>
            <span>Min: <b>₹500</b> · Admin pays from <b>bonagirispinoj-1@oksbi</b> · Processed within 48 hours</span>
          </div>
          <div id="wdAlert"></div>
          <div class="form-group">
            <label class="form-label">Amount (₹)</label>
            <input type="number" class="form-input" id="wAmt" placeholder="Minimum ₹500" min="500"/>
          </div>
          <div class="form-group">
            <label class="form-label">Your UPI ID or Bank Account</label>
            <input class="form-input" id="wUPI" placeholder="yourname@upi or account number"/>
          </div>
          <button class="btn btn-primary btn-full" onclick="doWithdraw()" style="justify-content:center;">
            Submit Withdrawal Request
          </button>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">📋</span>Transaction History</div>
          <div id="txList"><p style="color:var(--stone);font-size:.82rem;">Loading...</p></div>
        </div>
      </div>
    </div>

    <!-- ═══ PLAN ═══ -->
    <div class="pg" id="pg-plan">
      <div class="wrap">
        <div class="card">
          <div class="card-title"><span class="ct-ico">📊</span>Commission Plan</div>
          <div class="comm-grid">
            <div class="comm-box cb1"><div class="comm-l">L1</div><div class="comm-v">₹300</div><div class="comm-d">Direct</div></div>
            <div class="comm-box cb2"><div class="comm-l">L2</div><div class="comm-v">₹200</div><div class="comm-d">Via L1</div></div>
            <div class="comm-box cb3"><div class="comm-l">L3</div><div class="comm-v">₹100</div><div class="comm-d">Via L2</div></div>
            <div class="comm-box cb4"><div class="comm-l">L4</div><div class="comm-v">₹50</div><div class="comm-d">Via L3</div></div>
            <div class="comm-box cb5"><div class="comm-l">L5</div><div class="comm-v">₹25</div><div class="comm-d">Via L4</div></div>
          </div>
          <div class="alert alert-s" style="margin-top:12px;">
            <span class="ai">✅</span>
            <span><b>No cap · No blocking · Earn forever · 5 levels deep only</b><br/>
            Total payout per sale: ₹675 · You keep: ₹1,324 per book sold</span>
          </div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">💰</span>Income Example (Each person refers 5)</div>
          <div class="income-row ir-head"><span>Level</span><span>People</span><span>Each</span><span>You Earn</span></div>
          <div class="income-row ir1"><span><b>L1</b></span><span>5</span><span>₹300</span><span><b>₹1,500</b></span></div>
          <div class="income-row ir2"><span><b>L2</b></span><span>25</span><span>₹200</span><span><b>₹5,000</b></span></div>
          <div class="income-row ir3"><span><b>L3</b></span><span>125</span><span>₹100</span><span><b>₹12,500</b></span></div>
          <div class="income-row ir4"><span><b>L4</b></span><span>625</span><span>₹50</span><span><b>₹31,250</b></span></div>
          <div class="income-row ir5"><span><b>L5</b></span><span>3,125</span><span>₹25</span><span><b>₹78,125</b></span></div>
          <div class="income-row ir-tot"><span>MAX</span><span>3,905</span><span>—</span><span>₹1,28,375</span></div>
          <p style="font-size:.7rem;color:var(--stone);margin-top:8px;">*Illustrative. Actual depends on your effort and network growth.</p>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">🔒</span>Security &amp; Anti-Fraud</div>
          <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:8px;">
            <div style="background:var(--success-l);border-radius:10px;padding:12px;">
              <div style="font-weight:700;color:var(--success);font-size:.82rem;">✅ Duplicate UTR Block</div>
              <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">Same UTR auto-rejected</div>
            </div>
            <div style="background:var(--info-l);border-radius:10px;padding:12px;">
              <div style="font-weight:700;color:var(--info);font-size:.82rem;">✅ Button Lock</div>
              <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">Double-tap prevented</div>
            </div>
            <div style="background:var(--warn-l);border-radius:10px;padding:12px;">
              <div style="font-weight:700;color:var(--warn);font-size:.82rem;">✅ Admin Verify</div>
              <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">Manual UTR check</div>
            </div>
            <div style="background:#f0fdf4;border-radius:10px;padding:12px;">
              <div style="font-weight:700;color:var(--success);font-size:.82rem;">✅ Firebase SSL</div>
              <div style="font-size:.72rem;color:var(--stone);margin-top:3px;">256-bit encryption</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ ADMIN ═══ -->
    <div class="pg" id="pg-admin">
      <div class="wrap">
        <!-- Firebase Hosting ONE-CLICK DEPLOY -->
        <div id="fbDeployPanel" style="background:linear-gradient(135deg,#1a3a2a,#0f2419);
          border:1px solid rgba(255,165,0,.35);border-radius:14px;padding:18px;margin-bottom:16px;">

          <!-- Header row -->
          <div style="display:flex;align-items:center;gap:10px;margin-bottom:12px;flex-wrap:wrap;">
            <div style="background:rgba(255,165,0,.15);border-radius:8px;padding:6px 10px;
              font-size:1.1rem;">🔥</div>
            <div style="flex:1;">
              <div style="color:#ffa500;font-size:.8rem;font-weight:800;letter-spacing:1px;">
                FIREBASE HOSTING — ONE CLICK DEPLOY
              </div>
              <div style="color:rgba(255,255,255,.5);font-size:.7rem;margin-top:2px;">
                Live URL after deploy: <b style="color:#86efac;">https://neurocoin-ntc.web.app</b>
              </div>
            </div>
          </div>

          <!-- Step guide -->
          <div style="background:rgba(0,0,0,.3);border-radius:10px;padding:12px 14px;
            margin-bottom:14px;font-size:.74rem;color:rgba(255,255,255,.6);line-height:1.9;">
            <b style="color:#ffa500;">How it works:</b><br/>
            1️⃣ Click <b style="color:#fff;">"Get Token"</b> → Opens Firebase Console Cloud Shell<br/>
            2️⃣ Run the command shown → Copy the token<br/>
            3️⃣ Paste token below → Click <b style="color:#fff;">"🚀 Deploy Now"</b><br/>
            4️⃣ App goes live at <b style="color:#86efac;">neurocoin-ntc.web.app</b><br/>
            5️⃣ Firebase Console → Auth → Add <b style="color:#86efac;">neurocoin-ntc.web.app</b> ← <b style="color:#ffa500;">only manual step</b>
          </div>

          <!-- Token input row -->
          <div style="display:flex;gap:8px;margin-bottom:10px;flex-wrap:wrap;">
            <input id="fbTokenInp" placeholder="Paste your Firebase token here..."
              style="flex:1;min-width:200px;padding:10px 12px;border-radius:9px;
              border:1.5px solid rgba(255,165,0,.3);background:rgba(0,0,0,.4);
              color:#fff;font-family:monospace;font-size:.78rem;outline:none;"
              onfocus="this.style.borderColor='rgba(255,165,0,.7)'"
              onblur="this.style.borderColor='rgba(255,165,0,.3)'"/>
          </div>

          <!-- Buttons -->
          <div style="display:flex;gap:8px;flex-wrap:wrap;">
            <button onclick="openTokenGuide()" style="background:rgba(255,255,255,.08);
              border:1px solid rgba(255,255,255,.2);color:rgba(255,255,255,.8);
              padding:9px 16px;border-radius:9px;font-family:inherit;font-size:.76rem;
              font-weight:700;cursor:pointer;transition:.2s;"
              onmouseover="this.style.background='rgba(255,255,255,.15)'"
              onmouseout="this.style.background='rgba(255,255,255,.08)'">
              🔑 Get Token
            </button>
            <button onclick="deployToFirebase()" id="deployBtn"
              style="background:linear-gradient(135deg,#f97316,#d97706);border:none;
              color:#fff;padding:9px 20px;border-radius:9px;font-family:inherit;
              font-size:.76rem;font-weight:800;cursor:pointer;transition:.2s;
              box-shadow:0 3px 12px rgba(217,119,6,.4);">
              🚀 Deploy Now
            </button>
            <button onclick="downloadFirebaseFiles()" style="background:transparent;
              border:1px solid rgba(255,165,0,.3);color:rgba(255,165,0,.7);
              padding:9px 14px;border-radius:9px;font-family:inherit;font-size:.74rem;
              font-weight:600;cursor:pointer;transition:.2s;"
              onmouseover="this.style.borderColor='rgba(255,165,0,.7)'"
              onmouseout="this.style.borderColor='rgba(255,165,0,.3)'">
              📥 Files
            </button>
          </div>

          <!-- Deploy status -->
          <div id="deployStatus" style="margin-top:10px;min-height:18px;
            font-size:.76rem;color:rgba(255,255,255,.6);"></div>
        </div>
        <div class="stat-grid">
          <div class="stat-card"><div class="stat-v" id="aUsers">0</div><div class="stat-l">Users</div></div>
          <div class="stat-card gold"><div class="stat-v" id="aPaid">0</div><div class="stat-l">Paid</div></div>
          <div class="stat-card"><div class="stat-v" id="aRevenue">₹0</div><div class="stat-l">Revenue</div></div>
          <div class="stat-card warm"><div class="stat-v" id="aPending">0</div><div class="stat-l">Pending W/D</div></div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">🔒</span>Security &amp; System Status</div>
          <div class="alert alert-s">
            <span class="ai">✅</span>
            <span><b>PDF embedded.</b> No upload needed.
              <button class="btn btn-primary btn-sm" onclick="testPDF()" style="margin-left:8px;">⬇ Test PDF</button>
            </span>
          </div>
          <div class="alert alert-w">
            <span class="ai">⚠️</span>
            <span><b>Verify each UTR in your UPI app</b> before clicking Verify. Open Google Pay → History → match UTR number shown below. Fake UTR = fraud → click Reject immediately.</span>
          </div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">👥</span>All Users</div>
          <div class="admin-table-wrap">
            <table class="admin-table" id="admUsers">
              <thead><tr><th>Name</th><th>Email</th><th>Code</th><th>PDF</th><th>Earned</th><th>L1s</th></tr></thead>
              <tbody><tr><td colspan="6" style="text-align:center;color:var(--stone);padding:20px;">Loading...</td></tr></tbody>
            </table>
          </div>
        </div>

        <div class="card">
          <div class="card-title"><span class="ct-ico">💳</span>Payments — Verify Each UTR</div>
          <div class="admin-table-wrap">
            <table class="admin-table" id="admPay">
              <thead><tr><th>Name</th><th>Amount</th><th>UTR Number</th><th>Status</th><th>Date</th></tr></thead>
              <tbody><tr><td colspan="5" style="text-align:center;color:var(--stone);padding:20px;">Loading...</td></tr></tbody>
            </table>
          </div>
        </div>

        <div class="card">
          <div class="card-title">
            <span class="ct-ico">💸</span>Withdrawals
            <span style="font-size:.75rem;font-weight:400;color:var(--stone);margin-left:6px;">Pay from: bonagirispinoj-1@oksbi</span>
          </div>
          <div class="admin-table-wrap">
            <table class="admin-table" id="admWith">
              <thead><tr><th>Name</th><th>Amount</th><th>UPI</th><th>Status</th><th>Date</th><th>Action</th></tr></thead>
              <tbody><tr><td colspan="6" style="text-align:center;color:var(--stone);padding:20px;">Loading...</td></tr></tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

  </div><!-- /pages -->

  <!-- Bottom Navigation -->
  <div class="bottom-nav" id="bottomNav">
    <button class="nav-item active" id="nav-home" onclick="navTo('home')">
      <span class="nav-ico">🏠</span>
      <span class="nav-lbl">Home</span>
    </button>
    <button class="nav-item" id="nav-book" onclick="navTo('book')">
      <span class="nav-ico">📚</span>
      <span class="nav-lbl">Book</span>
    </button>
    <button class="nav-item" id="nav-earn" onclick="navTo('earn')">
      <span class="nav-ico">💰</span>
      <span class="nav-lbl">Earn</span>
    </button>
    <button class="nav-item" id="nav-wallet" onclick="navTo('wallet')">
      <span class="nav-ico">💳</span>
      <span class="nav-lbl">Wallet</span>
    </button>
    <button class="nav-item" id="nav-plan" onclick="navTo('plan')">
      <span class="nav-ico">📊</span>
      <span class="nav-lbl">Plan</span>
    </button>
    <button class="nav-item nav-admin" id="nav-admin" style="display:none;" onclick="navTo('admin')">
      <span class="nav-ico">⚙️</span>
      <span class="nav-lbl">Admin</span>
    </button>
  </div>

</div><!-- /appScreen -->

<!-- ════════ UPI PAYMENT SHEET ════════ -->
<div id="upiSheet" class="modal-backdrop">
  <div class="modal-sheet">
    <div class="modal-drag"></div>
    <div class="modal-head">
      <h3>Pay via UPI</h3>
      <p>Health Conscious Book — Lifetime PDF Access</p>
    </div>
    <div class="modal-body">
      <div class="upi-dest-card">
        <div style="font-size:.7rem;color:var(--stone);letter-spacing:.5px;text-transform:uppercase;margin-bottom:6px;">Pay to</div>
        <div class="upi-id">bonagirispinoj-1@oksbi</div>
        <div class="upi-amount">₹1,999</div>
        <div class="upi-note">Note: HCBook-<span id="upiNote">------</span></div>
      </div>

      <p style="font-size:.78rem;font-weight:600;color:var(--charcoal);margin-bottom:8px;">Open with your UPI app:</p>
      <div class="upi-apps-grid">
        <a id="gpayBtn" href="#" class="upi-app-btn">
          <div class="upi-app-ico">💚</div>
          <div class="upi-app-name">GPay</div>
        </a>
        <a id="phonepeBtn" href="#" class="upi-app-btn">
          <div class="upi-app-ico">💜</div>
          <div class="upi-app-name">PhonePe</div>
        </a>
        <a id="bhimBtn" href="#" class="upi-app-btn">
          <div class="upi-app-ico">🏦</div>
          <div class="upi-app-name">BHIM</div>
        </a>
        <a id="anyBtn" href="#" class="upi-app-btn any">
          <div class="upi-app-ico">📱</div>
          <div class="upi-app-name" style="color:var(--gold2);">Any UPI</div>
        </a>
      </div>

      <div class="txn-section">
        <p>✅ After paying — enter your Transaction ID / UTR:</p>
        <input id="txnInput" class="txn-input" placeholder="e.g. T2506XXXXXXX or 403210XXXXXXXX"/>
        <div class="txn-hint">Find in UPI app → Recent Transactions → UTR Number</div>
      </div>

      <button class="cta-btn" id="confirmBtn" onclick="confirmPayment()">
        Confirm Payment &amp; Unlock PDF
      </button>
      <button onclick="closeUPI()" style="width:100%;padding:11px;background:none;
        border:1px solid var(--border);border-radius:10px;cursor:pointer;
        font-family:'DM Sans',sans-serif;font-size:.84rem;color:var(--stone);margin-top:8px;">
        Cancel
      </button>
    </div>
  </div>
</div>

<!-- ════════ SUCCESS SCREEN ════════ -->
<div id="successModal" class="success-backdrop">
  <div class="success-card">
    <div class="success-ring">🎉</div>
    <div class="success-title">Payment Confirmed!</div>
    <div class="success-msg">
      Your PDF is <b style="color:var(--forest);">unlocked</b>!<br/>
      Your referral link is now <b style="color:var(--forest);">ACTIVE</b>!<br/>
      Start sharing and earn ₹300 per recruit.
    </div>
    <div class="txn-display">
      <div class="td-label">Transaction ID</div>
      <div class="td-value" id="successTxnId">—</div>
    </div>
    <button class="cta-btn" onclick="closeSuccess()">
      🔗 View My Referral Link →
    </button>
  </div>
</div>

<!-- ════════════════════════════════════════════════════════
     JAVASCRIPT — HEALTHCONSCIOUS V10
     Clean · Secure · Professional
════════════════════════════════════════════════════════ -->
<script>
// ═══ FIREBASE — inits first for fast login ════════════════
// ══ FIREBASE CONFIG ═══════════════════════════════════════════════
// Hosting: https://neurocoin-ntc.web.app (Firebase Hosting — free)
// Auth domains authorized: neurocoin-ntc.web.app + neurocoin-ntc.firebaseapp.com
// To add custom domain: Firebase Console → Authentication → Settings → Authorized domains
const FB_CFG = {
  apiKey:            "AIzaSyBIebPXVjzVBZl380ZCELg2LUSCLr-6QrE",
  authDomain:        "neurocoin-ntc.firebaseapp.com",
  databaseURL:       "https://neurocoin-ntc-default-rtdb.firebaseio.com",
  projectId:         "neurocoin-ntc",
  storageBucket:     "neurocoin-ntc.firebasestorage.app",
  messagingSenderId: "1040732555800",
  appId:             "1:1040732555800:web:55e63b5ff81781c6b1916d"
};
// ══ SECURITY & ANTI-CRASH ══════════════════════════════════
function san(s){
  if(s==null||s===undefined)return'';
  return String(s)
    .replace(/&/g,'&amp;').replace(/</g,'&lt;')
    .replace(/>/g,'&gt;').replace(/"/g,'&quot;')
    .replace(/'/g,'&#x27;');
}
function stripScripts(s){
  if(!s)return'';
  return s.replace(/<script[\s\S]*?<\/script>/gi,'')
    .replace(/javascript:/gi,'').replace(/on\w+\s*=/gi,'');
}
const _RL={};
function rateOK(key,max,winMs){
  const now=Date.now();if(!_RL[key])_RL[key]=[];
  _RL[key]=_RL[key].filter(t=>now-t<winMs);
  if(_RL[key].length>=max)return false;
  _RL[key].push(now);return true;
}
window.addEventListener('error',e=>{console.error('[HCBook]',e.message);return true;});
window.addEventListener('unhandledrejection',e=>{console.error('[HCBook]',e.reason);e.preventDefault();});

firebase.initializeApp(FB_CFG);
const auth = firebase.auth();
const db   = firebase.firestore();

// ═══ CONSTANTS ════════════════════════════════════════════
const ADMIN     = "bonagirispinoj@gmail.com";
const ADMIN_UPI = "bonagirispinoj-1@oksbi";
const PRICE     = 1999;
const MIN_WD    = 500;
const BONUS     = [300, 200, 100, 50, 25];

// ═══ STATE ════════════════════════════════════════════════
let CU = null, CD = null;
let _processing = false; // global flag — prevents double submissions

// ═══ HELPERS ═════════════════════════════════════════════
const $ = id => document.getElementById(id);
const fmtINR = n => '₹' + Number(n||0).toLocaleString('en-IN');
const genCode = () => Math.random().toString(36).substring(2,8).toUpperCase();

function toast(msg, dur=2500){
  const t=$('toast'); t.textContent=msg; t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'), dur);
}

function showAlert(msg, type, id){
  const el=$(id); if(!el) return;
  el.innerHTML=`<div class="alert alert-${type}"><span class="ai">${type==='s'?'✅':type==='e'?'❌':type==='w'?'⚠️':'ℹ️'}</span><span>${msg}</span></div>`;
  if(type!=='e') setTimeout(()=>{ if(el) el.innerHTML=''; }, 6000);
}

// ═══ SPLASH → AUTH ═══════════════════════════════════════
window.addEventListener('load', ()=>{
  setTimeout(()=>{
    $('splash').classList.remove('active');
    setTimeout(()=>{
      if(!CU) $('authScreen').classList.add('active');
    }, 350);
  }, 2400);
});

// ═══ SCREEN MANAGEMENT ═══════════════════════════════════
function showScreen(name){
  ['splash','authScreen','appScreen'].forEach(s=>{
    $(s).classList.remove('active');
  });
  setTimeout(()=>$(name).classList.add('active'), 50);
}

// ═══ AUTH ════════════════════════════════════════════════
function switchAuth(m){
  $('regForm').style.display = m==='reg'?'block':'none';
  $('logForm').style.display = m==='log'?'block':'none';
  $('regTab').classList.toggle('on', m==='reg');
  $('logTab').classList.toggle('on', m==='log');
  $('authErr').textContent='';
}

async function doRegister(){
  if(_processing) return;
  const name  = $('rName').value.trim();
  const email = $('rEmail').value.trim();
  const pass  = $('rPass').value;
  const refRaw = $('rRef').value.trim() || localStorage.getItem('pendingRef') || '';
  const ref   = refRaw.toUpperCase();

  if(!name||!email||!pass){$('authErr').textContent='Please fill all fields.';return;}
  if(pass.length<6){$('authErr').textContent='Password must be at least 6 characters.';return;}
  if(!email.includes('@')){$('authErr').textContent='Please enter a valid email address.';return;}

  _processing=true;
  $('regSubmitBtn').disabled=true;$('regSubmitBtn').classList.add('loading');
  $('authErr').textContent='';

  try{
    let uplineId=null;
    if(ref){
      const refUser = await getByCode(ref);
      if(!refUser){
        $('authErr').textContent='Invalid referral code. Please check and try again.';
        return;
      }
      if(!refUser.hasPaid){
        $('authErr').textContent='This referral code is not active yet — the person must purchase the book first.';
        return;
      }
      uplineId = refUser.id;
    }

    const cred = await auth.createUserWithEmailAndPassword(email, pass);
    const code = genCode();

    await db.collection('users').doc(cred.user.uid).set({
      name, email,
      referralCode:   code,
      referredBy:     ref||null,
      uplineId:       uplineId,
      wallet:         0,
      totalEarned:    0,
      totalWithdrawn: 0,
      hasPaid:        false,
      activeLink:     false,
      directRecruits: [],
      joinedAt:       firebase.firestore.FieldValue.serverTimestamp()
    });

    localStorage.removeItem('pendingRef');
    $('authErr').className='auth-err auth-ok';
    $('authErr').textContent='✅ Account created! Please login now.';
    setTimeout(()=>switchAuth('log'), 1800);

  } catch(e){
    let msg=e.message;
    if(e.code==='auth/email-already-in-use') msg='This email is already registered. Please login.';
    if(e.code==='auth/invalid-email')        msg='Please enter a valid email address.';
    $('authErr').textContent=msg;
  } finally{
    _processing=false;
    $('regSubmitBtn').disabled=false;
    $('regSubmitBtn').classList.remove('loading');
  }
}

async function doLogin(){
  if(_processing) return;
  const email=$('lEmail').value.trim(), pass=$('lPass').value;
  if(!email||!pass){$('authErr').textContent='Enter email and password.';return;}

  _processing=true;
  $('logSubmitBtn').disabled=true;$('logSubmitBtn').classList.add('loading');
  $('authErr').textContent='';

  try{
    await auth.signInWithEmailAndPassword(email, pass);
  } catch(e){
    let msg=e.message;
    if(e.code==='auth/user-not-found')    msg='No account found. Please register first.';
    if(e.code==='auth/wrong-password'||e.code==='auth/invalid-credential')
                                           msg='Wrong email or password. Please try again.';
    if(e.code==='auth/too-many-requests') msg='Too many failed attempts. Please wait a few minutes.';
    $('authErr').textContent=msg;
  } finally{
    _processing=false;
    $('logSubmitBtn').disabled=false;
    $('logSubmitBtn').classList.remove('loading');
  }
}

async function doLogout(){ await auth.signOut(); }

// ═══ AUTH STATE ═══════════════════════════════════════════
auth.onAuthStateChanged(async user=>{
  if(user){
    CU=user;
    CD=await getUser(user.uid);

    // Auto-create profile (for users from other apps like NeuroCoin)
    if(!CD){
      const code=genCode();
      await db.collection('users').doc(user.uid).set({
        name:  user.displayName||user.email.split('@')[0],
        email: user.email,
        referralCode:  code,
        referredBy:    null,
        uplineId:      null,
        wallet:        0, totalEarned:0, totalWithdrawn:0,
        hasPaid:false, activeLink:false, directRecruits:[],
        joinedAt:firebase.firestore.FieldValue.serverTimestamp()
      });
      CD=await getUser(user.uid);
    }
    if(!CD) return;

    // Auto-fix activeLink
    if(CD.hasPaid && !CD.activeLink){
      await db.collection('users').doc(CU.uid).update({activeLink:true});
      CD.activeLink=true;
    }

    // Auto-fill ref from URL
    const ref=new URLSearchParams(location.search).get('ref');
    if(ref){ localStorage.setItem('pendingRef',ref.toUpperCase()); }

    // Show app
    showScreen('appScreen');
    if(user.email===ADMIN) $('nav-admin').style.display='flex';
    refreshHome();
    navTo('home');

  } else {
    CU=null; CD=null;
    $('nav-admin').style.display='none';
    const bnavEl=document.getElementById('bnavEl');if(bnavEl)bnavEl.style.display='none';
    showScreen('authScreen');
  }
});

// ═══ DB ════════════════════════════════════════════════
async function getUser(uid){
  const d=await db.collection('users').doc(uid).get();
  return d.exists?{id:d.id,...d.data()}:null;
}
async function getByCode(code){
  const s=await db.collection('users').where('referralCode','==',code).limit(1).get();
  return s.empty?null:{id:s.docs[0].id,...s.docs[0].data()};
}

// ═══ MLM CHAIN ════════════════════════════════════════════
// Pay bonuses up 5 levels when someone buys
async function payChain(newUid, newName, uplineId){
  // Register new user under upline
  await db.collection('users').doc(uplineId).update({
    directRecruits: firebase.firestore.FieldValue.arrayUnion(newUid)
  });

  let currentId = uplineId;
  for(let i=0; i<BONUS.length; i++){
    if(!currentId) break;
    const u = await getUser(currentId);
    if(!u) break;

    // Pay this level
    await db.collection('users').doc(currentId).update({
      wallet:      firebase.firestore.FieldValue.increment(BONUS[i]),
      totalEarned: firebase.firestore.FieldValue.increment(BONUS[i]),
    });
    await db.collection('transactions').doc().set({
      uid:currentId, type:'bonus', level:i+1,
      fromUid:newUid, fromName:newName, amount:BONUS[i],
      ts:firebase.firestore.FieldValue.serverTimestamp()
    });

    currentId = u.uplineId||null;
  }
}

// ═══ NAVIGATION ═══════════════════════════════════════════
function navTo(name){
  document.querySelectorAll('.pg').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item,.bnav-item').forEach(n=>n.classList.remove('active'));
  $('pg-'+name)?.classList.add('active');
  $('nav-'+name)?.classList.add('active');
  $('bn-'+name)?.classList.add('active');
  $('pages').scrollTop=0;
  if(name==='earn')   loadEarn();
  if(name==='book')   loadBook();
  if(name==='wallet') loadWallet();
  if(name==='admin')  loadAdmin();
}

// ═══ HOME ═════════════════════════════════════════════════
function refreshHome(){
  if(!CD) return;
  $('hName').textContent    = CD.name;
  $('hWallet').textContent  = Number(CD.wallet||0).toLocaleString('en-IN');
  $('hEarned').textContent  = fmtINR(CD.totalEarned);
  $('hRefs').textContent    = (CD.directRecruits||[]).length;
  $('hPDF').textContent     = CD.hasPaid?'✅':'🔒';
  $('headerWallet').textContent = Number(CD.wallet||0).toLocaleString('en-IN');
}

// ═══ BOOK ═════════════════════════════════════════════════
function loadBook(){
  if(!CD) return;
  $('bookLocked').style.display = CD.hasPaid?'none':'block';
  $('bookOpen').style.display   = CD.hasPaid?'block':'none';
}

// ═══ UPI PAYMENT ══════════════════════════════════════════
function doBuy(){
  if(!CU||!CD){toast('Please login first.');return;}
  if(CD.hasPaid){toast('You already own the PDF!');return;}

  // Build UPI deep links
  const note = CU.uid.substring(0,8).toUpperCase();
  const upi  = ADMIN_UPI;
  const link = `upi://pay?pa=${upi}&pn=HealthConscious&am=1999&cu=INR&tn=HCBook-${note}`;

  $('upiNote').textContent = note;
  $('gpayBtn').href    = `gpay://upi/pay?pa=${upi}&pn=HealthConscious&am=1999&cu=INR`;
  $('phonepeBtn').href = `phonepe://pay?pa=${upi}&pn=HealthConscious&am=1999&cu=INR`;
  $('bhimBtn').href    = link;
  $('anyBtn').href     = link;
  $('txnInput').value  = '';
  $('confirmBtn').disabled=false;
  $('confirmBtn').textContent='Confirm Payment & Unlock PDF';
  $('upiSheet').classList.add('open');
}

function closeUPI(){
  $('upiSheet').classList.remove('open');
}

async function confirmPayment(){
  if(_processing){return;}
  // SECURITY: Rate limit
  if(!rateOK('pay',3,600000)){toast('⚠️ Too many attempts. Wait 10 min.');return;}
  const rawTxn=$('txnInput').value.trim();
  if(!rawTxn||rawTxn.length<6){toast('⚠️ Enter your UTR / Transaction ID');return;}
  const txn=rawTxn.replace(/[^a-zA-Z0-9]/g,'');
  if(txn.length<6){toast('⚠️ Invalid UTR format.');return;}

  // ── ANTI-FRAUD: Triple check ─────────────────────────────
  // 1. Check user isn't already paid
  const fresh = await getUser(CU.uid);
  if(fresh?.hasPaid){
    closeUPI();
    toast('Your account is already activated!');
    return;
  }

  // 2. Check UTR not already used
  const existing = await db.collection('payments')
    .where('upiTxnId','==',cleanTxn).limit(1).get();
  if(!existing.empty){
    toast('⚠️ This Transaction ID was already used. Contact support if you have a different UTR.');
    return;
  }

  // 3. Lock processing
  _processing=true;
  $('confirmBtn').disabled=true;
  $('confirmBtn').textContent='Processing...';

  try{
    // Activate account
    await db.collection('users').doc(CU.uid).update({
      hasPaid:true, activeLink:true
    });

    // Save payment (pending admin verification)
    await db.collection('payments').doc().set({
      uid:CU.uid, name:CD.name, email:CD.email,
      amount:PRICE, refCode:CD.referredBy||null,
      upiTxnId:txn, status:'pending_verification',
      adminVerified:false,
      ts:firebase.firestore.FieldValue.serverTimestamp()
    });

    // Pay MLM chain
    if(CD.uplineId) await payChain(CU.uid, CD.name, CD.uplineId);

    // Reload
    CD=await getUser(CU.uid);
    closeUPI();
    $('successTxnId').textContent=txn;
    $('successModal').classList.add('open');
    refreshHome(); loadBook(); loadEarn();

  } catch(e){
    toast('Error: '+e.message);
    $('confirmBtn').disabled=false;
    $('confirmBtn').textContent='Confirm Payment & Unlock PDF';
  } finally{
    _processing=false;
  }
}

function closeSuccess(){
  $('successModal').classList.remove('open');
  navTo('earn');
}

// ═══ DOWNLOAD ══════════════════════════════════════════
function doDownload(){
  if(!CD?.hasPaid){toast('Please purchase first.');return;}
  downloadPDF();
}
function testPDF(){ downloadPDF(); }

function downloadPDF(){
  if(!PDF_B64){
    toast('Preparing PDF...');
    setTimeout(downloadPDF, 500);
    return;
  }
  try{
    const bytes=atob(PDF_B64);
    const arr=new Uint8Array(bytes.length);
    for(let i=0;i<bytes.length;i++) arr[i]=bytes.charCodeAt(i);
    const blob=new Blob([arr],{type:'application/pdf'});
    const url=URL.createObjectURL(blob);
    const a=document.createElement('a');
    a.href=url;
    a.download='HealthConscious_Complete_Guide_Healthy_Eating.pdf';
    document.body.appendChild(a);a.click();
    document.body.removeChild(a);
    setTimeout(()=>URL.revokeObjectURL(url),5000);
    toast('📥 PDF downloading...');
  } catch(e){ toast('Download error: '+e.message); }
}

// ═══ EARN ══════════════════════════════════════════════
async function loadEarn(){
  if(!CD) return;

  // Fix missing activeLink
  if(CD.hasPaid && !CD.activeLink){
    await db.collection('users').doc(CU.uid).update({activeLink:true});
    CD.activeLink=true;
  }

  $('earnLocked').style.display = !CD.hasPaid?'block':'none';
  $('earnActive').style.display =  CD.hasPaid?'block':'none';
  if(!CD.hasPaid) return;

  // Set code and link
  $('myCode').textContent = CD.referralCode;
  const link = location.origin + location.pathname + '?ref=' + CD.referralCode;
  $('refLinkDisplay').textContent = link;
  $('earnMeta').textContent =
    `L1 Recruits: ${(CD.directRecruits||[]).length} · Total Earned: ${fmtINR(CD.totalEarned)}`;

  // Load recruits
  const refs = CD.directRecruits||[];
  if(!refs.length){
    $('recruitList').innerHTML=`<p style="color:var(--stone);font-size:.83rem;">No direct recruits yet. Share your link to start earning!</p>`;
  } else {
    let h='';
    for(const uid of refs.slice(0,20)){
      const u=await getUser(uid);
      if(!u) continue;
      h+=`<div class="recruit-row">
        <div class="recruit-avatar">${u.name.charAt(0).toUpperCase()}</div>
        <div>
          <div class="recruit-name">${u.name}</div>
          <div class="recruit-sub">Joined · ${(u.directRecruits||[]).length} L1 recruits</div>
        </div>
        ${u.hasPaid
          ?'<span class="badge badge-s">✅ Paid</span>'
          :'<span class="badge badge-n">Not paid</span>'}
      </div>`;
    }
    $('recruitList').innerHTML = h;
  }

  // Earnings breakdown
  try{
    const snap=await db.collection('transactions')
      .where('uid','==',CU.uid).where('type','==','bonus')
      .orderBy('ts','desc').limit(50).get();
    const byLv={1:0,2:0,3:0,4:0,5:0};
    snap.forEach(d=>{ const t=d.data(); byLv[t.level]=(byLv[t.level]||0)+t.amount; });
    const rows=[
      {l:1,cls:'er-l1',name:'Direct Recruits (L1)',rate:'₹300 each'},
      {l:2,cls:'er-l2',name:'L2 — Via L1 recruits', rate:'₹200 each'},
      {l:3,cls:'er-l3',name:'L3 — Via L2 recruits', rate:'₹100 each'},
      {l:4,cls:'er-l4',name:'L4 — Via L3 recruits', rate:'₹50 each'},
      {l:5,cls:'er-l5',name:'L5 — Via L4 recruits', rate:'₹25 each'},
    ];
    let h=rows.map(r=>`
      <div class="earn-row ${r.cls}">
        <div class="er-level">L${r.l}</div>
        <div>
          <div class="er-name">${r.name}</div>
          <div class="er-rate">${r.rate}</div>
        </div>
        <div class="er-total">${fmtINR(byLv[r.l])}</div>
      </div>`).join('');
    h+=`<div class="earn-row er-tot" style="margin-top:8px;">
      <div class="er-level" style="background:var(--gold);color:#fff;">∑</div>
      <div><div class="er-name" style="font-weight:700;">Total Earned (all levels)</div></div>
      <div class="er-total" style="color:var(--gold-dk);">${fmtINR(CD.totalEarned)}</div>
    </div>`;
    $('earnBreakdown').innerHTML=h;
  } catch(e){
    $('earnBreakdown').innerHTML='<p style="color:var(--stone);">Could not load breakdown.</p>';
  }
}

// ═══ COPY & SHARE ══════════════════════════════════════
function copyCode(){
  const code=CD?.referralCode||'';
  _copy(code);
  toast('📋 Code copied: '+code);
}

function copyLink(){
  const link=location.origin+location.pathname+'?ref='+(CD?.referralCode||'');
  _copy(link);
  const fl=$('copyFlash');
  if(fl){ fl.style.display='block'; setTimeout(()=>fl.style.display='none',2500); }
  toast('🔗 Referral link copied!');
}

function _copy(text){
  if(navigator.clipboard){
    navigator.clipboard.writeText(text).catch(()=>_fallbackCopy(text));
  } else { _fallbackCopy(text); }
}
function _fallbackCopy(text){
  const ta=document.createElement('textarea');
  ta.value=text;ta.style.cssText='position:fixed;opacity:0;top:0;left:0;';
  document.body.appendChild(ta);ta.select();
  try{document.execCommand('copy');}catch(e){}
  document.body.removeChild(ta);
}

function shareWA(){
  const link=location.origin+location.pathname+'?ref='+(CD?.referralCode||'');
  const msg=encodeURIComponent(
    '📗 *Health Conscious Book* — Complete Guide to Healthy Eating\n\n'+
    '✅ 15 Chapters | English · Telugu · Hindi\n'+
    '💰 Earn ₹300 per referral — no cap, forever!\n'+
    '📱 Only ₹1,999 — Instant PDF!\n\n'+
    'Buy via my link:\n'+link
  );
  window.open('https://wa.me/?text='+msg,'_blank');
}

function shareTG(){
  const link=location.origin+location.pathname+'?ref='+(CD?.referralCode||'');
  window.open(
    'https://t.me/share/url?url='+encodeURIComponent(link)+
    '&text='+encodeURIComponent('📗 Health Conscious Book ₹1,999 — Earn ₹300 per referral!'),
    '_blank'
  );
}

// ═══ WALLET ════════════════════════════════════════════
async function loadWallet(){
  if(!CD) return;
  $('wBalance').textContent   = fmtINR(CD.wallet);
  $('wTotalEarned').textContent= fmtINR(CD.totalEarned);
  $('wWithdrawn').textContent  = fmtINR(CD.totalWithdrawn);
  try{
    const snap=await db.collection('transactions')
      .where('uid','==',CU.uid).orderBy('ts','desc').limit(30).get();
    if(snap.empty){
      $('txList').innerHTML='<p style="color:var(--stone);font-size:.82rem;">No transactions yet.</p>';
      return;
    }
    let h='';
    snap.forEach(doc=>{
      const t=doc.data();
      const dt=t.ts?new Date(t.ts.toDate()).toLocaleDateString('en-IN'):'--';
      const isCredit=t.type==='bonus';
      h+=`<div class="tx-row">
        <div class="tx-ico ${isCredit?'credit':'debit'}">${isCredit?'💰':'💸'}</div>
        <div class="tx-info">
          <div class="tx-title">${isCredit?`Bonus — Level ${t.level} from ${t.fromName||'network'}`:'Withdrawal to '+t.note?.replace('Withdrawal to ','')}</div>
          <div class="tx-sub">${dt}</div>
        </div>
        <div class="tx-amount ${isCredit?'credit':'debit'}">${isCredit?'+':'-'}${fmtINR(t.amount)}</div>
      </div>`;
    });
    $('txList').innerHTML=h;
  } catch(e){}
}

async function doWithdraw(){
  if(_processing) return;
  const amt=parseInt($('wAmt').value);
  const upi=$('wUPI').value.trim();
  if(!amt||amt<MIN_WD){showAlert('Minimum withdrawal is ₹'+MIN_WD,'e','wdAlert');return;}
  if(!upi){showAlert('Enter your UPI ID or bank account.','e','wdAlert');return;}
  if(amt>(CD?.wallet||0)){showAlert('Insufficient balance. Available: '+fmtINR(CD?.wallet||0),'e','wdAlert');return;}

  _processing=true;
  try{
    const batch=db.batch();
    batch.update(db.collection('users').doc(CU.uid),{
      wallet:firebase.firestore.FieldValue.increment(-amt),
      totalWithdrawn:firebase.firestore.FieldValue.increment(amt)
    });
    batch.set(db.collection('withdrawals').doc(),{
      uid:CU.uid,name:CD.name,email:CD.email,
      amount:amt,upi,status:'pending',
      ts:firebase.firestore.FieldValue.serverTimestamp()
    });
    batch.set(db.collection('transactions').doc(),{
      uid:CU.uid,type:'withdrawal',amount:amt,
      note:'Withdrawal to '+upi,
      ts:firebase.firestore.FieldValue.serverTimestamp()
    });
    await batch.commit();
    CD=await getUser(CU.uid);
    refreshHome(); loadWallet();
    $('wAmt').value=''; $('wUPI').value='';
    showAlert('Withdrawal of '+fmtINR(amt)+' submitted! Processed within 48 hours.','s','wdAlert');
    toast('✅ Withdrawal submitted!');
  } catch(e){ showAlert('Error: '+e.message,'e','wdAlert'); }
  finally{ _processing=false; }
}

// ═══ ADMIN ═════════════════════════════════════════════
async function loadAdmin(){
  if(!CU||CU.email!==ADMIN){
    $('pg-admin').innerHTML='<div class="wrap"><div class="alert alert-e"><span class="ai">🚫</span><span>Access denied.</span></div></div>';
    return;
  }
  try{
    const us=await db.collection('users').get();
    const users=us.docs.map(d=>({id:d.id,...d.data()}));
    const paid=users.filter(u=>u.hasPaid);
    $('aUsers').textContent=users.length;
    $('aPaid').textContent=paid.length;
    $('aRevenue').textContent='₹'+(paid.length*PRICE).toLocaleString('en-IN');

    // Users table
    const ut=$('admUsers').querySelector('tbody');
    ut.innerHTML=users.map(u=>`<tr>
      <td><b>${u.name}</b></td>
      <td style="font-size:.72rem;">${u.email}</td>
      <td style="font-family:monospace;font-size:.74rem;">${u.referralCode}</td>
      <td>${u.hasPaid?'<span class="badge badge-s">✅</span>':'<span class="badge badge-n">No</span>'}</td>
      <td>${fmtINR(u.totalEarned||0)}</td>
      <td>${(u.directRecruits||[]).length}</td>
    </tr>`).join('');

    // Payments table
    const pySnap=await db.collection('payments').orderBy('ts','desc').limit(50).get();
    const pt=$('admPay').querySelector('tbody');
    let pending=0;
    pt.innerHTML=pySnap.empty
      ?'<tr><td colspan="5" style="text-align:center;color:var(--stone);padding:16px;">No payments yet</td></tr>'
      :pySnap.docs.map(d=>{
          const p=d.data(),pid=d.id;
          const v=p.adminVerified,r=p.status==='rejected';
          return `<tr>
            <td><b>${p.name}</b><br/><span style="font-size:.7rem;color:var(--stone);">${p.email}</span></td>
            <td><b>₹${p.amount}</b></td>
            <td style="font-family:monospace;font-size:.74rem;color:${v?'var(--success)':r?'var(--danger)':'var(--warn)'};">
              <b>${p.upiTxnId||'--'}</b>
            </td>
            <td>${v?'<span class="badge badge-s">✅ Verified</span>':r?'<span class="badge" style="background:var(--danger-l);color:var(--danger);">❌ Rejected</span>'
              :`<button class="btn btn-primary btn-sm" onclick="verifyPay('${pid}','${p.uid}')" style="margin-bottom:3px;">✓ Verify</button>
               <button class="btn btn-danger btn-sm" onclick="rejectPay('${pid}','${p.uid}')">✗ Reject</button>`}</td>
            <td>${p.ts?new Date(p.ts.toDate()).toLocaleDateString('en-IN'):'--'}</td>
          </tr>`;
        }).join('');

    // Withdrawals
    const ws=await db.collection('withdrawals').orderBy('ts','desc').limit(50).get();
    ws.forEach(d=>{ if(d.data().status==='pending') pending++; });
    $('aPending').textContent=pending;
    const wt=$('admWith').querySelector('tbody');
    wt.innerHTML=ws.empty
      ?'<tr><td colspan="6" style="text-align:center;color:var(--stone);padding:16px;">No withdrawal requests yet</td></tr>'
      :ws.docs.map(doc=>{
          const w=doc.data();
          return `<tr>
            <td><b>${w.name}</b></td>
            <td><b>₹${w.amount}</b></td>
            <td style="font-size:.74rem;">${w.upi}</td>
            <td>${w.status==='pending'
              ?'<span class="badge badge-w">Pending</span>'
              :'<span class="badge badge-s">Paid ✓</span>'}</td>
            <td>${w.ts?new Date(w.ts.toDate()).toLocaleDateString('en-IN'):'--'}</td>
            <td>${w.status==='pending'
              ?`<button class="btn btn-primary btn-sm" onclick="markPaid('${doc.id}')">Mark Paid</button>`
              :'—'}</td>
          </tr>`;
        }).join('');

  } catch(e){ console.error(e); }
}

async function verifyPay(pid,uid){
  if(!confirm('Confirm: Did you verify this UTR in your UPI app and the ₹1,999 payment was received?')) return;
  await db.collection('payments').doc(pid).update({adminVerified:true,status:'verified'});
  toast('✅ Payment verified!');
  loadAdmin();
}

async function rejectPay(pid,uid){
  if(!confirm('Reject this payment? This will DEACTIVATE the user account.')) return;
  await db.collection('payments').doc(pid).update({adminVerified:false,status:'rejected'});
  await db.collection('users').doc(uid).update({hasPaid:false,activeLink:false});
  toast('❌ Payment rejected. User deactivated.');
  loadAdmin();
}

async function markPaid(id){
  await db.collection('withdrawals').doc(id).update({status:'paid'});
  toast('✅ Marked as paid');
  loadAdmin();
}

// ═══ REF FROM URL AUTO-FILL ═══════════════════════════
(function(){
  const ref=new URLSearchParams(location.search).get('ref');
  if(ref){
    localStorage.setItem('pendingRef',ref.toUpperCase());
    const el=$('rRef'); if(el) el.value=ref.toUpperCase();
  }
})();

// ═══ PDF — LOADED LAST FOR FAST LOGIN ════════════════════
// PDF data is at the very end of the script.
// Firebase and all login functions initialize FIRST.
// PDF only loads after 200ms giving the app time to render.
let PDF_B64 = null;
setTimeout(()=>{
  PDF_B64 = "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NTYgNTU2IDU1NiA1NTYgNTU2IDU1NiA1NTYgNTU2IDU1NiAyNzcgNTU2IDI3NyA2NjYgNzIyCjU1NiA3MjIgMzMzIDMzMyAzMzMgMzMzIDY2NiA2NjYgODMzIDYxMCA1NTYgNTU2IDcyMiA3MjIgMzMzIDcyMgoxMDAwIDU1NiAyNzcgNjEwIDg4OSA2MTAgNTgzIDI3NyAyNzcgMjM3IDUwMCA1NTYgXQovRm9udERlc2NyaXB0b3IgMTk4NiAwIFIKL1RvVW5pY29kZSAxOTg3IDAgUgo+PgplbmRvYmoKCjE5ODkgMCBvYmoKPDwvRjEgMTk4OCAwIFIvRjIgMTk3OCAwIFIvRjMgMTk3MyAwIFIvRjQgMTk4MyAwIFIKPj4KZW5kb2JqCgoxOTkwIDAgb2JqCjw8Ci9Gb250IDE5ODkgMCBSCi9Qcm9jU2V0Wy9QREYvVGV4dF0KPj4KZW5kb2JqCgoxIDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAwCi9Db250ZW50cyAyIDAgUj4+CmVuZG9iagoKMTQgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDEKL0NvbnRlbnRzIDE1IDAgUj4+CmVuZG9iagoKOTQgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDIKL0NvbnRlbnRzIDk1IDAgUj4+CmVuZG9iagoKMTE5IDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAzCi9Db250ZW50cyAxMjAgMCBSPj4KZW5kb2JqCgoxNTkgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDQKL0NvbnRlbnRzIDE2MCAwIFI+PgplbmRvYmoKCjI3OSAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgNQovQ29udGVudHMgMjgwIDAgUj4+CmVuZG9iagoKMzUyIDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyA2Ci9Db250ZW50cyAzNTMgMCBSPj4KZW5kb2JqCgo0MzggMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDcKL0NvbnRlbnRzIDQzOSAwIFI+PgplbmRvYmoKCjU0MyAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgOAovQ29udGVudHMgNTQ0IDAgUj4+CmVuZG9iagoKNjAyIDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyA5Ci9Db250ZW50cyA2MDMgMCBSPj4KZW5kb2JqCgo2NjcgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDEwCi9Db250ZW50cyA2NjggMCBSPj4KZW5kb2JqCgo3MjcgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDExCi9Db250ZW50cyA3MjggMCBSPj4KZW5kb2JqCgo3ODggMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDEyCi9Db250ZW50cyA3ODkgMCBSPj4KZW5kb2JqCgo4NjIgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDEzCi9Db250ZW50cyA4NjMgMCBSPj4KZW5kb2JqCgo5MDEgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDE0Ci9Db250ZW50cyA5MDIgMCBSPj4KZW5kb2JqCgo5NTggMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDE1Ci9Db250ZW50cyA5NTkgMCBSPj4KZW5kb2JqCgoxMDUxIDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAxNgovQ29udGVudHMgMTA1MiAwIFI+PgplbmRvYmoKCjEwNjkgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDE3Ci9Db250ZW50cyAxMDcwIDAgUj4+CmVuZG9iagoKMTEyNiAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgMTgKL0NvbnRlbnRzIDExMjcgMCBSPj4KZW5kb2JqCgoxMTU3IDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAxOQovQ29udGVudHMgMTE1OCAwIFI+PgplbmRvYmoKCjEyMTYgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDIwCi9Db250ZW50cyAxMjE3IDAgUj4+CmVuZG9iagoKMTI1NCAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgMjEKL0NvbnRlbnRzIDEyNTUgMCBSPj4KZW5kb2JqCgoxMzE0IDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAyMgovQ29udGVudHMgMTMxNSAwIFI+PgplbmRvYmoKCjEzOTUgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDIzCi9Db250ZW50cyAxMzk2IDAgUj4+CmVuZG9iagoKMTQwNCAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgMjQKL0NvbnRlbnRzIDE0MDUgMCBSPj4KZW5kb2JqCgoxNDQ5IDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAyNQovQ29udGVudHMgMTQ1MCAwIFI+PgplbmRvYmoKCjE1MDUgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDI2Ci9Db250ZW50cyAxNTA2IDAgUj4+CmVuZG9iagoKMTU5MyAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgMjcKL0NvbnRlbnRzIDE1OTQgMCBSPj4KZW5kb2JqCgoxNjQ3IDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAyOAovQ29udGVudHMgMTY0OCAwIFI+PgplbmRvYmoKCjE3NjAgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDI5Ci9Db250ZW50cyAxNzYxIDAgUj4+CmVuZG9iagoKMTc5OSAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgMzAKL0NvbnRlbnRzIDE4MDAgMCBSPj4KZW5kb2JqCgoxODI4IDAgb2JqCjw8L1R5cGUvUGFnZS9QYXJlbnQgMTk2OCAwIFIvUmVzb3VyY2VzIDE5OTAgMCBSL01lZGlhQm94WzAgMCA1OTUuMzAzOTM3MDA3ODc0IDg0MS44ODk3NjM3Nzk1MjhdL1RhYnMvUwovU3RydWN0UGFyZW50cyAzMQovQ29udGVudHMgMTgyOSAwIFI+PgplbmRvYmoKCjE5MTQgMCBvYmoKPDwvVHlwZS9QYWdlL1BhcmVudCAxOTY4IDAgUi9SZXNvdXJjZXMgMTk5MCAwIFIvTWVkaWFCb3hbMCAwIDU5NS4zMDM5MzcwMDc4NzQgODQxLjg4OTc2Mzc3OTUyOF0vVGFicy9TCi9TdHJ1Y3RQYXJlbnRzIDMyCi9Db250ZW50cyAxOTE1IDAgUj4+CmVuZG9iagoKMTk2MiAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDE5NjggMCBSL1Jlc291cmNlcyAxOTkwIDAgUi9NZWRpYUJveFswIDAgNTk1LjMwMzkzNzAwNzg3NCA4NDEuODg5NzYzNzc5NTI4XS9UYWJzL1MKL1N0cnVjdFBhcmVudHMgMzMKL0NvbnRlbnRzIDE5NjMgMCBSPj4KZW5kb2JqCgo1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0IDAgUgovUGcgMSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9UZXh0QWxpZ24vQ2VudGVyCj4+Ci9LWzAgXQo+PgplbmRvYmoKCjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyAxIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMjQKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMSBdCj4+CmVuZG9iagoKNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDEgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4yCi9UZXh0QWxpZ24vQ2VudGVyCj4+Ci9LWzIgXQo+PgplbmRvYmoKCjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyAxIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMTIKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMyBdCj4+CmVuZG9iagoKOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDEgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wOAovVGV4dEFsaWduL0NlbnRlcgo+PgovS1s0IF0KPj4KZW5kb2JqCgoxMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDEgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovVGV4dEFsaWduL0NlbnRlcgo+PgovS1s1IF0KPj4KZW5kb2JqCgoxMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDEgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovVGV4dEFsaWduL0NlbnRlcgo+PgovS1s2IF0KPj4KZW5kb2JqCgoxMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDEgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovVGV4dEFsaWduL0NlbnRlcgo+PgovS1s3IF0KPj4KZW5kb2JqCgoxMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDEgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovVGV4dEFsaWduL0NlbnRlcgo+PgovS1s4IF0KPj4KZW5kb2JqCgoxNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMCBdCj4+CmVuZG9iagoKMjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDIwIDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxIF0KPj4KZW5kb2JqCgoyMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTkgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi4xOTkKL0hlaWdodCAwLjM3Mgo+PgovS1syMSAwIFIgIF0KPj4KZW5kb2JqCgoyMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMjIgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIgXQo+PgplbmRvYmoKCjIyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxOSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA3LjE2MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzIzIDAgUiAgXQo+PgplbmRvYmoKCjE5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxOCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjAgMCBSICAyMiAwIFIgIF0KPj4KZW5kb2JqCgoyNiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMjUgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzMgXQo+PgplbmRvYmoKCjI1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAyNCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjE5OQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzI2IDAgUiAgXQo+PgplbmRvYmoKCjI4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAyNyAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNCBdCj4+CmVuZG9iagoKMjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDI0IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDcuMTYxCi9IZWlnaHQgMC4zNzIKPj4KL0tbMjggMCBSICBdCj4+CmVuZG9iagoKMjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDE4IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNSAwIFIgIDI3IDAgUiAgXQo+PgplbmRvYmoKCjMxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAzMCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNSBdCj4+CmVuZG9iagoKMzAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDI5IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDIuMTk5Ci9IZWlnaHQgMC4zNzIKPj4KL0tbMzEgMCBSICBdCj4+CmVuZG9iagoKMzMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDMyIDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s2IF0KPj4KZW5kb2JqCgozMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMjkgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNy4xNjEKL0hlaWdodCAwLjM3Mgo+PgovS1szMyAwIFIgIF0KPj4KZW5kb2JqCgoyOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTggMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzMwIDAgUiAgMzIgMCBSICBdCj4+CmVuZG9iagoKMzYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDM1IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s3IF0KPj4KZW5kb2JqCgozNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzQgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi4xOTkKL0hlaWdodCAwLjM3Mgo+PgovS1szNiAwIFIgIF0KPj4KZW5kb2JqCgozOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzcgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzggXQo+PgplbmRvYmoKCjM3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzNCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA3LjE2MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzM4IDAgUiAgXQo+PgplbmRvYmoKCjM0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxOCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzUgMCBSICAzNyAwIFIgIF0KPj4KZW5kb2JqCgo0MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDAgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzkgXQo+PgplbmRvYmoKCjQwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzOSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjE5OQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzQxIDAgUiAgXQo+PgplbmRvYmoKCjQzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0MiAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMTAgXQo+PgplbmRvYmoKCjQyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzOSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA3LjE2MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzQzIDAgUiAgXQo+PgplbmRvYmoKCjM5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxOCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDAgMCBSICA0MiAwIFIgIF0KPj4KZW5kb2JqCgo0NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDUgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzExIF0KPj4KZW5kb2JqCgo0NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDQgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi4xOTkKL0hlaWdodCAwLjM3Mgo+PgovS1s0NiAwIFIgIF0KPj4KZW5kb2JqCgo0OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDcgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzEyIF0KPj4KZW5kb2JqCgo0NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDQgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNy4xNjEKL0hlaWdodCAwLjM3Mgo+PgovS1s0OCAwIFIgIF0KPj4KZW5kb2JqCgo0NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTggMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzQ1IDAgUiAgNDcgMCBSICBdCj4+CmVuZG9iagoKNTEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDUwIDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxMyBdCj4+CmVuZG9iagoKNTAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDQ5IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDIuMTk5Ci9IZWlnaHQgMC4zNzIKPj4KL0tbNTEgMCBSICBdCj4+CmVuZG9iagoKNTMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDUyIDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxNCBdCj4+CmVuZG9iagoKNTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDQ5IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDcuMTYxCi9IZWlnaHQgMC4zNzIKPj4KL0tbNTMgMCBSICBdCj4+CmVuZG9iagoKNDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDE4IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s1MCAwIFIgIDUyIDAgUiAgXQo+PgplbmRvYmoKCjU2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1NSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMTUgXQo+PgplbmRvYmoKCjU1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1NCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjE5OQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzU2IDAgUiAgXQo+PgplbmRvYmoKCjU4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1NyAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMTYgXQo+PgplbmRvYmoKCjU3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1NCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA3LjE2MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzU4IDAgUiAgXQo+PgplbmRvYmoKCjU0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxOCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNTUgMCBSICA1NyAwIFIgIF0KPj4KZW5kb2JqCgo2MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNjAgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE3IF0KPj4KZW5kb2JqCgo2MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTkgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi4xOTkKL0hlaWdodCAwLjM3Mgo+PgovS1s2MSAwIFIgIF0KPj4KZW5kb2JqCgo2MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNjIgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE4IF0KPj4KZW5kb2JqCgo2MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTkgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNy4xNjEKL0hlaWdodCAwLjM3Mgo+PgovS1s2MyAwIFIgIF0KPj4KZW5kb2JqCgo1OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTggMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzYwIDAgUiAgNjIgMCBSICBdCj4+CmVuZG9iagoKNjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY1IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxOSBdCj4+CmVuZG9iagoKNjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY0IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDIuMTk5Ci9IZWlnaHQgMC4zNzIKPj4KL0tbNjYgMCBSICBdCj4+CmVuZG9iagoKNjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY3IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syMCBdCj4+CmVuZG9iagoKNjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY0IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDcuMTYxCi9IZWlnaHQgMC4zNzIKPj4KL0tbNjggMCBSICBdCj4+CmVuZG9iagoKNjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDE4IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s2NSAwIFIgIDY3IDAgUiAgXQo+PgplbmRvYmoKCjcxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA3MCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjEgXQo+PgplbmRvYmoKCjcwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA2OSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjE5OQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzcxIDAgUiAgXQo+PgplbmRvYmoKCjczIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA3MiAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjIgXQo+PgplbmRvYmoKCjcyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA2OSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA3LjE2MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzczIDAgUiAgXQo+PgplbmRvYmoKCjY5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxOCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNzAgMCBSICA3MiAwIFIgIF0KPj4KZW5kb2JqCgo3NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNzUgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIzIF0KPj4KZW5kb2JqCgo3NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNzQgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi4xOTkKL0hlaWdodCAwLjM3Mgo+PgovS1s3NiAwIFIgIF0KPj4KZW5kb2JqCgo3OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNzcgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI0IF0KPj4KZW5kb2JqCgo3NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNzQgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNy4xNjEKL0hlaWdodCAwLjM3Mgo+PgovS1s3OCAwIFIgIF0KPj4KZW5kb2JqCgo3NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTggMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzc1IDAgUiAgNzcgMCBSICBdCj4+CmVuZG9iagoKODEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDgwIDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNSBdCj4+CmVuZG9iagoKODAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDc5IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDIuMTk5Ci9IZWlnaHQgMC4zNzIKPj4KL0tbODEgMCBSICBdCj4+CmVuZG9iagoKODMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDgyIDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNiBdCj4+CmVuZG9iagoKODIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDc5IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDcuMTYxCi9IZWlnaHQgMC4zNzIKPj4KL0tbODMgMCBSICBdCj4+CmVuZG9iagoKNzkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDE4IDAgUgovUGcgMTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s4MCAwIFIgIDgyIDAgUiAgXQo+PgplbmRvYmoKCjg2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA4NSAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjcgXQo+PgplbmRvYmoKCjg1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA4NCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjE5OQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzg2IDAgUiAgXQo+PgplbmRvYmoKCjg4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA4NyAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjggXQo+PgplbmRvYmoKCjg3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA4NCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA3LjE2MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzg4IDAgUiAgXQo+PgplbmRvYmoKCjg0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxOCAwIFIKL1BnIDE0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbODUgMCBSICA4NyAwIFIgIF0KPj4KZW5kb2JqCgo5MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgOTAgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI5IF0KPj4KZW5kb2JqCgo5MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgODkgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi4xOTkKL0hlaWdodCAwLjM3Mgo+PgovS1s5MSAwIFIgIF0KPj4KZW5kb2JqCgo5MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgOTIgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzMwIF0KPj4KZW5kb2JqCgo5MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgODkgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNy4xNjEKL0hlaWdodCAwLjM3Mgo+PgovS1s5MyAwIFIgIF0KPj4KZW5kb2JqCgo4OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTggMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzkwIDAgUiAgOTIgMCBSICBdCj4+CmVuZG9iagoKMTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyAxNCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUFmdGVyIDAuMDAyCi9TdGFydEluZGVudCAwLjAwMQovRW5kSW5kZW50IDAuMjc3Ci9XaWR0aCA5LjYzOAovSGVpZ2h0IDUuNTgyCi9CQm94WzU2LjcgNDQzLjU4OSA1MzguNiA3MjIuNjg5XQo+PgovS1sxOSAwIFIgIDI0IDAgUiAgMjkgMCBSICAzNCAwIFIgIDM5IDAgUiAgNDQgMCBSICA0OSAwIFIgIDU0IDAgUiAgNTkgMCBSICA2NCAwIFIgIDY5IDAgUiAgNzQgMCBSICA3OSAwIFIgIDg0IDAgUiAgODkgMCBSICBdCj4+CmVuZG9iagoKOTcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyA5NCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzAgXQo+PgplbmRvYmoKCjk4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0IDAgUgovUGcgOTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4xNAo+PgovS1sxIDIgMyBdCj4+CmVuZG9iagoKOTkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyA5NCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzQgNSA2IDcgXQo+PgplbmRvYmoKCjEwMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDk0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDgKPj4KL0tbOCBdCj4+CmVuZG9iagoKMTAzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgMTAyIDAgUgovUGcgOTQgMCBSCi9LWzkgXQo+PgplbmRvYmoKCjEwNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCAxMDQgMCBSCi9QZyA5NCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzEwIF0KPj4KZW5kb2JqCgoxMDQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDEwMiAwIFIKL1BnIDk0IDAgUgovS1sxMDUgMCBSICBdCj4+CmVuZG9iagoKMTAyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAxMDEgMCBSCi9QZyA5NCAwIFIKL0tbMTAzIDAgUiAgMTA0IDAgUiAgXQo+PgplbmRvYmoKCjEwNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDEwNiAwIFIKL1BnIDk0IDAgUgovS1sxMSBdCj4+CmVuZG9iagoKMTA5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDEwOCAwIFIKL1BnIDk0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMTIgXQo+PgplbmRvYmoKCjEwOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMTA2IDAgUgovUGcgOTQgMCBSCi9LWzEwOSAwIFIgIF0KPj4KZW5kb2JqCgoxMDYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDEwMSAwIFIKL1BnIDk0IDAgUgovS1sxMDcgMCBSICAxMDggMCBSICBdCj4+CmVuZG9iagoKMTExIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgMTEwIDAgUgovUGcgOTQgMCBSCi9LWzEzIF0KPj4KZW5kb2JqCgoxMTMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMTEyIDAgUgovUGcgOTQgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1sxNCBdCj4+CmVuZG9iagoKMTEyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCAxMTAgMCBSCi9QZyA5NCAwIFIKL0tbMTEzIDAgUiAgXQo+PgplbmRvYmoKCjExMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgMTAxIDAgUgovUGcgOTQgMCBSCi9LWzExMSAwIFIgIDExMiAwIFIgIF0KPj4KZW5kb2JqCgoxMTUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAxMTQgMCBSCi9QZyA5NCAwIFIKL0tbMTUgXQo+PgplbmRvYmoKCjExNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCAxMTYgMCBSCi9QZyA5NCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzE2IF0KPj4KZW5kb2JqCgoxMTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDExNCAwIFIKL1BnIDk0IDAgUgovS1sxMTcgMCBSICBdCj4+CmVuZG9iagoKMTE0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAxMDEgMCBSCi9QZyA5NCAwIFIKL0tbMTE1IDAgUiAgMTE2IDAgUiAgXQo+PgplbmRvYmoKCjEwMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTAovUCA0IDAgUgovUGcgOTQgMCBSCi9BIDw8L08vTGlzdC9MaXN0TnVtYmVyaW5nL0RlY2ltYWwKPj4KL0tbMTAyIDAgUiAgMTA2IDAgUiAgMTEwIDAgUiAgMTE0IDAgUiAgXQo+PgplbmRvYmoKCjExOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDk0IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDgKPj4KL0tbMTcgMTggMTkgXQo+PgplbmRvYmoKCjEyNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTI0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMCBdCj4+CmVuZG9iagoKMTI2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxMjQgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNgo+PgovS1sxIF0KPj4KZW5kb2JqCgoxMjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDEyMyAwIFIKL1BnIDExOSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDEuMTg0Cj4+Ci9LWzEyNSAwIFIgIDEyNiAwIFIgIF0KPj4KZW5kb2JqCgoxMjMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDEyMiAwIFIKL1BnIDExOSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzEyNCAwIFIgIF0KPj4KZW5kb2JqCgoxMjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VBZnRlciAwLjAwNQovU3RhcnRJbmRlbnQgMC4wMDIKL0VuZEluZGVudCAwLjI3NgovV2lkdGggOS42MzgKL0hlaWdodCAxLjE4OQovQkJveFs1Ni43IDcyNS43MzkgNTM4LjYgNzg1LjE4OV0KPj4KL0tbMTIzIDAgUiAgXQo+PgplbmRvYmoKCjEyNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDExOSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzIgMyA0IDUgXQo+PgplbmRvYmoKCjEyOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDExOSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjE4Cj4+Ci9LWzYgXQo+PgplbmRvYmoKCjEzMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTMxIDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNyBdCj4+CmVuZG9iagoKMTMxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxMzAgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAwLjQ0NQo+PgovS1sxMzIgMCBSICBdCj4+CmVuZG9iagoKMTMwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxMjkgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxMzEgMCBSICBdCj4+CmVuZG9iagoKMTM1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxMzQgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNgo+PgovS1s4IDkgMTAgMTEgXQo+PgplbmRvYmoKCjEzNiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTM0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMTIgMTMgMTQgMTUgXQo+PgplbmRvYmoKCjEzNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTM0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMTYgMTcgMTggXQo+PgplbmRvYmoKCjEzOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTM0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMTkgMjAgMjEgXQo+PgplbmRvYmoKCjEzOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTM0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMjIgMjMgMjQgXQo+PgplbmRvYmoKCjE0MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTM0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMjUgMjYgMjcgXQo+PgplbmRvYmoKCjE0MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTM0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKL1NwYWNlQWZ0ZXIgMC4wNgo+PgovS1syOCAyOSAzMCBdCj4+CmVuZG9iagoKMTM0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxMzMgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCA2LjQ5Cj4+Ci9LWzEzNSAwIFIgIDEzNiAwIFIgIDEzNyAwIFIgIDEzOCAwIFIgIDEzOSAwIFIgIDE0MCAwIFIgIDE0MSAwIFIgIF0KPj4KZW5kb2JqCgoxMzMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDEyOSAwIFIKL1BnIDExOSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzEzNCAwIFIgIF0KPj4KZW5kb2JqCgoxMjkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyAxMTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VBZnRlciAwLjAwMgovU3RhcnRJbmRlbnQgMC4wMQovRW5kSW5kZW50IDAuMjY4Ci9XaWR0aCA5LjYzOAovSGVpZ2h0IDYuOTM3Ci9CQm94WzU2LjcgMjI4LjA4OSA1MzguNiA1NzQuOTM5XQo+PgovS1sxMzAgMCBSICAxMzMgMCBSICBdCj4+CmVuZG9iagoKMTQyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMTgKPj4KL0tbMzEgXQo+PgplbmRvYmoKCjE0NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTQ1IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMzIgXQo+PgplbmRvYmoKCjE0NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTQ0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC40NTgKPj4KL0tbMTQ2IDAgUiAgXQo+PgplbmRvYmoKCjE0OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTQ3IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMzMgXQo+PgplbmRvYmoKCjE0NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTQ0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC40NTgKPj4KL0tbMTQ4IDAgUiAgXQo+PgplbmRvYmoKCjE0NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTQzIDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMTQ1IDAgUiAgMTQ3IDAgUiAgXQo+PgplbmRvYmoKCjE1MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTUwIDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzQgXQo+PgplbmRvYmoKCjE1MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTQ5IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC42MjUKPj4KL0tbMTUxIDAgUiAgXQo+PgplbmRvYmoKCjE1MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTUyIDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzUgMzYgXQo+PgplbmRvYmoKCjE1MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTQ5IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC42MjUKPj4KL0tbMTUzIDAgUiAgXQo+PgplbmRvYmoKCjE0OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTQzIDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMTUwIDAgUiAgMTUyIDAgUiAgXQo+PgplbmRvYmoKCjE1NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTU1IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzcgXQo+PgplbmRvYmoKCjE1NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTU0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbMTU2IDAgUiAgXQo+PgplbmRvYmoKCjE1OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTU3IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzggXQo+PgplbmRvYmoKCjE1NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTU0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbMTU4IDAgUiAgXQo+PgplbmRvYmoKCjE1NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMTQzIDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMTU1IDAgUiAgMTU3IDAgUiAgXQo+PgplbmRvYmoKCjE2NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTYzIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMCBdCj4+CmVuZG9iagoKMTYzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxNjIgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxNjQgMCBSICBdCj4+CmVuZG9iagoKMTY2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxNjUgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxIF0KPj4KZW5kb2JqCgoxNjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDE2MiAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzE2NiAwIFIgIF0KPj4KZW5kb2JqCgoxNjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDE0MyAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE2MyAwIFIgIDE2NSAwIFIgIF0KPj4KZW5kb2JqCgoxNjkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDE2OCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIgXQo+PgplbmRvYmoKCjE2OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTY3IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC42MjIKPj4KL0tbMTY5IDAgUiAgXQo+PgplbmRvYmoKCjE3MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTcwIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMyA0IF0KPj4KZW5kb2JqCgoxNzAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDE2NyAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNjIyCj4+Ci9LWzE3MSAwIFIgIF0KPj4KZW5kb2JqCgoxNjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDE0MyAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE2OCAwIFIgIDE3MCAwIFIgIF0KPj4KZW5kb2JqCgoxNzQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDE3MyAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzUgXQo+PgplbmRvYmoKCjE3MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMTcyIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbMTc0IDAgUiAgXQo+PgplbmRvYmoKCjE3NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMTc1IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNiBdCj4+CmVuZG9iagoKMTc1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxNzIgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxNzYgMCBSICBdCj4+CmVuZG9iagoKMTcyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxNDMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxNzMgMCBSICAxNzUgMCBSICBdCj4+CmVuZG9iagoKMTc5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxNzggMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s3IF0KPj4KZW5kb2JqCgoxNzggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDE3NyAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNjIyCj4+Ci9LWzE3OSAwIFIgIF0KPj4KZW5kb2JqCgoxODEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDE4MCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzggOSBdCj4+CmVuZG9iagoKMTgwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxNzcgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjYyMgo+PgovS1sxODEgMCBSICBdCj4+CmVuZG9iagoKMTc3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxNDMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxNzggMCBSICAxODAgMCBSICBdCj4+CmVuZG9iagoKMTg0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxODMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxMCBdCj4+CmVuZG9iagoKMTgzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxODIgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxODQgMCBSICBdCj4+CmVuZG9iagoKMTg2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxODUgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxMSBdCj4+CmVuZG9iagoKMTg1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxODIgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxODYgMCBSICBdCj4+CmVuZG9iagoKMTgyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxNDMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxODMgMCBSICAxODUgMCBSICBdCj4+CmVuZG9iagoKMTg5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxODggMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxMiBdCj4+CmVuZG9iagoKMTg4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxODcgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxODkgMCBSICBdCj4+CmVuZG9iagoKMTkxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxOTAgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxMyBdCj4+CmVuZG9iagoKMTkwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxODcgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxOTEgMCBSICBdCj4+CmVuZG9iagoKMTg3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxNDMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxODggMCBSICAxOTAgMCBSICBdCj4+CmVuZG9iagoKMTk0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxOTMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxNCBdCj4+CmVuZG9iagoKMTkzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxOTIgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjYyMgo+PgovS1sxOTQgMCBSICBdCj4+CmVuZG9iagoKMTk2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxOTUgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxNSAxNiBdCj4+CmVuZG9iagoKMTk1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxOTIgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjYyMgo+PgovS1sxOTYgMCBSICBdCj4+CmVuZG9iagoKMTkyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxNDMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxOTMgMCBSICAxOTUgMCBSICBdCj4+CmVuZG9iagoKMTk5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAxOTggMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxNyBdCj4+CmVuZG9iagoKMTk4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxOTcgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1sxOTkgMCBSICBdCj4+CmVuZG9iagoKMjAxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAyMDAgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxOCBdCj4+CmVuZG9iagoKMjAwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAxOTcgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDQuNjgKL0hlaWdodCAwLjM5Mgo+PgovS1syMDEgMCBSICBdCj4+CmVuZG9iagoKMTk3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAxNDMgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1sxOTggMCBSICAyMDAgMCBSICBdCj4+CmVuZG9iagoKMTQzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgMTE5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDIKL1N0YXJ0SW5kZW50IDAuMDAyCi9FbmRJbmRlbnQgMC4yNzYKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMS40NzcKPj4KL0tbMTQ0IDAgUiAgMTQ5IDAgUiAgMTU0IDAgUiAgMTYyIDAgUiAgMTY3IDAgUiAgMTcyIDAgUiAgMTc3IDAgUiAgMTgyIDAgUiAgMTg3IDAgUiAgMTkyIDAgUiAgMTk3IDAgUiAgXQo+PgplbmRvYmoKCjIwMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjE4Cj4+Ci9LWzE5IF0KPj4KZW5kb2JqCgoyMDYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDIwNSAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIwIF0KPj4KZW5kb2JqCgoyMDUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDIwNCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDAuNDQ1Cj4+Ci9LWzIwNiAwIFIgIF0KPj4KZW5kb2JqCgoyMDQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDIwMyAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIwNSAwIFIgIF0KPj4KZW5kb2JqCgoyMDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDIwOCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzIxIDIyIF0KPj4KZW5kb2JqCgoyMTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMTEgMCBSCi9QZyAxNTkgMCBSCi9LWzIzIF0KPj4KZW5kb2JqCgoyMTQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjEzIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMjQgMjUgXQo+PgplbmRvYmoKCjIxMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjExIDAgUgovUGcgMTU5IDAgUgovS1syMTQgMCBSICBdCj4+CmVuZG9iagoKMjExIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyMTAgMCBSCi9QZyAxNTkgMCBSCi9LWzIxMiAwIFIgIDIxMyAwIFIgIF0KPj4KZW5kb2JqCgoyMTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMTUgMCBSCi9QZyAxNTkgMCBSCi9LWzI2IF0KPj4KZW5kb2JqCgoyMTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjE3IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMjcgXQo+PgplbmRvYmoKCjIxNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjE1IDAgUgovUGcgMTU5IDAgUgovS1syMTggMCBSICBdCj4+CmVuZG9iagoKMjE1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyMTAgMCBSCi9QZyAxNTkgMCBSCi9LWzIxNiAwIFIgIDIxNyAwIFIgIF0KPj4KZW5kb2JqCgoyMjAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMTkgMCBSCi9QZyAxNTkgMCBSCi9LWzI4IF0KPj4KZW5kb2JqCgoyMjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjIxIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMjkgXQo+PgplbmRvYmoKCjIyMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjE5IDAgUgovUGcgMTU5IDAgUgovS1syMjIgMCBSICBdCj4+CmVuZG9iagoKMjE5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyMTAgMCBSCi9QZyAxNTkgMCBSCi9LWzIyMCAwIFIgIDIyMSAwIFIgIF0KPj4KZW5kb2JqCgoyMjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMjMgMCBSCi9QZyAxNTkgMCBSCi9LWzMwIF0KPj4KZW5kb2JqCgoyMjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjI1IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMzEgXQo+PgplbmRvYmoKCjIyNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjIzIDAgUgovUGcgMTU5IDAgUgovS1syMjYgMCBSICBdCj4+CmVuZG9iagoKMjIzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyMTAgMCBSCi9QZyAxNTkgMCBSCi9LWzIyNCAwIFIgIDIyNSAwIFIgIF0KPj4KZW5kb2JqCgoyMjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMjcgMCBSCi9QZyAxNTkgMCBSCi9LWzMyIF0KPj4KZW5kb2JqCgoyMzAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjI5IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMzMgXQo+PgplbmRvYmoKCjIyOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjI3IDAgUgovUGcgMTU5IDAgUgovS1syMzAgMCBSICBdCj4+CmVuZG9iagoKMjI3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyMTAgMCBSCi9QZyAxNTkgMCBSCi9LWzIyOCAwIFIgIDIyOSAwIFIgIF0KPj4KZW5kb2JqCgoyMzIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMzEgMCBSCi9QZyAxNTkgMCBSCi9LWzM0IF0KPj4KZW5kb2JqCgoyMzQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjMzIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMzUgXQo+PgplbmRvYmoKCjIzMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjMxIDAgUgovUGcgMTU5IDAgUgovS1syMzQgMCBSICBdCj4+CmVuZG9iagoKMjMxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyMTAgMCBSCi9QZyAxNTkgMCBSCi9LWzIzMiAwIFIgIDIzMyAwIFIgIF0KPj4KZW5kb2JqCgoyMzYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyMzUgMCBSCi9QZyAxNTkgMCBSCi9LWzM2IF0KPj4KZW5kb2JqCgoyMzggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjM3IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1NwYWNlQWZ0ZXIgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1szNyBdCj4+CmVuZG9iagoKMjM3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCAyMzUgMCBSCi9QZyAxNTkgMCBSCi9LWzIzOCAwIFIgIF0KPj4KZW5kb2JqCgoyMzUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDIxMCAwIFIKL1BnIDE1OSAwIFIKL0tbMjM2IDAgUiAgMjM3IDAgUiAgXQo+PgplbmRvYmoKCjIxMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTAovUCAyMDggMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGlzdC9MaXN0TnVtYmVyaW5nL0Rpc2MKPj4KL0tbMjExIDAgUiAgMjE1IDAgUiAgMjE5IDAgUiAgMjIzIDAgUiAgMjI3IDAgUiAgMjMxIDAgUiAgMjM1IDAgUiAgXQo+PgplbmRvYmoKCjIwOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMjA3IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMy41MTIKPj4KL0tbMjA5IDAgUiAgMjEwIDAgUiAgXQo+PgplbmRvYmoKCjIwNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMjAzIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjA4IDAgUiAgXQo+PgplbmRvYmoKCjIwMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVGFibGUKL1AgNCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUFmdGVyIDAuMDAyCi9TdGFydEluZGVudCAwLjAxCi9FbmRJbmRlbnQgMC4yNjgKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMy45NTkKL0JCb3hbNTYuNyAzMDMuNjM5IDUzOC42IDUwMS41ODldCj4+Ci9LWzIwNCAwIFIgIDIwNyAwIFIgIF0KPj4KZW5kb2JqCgoyNDIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDI0MSAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzM4IF0KPj4KZW5kb2JqCgoyNDEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDI0MCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDAuNDQ1Cj4+Ci9LWzI0MiAwIFIgIF0KPj4KZW5kb2JqCgoyNDAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDIzOSAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI0MSAwIFIgIF0KPj4KZW5kb2JqCgoyNDUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDI0NCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzM5IDQwIF0KPj4KZW5kb2JqCgoyNDggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNDcgMCBSCi9QZyAxNTkgMCBSCi9LWzQxIF0KPj4KZW5kb2JqCgoyNTAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjQ5IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNDIgXQo+PgplbmRvYmoKCjI0OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjQ3IDAgUgovUGcgMTU5IDAgUgovS1syNTAgMCBSICBdCj4+CmVuZG9iagoKMjQ3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyNDYgMCBSCi9QZyAxNTkgMCBSCi9LWzI0OCAwIFIgIDI0OSAwIFIgIF0KPj4KZW5kb2JqCgoyNTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNTEgMCBSCi9QZyAxNTkgMCBSCi9LWzQzIF0KPj4KZW5kb2JqCgoyNTQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjUzIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNDQgXQo+PgplbmRvYmoKCjI1MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjUxIDAgUgovUGcgMTU5IDAgUgovS1syNTQgMCBSICBdCj4+CmVuZG9iagoKMjUxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyNDYgMCBSCi9QZyAxNTkgMCBSCi9LWzI1MiAwIFIgIDI1MyAwIFIgIF0KPj4KZW5kb2JqCgoyNTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNTUgMCBSCi9QZyAxNTkgMCBSCi9LWzQ1IF0KPj4KZW5kb2JqCgoyNTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjU3IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNDYgXQo+PgplbmRvYmoKCjI1NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjU1IDAgUgovUGcgMTU5IDAgUgovS1syNTggMCBSICBdCj4+CmVuZG9iagoKMjU1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyNDYgMCBSCi9QZyAxNTkgMCBSCi9LWzI1NiAwIFIgIDI1NyAwIFIgIF0KPj4KZW5kb2JqCgoyNjAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNTkgMCBSCi9QZyAxNTkgMCBSCi9LWzQ3IF0KPj4KZW5kb2JqCgoyNjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjYxIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNDggXQo+PgplbmRvYmoKCjI2MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjU5IDAgUgovUGcgMTU5IDAgUgovS1syNjIgMCBSICBdCj4+CmVuZG9iagoKMjU5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyNDYgMCBSCi9QZyAxNTkgMCBSCi9LWzI2MCAwIFIgIDI2MSAwIFIgIF0KPj4KZW5kb2JqCgoyNjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNjMgMCBSCi9QZyAxNTkgMCBSCi9LWzQ5IF0KPj4KZW5kb2JqCgoyNjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjY1IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNTAgXQo+PgplbmRvYmoKCjI2NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjYzIDAgUgovUGcgMTU5IDAgUgovS1syNjYgMCBSICBdCj4+CmVuZG9iagoKMjYzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyNDYgMCBSCi9QZyAxNTkgMCBSCi9LWzI2NCAwIFIgIDI2NSAwIFIgIF0KPj4KZW5kb2JqCgoyNjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNjcgMCBSCi9QZyAxNTkgMCBSCi9LWzUxIF0KPj4KZW5kb2JqCgoyNzAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjY5IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNTIgXQo+PgplbmRvYmoKCjI2OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjY3IDAgUgovUGcgMTU5IDAgUgovS1syNzAgMCBSICBdCj4+CmVuZG9iagoKMjY3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyNDYgMCBSCi9QZyAxNTkgMCBSCi9LWzI2OCAwIFIgIDI2OSAwIFIgIF0KPj4KZW5kb2JqCgoyNzIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyNzEgMCBSCi9QZyAxNTkgMCBSCi9LWzUzIF0KPj4KZW5kb2JqCgoyNzQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjczIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1NwYWNlQWZ0ZXIgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1s1NCBdCj4+CmVuZG9iagoKMjczIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCAyNzEgMCBSCi9QZyAxNTkgMCBSCi9LWzI3NCAwIFIgIF0KPj4KZW5kb2JqCgoyNzEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDI0NiAwIFIKL1BnIDE1OSAwIFIKL0tbMjcyIDAgUiAgMjczIDAgUiAgXQo+PgplbmRvYmoKCjI0NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTAovUCAyNDQgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGlzdC9MaXN0TnVtYmVyaW5nL0Rpc2MKPj4KL0tbMjQ3IDAgUiAgMjUxIDAgUiAgMjU1IDAgUiAgMjU5IDAgUiAgMjYzIDAgUiAgMjY3IDAgUiAgMjcxIDAgUiAgXQo+PgplbmRvYmoKCjI0NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMjQzIDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMy4yNwo+PgovS1syNDUgMCBSICAyNDYgMCBSICBdCj4+CmVuZG9iagoKMjQzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAyMzkgMCBSCi9QZyAxNTkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNDQgMCBSICBdCj4+CmVuZG9iagoKMjM5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDIKL1N0YXJ0SW5kZW50IDAuMDEKL0VuZEluZGVudCAwLjI2OAovV2lkdGggOS42MzgKL0hlaWdodCAzLjcxNwovQkJveFs1Ni43IDEwNS4xMzkgNTM4LjYgMjkwLjk4OV0KPj4KL0tbMjQwIDAgUiAgMjQzIDAgUiAgXQo+PgplbmRvYmoKCjI3OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMjc3IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNTUgXQo+PgplbmRvYmoKCjI3NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMjc2IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMC40NDUKPj4KL0tbMjc4IDAgUiAgXQo+PgplbmRvYmoKCjI3NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMjc1IDAgUgovUGcgMTU5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjc3IDAgUiAgXQo+PgplbmRvYmoKCjI4NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMjgzIDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDgKPj4KL0tbMCAxIF0KPj4KZW5kb2JqCgoyODcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyODYgMCBSCi9QZyAyNzkgMCBSCi9LWzIgXQo+PgplbmRvYmoKCjI4OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCAyODggMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1szIF0KPj4KZW5kb2JqCgoyODggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDI4NiAwIFIKL1BnIDI3OSAwIFIKL0tbMjg5IDAgUiAgXQo+PgplbmRvYmoKCjI4NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgMjg1IDAgUgovUGcgMjc5IDAgUgovS1syODcgMCBSICAyODggMCBSICBdCj4+CmVuZG9iagoKMjkxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgMjkwIDAgUgovUGcgMjc5IDAgUgovS1s0IF0KPj4KZW5kb2JqCgoyOTMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMjkyIDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNSBdCj4+CmVuZG9iagoKMjkyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCAyOTAgMCBSCi9QZyAyNzkgMCBSCi9LWzI5MyAwIFIgIF0KPj4KZW5kb2JqCgoyOTAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDI4NSAwIFIKL1BnIDI3OSAwIFIKL0tbMjkxIDAgUiAgMjkyIDAgUiAgXQo+PgplbmRvYmoKCjI5NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDI5NCAwIFIKL1BnIDI3OSAwIFIKL0tbNiBdCj4+CmVuZG9iagoKMjk3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDI5NiAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzcgXQo+PgplbmRvYmoKCjI5NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMjk0IDAgUgovUGcgMjc5IDAgUgovS1syOTcgMCBSICBdCj4+CmVuZG9iagoKMjk0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyODUgMCBSCi9QZyAyNzkgMCBSCi9LWzI5NSAwIFIgIDI5NiAwIFIgIF0KPj4KZW5kb2JqCgoyOTkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAyOTggMCBSCi9QZyAyNzkgMCBSCi9LWzggXQo+PgplbmRvYmoKCjMwMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCAzMDAgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1s5IF0KPj4KZW5kb2JqCgozMDAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDI5OCAwIFIKL1BnIDI3OSAwIFIKL0tbMzAxIDAgUiAgXQo+PgplbmRvYmoKCjI5OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgMjg1IDAgUgovUGcgMjc5IDAgUgovS1syOTkgMCBSICAzMDAgMCBSICBdCj4+CmVuZG9iagoKMzAzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgMzAyIDAgUgovUGcgMjc5IDAgUgovS1sxMCBdCj4+CmVuZG9iagoKMzA1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDMwNCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzExIF0KPj4KZW5kb2JqCgozMDQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDMwMiAwIFIKL1BnIDI3OSAwIFIKL0tbMzA1IDAgUiAgXQo+PgplbmRvYmoKCjMwMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgMjg1IDAgUgovUGcgMjc5IDAgUgovS1szMDMgMCBSICAzMDQgMCBSICBdCj4+CmVuZG9iagoKMzA3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgMzA2IDAgUgovUGcgMjc5IDAgUgovS1sxMiBdCj4+CmVuZG9iagoKMzA5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDMwOCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzEzIF0KPj4KZW5kb2JqCgozMDggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDMwNiAwIFIKL1BnIDI3OSAwIFIKL0tbMzA5IDAgUiAgXQo+PgplbmRvYmoKCjMwNiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgMjg1IDAgUgovUGcgMjc5IDAgUgovS1szMDcgMCBSICAzMDggMCBSICBdCj4+CmVuZG9iagoKMzExIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgMzEwIDAgUgovUGcgMjc5IDAgUgovS1sxNCBdCj4+CmVuZG9iagoKMzEzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDMxMiAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TcGFjZUFmdGVyIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMTUgXQo+PgplbmRvYmoKCjMxMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzEwIDAgUgovUGcgMjc5IDAgUgovS1szMTMgMCBSICBdCj4+CmVuZG9iagoKMzEwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAyODUgMCBSCi9QZyAyNzkgMCBSCi9LWzMxMSAwIFIgIDMxMiAwIFIgIF0KPj4KZW5kb2JqCgoyODUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0wKL1AgMjgzIDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xpc3QvTGlzdE51bWJlcmluZy9EaXNjCj4+Ci9LWzI4NiAwIFIgIDI5MCAwIFIgIDI5NCAwIFIgIDI5OCAwIFIgIDMwMiAwIFIgIDMwNiAwIFIgIDMxMCAwIFIgIF0KPj4KZW5kb2JqCgoyODMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDI4MiAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDMuMjcKPj4KL0tbMjg0IDAgUiAgMjg1IDAgUiAgXQo+PgplbmRvYmoKCjI4MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMjc1IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjgzIDAgUiAgXQo+PgplbmRvYmoKCjI3NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVGFibGUKL1AgNCAwIFIKL1BnIDE1OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUFmdGVyIDAuMDIKL1N0YXJ0SW5kZW50IDAuMDEKL0VuZEluZGVudCAwLjI2OAovV2lkdGggOS42MzgKL0hlaWdodCAwLjQ2NQo+PgovS1syNzYgMCBSICAyODIgMCBSICBdCj4+CmVuZG9iagoKMzE0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMTgKPj4KL0tbMTYgXQo+PgplbmRvYmoKCjMxNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzE3IDE4IF0KPj4KZW5kb2JqCgozMTkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDMxOCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE5IF0KPj4KZW5kb2JqCgozMTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDMxNyAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi43OTkKL0hlaWdodCAwLjM5NQo+PgovS1szMTkgMCBSICBdCj4+CmVuZG9iagoKMzIxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAzMjAgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syMCBdCj4+CmVuZG9iagoKMzIwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzMTcgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDMuMjgxCi9IZWlnaHQgMC4zOTUKPj4KL0tbMzIxIDAgUiAgXQo+PgplbmRvYmoKCjMyMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzIyIDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjEgXQo+PgplbmRvYmoKCjMyMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzE3IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAzLjI4Ci9IZWlnaHQgMC4zOTUKPj4KL0tbMzIzIDAgUiAgXQo+PgplbmRvYmoKCjMxNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMzE2IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzE4IDAgUiAgMzIwIDAgUiAgMzIyIDAgUiAgXQo+PgplbmRvYmoKCjMyNiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzI1IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjIgXQo+PgplbmRvYmoKCjMyNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzI0IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjc5OQovSGVpZ2h0IDAuMzc1Cj4+Ci9LWzMyNiAwIFIgIF0KPj4KZW5kb2JqCgozMjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDMyNyAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIzIF0KPj4KZW5kb2JqCgozMjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDMyNCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMy4yODEKL0hlaWdodCAwLjM3NQo+PgovS1szMjggMCBSICBdCj4+CmVuZG9iagoKMzMwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAzMjkgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNCBdCj4+CmVuZG9iagoKMzI5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzMjQgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDMuMjgKL0hlaWdodCAwLjM3NQo+PgovS1szMzAgMCBSICBdCj4+CmVuZG9iagoKMzI0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAzMTYgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1szMjUgMCBSICAzMjcgMCBSICAzMjkgMCBSICBdCj4+CmVuZG9iagoKMzMzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAzMzIgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNSBdCj4+CmVuZG9iagoKMzMyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzMzEgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDIuNzk5Ci9IZWlnaHQgMC4zNzIKPj4KL0tbMzMzIDAgUiAgXQo+PgplbmRvYmoKCjMzNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzM0IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjYgXQo+PgplbmRvYmoKCjMzNCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzMxIDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAzLjI4MQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzMzNSAwIFIgIF0KPj4KZW5kb2JqCgozMzcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDMzNiAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI3IF0KPj4KZW5kb2JqCgozMzYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDMzMSAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMy4yOAovSGVpZ2h0IDAuMzcyCj4+Ci9LWzMzNyAwIFIgIF0KPj4KZW5kb2JqCgozMzEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDMxNiAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzMzMiAwIFIgIDMzNCAwIFIgIDMzNiAwIFIgIF0KPj4KZW5kb2JqCgozNDAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDMzOSAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI4IF0KPj4KZW5kb2JqCgozMzkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDMzOCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMi43OTkKL0hlaWdodCAwLjM3Mgo+PgovS1szNDAgMCBSICBdCj4+CmVuZG9iagoKMzQyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAzNDEgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syOSBdCj4+CmVuZG9iagoKMzQxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzMzggMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDMuMjgxCi9IZWlnaHQgMC4zNzIKPj4KL0tbMzQyIDAgUiAgXQo+PgplbmRvYmoKCjM0NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzQzIDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzAgXQo+PgplbmRvYmoKCjM0MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzM4IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAzLjI4Ci9IZWlnaHQgMC4zNzIKPj4KL0tbMzQ0IDAgUiAgXQo+PgplbmRvYmoKCjMzOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMzE2IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzM5IDAgUiAgMzQxIDAgUiAgMzQzIDAgUiAgXQo+PgplbmRvYmoKCjM0NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzQ2IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzEgXQo+PgplbmRvYmoKCjM0NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzQ1IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCAyLjc5OQovSGVpZ2h0IDAuMzcyCj4+Ci9LWzM0NyAwIFIgIF0KPj4KZW5kb2JqCgozNDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDM0OCAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzMyIF0KPj4KZW5kb2JqCgozNDggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDM0NSAwIFIKL1BnIDI3OSAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggMy4yODEKL0hlaWdodCAwLjM3Mgo+PgovS1szNDkgMCBSICBdCj4+CmVuZG9iagoKMzUxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCAzNTAgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1szMyBdCj4+CmVuZG9iagoKMzUwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzNDUgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDMuMjgKL0hlaWdodCAwLjM3Mgo+PgovS1szNTEgMCBSICBdCj4+CmVuZG9iagoKMzQ1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAzMTYgMCBSCi9QZyAyNzkgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1szNDYgMCBSICAzNDggMCBSICAzNTAgMCBSICBdCj4+CmVuZG9iagoKMzE2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgMjc5IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDIKL1N0YXJ0SW5kZW50IDAuMDAyCi9FbmRJbmRlbnQgMC4yNzYKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMS44ODgKL0JCb3hbNTYuNyAzODkuMDM5IDUzOC42IDQ4My40MzldCj4+Ci9LWzMxNyAwIFIgIDMyNCAwIFIgIDMzMSAwIFIgIDMzOCAwIFIgIDM0NSAwIFIgIF0KPj4KZW5kb2JqCgozNTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDM1NyAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzAgXQo+PgplbmRvYmoKCjM1OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgMzU3IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMSBdCj4+CmVuZG9iagoKMzU3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCAzNTYgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAxLjE4NAo+PgovS1szNTggMCBSICAzNTkgMCBSICBdCj4+CmVuZG9iagoKMzU2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCAzNTUgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1szNTcgMCBSICBdCj4+CmVuZG9iagoKMzU1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDUKL1N0YXJ0SW5kZW50IDAuMDAyCi9FbmRJbmRlbnQgMC4yNzYKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMS4xODkKL0JCb3hbNTYuNyA3MjUuNzM5IDUzOC42IDc4NS4xODldCj4+Ci9LWzM1NiAwIFIgIF0KPj4KZW5kb2JqCgozNjAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wOAo+PgovS1syIDMgNCA1IF0KPj4KZW5kb2JqCgozNjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4xOAo+PgovS1s2IF0KPj4KZW5kb2JqCgozNjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDM2NCAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzcgXQo+PgplbmRvYmoKCjM2NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzYzIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMC40NDUKPj4KL0tbMzY1IDAgUiAgXQo+PgplbmRvYmoKCjM2MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMzYyIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzY0IDAgUiAgXQo+PgplbmRvYmoKCjM3MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDM2OSAwIFIKL1BnIDM1MiAwIFIKL0tbOCBdCj4+CmVuZG9iagoKMzcyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDM3MSAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzkgMTAgXQo+PgplbmRvYmoKCjM3MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzY5IDAgUgovUGcgMzUyIDAgUgovS1szNzIgMCBSICBdCj4+CmVuZG9iagoKMzY5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM3MCAwIFIgIDM3MSAwIFIgIF0KPj4KZW5kb2JqCgozNzQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzNzMgMCBSCi9QZyAzNTIgMCBSCi9LWzExIF0KPj4KZW5kb2JqCgozNzYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzc1IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMTIgXQo+PgplbmRvYmoKCjM3NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzczIDAgUgovUGcgMzUyIDAgUgovS1szNzYgMCBSICBdCj4+CmVuZG9iagoKMzczIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM3NCAwIFIgIDM3NSAwIFIgIF0KPj4KZW5kb2JqCgozNzggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzNzcgMCBSCi9QZyAzNTIgMCBSCi9LWzEzIF0KPj4KZW5kb2JqCgozODAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzc5IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMTQgXQo+PgplbmRvYmoKCjM3OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzc3IDAgUgovUGcgMzUyIDAgUgovS1szODAgMCBSICBdCj4+CmVuZG9iagoKMzc3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM3OCAwIFIgIDM3OSAwIFIgIF0KPj4KZW5kb2JqCgozODIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzODEgMCBSCi9QZyAzNTIgMCBSCi9LWzE1IF0KPj4KZW5kb2JqCgozODQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzgzIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMTYgXQo+PgplbmRvYmoKCjM4MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzgxIDAgUgovUGcgMzUyIDAgUgovS1szODQgMCBSICBdCj4+CmVuZG9iagoKMzgxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM4MiAwIFIgIDM4MyAwIFIgIF0KPj4KZW5kb2JqCgozODYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzODUgMCBSCi9QZyAzNTIgMCBSCi9LWzE3IF0KPj4KZW5kb2JqCgozODggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzg3IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMTggXQo+PgplbmRvYmoKCjM4NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzg1IDAgUgovUGcgMzUyIDAgUgovS1szODggMCBSICBdCj4+CmVuZG9iagoKMzg1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM4NiAwIFIgIDM4NyAwIFIgIF0KPj4KZW5kb2JqCgozOTAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzODkgMCBSCi9QZyAzNTIgMCBSCi9LWzE5IF0KPj4KZW5kb2JqCgozOTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzkxIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMjAgXQo+PgplbmRvYmoKCjM5MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzg5IDAgUgovUGcgMzUyIDAgUgovS1szOTIgMCBSICBdCj4+CmVuZG9iagoKMzg5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM5MCAwIFIgIDM5MSAwIFIgIF0KPj4KZW5kb2JqCgozOTQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzOTMgMCBSCi9QZyAzNTIgMCBSCi9LWzIxIF0KPj4KZW5kb2JqCgozOTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzk1IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMjIgXQo+PgplbmRvYmoKCjM5NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgMzkzIDAgUgovUGcgMzUyIDAgUgovS1szOTYgMCBSICBdCj4+CmVuZG9iagoKMzkzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCAzNjggMCBSCi9QZyAzNTIgMCBSCi9LWzM5NCAwIFIgIDM5NSAwIFIgIF0KPj4KZW5kb2JqCgozOTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCAzOTcgMCBSCi9QZyAzNTIgMCBSCi9LWzIzIF0KPj4KZW5kb2JqCgo0MDAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgMzk5IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1NwYWNlQWZ0ZXIgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1syNCAyNSBdCj4+CmVuZG9iagoKMzk5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCAzOTcgMCBSCi9QZyAzNTIgMCBSCi9LWzQwMCAwIFIgIF0KPj4KZW5kb2JqCgozOTcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDM2OCAwIFIKL1BnIDM1MiAwIFIKL0tbMzk4IDAgUiAgMzk5IDAgUiAgXQo+PgplbmRvYmoKCjM2OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTAovUCAzNjcgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGlzdC9MaXN0TnVtYmVyaW5nL0Rpc2MKPj4KL0tbMzY5IDAgUiAgMzczIDAgUiAgMzc3IDAgUiAgMzgxIDAgUiAgMzg1IDAgUiAgMzg5IDAgUiAgMzkzIDAgUiAgMzk3IDAgUiAgXQo+PgplbmRvYmoKCjM2NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgMzY2IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMy4xMjgKPj4KL0tbMzY4IDAgUiAgXQo+PgplbmRvYmoKCjM2NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgMzYyIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzY3IDAgUiAgXQo+PgplbmRvYmoKCjM2MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVGFibGUKL1AgNCAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjE0Ci9TcGFjZUFmdGVyIDAuMDAyCi9TdGFydEluZGVudCAwLjAxCi9FbmRJbmRlbnQgMC4yNjgKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMy43MTUKL0JCb3hbNTYuNyA0MDguODM5IDUzOC42IDU5NC41ODldCj4+Ci9LWzM2MyAwIFIgIDM2NiAwIFIgIF0KPj4KZW5kb2JqCgo0MDQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQwMyAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI2IF0KPj4KZW5kb2JqCgo0MDMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDQwMiAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDAuNDQ1Cj4+Ci9LWzQwNCAwIFIgIF0KPj4KZW5kb2JqCgo0MDIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDQwMSAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzQwMyAwIFIgIF0KPj4KZW5kb2JqCgo0MDcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQwNiAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzI3IDI4IDI5IF0KPj4KZW5kb2JqCgo0MTAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCA0MDkgMCBSCi9QZyAzNTIgMCBSCi9LWzMwIF0KPj4KZW5kb2JqCgo0MTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgNDExIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMzEgXQo+PgplbmRvYmoKCjQxMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgNDA5IDAgUgovUGcgMzUyIDAgUgovS1s0MTIgMCBSICBdCj4+CmVuZG9iagoKNDA5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCA0MDggMCBSCi9QZyAzNTIgMCBSCi9LWzQxMCAwIFIgIDQxMSAwIFIgIF0KPj4KZW5kb2JqCgo0MTQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCA0MTMgMCBSCi9QZyAzNTIgMCBSCi9LWzMyIF0KPj4KZW5kb2JqCgo0MTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgNDE1IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMzMgXQo+PgplbmRvYmoKCjQxNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgNDEzIDAgUgovUGcgMzUyIDAgUgovS1s0MTYgMCBSICBdCj4+CmVuZG9iagoKNDEzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCA0MDggMCBSCi9QZyAzNTIgMCBSCi9LWzQxNCAwIFIgIDQxNSAwIFIgIF0KPj4KZW5kb2JqCgo0MTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCA0MTcgMCBSCi9QZyAzNTIgMCBSCi9LWzM0IF0KPj4KZW5kb2JqCgo0MjAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgNDE5IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMzUgXQo+PgplbmRvYmoKCjQxOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgNDE3IDAgUgovUGcgMzUyIDAgUgovS1s0MjAgMCBSICBdCj4+CmVuZG9iagoKNDE3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCA0MDggMCBSCi9QZyAzNTIgMCBSCi9LWzQxOCAwIFIgIDQxOSAwIFIgIF0KPj4KZW5kb2JqCgo0MjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCA0MjEgMCBSCi9QZyAzNTIgMCBSCi9LWzM2IF0KPj4KZW5kb2JqCgo0MjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgNDIzIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1NwYWNlQWZ0ZXIgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1szNyBdCj4+CmVuZG9iagoKNDIzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCA0MjEgMCBSCi9QZyAzNTIgMCBSCi9LWzQyNCAwIFIgIF0KPj4KZW5kb2JqCgo0MjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDQwOCAwIFIKL1BnIDM1MiAwIFIKL0tbNDIyIDAgUiAgNDIzIDAgUiAgXQo+PgplbmRvYmoKCjQwOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTAovUCA0MDYgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGlzdC9MaXN0TnVtYmVyaW5nL0Rpc2MKPj4KL0tbNDA5IDAgUiAgNDEzIDAgUiAgNDE3IDAgUiAgNDIxIDAgUiAgXQo+PgplbmRvYmoKCjQwNiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDA1IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMi42NDQKPj4KL0tbNDA3IDAgUiAgNDA4IDAgUiAgXQo+PgplbmRvYmoKCjQwNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDAxIDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDA2IDAgUiAgXQo+PgplbmRvYmoKCjQwMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVGFibGUKL1AgNCAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUFmdGVyIDAuMDAyCi9TdGFydEluZGVudCAwLjAxCi9FbmRJbmRlbnQgMC4yNjgKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMy4wOTEKL0JCb3hbNTYuNyAyNDEuNjM5IDUzOC42IDM5Ni4xODldCj4+Ci9LWzQwMiAwIFIgIDQwNSAwIFIgIF0KPj4KZW5kb2JqCgo0MjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4xOAo+PgovS1szOCBdCj4+CmVuZG9iagoKNDI2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMTQKPj4KL0tbMzkgNDAgNDEgXQo+PgplbmRvYmoKCjQzMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDI5IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDIgXQo+PgplbmRvYmoKCjQyOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDI4IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMC40NDUKPj4KL0tbNDMwIDAgUiAgXQo+PgplbmRvYmoKCjQyOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDI3IDAgUgovUGcgMzUyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDI5IDAgUiAgXQo+PgplbmRvYmoKCjQzNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDQzNCAwIFIKL1BnIDM1MiAwIFIKL0tbNDMgXQo+PgplbmRvYmoKCjQzNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCA0MzYgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1s0NCBdCj4+CmVuZG9iagoKNDM2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCA0MzQgMCBSCi9QZyAzNTIgMCBSCi9LWzQzNyAwIFIgIF0KPj4KZW5kb2JqCgo0MzQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDQzMyAwIFIKL1BnIDM1MiAwIFIKL0tbNDM1IDAgUiAgNDM2IDAgUiAgXQo+PgplbmRvYmoKCjQ0MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDQ0MSAwIFIKL1BnIDQzOCAwIFIKL0tbMCBdCj4+CmVuZG9iagoKNDQ0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDQ0MyAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzEgXQo+PgplbmRvYmoKCjQ0MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgNDQxIDAgUgovUGcgNDM4IDAgUgovS1s0NDQgMCBSICBdCj4+CmVuZG9iagoKNDQxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCA0MzMgMCBSCi9QZyA0MzggMCBSCi9LWzQ0MiAwIFIgIDQ0MyAwIFIgIF0KPj4KZW5kb2JqCgo0NDYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCA0NDUgMCBSCi9QZyA0MzggMCBSCi9LWzIgXQo+PgplbmRvYmoKCjQ0OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCA0NDcgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1szIF0KPj4KZW5kb2JqCgo0NDcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDQ0NSAwIFIKL1BnIDQzOCAwIFIKL0tbNDQ4IDAgUiAgXQo+PgplbmRvYmoKCjQ0NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNDMzIDAgUgovUGcgNDM4IDAgUgovS1s0NDYgMCBSICA0NDcgMCBSICBdCj4+CmVuZG9iagoKNDUwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNDQ5IDAgUgovUGcgNDM4IDAgUgovS1s0IF0KPj4KZW5kb2JqCgo0NTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgNDUxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNSBdCj4+CmVuZG9iagoKNDUxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCA0NDkgMCBSCi9QZyA0MzggMCBSCi9LWzQ1MiAwIFIgIF0KPj4KZW5kb2JqCgo0NDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDQzMyAwIFIKL1BnIDQzOCAwIFIKL0tbNDUwIDAgUiAgNDUxIDAgUiAgXQo+PgplbmRvYmoKCjQzMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTAovUCA0MzIgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGlzdC9MaXN0TnVtYmVyaW5nL0Rpc2MKPj4KL0tbNDM0IDAgUiAgNDQxIDAgUiAgNDQ1IDAgUiAgNDQ5IDAgUiAgXQo+PgplbmRvYmoKCjQ1MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDMyIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDgKL1NwYWNlQWZ0ZXIgMC4wOAo+PgovS1s2IF0KPj4KZW5kb2JqCgo0MzIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDQzMSAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDAuNTUzCj4+Ci9LWzQzMyAwIFIgIDQ1MyAwIFIgIF0KPj4KZW5kb2JqCgo0MzEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDQyNyAwIFIKL1BnIDM1MiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzQzMiAwIFIgIF0KPj4KZW5kb2JqCgo0MjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyAzNTIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VBZnRlciAwLjAwMgovU3RhcnRJbmRlbnQgMC4wMQovRW5kSW5kZW50IDAuMjY4Ci9XaWR0aCA5LjYzOAovSGVpZ2h0IDEKPj4KL0tbNDI4IDAgUiAgNDMxIDAgUiAgXQo+PgplbmRvYmoKCjQ1NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDU2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNyBdCj4+CmVuZG9iagoKNDU2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA0NTUgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAwLjQ0NQo+PgovS1s0NTcgMCBSICBdCj4+CmVuZG9iagoKNDU1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA0NTQgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s0NTYgMCBSICBdCj4+CmVuZG9iagoKNDYwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA0NTkgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNgo+PgovS1s4IDkgMTAgXQo+PgplbmRvYmoKCjQ2MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDU5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMTEgMTIgMTMgXQo+PgplbmRvYmoKCjQ2MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDU5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMTQgMTUgXQo+PgplbmRvYmoKCjQ2MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDU5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMTYgMTcgXQo+PgplbmRvYmoKCjQ2NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDU5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKL1NwYWNlQWZ0ZXIgMC4wNgo+PgovS1sxOCAxOSAyMCBdCj4+CmVuZG9iagoKNDU5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA0NTggMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAyLjU1Ngo+PgovS1s0NjAgMCBSICA0NjEgMCBSICA0NjIgMCBSICA0NjMgMCBSICA0NjQgMCBSICBdCj4+CmVuZG9iagoKNDU4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA0NTQgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s0NTkgMCBSICBdCj4+CmVuZG9iagoKNDU0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDIKL1N0YXJ0SW5kZW50IDAuMDEKL0VuZEluZGVudCAwLjI2OAovV2lkdGggOS42MzgKL0hlaWdodCAzLjAwMwovQkJveFs1Ni43IDUzMC41ODkgNTM4LjYgNjgwLjczOV0KPj4KL0tbNDU1IDAgUiAgNDU4IDAgUiAgXQo+PgplbmRvYmoKCjQ2OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDY3IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMjEgXQo+PgplbmRvYmoKCjQ2NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDY2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC40NTgKPj4KL0tbNDY4IDAgUiAgXQo+PgplbmRvYmoKCjQ3MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDY5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1RleHRBbGlnbi9DZW50ZXIKPj4KL0tbMjIgXQo+PgplbmRvYmoKCjQ2OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDY2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC40NTgKPj4KL0tbNDcwIDAgUiAgXQo+PgplbmRvYmoKCjQ2NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDY3IDAgUiAgNDY5IDAgUiAgXQo+PgplbmRvYmoKCjQ3MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDcyIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjMgXQo+PgplbmRvYmoKCjQ3MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDcxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTUKPj4KL0tbNDczIDAgUiAgXQo+PgplbmRvYmoKCjQ3NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDc0IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjQgXQo+PgplbmRvYmoKCjQ3NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDcxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTUKPj4KL0tbNDc1IDAgUiAgXQo+PgplbmRvYmoKCjQ3MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDcyIDAgUiAgNDc0IDAgUiAgXQo+PgplbmRvYmoKCjQ3OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDc3IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjUgXQo+PgplbmRvYmoKCjQ3NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDc2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDc4IDAgUiAgXQo+PgplbmRvYmoKCjQ4MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDc5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjYgXQo+PgplbmRvYmoKCjQ3OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDc2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDgwIDAgUiAgXQo+PgplbmRvYmoKCjQ3NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDc3IDAgUiAgNDc5IDAgUiAgXQo+PgplbmRvYmoKCjQ4MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDgyIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjcgXQo+PgplbmRvYmoKCjQ4MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDgxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDgzIDAgUiAgXQo+PgplbmRvYmoKCjQ4NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDg0IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjggXQo+PgplbmRvYmoKCjQ4NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDgxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDg1IDAgUiAgXQo+PgplbmRvYmoKCjQ4MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDgyIDAgUiAgNDg0IDAgUiAgXQo+PgplbmRvYmoKCjQ4OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDg3IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMjkgXQo+PgplbmRvYmoKCjQ4NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDg2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDg4IDAgUiAgXQo+PgplbmRvYmoKCjQ5MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDg5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzAgXQo+PgplbmRvYmoKCjQ4OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDg2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDkwIDAgUiAgXQo+PgplbmRvYmoKCjQ4NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDg3IDAgUiAgNDg5IDAgUiAgXQo+PgplbmRvYmoKCjQ5MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDkyIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzEgXQo+PgplbmRvYmoKCjQ5MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDkxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDkzIDAgUiAgXQo+PgplbmRvYmoKCjQ5NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDk0IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzIgXQo+PgplbmRvYmoKCjQ5NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDkxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDk1IDAgUiAgXQo+PgplbmRvYmoKCjQ5MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDkyIDAgUiAgNDk0IDAgUiAgXQo+PgplbmRvYmoKCjQ5OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDk3IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzMgXQo+PgplbmRvYmoKCjQ5NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDk2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNDk4IDAgUiAgXQo+PgplbmRvYmoKCjUwMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNDk5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzQgXQo+PgplbmRvYmoKCjQ5OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNDk2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNTAwIDAgUiAgXQo+PgplbmRvYmoKCjQ5NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNDk3IDAgUiAgNDk5IDAgUiAgXQo+PgplbmRvYmoKCjUwMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNTAyIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzUgXQo+PgplbmRvYmoKCjUwMiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTAxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNTAzIDAgUiAgXQo+PgplbmRvYmoKCjUwNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNTA0IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzYgXQo+PgplbmRvYmoKCjUwNCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTAxIDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNTA1IDAgUiAgXQo+PgplbmRvYmoKCjUwMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNTAyIDAgUiAgNTA0IDAgUiAgXQo+PgplbmRvYmoKCjUwOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNTA3IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzcgXQo+PgplbmRvYmoKCjUwNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTA2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNTA4IDAgUiAgXQo+PgplbmRvYmoKCjUxMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNTA5IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMzggXQo+PgplbmRvYmoKCjUwOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTA2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA0LjY4Ci9IZWlnaHQgMC4zOTIKPj4KL0tbNTEwIDAgUiAgXQo+PgplbmRvYmoKCjUwNiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNDY1IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNTA3IDAgUiAgNTA5IDAgUiAgXQo+PgplbmRvYmoKCjQ2NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVGFibGUKL1AgNCAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUFmdGVyIDAuMDAyCi9TdGFydEluZGVudCAwLjAwMgovRW5kSW5kZW50IDAuMjc2Ci9XaWR0aCA5LjYzOAovSGVpZ2h0IDMuNTk5Ci9CQm94WzU2LjcgMzM3Ljk4OSA1MzguNiA1MTcuOTM5XQo+PgovS1s0NjYgMCBSICA0NzEgMCBSICA0NzYgMCBSICA0ODEgMCBSICA0ODYgMCBSICA0OTEgMCBSICA0OTYgMCBSICA1MDEgMCBSICA1MDYgMCBSICBdCj4+CmVuZG9iagoKNTE0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1MTMgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1szOSBdCj4+CmVuZG9iagoKNTEzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1MTIgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAwLjQ0NQo+PgovS1s1MTQgMCBSICBdCj4+CmVuZG9iagoKNTEyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA1MTEgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s1MTMgMCBSICBdCj4+CmVuZG9iagoKNTE3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1MTYgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wOAo+PgovS1s0MCA0MSBdCj4+CmVuZG9iagoKNTIwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTE5IDAgUgovUGcgNDM4IDAgUgovS1s0MiBdCj4+CmVuZG9iagoKNTIyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDUyMSAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzQzIDQ0IF0KPj4KZW5kb2JqCgo1MjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDUxOSAwIFIKL1BnIDQzOCAwIFIKL0tbNTIyIDAgUiAgXQo+PgplbmRvYmoKCjUxOSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTE4IDAgUgovUGcgNDM4IDAgUgovS1s1MjAgMCBSICA1MjEgMCBSICBdCj4+CmVuZG9iagoKNTI0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTIzIDAgUgovUGcgNDM4IDAgUgovS1s0NSBdCj4+CmVuZG9iagoKNTI2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDUyNSAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzQ2IDQ3IF0KPj4KZW5kb2JqCgo1MjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDUyMyAwIFIKL1BnIDQzOCAwIFIKL0tbNTI2IDAgUiAgXQo+PgplbmRvYmoKCjUyMyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTE4IDAgUgovUGcgNDM4IDAgUgovS1s1MjQgMCBSICA1MjUgMCBSICBdCj4+CmVuZG9iagoKNTI4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTI3IDAgUgovUGcgNDM4IDAgUgovS1s0OCBdCj4+CmVuZG9iagoKNTMwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDUyOSAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzQ5IF0KPj4KZW5kb2JqCgo1MjkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDUyNyAwIFIKL1BnIDQzOCAwIFIKL0tbNTMwIDAgUiAgXQo+PgplbmRvYmoKCjUyNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTE4IDAgUgovUGcgNDM4IDAgUgovS1s1MjggMCBSICA1MjkgMCBSICBdCj4+CmVuZG9iagoKNTMyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTMxIDAgUgovUGcgNDM4IDAgUgovS1s1MCBdCj4+CmVuZG9iagoKNTM0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDUzMyAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzUxIF0KPj4KZW5kb2JqCgo1MzMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDUzMSAwIFIKL1BnIDQzOCAwIFIKL0tbNTM0IDAgUiAgXQo+PgplbmRvYmoKCjUzMSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTE4IDAgUgovUGcgNDM4IDAgUgovS1s1MzIgMCBSICA1MzMgMCBSICBdCj4+CmVuZG9iagoKNTM2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTM1IDAgUgovUGcgNDM4IDAgUgovS1s1MiBdCj4+CmVuZG9iagoKNTM4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDUzNyAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzUzIF0KPj4KZW5kb2JqCgo1MzcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDUzNSAwIFIKL1BnIDQzOCAwIFIKL0tbNTM4IDAgUiAgXQo+PgplbmRvYmoKCjUzNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTE4IDAgUgovUGcgNDM4IDAgUgovS1s1MzYgMCBSICA1MzcgMCBSICBdCj4+CmVuZG9iagoKNTQwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTM5IDAgUgovUGcgNDM4IDAgUgovS1s1NCBdCj4+CmVuZG9iagoKNTQyIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDU0MSAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TcGFjZUFmdGVyIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNTUgNTYgXQo+PgplbmRvYmoKCjU0MSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgNTM5IDAgUgovUGcgNDM4IDAgUgovS1s1NDIgMCBSICBdCj4+CmVuZG9iagoKNTM5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCA1MTggMCBSCi9QZyA0MzggMCBSCi9LWzU0MCAwIFIgIDU0MSAwIFIgIF0KPj4KZW5kb2JqCgo1MTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0wKL1AgNTE2IDAgUgovUGcgNDM4IDAgUgovQSA8PC9PL0xpc3QvTGlzdE51bWJlcmluZy9EaXNjCj4+Ci9LWzUxOSAwIFIgIDUyMyAwIFIgIDUyNyAwIFIgIDUzMSAwIFIgIDUzNSAwIFIgIDUzOSAwIFIgIF0KPj4KZW5kb2JqCgo1MTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDUxNSAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDMuNzAzCj4+Ci9LWzUxNyAwIFIgIDUxOCAwIFIgIF0KPj4KZW5kb2JqCgo1MTUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDUxMSAwIFIKL1BnIDQzOCAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzUxNiAwIFIgIF0KPj4KZW5kb2JqCgo1MTEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyA0MzggMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VBZnRlciAwLjAwMgovU3RhcnRJbmRlbnQgMC4wMQovRW5kSW5kZW50IDAuMjY4Ci9XaWR0aCA5LjYzOAovSGVpZ2h0IDQuMTUKL0JCb3hbNTYuNyAxMDUuMTg5IDUzOC42IDMxMi42ODldCj4+Ci9LWzUxMiAwIFIgIDUxNSAwIFIgIF0KPj4KZW5kb2JqCgo1NDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU0OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzAgXQo+PgplbmRvYmoKCjU1MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNTQ4IDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbMSBdCj4+CmVuZG9iagoKNTQ4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1NDcgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAxLjE4NAo+PgovS1s1NDkgMCBSICA1NTAgMCBSICBdCj4+CmVuZG9iagoKNTQ3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA1NDYgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s1NDggMCBSICBdCj4+CmVuZG9iagoKNTQ2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDUKL1N0YXJ0SW5kZW50IDAuMDAyCi9FbmRJbmRlbnQgMC4yNzYKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMS4xODkKL0JCb3hbNTYuNyA3MjUuNzM5IDUzOC42IDc4NS4xODldCj4+Ci9LWzU0NyAwIFIgIF0KPj4KZW5kb2JqCgo1NTEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wOAo+PgovS1syIDMgNCA1IF0KPj4KZW5kb2JqCgo1NTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4xOAo+PgovS1s2IF0KPj4KZW5kb2JqCgo1NTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1NSAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzcgXQo+PgplbmRvYmoKCjU1NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTU0IDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMC40NDUKPj4KL0tbNTU2IDAgUiAgXQo+PgplbmRvYmoKCjU1NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNTUzIDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNTU1IDAgUiAgXQo+PgplbmRvYmoKCjU1OSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNTU4IDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDYKPj4KL0tbOCA5IF0KPj4KZW5kb2JqCgo1NjAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Cj4+Ci9LWzEwIDExIF0KPj4KZW5kb2JqCgo1NjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Cj4+Ci9LWzEyIDEzIF0KPj4KZW5kb2JqCgo1NjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Cj4+Ci9LWzE0IDE1IF0KPj4KZW5kb2JqCgo1NjMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Cj4+Ci9LWzE2IDE3IF0KPj4KZW5kb2JqCgo1NjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Cj4+Ci9LWzE4IDE5IF0KPj4KZW5kb2JqCgo1NjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Cj4+Ci9LWzIwIDIxIDIyIF0KPj4KZW5kb2JqCgo1NjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDU1OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA2Ci9TcGFjZUFmdGVyIDAuMDYKPj4KL0tbMjMgMjQgXQo+PgplbmRvYmoKCjU1OCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVEQKL1AgNTU3IDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvSW5saW5lCi9XaWR0aCA5LjM2Ci9IZWlnaHQgMi45NzgKPj4KL0tbNTU5IDAgUiAgNTYwIDAgUiAgNTYxIDAgUiAgNTYyIDAgUiAgNTYzIDAgUiAgNTY0IDAgUiAgNTY1IDAgUiAgNTY2IDAgUiAgXQo+PgplbmRvYmoKCjU1NyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVFIKL1AgNTUzIDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNTU4IDAgUiAgXQo+PgplbmRvYmoKCjU1MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvVGFibGUKL1AgNCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjE0Ci9TcGFjZUFmdGVyIDAuMDAyCi9TdGFydEluZGVudCAwLjAxCi9FbmRJbmRlbnQgMC4yNjgKL1dpZHRoIDkuNjM4Ci9IZWlnaHQgMy41NjUKL0JCb3hbNTYuNyA0MTYuMzM5IDUzOC42IDU5NC41ODldCj4+Ci9LWzU1NCAwIFIgIDU1NyAwIFIgIF0KPj4KZW5kb2JqCgo1NjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDQgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4xOAo+PgovS1syNSBdCj4+CmVuZG9iagoKNTcxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1NzAgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1syNiBdCj4+CmVuZG9iagoKNTcwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1NjkgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAwLjQ0NQo+PgovS1s1NzEgMCBSICBdCj4+CmVuZG9iagoKNTY5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA1NjggMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s1NzAgMCBSICBdCj4+CmVuZG9iagoKNTc0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1NzMgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wOAovU3BhY2VBZnRlciAwLjA4Cj4+Ci9LWzI3IDI4IDI5IDMwIF0KPj4KZW5kb2JqCgo1NzMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDU3MiAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDEuNDMyCj4+Ci9LWzU3NCAwIFIgIF0KPj4KZW5kb2JqCgo1NzIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDU2OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzU3MyAwIFIgIF0KPj4KZW5kb2JqCgo1NjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4xNAovU3BhY2VBZnRlciAwLjAwMgovU3RhcnRJbmRlbnQgMC4wMQovRW5kSW5kZW50IDAuMjY4Ci9XaWR0aCA5LjYzOAovSGVpZ2h0IDIuMDE5Ci9CQm94WzU2LjcgMjQyLjgzOSA1MzguNiAzNDMuNzg5XQo+PgovS1s1NjkgMCBSICA1NzIgMCBSICBdCj4+CmVuZG9iagoKNTc4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA1NzcgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1szMSBdCj4+CmVuZG9iagoKNTc3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1NzYgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAwLjQ0NQo+PgovS1s1NzggMCBSICBdCj4+CmVuZG9iagoKNTc2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA1NzUgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s1NzcgMCBSICBdCj4+CmVuZG9iagoKNTgzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTgyIDAgUgovUGcgNTQzIDAgUgovS1szMiBdCj4+CmVuZG9iagoKNTg1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDU4NCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzMzIDM0IF0KPj4KZW5kb2JqCgo1ODQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDU4MiAwIFIKL1BnIDU0MyAwIFIKL0tbNTg1IDAgUiAgXQo+PgplbmRvYmoKCjU4MiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTgxIDAgUgovUGcgNTQzIDAgUgovS1s1ODMgMCBSICA1ODQgMCBSICBdCj4+CmVuZG9iagoKNTg3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTg2IDAgUgovUGcgNTQzIDAgUgovS1szNSBdCj4+CmVuZG9iagoKNTg5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDU4OCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzM2IDM3IF0KPj4KZW5kb2JqCgo1ODggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDU4NiAwIFIKL1BnIDU0MyAwIFIKL0tbNTg5IDAgUiAgXQo+PgplbmRvYmoKCjU4NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTgxIDAgUgovUGcgNTQzIDAgUgovS1s1ODcgMCBSICA1ODggMCBSICBdCj4+CmVuZG9iagoKNTkxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTkwIDAgUgovUGcgNTQzIDAgUgovS1szOCBdCj4+CmVuZG9iagoKNTkzIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDU5MiAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzM5IF0KPj4KZW5kb2JqCgo1OTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDU5MCAwIFIKL1BnIDU0MyAwIFIKL0tbNTkzIDAgUiAgXQo+PgplbmRvYmoKCjU5MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTgxIDAgUgovUGcgNTQzIDAgUgovS1s1OTEgMCBSICA1OTIgMCBSICBdCj4+CmVuZG9iagoKNTk1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTk0IDAgUgovUGcgNTQzIDAgUgovS1s0MCBdCj4+CmVuZG9iagoKNTk3IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDU5NiAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzQxIDQyIF0KPj4KZW5kb2JqCgo1OTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDU5NCAwIFIKL1BnIDU0MyAwIFIKL0tbNTk3IDAgUiAgXQo+PgplbmRvYmoKCjU5NCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTgxIDAgUgovUGcgNTQzIDAgUgovS1s1OTUgMCBSICA1OTYgMCBSICBdCj4+CmVuZG9iagoKNTk5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNTk4IDAgUgovUGcgNTQzIDAgUgovS1s0MyBdCj4+CmVuZG9iagoKNjAxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDYwMCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TcGFjZUFmdGVyIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbNDQgNDUgXQo+PgplbmRvYmoKCjYwMCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEJvZHkKL1AgNTk4IDAgUgovUGcgNTQzIDAgUgovS1s2MDEgMCBSICBdCj4+CmVuZG9iagoKNTk4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MSQovUCA1ODEgMCBSCi9QZyA1NDMgMCBSCi9LWzU5OSAwIFIgIDYwMCAwIFIgIF0KPj4KZW5kb2JqCgo2MDYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xibAovUCA2MDUgMCBSCi9QZyA2MDIgMCBSCi9LWzAgXQo+PgplbmRvYmoKCjYwOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGlzdCMyMFBhcmFncmFwaAovUCA2MDcgMCBSCi9QZyA2MDIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNAovU3RhcnRJbmRlbnQgMC4yOAo+PgovS1sxIF0KPj4KZW5kb2JqCgo2MDcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDYwNSAwIFIKL1BnIDYwMiAwIFIKL0tbNjA4IDAgUiAgXQo+PgplbmRvYmoKCjYwNSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTgxIDAgUgovUGcgNjAyIDAgUgovS1s2MDYgMCBSICA2MDcgMCBSICBdCj4+CmVuZG9iagoKNjEwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MYmwKL1AgNjA5IDAgUgovUGcgNjAyIDAgUgovS1syIF0KPj4KZW5kb2JqCgo2MTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xpc3QjMjBQYXJhZ3JhcGgKL1AgNjExIDAgUgovUGcgNjAyIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQmVmb3JlIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbMyBdCj4+CmVuZG9iagoKNjExIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCA2MDkgMCBSCi9QZyA2MDIgMCBSCi9LWzYxMiAwIFIgIF0KPj4KZW5kb2JqCgo2MDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDU4MSAwIFIKL1BnIDYwMiAwIFIKL0tbNjEwIDAgUiAgNjExIDAgUiAgXQo+PgplbmRvYmoKCjYxNCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDYxMyAwIFIKL1BnIDYwMiAwIFIKL0tbNCBdCj4+CmVuZG9iagoKNjE2IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDYxNSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TdGFydEluZGVudCAwLjI4Cj4+Ci9LWzUgNiBdCj4+CmVuZG9iagoKNjE1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MQm9keQovUCA2MTMgMCBSCi9QZyA2MDIgMCBSCi9LWzYxNiAwIFIgIF0KPj4KZW5kb2JqCgo2MTMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xJCi9QIDU4MSAwIFIKL1BnIDYwMiAwIFIKL0tbNjE0IDAgUiAgNjE1IDAgUiAgXQo+PgplbmRvYmoKCjYxOCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTGJsCi9QIDYxNyAwIFIKL1BnIDYwMiAwIFIKL0tbNyBdCj4+CmVuZG9iagoKNjIwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MaXN0IzIwUGFyYWdyYXBoCi9QIDYxOSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA0Ci9TcGFjZUFmdGVyIDAuMDQKL1N0YXJ0SW5kZW50IDAuMjgKPj4KL0tbOCA5IF0KPj4KZW5kb2JqCgo2MTkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL0xCb2R5Ci9QIDYxNyAwIFIKL1BnIDYwMiAwIFIKL0tbNjIwIDAgUiAgXQo+PgplbmRvYmoKCjYxNyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvTEkKL1AgNTgxIDAgUgovUGcgNjAyIDAgUgovS1s2MTggMCBSICA2MTkgMCBSICBdCj4+CmVuZG9iagoKNTgxIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9MCi9QIDU4MCAwIFIKL1BnIDU0MyAwIFIKL0EgPDwvTy9MaXN0L0xpc3ROdW1iZXJpbmcvRGlzYwo+PgovS1s1ODIgMCBSICA1ODYgMCBSICA1OTAgMCBSICA1OTQgMCBSICA1OTggMCBSICA2MDUgMCBSICA2MDkgMCBSICA2MTMgMCBSICA2MTcgMCBSICBdCj4+CmVuZG9iagoKNTgwIDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA1NzkgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAyLjczMwo+PgovS1s1ODEgMCBSICBdCj4+CmVuZG9iagoKNTc5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA1NzUgMCBSCi9QZyA1NDMgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s1ODAgMCBSICBdCj4+CmVuZG9iagoKNTc1IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UYWJsZQovUCA0IDAgUgovUGcgNTQzIDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKL1NwYWNlQWZ0ZXIgMC4wMDIKL1N0YXJ0SW5kZW50IDAuMDEKL0VuZEluZGVudCAwLjI2OAovV2lkdGggOS42MzgKL0hlaWdodCAzLjE4Cj4+Ci9LWzU3NiAwIFIgIDU3OSAwIFIgIF0KPj4KZW5kb2JqCgo2MjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYyMyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9UZXh0QWxpZ24vQ2VudGVyCj4+Ci9LWzEwIF0KPj4KZW5kb2JqCgo2MjMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYyMiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNDU4Cj4+Ci9LWzYyNCAwIFIgIF0KPj4KZW5kb2JqCgo2MjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYyNSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9UZXh0QWxpZ24vQ2VudGVyCj4+Ci9LWzExIF0KPj4KZW5kb2JqCgo2MjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYyMiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNDU4Cj4+Ci9LWzYyNiAwIFIgIF0KPj4KZW5kb2JqCgo2MjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzYyMyAwIFIgIDYyNSAwIFIgIF0KPj4KZW5kb2JqCgo2MjkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYyOCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzEyIF0KPj4KZW5kb2JqCgo2MjggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYyNyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzk1Cj4+Ci9LWzYyOSAwIFIgIF0KPj4KZW5kb2JqCgo2MzEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYzMCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzEzIF0KPj4KZW5kb2JqCgo2MzAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYyNyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzk1Cj4+Ci9LWzYzMSAwIFIgIF0KPj4KZW5kb2JqCgo2MjcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzYyOCAwIFIgIDYzMCAwIFIgIF0KPj4KZW5kb2JqCgo2MzQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYzMyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE0IF0KPj4KZW5kb2JqCgo2MzMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYzMiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzYzNCAwIFIgIF0KPj4KZW5kb2JqCgo2MzYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYzNSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE1IF0KPj4KZW5kb2JqCgo2MzUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYzMiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzYzNiAwIFIgIF0KPj4KZW5kb2JqCgo2MzIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzYzMyAwIFIgIDYzNSAwIFIgIF0KPj4KZW5kb2JqCgo2MzkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDYzOCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE2IF0KPj4KZW5kb2JqCgo2MzggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYzNyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNjIyCj4+Ci9LWzYzOSAwIFIgIF0KPj4KZW5kb2JqCgo2NDEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY0MCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE3IDE4IF0KPj4KZW5kb2JqCgo2NDAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDYzNyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNjIyCj4+Ci9LWzY0MSAwIFIgIF0KPj4KZW5kb2JqCgo2MzcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzYzOCAwIFIgIDY0MCAwIFIgIF0KPj4KZW5kb2JqCgo2NDQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY0MyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzE5IF0KPj4KZW5kb2JqCgo2NDMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY0MiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY0NCAwIFIgIF0KPj4KZW5kb2JqCgo2NDYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY0NSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIwIF0KPj4KZW5kb2JqCgo2NDUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY0MiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY0NiAwIFIgIF0KPj4KZW5kb2JqCgo2NDIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzY0MyAwIFIgIDY0NSAwIFIgIF0KPj4KZW5kb2JqCgo2NDkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY0OCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIxIF0KPj4KZW5kb2JqCgo2NDggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY0NyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY0OSAwIFIgIF0KPj4KZW5kb2JqCgo2NTEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY1MCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIyIF0KPj4KZW5kb2JqCgo2NTAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY0NyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY1MSAwIFIgIF0KPj4KZW5kb2JqCgo2NDcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzY0OCAwIFIgIDY1MCAwIFIgIF0KPj4KZW5kb2JqCgo2NTQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY1MyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzIzIF0KPj4KZW5kb2JqCgo2NTMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY1MiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY1NCAwIFIgIF0KPj4KZW5kb2JqCgo2NTYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY1NSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI0IF0KPj4KZW5kb2JqCgo2NTUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY1MiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY1NiAwIFIgIF0KPj4KZW5kb2JqCgo2NTIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzY1MyAwIFIgIDY1NSAwIFIgIF0KPj4KZW5kb2JqCgo2NTkgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY1OCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI1IF0KPj4KZW5kb2JqCgo2NTggMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY1NyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNjIyCj4+Ci9LWzY1OSAwIFIgIF0KPj4KZW5kb2JqCgo2NjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY2MCAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI2IDI3IF0KPj4KZW5kb2JqCgo2NjAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY1NyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuNjIyCj4+Ci9LWzY2MSAwIFIgIF0KPj4KZW5kb2JqCgo2NTcgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzY1OCAwIFIgIDY2MCAwIFIgIF0KPj4KZW5kb2JqCgo2NjQgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY2MyAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI4IF0KPj4KZW5kb2JqCgo2NjMgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY2MiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY2NCAwIFIgIF0KPj4KZW5kb2JqCgo2NjYgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1N0YW5kYXJkCi9QIDY2NSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzI5IF0KPj4KZW5kb2JqCgo2NjUgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY2MiAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggNC42OAovSGVpZ2h0IDAuMzkyCj4+Ci9LWzY2NiAwIFIgIF0KPj4KZW5kb2JqCgo2NjIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDYyMSAwIFIKL1BnIDYwMiAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzY2MyAwIFIgIDY2NSAwIFIgIF0KPj4KZW5kb2JqCgo2MjEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyA2MDIgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VBZnRlciAwLjAwMgovU3RhcnRJbmRlbnQgMC4wMDIKL0VuZEluZGVudCAwLjI3NgovV2lkdGggOS42MzgKL0hlaWdodCA0LjA1OQovQkJveFs1Ni43IDQ1OS4wMzkgNTM4LjYgNjYxLjk4OV0KPj4KL0tbNjIyIDAgUiAgNjI3IDAgUiAgNjMyIDAgUiAgNjM3IDAgUiAgNjQyIDAgUiAgNjQ3IDAgUiAgNjUyIDAgUiAgNjU3IDAgUiAgNjYyIDAgUiAgXQo+PgplbmRvYmoKCjY3MyAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNjcyIDAgUgovUGcgNjY3IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbMCBdCj4+CmVuZG9iagoKNjc0IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9TdGFuZGFyZAovUCA2NzIgMCBSCi9QZyA2NjcgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VCZWZvcmUgMC4wNgo+PgovS1sxIF0KPj4KZW5kb2JqCgo2NzIgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RECi9QIDY3MSAwIFIKL1BnIDY2NyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0lubGluZQovV2lkdGggOS4zNgovSGVpZ2h0IDEuMTg0Cj4+Ci9LWzY3MyAwIFIgIDY3NCAwIFIgIF0KPj4KZW5kb2JqCgo2NzEgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RSCi9QIDY3MCAwIFIKL1BnIDY2NyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCj4+Ci9LWzY3MiAwIFIgIF0KPj4KZW5kb2JqCgo2NzAgMCBvYmoKPDwvVHlwZS9TdHJ1Y3RFbGVtCi9TL1RhYmxlCi9QIDQgMCBSCi9QZyA2NjcgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawovU3BhY2VBZnRlciAwLjAwNQovU3RhcnRJbmRlbnQgMC4wMDIKL0VuZEluZGVudCAwLjI3NgovV2lkdGggOS42MzgKL0hlaWdodCAxLjE4OQovQkJveFs1Ni43IDcyNS43MzkgNTM4LjYgNzg1LjE4OV0KPj4KL0tbNjcxIDAgUiAgXQo+PgplbmRvYmoKCjY3NSAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDY2NyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjA4Cj4+Ci9LWzIgMyA0IDUgXQo+PgplbmRvYmoKCjY3NiAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNCAwIFIKL1BnIDY2NyAwIFIKL0EgPDwvTy9MYXlvdXQvUGxhY2VtZW50L0Jsb2NrCi9TcGFjZUJlZm9yZSAwLjE4Cj4+Ci9LWzYgXQo+PgplbmRvYmoKCjY4MCAwIG9iago8PC9UeXBlL1N0cnVjdEVsZW0KL1MvU3RhbmRhcmQKL1AgNjc5IDAgUgovUGcgNjY3IDAgUgovQSA8PC9PL0xheW91dC9QbGFjZW1lbnQvQmxvY2sKPj4KL0tbNyBdCj4+CmVuZG9iagoKNjc5IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9URAovUCA2NzggMCBSCi9QZyA2NjcgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9JbmxpbmUKL1dpZHRoIDkuMzYKL0hlaWdodCAwLjQ0NQo+PgovS1s2ODAgMCBSICBdCj4+CmVuZG9iagoKNjc4IDAgb2JqCjw8L1R5cGUvU3RydWN0RWxlbQovUy9UUgovUCA2NzcgMCBSCi9QZyA2NjcgMCBSCi9BIDw8L08vTGF5b3V0L1BsYWNlbWVudC9CbG9jawo+PgovS1s2NzkgMCBSICBdCj4+CmVuZG9iagoKNjgzIDAgb2JqCjw8L1R5cGUvU3RydW
