<!doctype html><html><head><meta charset=utf8><meta name=viewport content="width=device-width,initial-scale=1,viewport-fit=cover"><style>:root{color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}html{scroll-padding-top:env(safe-area-inset-top,0px)}body{margin:0;padding:0;font:14px -apple-system,BlinkMacSystemFont,sans-serif;background:#fff;color:#000}img{max-width:100%}[hidden]:not([hidden=until-found i]){display:none!important}</style></head><body>
<title>PHONE LAB</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap" rel="stylesheet">
<script src="https://cdn.tailwindcss.com/3.4.17"></script>
<style>
/* Layout: sticky black bar, centered neon hero with a dual search box, a three-column verdict card, then phone/game catalogue views. Dark by choice (gaming look). */
:root{
  --bg:#060a14;
  --surface:#0b1322;
  --surface2:#111c33;
  --line:#1c2a47;
  --fg:#e9f1ff;
  --muted:#8d9dbd;
  --neon:#00D5FF;
  --neon-dim:rgba(0,213,255,.14);
  --grid:rgba(120,160,255,.045);
  --ok:#2ee6a0;
  --warn:#ffc24a;
  --bad:#ff5d6c;
  --font:'Tajawal',system-ui,-apple-system,'Segoe UI',Tahoma,sans-serif;
  color-scheme:dark;
}
html{background:var(--bg)}
body{background:var(--bg);color:var(--fg);margin:0}
body::before{content:"";position:fixed;inset:0 0 auto;height:env(safe-area-inset-top,0px);z-index:50;background:#000}
#app{font-family:var(--font);font-size:16px;line-height:1.6;min-height:100%;display:flex;flex-direction:column}
#app *{box-sizing:border-box}
#app a{color:inherit;text-decoration:none}
#app button{font-family:inherit;cursor:pointer}
#app :focus-visible{outline:2px solid var(--neon);outline-offset:2px}
.wrap{width:100%;max-width:1120px;margin-inline:auto;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px))}

/* access gate */
.gate{position:fixed;inset:0;z-index:100;display:flex;align-items:center;justify-content:center;overflow-y:auto;
  padding:max(16px,env(safe-area-inset-top,0px)) max(16px,env(safe-area-inset-right,0px)) max(16px,env(safe-area-inset-bottom,0px)) max(16px,env(safe-area-inset-left,0px));
  background:radial-gradient(60% 60% at 50% 0%,rgba(0,213,255,.12),transparent 70%),linear-gradient(var(--grid) 1px,transparent 1px) 0 0/44px 44px,linear-gradient(90deg,var(--grid) 1px,transparent 1px) 0 0/44px 44px,var(--bg)}
.gate-card{width:100%;max-width:400px;display:flex;flex-direction:column;align-items:stretch;gap:14px;text-align:center;padding:28px clamp(18px,5vw,30px);background:var(--surface);border:1px solid var(--line);border-radius:22px;box-shadow:0 0 0 1px rgba(0,213,255,.07),0 24px 70px -24px rgba(0,213,255,.3)}
.gate-logo{font-weight:900;font-size:1.9rem;letter-spacing:.14em;direction:ltr}
.gate-logo i{font-style:normal;color:var(--neon)}
.gate-card .by{font-size:.68rem;font-weight:700;letter-spacing:.24em;color:var(--muted);margin-top:-8px;direction:ltr}
.gate-card h2{margin:10px 0 0;font-size:1.3rem;font-weight:800}
.gate-sub{margin:0;color:var(--muted);font-size:.92rem}
.gate-err{margin:0;font-size:.9rem;font-weight:700}

/* header */
.site-head{position:sticky;top:env(safe-area-inset-top,0px);z-index:40;background:#000;border-bottom:1px solid var(--line)}
.head-in{display:flex;align-items:center;justify-content:space-between;gap:8px 20px;flex-wrap:wrap;padding-block:10px}
.logo{font-weight:900;font-size:1.45rem;letter-spacing:.14em;direction:ltr;color:var(--fg)}
.logo i{font-style:normal;color:var(--neon)}
.logo{display:inline-flex;align-items:baseline;gap:10px;flex-wrap:wrap}
.logo .by{font-size:.62rem;font-weight:700;letter-spacing:.22em;color:var(--muted)}
@media(max-width:520px){.logo .by{font-size:.55rem;letter-spacing:.16em}}
.nav{display:flex;gap:4px;flex-wrap:wrap}
.nav a{padding:8px 14px;border-radius:10px;font-weight:700;font-size:.95rem;color:var(--muted);border-bottom:2px solid transparent;transition:color .15s,background .15s}
.nav a:hover{color:var(--fg);background:var(--surface)}
.nav a.on{color:var(--neon);border-bottom-color:var(--neon)}
@media(max-width:520px){.nav a{padding:7px 10px;font-size:.88rem}.logo{font-size:1.2rem}}

/* hero */
.hero{padding-block:clamp(32px,7vw,76px) 28px;text-align:center;
  background:
    radial-gradient(60% 70% at 50% 0%,rgba(0,213,255,.10),transparent 70%),
    linear-gradient(var(--grid) 1px,transparent 1px) 0 0/44px 44px,
    linear-gradient(90deg,var(--grid) 1px,transparent 1px) 0 0/44px 44px}
.kicker{margin:0 0 14px;color:var(--neon);font-weight:700;font-size:.9rem;letter-spacing:.04em}
h1.big{margin:0 auto;max-width:18ch;font-size:clamp(2rem,6vw,3.7rem);line-height:1.2;font-weight:900;text-wrap:balance}
h1.big em{font-style:normal;color:var(--neon);text-shadow:0 0 28px rgba(0,213,255,.45)}
.sub{margin:16px auto 0;max-width:56ch;color:var(--muted);font-size:1.05rem;text-wrap:balance}

.searchbox{display:grid;grid-template-columns:1fr 1fr auto;gap:8px;padding:8px;margin:30px auto 0;max-width:1000px;
  background:var(--surface);border:1px solid var(--line);border-radius:22px;
  box-shadow:0 0 0 1px rgba(0,213,255,.07),0 24px 70px -24px rgba(0,213,255,.3);text-align:start}
@media(max-width:780px){.searchbox{grid-template-columns:1fr}}
.field{position:relative;display:flex;align-items:center;gap:10px;min-height:58px;padding-inline:14px;background:var(--bg);border:1px solid var(--line);border-radius:15px;transition:border-color .15s,box-shadow .15s}
.field:focus-within{border-color:var(--neon);box-shadow:0 0 0 3px var(--neon-dim)}
.field svg{flex:none;color:var(--neon)}
.field input{flex:1;min-width:0;width:100%;background:transparent;border:0;outline:0;color:var(--fg);font:inherit;font-size:16px;padding:0}
.field input::placeholder{color:#5f7096}
.go{min-height:58px;padding:0 30px;border:0;border-radius:15px;background:var(--neon);color:#021019;font-weight:900;font-size:1.1rem;transition:filter .15s,transform .15s;box-shadow:0 0 30px -6px rgba(0,213,255,.7)}
.go:hover{filter:brightness(1.1)}
.go:active{transform:scale(.98)}
.sugg{position:absolute;inset-inline:0;top:calc(100% + 8px);z-index:30;margin:0;padding:6px;list-style:none;max-height:310px;overflow:auto;background:var(--surface2);border:1px solid var(--line);border-radius:15px;box-shadow:0 18px 40px rgba(0,0,0,.55)}
.sugg li{display:flex;justify-content:space-between;align-items:center;gap:12px;padding:10px 12px;border-radius:10px;cursor:pointer}
.sugg li[aria-selected="true"],.sugg li:hover{background:var(--neon-dim)}
.sugg li.none{cursor:default;color:var(--muted);font-size:.9rem;white-space:normal}
.sugg li.none:hover{background:transparent}
.sugg .nm{font-weight:700;direction:ltr;unicode-bidi:plaintext;min-width:0;overflow-wrap:anywhere}
.sugg .mt{flex:none;color:var(--muted);font-size:.8rem;font-variant-numeric:tabular-nums}
.examples{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;align-items:center;margin-top:20px;color:var(--muted);font-size:.9rem}
.chip{padding:6px 12px;border-radius:999px;border:1px solid var(--line);background:var(--surface);color:var(--fg);font-size:.85rem;font-weight:500;transition:border-color .15s,color .15s}
.chip:hover{border-color:var(--neon);color:var(--neon)}
.chip.on{border-color:var(--neon);color:var(--neon);background:var(--neon-dim)}
.dbcount{margin:16px 0 0;color:var(--muted);font-size:.85rem;font-variant-numeric:tabular-nums}

/* result card */
#result{padding-block:6px 40px;min-height:24px}
.res{background:var(--surface);border:1px solid var(--line);border-radius:22px;overflow:hidden;animation:rise .35s ease both}
@keyframes rise{from{opacity:.0;transform:translateY(8px)}to{opacity:1;transform:none}}
.res-head{display:flex;flex-wrap:wrap;gap:14px 28px;align-items:center;justify-content:space-between;padding:20px clamp(16px,3vw,28px);border-bottom:1px solid var(--line)}
.verdict{margin:0;font-size:clamp(1.25rem,3.4vw,1.8rem);font-weight:900;text-wrap:balance}
.verdict.ok{color:var(--ok)}.verdict.warn{color:var(--warn)}.verdict.bad{color:var(--bad)}
.pair{display:flex;flex-wrap:wrap;gap:8px}
.tag{padding:6px 12px;border-radius:10px;background:var(--bg);border:1px solid var(--line);font-size:.85rem;color:var(--muted);min-width:0;overflow-wrap:anywhere}
.tag b{color:var(--fg);direction:ltr;unicode-bidi:plaintext;font-weight:700}
.guess{padding:10px clamp(16px,3vw,28px);background:var(--neon-dim);color:var(--neon);font-size:.9rem;border-bottom:1px solid var(--line)}
.cols{display:grid;grid-template-columns:repeat(3,minmax(0,1fr))}
@media(max-width:860px){.cols{grid-template-columns:minmax(0,1fr)}}
.col{display:flex;flex-direction:column;gap:14px;padding:22px clamp(16px,3vw,28px);min-width:0}
.col+.col{border-inline-start:1px solid var(--line)}
@media(max-width:860px){.col+.col{border-inline-start:0;border-top:1px solid var(--line)}}
.col h3{margin:0;font-size:1rem;font-weight:800;color:var(--fg)}
.col h3 small{display:block;color:var(--muted);font-weight:500;font-size:.8rem}
.row{display:flex;justify-content:space-between;align-items:baseline;gap:12px;padding-bottom:9px;border-bottom:1px dashed var(--line)}
.row span{color:var(--muted);font-size:.92rem}
.row b{font-size:1.15rem;font-variant-numeric:tabular-nums;direction:ltr;unicode-bidi:plaintext}
.row em{display:block;font-style:normal;font-size:.75rem;color:var(--muted);font-weight:400;text-align:end}
.status{margin-top:auto;padding:11px 14px;border-radius:13px;font-weight:800}
.status.ok{background:rgba(46,230,160,.1);color:var(--ok)}
.status.warn{background:rgba(255,194,74,.1);color:var(--warn)}
.status.bad{background:rgba(255,93,108,.1);color:var(--bad)}
.note{margin:0;color:var(--muted);font-size:.9rem}
.fps-box{display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;gap:6px;flex:1;padding-block:8px}
.fps{font-size:clamp(2.6rem,8vw,3.9rem);line-height:1.05;font-weight:900;color:var(--neon);font-variant-numeric:tabular-nums;direction:ltr;text-shadow:0 0 34px rgba(0,213,255,.4)}
.fps.bad{color:var(--bad);text-shadow:none}
.fps-set{font-size:1.05rem;font-weight:700}
.fine{margin:0;color:var(--muted);font-size:.78rem}
.ai-flag{display:inline-block;margin-inline-start:8px;padding:2px 8px;border-radius:8px;background:rgba(255,194,74,.12);color:var(--warn);font-size:.72rem;font-weight:700;vertical-align:middle}
.res-foot{padding:14px clamp(16px,3vw,28px);border-top:1px solid var(--line);color:var(--muted);font-size:.8rem}

/* notices */
.notice{background:var(--surface);border:1px solid var(--line);border-radius:18px;padding:18px clamp(16px,3vw,24px);display:flex;flex-direction:column;gap:14px;animation:rise .3s ease both}
.notice h3{margin:0;font-size:1.05rem}
.notice p{margin:0;color:var(--muted);font-size:.92rem}
.notice .alts{display:flex;flex-wrap:wrap;gap:8px}
.btn2{padding:9px 16px;border-radius:12px;border:1px solid var(--neon);background:transparent;color:var(--neon);font-weight:700;font-size:.92rem}
.btn2:hover{background:var(--neon-dim)}
.btn2[disabled]{opacity:.6;cursor:progress}
.err{color:var(--bad)!important}

/* catalogue views */
.page{padding-block:clamp(24px,5vw,48px) 48px}
.page h2{margin:0;font-size:clamp(1.5rem,4vw,2.1rem);font-weight:900}
.page .lead{margin:6px 0 0;color:var(--muted)}
.toolbar{display:flex;flex-direction:column;gap:12px;margin-block:22px 18px}
.toolbar .field{max-width:520px}
.chips{display:flex;gap:8px;overflow-x:auto;padding-bottom:4px;scrollbar-width:thin}
.chips .chip{flex:none}
.cards{display:grid;grid-template-columns:repeat(auto-fill,minmax(min(100%,290px),1fr));gap:12px}
.card{display:flex;flex-direction:column;gap:12px;padding:16px;background:var(--surface);border:1px solid var(--line);border-radius:16px;min-width:0}
.card h4{margin:0;font-size:1.05rem;font-weight:800;direction:ltr;unicode-bidi:plaintext;text-align:start;overflow-wrap:anywhere}
.card .meta{display:flex;flex-wrap:wrap;gap:6px 14px;color:var(--muted);font-size:.85rem}
.card .meta b{color:var(--fg);font-variant-numeric:tabular-nums}
.pill{display:inline-block;padding:2px 10px;border-radius:999px;background:var(--neon-dim);color:var(--neon);font-size:.75rem;font-weight:700}
.card .top{display:flex;justify-content:space-between;align-items:start;gap:10px}
.card .use{margin-top:auto;align-self:flex-start}
.more{display:block;margin:22px auto 0}
.empty{padding:30px;text-align:center;color:var(--muted);border:1px dashed var(--line);border-radius:16px}
footer{margin-top:auto;border-top:1px solid var(--line);padding-block:20px;color:var(--muted);font-size:.8rem;text-align:center}
footer p{margin:0 auto;max-width:70ch}
@media(prefers-reduced-motion:reduce){.res,.notice{animation:none}*{transition:none!important}}
</style>

<div id="app" dir="rtl" lang="ar">
  <div id="gate" class="gate" role="dialog" aria-modal="true" aria-labelledby="gate-t">
    <form id="gate-form" class="gate-card" autocomplete="off" novalidate>
      <div class="gate-logo">PHONE <i>LAB</i></div>
      <small class="by">BY ADAM GG</small>
      <h2 id="gate-t">أدخل كود الدخول</h2>
      <p class="gate-sub">الموقع محمي. اكتب الكود للمتابعة.</p>
      <div class="field">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><rect x="4.5" y="10.5" width="15" height="10" rx="2.5"/><path d="M8 10.5V8a4 4 0 0 1 8 0v2.5"/></svg>
        <input id="gate-in" type="password" aria-label="كود الدخول" placeholder="الكود" dir="ltr" autocapitalize="characters" spellcheck="false" autocomplete="off">
      </div>
      <button class="go" type="submit">دخول</button>
      <p class="err gate-err" id="gate-err" role="alert" hidden>الكود غير صحيح. حاول مرة أخرى.</p>
    </form>
  </div>
  <header class="site-head">
    <div class="wrap head-in">
      <a class="logo" href="#home" aria-label="PHONE LAB BY ADAM GG"><span>PHONE <i>LAB</i></span><small class="by">BY ADAM GG</small></a>
      <nav class="nav" aria-label="القائمة الرئيسية">
        <a href="#home" data-v="home">الرئيسية</a>
        <a href="#phones" data-v="phones">قائمة الهواتف</a>
        <a href="#games" data-v="games">قائمة الألعاب</a>
      </nav>
    </div>
  </header>

  <main>
    <section id="v-home" class="view">
      <div class="hero">
        <div class="wrap">
          <p class="kicker">PHONE LAB · فحص أداء الألعاب</p>
          <h1 class="big">هل هاتفك يشغل <em>أقوى الألعاب</em>؟</h1>
          <p class="sub">اكتب اسم هاتفك واسم اللعبة، وسنعرض لك الحد الأدنى والحد الموصى به وعدد الفريمات المتوقع.</p>

          <form id="sform" class="searchbox" autocomplete="off" novalidate>
            <div class="field" id="f-phone">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><rect x="6.5" y="2.5" width="11" height="19" rx="2.5"/><path d="M10.5 18.5h3"/></svg>
              <input id="phone-in" type="text" role="combobox" aria-expanded="false" aria-controls="phone-sugg" aria-label="اسم الهاتف" placeholder="اكتب اسم هاتفك مثلاً: POCO F5 أو S23 Ultra" enterkeyhint="next" autocapitalize="off" spellcheck="false">
              <ul class="sugg" id="phone-sugg" role="listbox" hidden></ul>
            </div>
            <div class="field" id="f-game">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M7 7h10a4.5 4.5 0 0 1 4.4 5.4l-.8 4a2.6 2.6 0 0 1-4.5 1.2L14.5 16h-5l-1.6 1.6a2.6 2.6 0 0 1-4.5-1.2l-.8-4A4.5 4.5 0 0 1 7 7z"/><path d="M8 10v3M6.5 11.5h3"/><circle cx="15.5" cy="10.5" r=".6" fill="currentColor"/><circle cx="17.5" cy="12.5" r=".6" fill="currentColor"/></svg>
              <input id="game-in" type="text" role="combobox" aria-expanded="false" aria-controls="game-sugg" aria-label="اسم اللعبة" placeholder="اكتب اسم اللعبة مثلاً: Where Winds Meet أو ببجي" enterkeyhint="search" autocapitalize="off" spellcheck="false">
              <ul class="sugg" id="game-sugg" role="listbox" hidden></ul>
            </div>
            <button class="go" type="submit">هل سيشغلها؟</button>
          </form>

          <div class="examples" id="examples"><span>جرّب:</span></div>
          <p class="dbcount" id="dbcount"></p>
        </div>
      </div>
      <div class="wrap"><div id="result" aria-live="polite"></div></div>
    </section>

    <section id="v-phones" class="view" hidden>
      <div class="wrap page">
        <h2>قائمة الهواتف</h2>
        <p class="lead" id="phones-count"></p>
        <div class="toolbar">
          <div class="field">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" aria-hidden="true"><circle cx="11" cy="11" r="6.5"/><path d="m20 20-4-4"/></svg>
            <input id="lp-q" type="search" aria-label="ابحث في الهواتف" placeholder="ابحث عن هاتف…" autocapitalize="off" spellcheck="false">
          </div>
          <div class="chips" id="lp-brands"></div>
        </div>
        <div class="cards" id="lp-cards"></div>
        <button class="btn2 more" id="lp-more" hidden>عرض المزيد</button>
      </div>
    </section>

    <section id="v-games" class="view" hidden>
      <div class="wrap page">
        <h2>قائمة الألعاب</h2>
        <p class="lead" id="games-count"></p>
        <div class="toolbar">
          <div class="field">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" aria-hidden="true"><circle cx="11" cy="11" r="6.5"/><path d="m20 20-4-4"/></svg>
            <input id="lg-q" type="search" aria-label="ابحث في الألعاب" placeholder="ابحث عن لعبة… (يدعم العربية والأخطاء الإملائية)" autocapitalize="off" spellcheck="false">
          </div>
        </div>
        <div class="cards" id="lg-cards"></div>
        <button class="btn2 more" id="lg-more" hidden>عرض المزيد</button>
      </div>
    </section>
  </main>

  <footer>
    <div class="wrap">
      <p>الأرقام تقريبية ومبنية على نتائج AnTuTu v10 والمتطلبات المعلنة وتجارب المستخدمين. الأداء الفعلي يتغير حسب الحرارة والتحديثات ونسخة الهاتف.</p>
    </div>
  </footer>
</div>

<script id="core">
/* قاعدة البيانات + محرك البحث الذكي (بدون DOM) */
(function(){
'use strict';

/* ---------- تطبيع الأسماء (عربي/إنجليزي/أخطاء إملائية) ---------- */
var AR={'ا':'a','ء':'','ؤ':'o','ئ':'i','ب':'b','ت':'t','ث':'s','ج':'j','ح':'h','خ':'k','د':'d','ذ':'z','ر':'r','ز':'z','س':'s','ص':'s','ض':'d','ط':'t','ظ':'z','ع':'a','غ':'g','ف':'f','ق':'g','ك':'k','ل':'l','م':'m','ن':'n','ه':'h','ة':'h','ش':'sh','پ':'b','چ':'j','ڤ':'f','گ':'g'};
function arn(s){return s.replace(/[أإآ]/g,'ا').replace(/ة/g,'ه').replace(/ى/g,'ي');}
var BR_RAW=[['ريد ماجيك','redmagic'],['ريدماجيك','redmagic'],['ون بلس','oneplus'],['وان بلس','oneplus'],['ايفون','iphone'],['آيفون','iphone'],['سامسونج','samsung'],['سامسونغ','samsung'],['جالكسي','galaxy'],['جلاكسي','galaxy'],['قالكسي','galaxy'],['شاومي','xiaomi'],['ريدمي','redmi'],['بوكو','poco'],['ريلمي','realme'],['ريالمي','realme'],['اوبو','oppo'],['فيفو','vivo'],['هونر','honor'],['هانر','honor'],['انفنكس','infinix'],['انفينكس','infinix'],['تكنو','tecno'],['بكسل','pixel'],['بيكسل','pixel'],['جوجل','google'],['موتورولا','motorola'],['ناثينج','nothing'],['ناثنق','nothing'],['اسوس','asus'],['الترا','ultra'],['ألترا','ultra'],['برو','pro'],['ماكس','max'],['بلس','plus'],['بلاس','plus'],['نوت','note'],['ميني','mini']];
var BR=BR_RAW.map(function(x){return [arn(x[0]),x[1]];});
function pre(s){
  s=arn(String(s||'').toLowerCase().replace(/[ً-ٟـ]/g,'').trim());
  for(var i=0;i<BR.length;i++){s=s.split(BR[i][0]).join(' '+BR[i][1]+' ');}
  return s.rep
