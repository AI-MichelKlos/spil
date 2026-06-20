<!DOCTYPE html>
<html lang="da">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Spin &amp; Skandale · Krisemanageren</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@300;500;600;700&family=Inter:wght@400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#14181c; --ink-2:#1b2127; --ink-3:#222a31;
    --paper:#f2eee3; --paper-2:#e7e1d2;
    --text:#1c1a17; --muted:#8a8f94; --muted-paper:#7a7464;
    --green:#6b9e78; --green-dk:#4d7a59;
    --red:#d13b2e; --red-dk:#a82d23;
    --gold:#c9a24b;
    --line:#2c353d; --line-paper:#d4cdbb;
    --shadow:0 24px 60px -18px rgba(0,0,0,.65);
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html,body{height:100%}
  body{
    font-family:'Inter',system-ui,sans-serif;
    background:
      radial-gradient(1200px 600px at 70% -10%, #1f272e 0%, transparent 60%),
      radial-gradient(900px 500px at 0% 110%, #11181d 0%, transparent 55%),
      var(--ink);
    color:var(--paper);min-height:100%;
    display:flex;flex-direction:column;align-items:center;
    padding:18px 16px 40px;-webkit-font-smoothing:antialiased;
  }
  .stage{width:100%;max-width:640px;display:flex;flex-direction:column;gap:14px}

  header.bar{display:flex;align-items:baseline;justify-content:space-between;gap:12px;padding:2px 4px;flex-wrap:wrap}
  .brand{display:flex;align-items:baseline;gap:10px;line-height:1}
  .brand .logo{font-family:'Oswald',sans-serif;font-weight:700;font-size:22px;letter-spacing:.5px;text-transform:uppercase}
  .brand .logo .amp{color:var(--red);font-style:italic}
  .brand .tag{font-family:'Space Mono',monospace;font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:2px}
  .casecount{font-family:'Space Mono',monospace;font-size:12px;color:var(--gold);letter-spacing:1px;white-space:nowrap}

  .record{display:flex;align-items:center;gap:10px;background:var(--ink-2);border:1px solid var(--line);border-radius:12px;padding:11px 14px}
  .segs{display:flex;gap:5px;flex:1}
  .seg{flex:1;height:18px;border-radius:4px;background:#0d1115;display:grid;place-items:center;font-family:'Space Mono',monospace;font-size:11px;font-weight:700;color:#fff;line-height:1;transition:background .4s,box-shadow .2s}
  .seg.r{background:var(--green)} .seg.w{background:var(--red)}
  .seg.cur{box-shadow:0 0 0 2px var(--gold)}
  .rec-lbl{font-family:'Space Mono',monospace;font-size:11.5px;color:#aeb4ba;white-space:nowrap;letter-spacing:.5px}
  .rec-lbl b{color:var(--green)}

  .panel{position:relative}
  .card{background:url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNjAiIGhlaWdodD0iMTYwIj48ZmlsdGVyIGlkPSJuIj48ZmVUdXJidWxlbmNlIHR5cGU9ImZyYWN0YWxOb2lzZSIgYmFzZUZyZXF1ZW5jeT0iMC44IiBudW1PY3RhdmVzPSIyIiBzdGl0Y2hUaWxlcz0ic3RpdGNoIi8+PGZlQ29sb3JNYXRyaXggdHlwZT0ic2F0dXJhdGUiIHZhbHVlcz0iMCIvPjwvZmlsdGVyPjxyZWN0IHdpZHRoPSIxNjAiIGhlaWdodD0iMTYwIiBmaWx0ZXI9InVybCgjbikiIG9wYWNpdHk9IjAuNSIvPjwvc3ZnPg=="),linear-gradient(180deg,var(--paper) 0%,var(--paper-2) 100%);background-blend-mode:soft-light;color:var(--text);border-radius:6px;padding:26px 24px 24px;box-shadow:var(--shadow);position:relative;overflow:hidden;border:1px solid var(--line-paper)}
  .card > *{position:relative;z-index:1}
  .card > .stamp{position:absolute;z-index:3}
  .card::before{content:"";position:absolute;top:0;left:0;right:0;height:7px;background:repeating-linear-gradient(90deg,var(--red) 0 22px,#b5b0a2 22px 30px);opacity:.85;z-index:2}
  .card::after{content:"FORTROLIGT";position:absolute;top:50%;left:50%;transform:translate(-50%,-50%) rotate(-20deg);font-family:'Oswald',sans-serif;font-weight:700;font-size:clamp(48px,15vw,80px);letter-spacing:8px;color:rgba(168,45,35,.06);white-space:nowrap;pointer-events:none;z-index:0}
  .stamp{position:absolute;top:18px;right:-6px;transform:rotate(7deg);font-family:'Oswald',sans-serif;font-weight:700;font-size:13px;letter-spacing:3px;text-transform:uppercase;color:var(--red);border:2.5px solid var(--red);border-radius:4px;padding:4px 10px;opacity:.78}
  .stamp.land{animation:stampIn .55s cubic-bezier(.18,1.25,.3,1) both}
  @keyframes stampIn{0%{opacity:0;transform:rotate(7deg) scale(2.7)}55%{opacity:.85;transform:rotate(7deg) scale(.9)}75%{transform:rotate(7deg) scale(1.05)}100%{opacity:.78;transform:rotate(7deg) scale(1)}}
  .meta{font-family:'Space Mono',monospace;font-size:11px;color:var(--muted-paper);letter-spacing:1px;text-transform:uppercase;margin:6px 0 2px}
  .case-title{font-family:'Oswald',sans-serif;font-weight:700;font-size:clamp(26px,7vw,38px);line-height:1.02;text-transform:uppercase;letter-spacing:.3px;margin:2px 0 12px;color:#16140f}
  .situation{font-size:15.5px;line-height:1.55;color:#2c2823}
  .prompt{font-family:'Oswald',sans-serif;font-weight:600;font-size:13px;letter-spacing:1.5px;text-transform:uppercase;color:#6b6457;margin:20px 0 10px;display:flex;align-items:center;gap:8px}
  .prompt::after{content:"";flex:1;height:1px;background:var(--line-paper)}

  .choices{display:flex;flex-direction:column;gap:10px}
  /* begge svar ens i farven, det skal ikke være oplagt */
  .choice{text-align:left;width:100%;cursor:pointer;background:#fbf9f3;border:1.5px solid var(--line-paper);border-radius:6px;padding:14px 16px;display:flex;gap:13px;align-items:flex-start;font-family:inherit;font-size:14.5px;line-height:1.45;color:#2a2620;transition:transform .12s ease,border-color .15s,background .15s,box-shadow .15s}
  .choice:hover{transform:translateY(-1px);border-color:#9c9482;background:#fff;box-shadow:0 6px 16px -10px rgba(0,0,0,.4)}
  .choice:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
  .choice .key{font-family:'Oswald',sans-serif;font-weight:700;font-size:18px;width:30px;height:30px;flex:none;border-radius:50%;display:grid;place-items:center;background:var(--ink);color:var(--paper)}

  .verdict{display:flex;align-items:center;gap:11px;font-family:'Oswald',sans-serif;font-weight:700;font-size:clamp(24px,7vw,30px);text-transform:uppercase;letter-spacing:1px;margin-bottom:4px}
  .verdict .dot{width:15px;height:15px;border-radius:50%;flex:none}
  .verdict.good{color:var(--green-dk)} .verdict.good .dot{background:var(--green)}
  .verdict.bad{color:var(--red-dk)} .verdict.bad .dot{background:var(--red)}
  .vsub{font-family:'Space Mono',monospace;font-size:12px;letter-spacing:.5px;color:#6b6457;margin-bottom:14px}
  .consequence{font-size:15px;line-height:1.55;color:#2c2823}
  .truth{margin-top:16px;padding:13px 15px;background:rgba(0,0,0,.05);border-left:3px solid var(--gold);border-radius:4px;font-size:13.5px;line-height:1.5;color:#4a443a}
  .truth .lab{font-family:'Space Mono',monospace;font-size:10.5px;letter-spacing:1.2px;text-transform:uppercase;color:var(--muted-paper);display:block;margin-bottom:7px}
  .country{display:inline-block;font-family:'Oswald',sans-serif;font-weight:700;font-size:12px;letter-spacing:2.5px;text-transform:uppercase;color:var(--paper);background:#2c2823;padding:4px 11px;border-radius:4px;margin:2px 0 9px}
  .cardsub{font-family:'Space Mono',monospace;font-size:11px;color:var(--muted-paper);letter-spacing:.5px;margin:-4px 0 14px}
  .cover-title{font-family:'Oswald',sans-serif;font-weight:700;font-size:clamp(34px,9vw,52px);line-height:.98;text-transform:uppercase;letter-spacing:.5px;color:#16140f;margin:6px 0 2px}
  .cover-title .amp{color:var(--red);font-style:italic}
  .cover-sub{font-family:'Oswald',sans-serif;font-weight:300;font-size:clamp(15px,4vw,19px);letter-spacing:5px;text-transform:uppercase;color:var(--muted-paper);margin-bottom:16px}
  .dossier{border-top:1px solid var(--line-paper);border-bottom:1px solid var(--line-paper);padding:12px 0;margin:0 0 16px;display:flex;flex-direction:column;gap:8px}
  .drow{display:flex;gap:12px;align-items:center;font-size:13.5px}
  .dk{font-family:'Space Mono',monospace;font-size:10.5px;letter-spacing:1.2px;text-transform:uppercase;color:var(--muted-paper);width:92px;flex:none}
  .dv{color:#2c2823}
  .redact{display:inline-block;height:15px;background:#1c1a17;border-radius:2px}
  .truth .tag{display:inline-block;font-family:'Space Mono',monospace;font-size:11px;font-weight:700;letter-spacing:.3px;padding:3px 9px;border-radius:20px;margin-bottom:8px}
  .truth .tag.right{background:rgba(107,158,120,.2);color:var(--green-dk)}
  .truth .tag.wrong{background:rgba(209,59,46,.16);color:var(--red-dk)}
  .truth .cmp{color:var(--muted-paper);font-weight:400}

  .actions{margin-top:18px;display:flex;justify-content:flex-end}
  .btn{font-family:'Oswald',sans-serif;font-weight:600;font-size:15px;letter-spacing:1px;text-transform:uppercase;cursor:pointer;border:none;border-radius:6px;padding:13px 24px;background:var(--ink);color:var(--paper);transition:transform .12s,box-shadow .15s,background .15s}
  .btn:hover{transform:translateY(-1px);box-shadow:0 8px 20px -10px rgba(0,0,0,.6)}
  .btn:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
  .btn.go{background:var(--green-dk)} .btn.go:hover{background:var(--green)}
  .btn.big{font-size:18px;padding:16px 32px}

  .screen{background:var(--ink-2);border:1px solid var(--line);border-radius:12px;padding:34px 28px;box-shadow:var(--shadow)}
  .kicker{font-family:'Space Mono',monospace;font-size:12px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-bottom:14px}
  .hero-title{font-family:'Oswald',sans-serif;font-weight:700;font-size:clamp(34px,10vw,56px);line-height:.96;text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px}
  .hero-title .amp{color:var(--red);font-style:italic}
  .hero-sub{font-family:'Oswald',sans-serif;font-weight:300;font-size:clamp(16px,4vw,20px);letter-spacing:4px;text-transform:uppercase;color:var(--muted);margin-bottom:22px}
  .lede{font-size:15.5px;line-height:1.6;color:#cfd4d8;max-width:54ch}
  .lede + .lede{margin-top:12px}
  .lede strong{color:var(--paper)}
  .phone{font-size:46px;line-height:1;margin-bottom:8px;animation:ring 1.6s ease-in-out infinite}
  @keyframes ring{0%,60%,100%{transform:rotate(0)}10%,30%,50%{transform:rotate(-12deg)}20%,40%{transform:rotate(12deg)}}

  .rank-badge{font-family:'Oswald',sans-serif;font-weight:700;font-size:clamp(26px,7vw,40px);text-transform:uppercase;letter-spacing:.5px;margin:6px 0 10px;line-height:1.05}
  .bigscore{font-family:'Oswald',sans-serif;font-weight:700;font-size:54px;line-height:1;margin:18px 0 2px}
  .scoreline{font-family:'Space Mono',monospace;font-size:13px;color:var(--muted);margin-top:4px}

  .art-banner{border-radius:10px;overflow:hidden;border:1px solid var(--line);margin:12px 0 2px;line-height:0;background:#0d141a}
  .art-banner svg{display:block;width:100%}
  .league{margin-top:24px;border-top:1px solid var(--line);padding-top:18px;text-align:left}
  .league h3{font-family:'Oswald',sans-serif;font-weight:600;font-size:13px;letter-spacing:1.5px;text-transform:uppercase;color:var(--paper);margin-bottom:4px}
  .league .lsub{font-size:13px;color:#9aa0a6;margin-bottom:14px;line-height:1.45}
  .leg{display:flex;gap:12px;padding:11px 13px;border-radius:9px;background:var(--ink-3);margin-bottom:8px;border:1px solid transparent}
  .leg.me{border-color:var(--gold);background:rgba(201,162,75,.12)}
  .leg .rk{font-family:'Oswald',sans-serif;font-weight:700;font-size:18px;color:var(--gold);width:22px;flex:none;text-align:center;line-height:1.35}
  .leg .nm{font-family:'Oswald',sans-serif;font-weight:600;font-size:15px;color:var(--paper);display:flex;align-items:center;gap:8px;flex-wrap:wrap}
  .leg .nm .you{font-family:'Space Mono',monospace;font-size:9px;letter-spacing:1px;background:var(--gold);color:var(--ink);padding:2px 7px;border-radius:10px;text-transform:uppercase}
  .leg .ds{font-size:12.5px;line-height:1.45;color:#aab0b6;margin-top:3px}

  .fade{animation:fade .45s ease}
  @keyframes fade{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}

  .footer{text-align:center;font-family:'Space Mono',monospace;font-size:10.5px;color:#566069;letter-spacing:.5px;line-height:1.6;margin-top:4px}
  .footer span{color:var(--green)}

  @media (max-width:430px){
    .card{padding:24px 18px 20px}
    .screen{padding:26px 20px}
  }
  @media (prefers-reduced-motion:reduce){*{animation:none !important;transition:none !important}}
</style>
</head>
<body>
<div class="stage">

  <header class="bar">
    <div class="brand">
      <span class="logo">Spin <span class="amp">&amp;</span> Skandale</span>
      <span class="tag">Krisemanageren</span>
    </div>
    <span class="casecount" id="casecount"></span>
  </header>

  <div class="record" id="record" style="display:none">
    <div class="segs" id="segs"></div>
    <span class="rec-lbl" id="rec-lbl"><b>0</b> rigtige</span>
  </div>

  <div id="app"></div>

  <div class="footer">
    Satire · alle sager bygger på virkelige politiske skandaler<br>
    Spil og koncept · <span>Krisemanageren</span>
  </div>
</div>

<script>
/* ---------------------------------------------------------
   To svar pr. sag: ét ansvarligt (RIGTIGT), ét spin (FORKERT).
   Rækkefølgen blandes. I udfaldsteksten vejes de tre hensyn
  , Pressen, Baglandet, Loven, mod hinanden.
   "rigtigt" markerer, om virkelighedens aktør valgte det rigtige svar.
--------------------------------------------------------- */
const LEVELS = [
  { sag:"01", titel:"Watergate", based:"USA · Richard Nixon · 1972-74",
    situation:"Folk med forbindelse til præsidentens kampagne er fanget i et indbrud i oppositionens hovedkvarter i Watergate-bygningen. Sporene peger opad, og der findes båndoptagelser fra Det Ovale Værelse.",
    rigtige:{ tekst:"Læg det hele frem, udléver båndene, og saml op om efterforskningen, også hvor det gør ondt.",
              kon:"Pressen og domstolene får, hvad de beder om, og du fjerner selve mørklægnings-anklagen. Dine loyale rådgivere føler sig udleveret, men det er prisen for at overleve." },
    forkerte:{ tekst:"Benægt enhver viden, brug magtapparatet til at stoppe efterforskningen, og hold på båndene.",
               kon:"Et øjeblik holder muren, men pressen graver, og båndene findes alligevel. Mørklægningen bliver en større forbrydelse end indbruddet, og juridisk er det enden." },
    virkelighed:"Nixon valgte mørklægningen: han forsøgte at stoppe FBI’s efterforskning og tilbageholdt båndene. Da de kom frem, var embedet umuligt at redde, og han trådte tilbage i 1974, den eneste amerikanske præsident, der har gjort det.",
    valgteRigtigt:false },

  { sag:"02", titel:"Lewinsky-sagen", based:"USA · Bill Clinton · 1998",
    situation:"Det kommer frem, at præsidenten har haft et forhold til en ung praktikant i Det Hvide Hus. Han bliver bedt om at svare på det, under ed.",
    rigtige:{ tekst:"Erkend forholdet med det samme, undskyld offentligt, og lad være med at lyve under ed.",
              kon:"Pressen får sin indrømmelse, og du undgår den langt farligere mened-anklage. Baglandet er flovt, men slipper for en månedlang udmattelseskrig." },
    forkerte:{ tekst:"Benægt det hele kategorisk og offentligt, også under ed.",
               kon:"Benægtelsen holder kort, men beviserne dukker op. Nu handler sagen ikke om affæren, men om løgn under ed, og det udløser en rigsretssag." },
    virkelighed:"Bill Clinton benægtede først kategorisk (“I did not have sexual relations with that woman”) og under ed. Da sandheden kom frem, blev han stillet for en rigsret af Repræsentanternes Hus for mened, men frikendt i Senatet og sad perioden ud.",
    valgteRigtigt:false },

  { sag:"03", titel:"Svinebugten", based:"USA · John F. Kennedy · 1961",
    situation:"En hemmelig invasion, du som ny præsident godkendte, er slået fuldstændig fejl og er en offentlig ydmygelse. Skylden kan let skubbes over på efterretningstjenesten, der planlagde den.",
    rigtige:{ tekst:"Tag det fulde ansvar offentligt som landets leder, uanset hvem der planlagde fiaskoen.",
              kon:"Pressen havde forventet bortforklaringer og bliver afvæbnet. Baglandet samler sig om en leder, der står ved sit ansvar, og juridisk er der intet at komme efter. Et nederlag bliver vendt til respekt." },
    forkerte:{ tekst:"Skub ansvaret over på efterretningstjenesten og militæret, der lavede planen.",
               kon:"Det redder måske ansigt en dag eller to, men det ligner en leder, der ikke tør stå ved sine beslutninger. Pressen lugter svaghed, og baglandet mister troen på dig." },
    virkelighed:"Kennedy tog det fulde ansvar offentligt og slog fast, at sejre har mange fædre, mens nederlag er forældreløse. I stedet for at skade ham steg hans popularitet markant.",
    valgteRigtigt:true },

  { sag:"04", titel:"Profumo-sagen", based:"Storbritannien · John Profumo · 1963",
    situation:"Krigsministeren har haft en affære med en ung kvinde, der samtidig omgikkes en sovjetisk diplomat midt under den kolde krig. Han bliver spurgt direkte i Underhuset.",
    rigtige:{ tekst:"Fortæl sandheden om affæren med det samme, også over for parlamentet.",
              kon:"Pinligt, og pressen vil have sit, men du undgår den dødelige anklage om at have løjet for parlamentet, og juridisk står du rent." },
    forkerte:{ tekst:"Benægt enhver upassende forbindelse direkte i Underhuset.",
               kon:"Et øjeblik køber benægtelsen ro, men sandheden kommer frem. At have løjet for parlamentet vejer tungere end selve affæren, og baglandet kan ikke forsvare dig." },
    virkelighed:"John Profumo benægtede affæren over for Underhuset. Da løgnen blev afsløret få uger senere, måtte han træde tilbage i vanære, en af britisk politiks mest berømte skandaler.",
    valgteRigtigt:false },

  { sag:"05", titel:"Partygate", based:"Storbritannien · Boris Johnson · 2020-22",
    situation:"Mens landet er lukket ned under strenge corona-regler, har der været fester i regeringschefens egen embedsbolig. Nu spørger både pressen og parlamentet, om reglerne blev brudt.",
    rigtige:{ tekst:"Erkend, at der blev holdt fester, undskyld klart, og samarbejd med undersøgelsen.",
              kon:"Pressen får sin indrømmelse, og du tager brodden af sagen. Baglandet er rasende over ydmygelsen, men en hurtig undskyldning er bedre end en langtrukken benægtelse." },
    forkerte:{ tekst:"Afvis, at der var fester, og forsikr parlamentet om, at alle regler blev fulgt.",
               kon:"Benægtelsen smuldrer billede for billede. Bøderne kommer, og anklagen om at have vildledt parlamentet bliver det, der vælter dig, ikke selve festen." },
    virkelighed:"Boris Johnson afviste længe, at reglerne var brudt, og forsikrede parlamentet om det modsatte. Han blev idømt bøde af politiet, et udvalg fandt, at han bevidst havde vildledt parlamentet, og han endte med at træde tilbage.",
    valgteRigtigt:false },

  { sag:"06", titel:"Cahuzac-sagen", based:"Frankrig · Jérôme Cahuzac · 2013",
    situation:"Budgetministeren, der står i spidsen for kampen mod skattesnyd, anklages for selv at have en hemmelig konto i udlandet. Han bliver spurgt direkte i Nationalforsamlingen.",
    rigtige:{ tekst:"Indrøm kontoen straks, træd tilbage, og lad skattemyndighederne få fuld adgang.",
              kon:"Ydmygende, og pressen vil rive dig fra hinanden, men du undgår at lyve for forsamlingen, og en hurtig exit begrænser skaden for regeringen." },
    forkerte:{ tekst:"Benægt blankt og se forsamlingen i øjnene: der er ingen konto.",
               kon:"Benægtelsen er kategorisk, og derfor knusende, da kontoen bekræftes. Nu er det løgn for parlamentet og hykleri på én gang, og juridisk er det skattesvig." },
    virkelighed:"Jérôme Cahuzac benægtede kontoen direkte i Nationalforsamlingen. Da den blev afsløret, tilstod han, trådte tilbage og blev senere dømt for skattesvig, en alvorlig krise for hele regeringen.",
    valgteRigtigt:false },

  { sag:"07", titel:"Wulff-sagen", based:"Tyskland · Christian Wulff · 2011-12",
    situation:"Forbundspræsidenten er ramt af en sag om et privat lån. En stor avis er på vej med historien, og han overvejer at lægge pres på chefredaktøren for at stoppe den.",
    rigtige:{ tekst:"Lad historien køre, svar åbent på spørgsmålene, og læg dig ikke ud med pressen.",
              kon:"Lånesagen er ubehagelig, men håndterbar. Ved ikke at true pressen undgår du at lave en lille sag om til et angreb på pressefriheden, og baglandet kan stadig forsvare dig." },
    forkerte:{ tekst:"Ring til chefredaktøren og efterlad en truende besked for at få historien stoppet.",
               kon:"Selve lånet drukner nu i noget langt værre: et statsoverhoved, der truer pressen. Det bliver historien, og hverken pressen eller baglandet kan se bort fra det." },
    virkelighed:"Christian Wulff lagde en truende besked på chefredaktørens telefonsvarer. Det blev kernen i sagen og tvang ham til at træde tilbage, selvom han senere blev frifundet i retten for de oprindelige anklager.",
    valgteRigtigt:false },

  { sag:"08", titel:"Guttenberg-sagen", based:"Tyskland · Karl-Theodor zu Guttenberg · 2011",
    situation:"Den populære forsvarsminister beskyldes for at have afskrevet store dele af sin juridiske doktorafhandling uden kilder. Beviserne hober sig op online.",
    rigtige:{ tekst:"Erkend plagiatet, læg titlen fra dig, og undskyld for at have vildledt.",
              kon:"Pressen anerkender ærligheden, og sagen lukkes hurtigt. Baglandet mister en stjerne, men slipper for en pinlig daglig afsløringsrunde." },
    forkerte:{ tekst:"Afvis det som absurde anklager, og hold fast i, at afhandlingen er din egen.",
               kon:"Afvisningen holder ikke, når dokumentationen vokser dag for dag. Pressen kører videre, universitetet trækker titlen tilbage, og din troværdighed smuldrer." },
    virkelighed:"Karl-Theodor zu Guttenberg kaldte først anklagerne absurde, men i takt med at beviserne voksede, måtte han træde tilbage, og universitetet fratog ham doktortitlen.",
    valgteRigtigt:false },

  { sag:"09", titel:"Rob Ford-sagen", based:"Canada · Rob Ford, Toronto · 2013",
    situation:"Der verserer en video, hvor byens borgmester ryger crack. Han bliver spurgt igen og igen, om videoen findes.",
    rigtige:{ tekst:"Erkend problemet, søg hjælp for misbrug, og vær ærlig om situationen.",
              kon:"Ydmygende, men pressen respekterer ærligheden, og fokus flytter fra skandale til sygdom. Baglandet kan stå ved en, der søger hjælp." },
    forkerte:{ tekst:"Benægt gentagne gange, at videoen overhovedet eksisterer.",
               kon:"Benægtelserne hober sig op, indtil politiet bekræfter, at de har videoen. Så står hver eneste benægtelse som en løgn, og pressen jubler over faldet." },
    virkelighed:"Rob Ford benægtede i månedsvis, at videoen fandtes, indtil politiet bekræftede den. Han indrømmede så at have røget crack, men nægtede at gå af; byrådet fratog ham størstedelen af hans beføjelser.",
    valgteRigtigt:false },

  { sag:"10", titel:"Nkandla-sagen", based:"Sydafrika · Jacob Zuma · 2014-16",
    situation:"Det kommer frem, at der er brugt et trecifret millionbeløb af offentlige midler på præsidentens private hjem, blandt andet en swimmingpool, der forklares som et brandsikkerheds-anlæg.",
    rigtige:{ tekst:"Erkend, at offentlige penge ikke burde være brugt sådan, og betal det omstridte tilbage.",
              kon:"Pressen og domstolene beroliges, og du fjerner den værste korruptionsvinkel. Baglandet ærgrer sig, men du undgår en forfatningskrise." },
    forkerte:{ tekst:"Afvis enhver fejl, og fasthold, at alt, også poolen, var nødvendig sikkerhed.",
               kon:"Bortforklaringerne bliver til landsdækkende satire, og pressen river dem fra hinanden. Til sidst slår landets højeste domstol fast, at du har svigtet forfatningen." },
    virkelighed:"Jacob Zuma afviste længe enhver fejl og fastholdt sikkerhedsforklaringen. Sydafrikas forfatningsdomstol fastslog i 2016, at han havde svigtet forfatningen, og han blev pålagt at betale en del af pengene tilbage.",
    valgteRigtigt:false }
];

const SLOTS = ["A","B"];

/* Spindoktor-ligaen, rangeret 1 (mest legendarisk) → 7. Score-krav: 10→#1 … 5→#6; under 5 → Rossen (#7) */
const LEGENDS = [
  { navn:"Grigorij Rasputin", pron:"han", flavor:"den sibiriske mystiker, der hviskede tsarer i øret og styrede udnævnelser fra kulissen",
    desc:"Sibirisk mystiker, der fik hypnotisk indflydelse på den russiske tsarfamilie i starten af 1900-tallet og reelt styrede politiske udnævnelser i kulissen, indtil han blev snigmyrdet." },
  { navn:"Steve Bannon", pron:"han", flavor:"kaos-ingeniøren bag Trumps 2016-sejr",
    desc:"Den højrepopulistiske, ideologiske bulldozer bag Donald Trumps valgsejr i 2016. Brugte aggressiv kulturkamp, internet-memes og bevidst kaos til at ryste det politiske etablissement." },
  { navn:"Alastair Campbell", pron:"han", flavor:"Blairs frygtede pressechef, manden bag selve ordet \u2019spin\u2019",
    desc:"Tony Blairs frygtede pressechef, der i 90'erne og 00'erne lagde navn til begrebet \u201Dspin\u201D. Kendt for sit aggressive temperament og et jerngreb om den britiske presse." },
  { navn:"Dominic Cummings", pron:"han", flavor:"Brexit-hjernen med foragt for embedsv\u00e6rket",
    desc:"Den uortodokse, systemkritiske hjerne bag Brexit-kampagnen og toprådgiver for Boris Johnson. Styrede Downing Street med en kaotisk, disruptiv filosofi og foragt for embedsværket." },
  { navn:"Karl Rove", pron:"han", flavor:"\u2019Bush\u2019s Brain\u2019 \u2014 datadrevet og nådesløs",
    desc:"Manden bag George W. Bush, kendt som \u201DBush's Brain\u201D. Revolutionerede amerikansk politik ved at bruge avanceret datastyring og aggressive, langsigtede strategier til at knuse modstanderne." },
  { navn:"Judy Smith", pron:"hun", flavor:"Washingtons mester i at begrave skandaler \u2014 forbilledet for tv-serien Scandal",
    desc:"USA's mest kendte krise-PR-ekspert og tidligere pressechef i Det Hvide Hus. Lever af at begrave topskandaler for politikere og var inspirationen til tv-serien Scandal." },
  { navn:"Martin Rossen", pron:"han", flavor:"Mette Frederiksens tidligere stabschef",
    desc:"Mette Frederiksens tætte stabschef under hendes første regering. Fik hidtil uset formel magt i regeringens topudvalg og blev af oppositionen udråbt som landets mægtigste, uvalgte politiker." }
];

let state = { i:0, history:[], rigtige:0, slots:{}, started:false };
const app = document.getElementById('app');
const recordEl = document.getElementById('record');
const segsEl = document.getElementById('segs');
const recLbl = document.getElementById('rec-lbl');
const caseCount = document.getElementById('casecount');

segsEl.innerHTML = LEVELS.map((_,i)=>`<span class="seg" id="seg-${i}"></span>`).join('');

function renderRecord(){
  LEVELS.forEach((_,i)=>{
    const seg = document.getElementById('seg-'+i);
    seg.className = 'seg' + (state.history[i]===true?' r':state.history[i]===false?' w':'');
    seg.textContent = state.history[i]===true ? '\u2713' : state.history[i]===false ? '\u2717' : '';
    if(i===state.i && state.history[i]===undefined) seg.classList.add('cur');
  });
  recLbl.innerHTML = `<b>${state.rigtige}</b> rigtige`;
}

function intro(){
  recordEl.style.display = 'none';
  caseCount.textContent = '';
  app.innerHTML = `
    <div class="panel fade">
      <div class="card">
        <div class="stamp land">Klassificeret</div>
        <div class="meta">Sagsmappe // kun til dine øjne</div>
        <h1 class="cover-title">Spin <span class="amp">&amp;</span> Skandale</h1>
        <div class="cover-sub">Krisemanageren</div>
        <div class="dossier">
          <div class="drow"><span class="dk">Klient</span><span class="redact" style="width:150px"></span></div>
          <div class="drow"><span class="dk">Din status</span><span class="dv">Praktikant uden referencer</span></div>
          <div class="drow"><span class="dk">Opgave</span><span class="dv">10 skandaler. Imponér ligaen.</span></div>
        </div>
        <p class="situation">Du er fuldstændig ny i branchen, en grøn praktikant i krisekommunikationens skyggeverden. Et sted derude sidder spindoktor-ligaen: historiens skarpeste manipulatorer, og de holder øje. Tackler du ti skandaler flot nok, ringer en af dem måske med dit livs jobtilbud.</p>
        <p class="situation" style="margin-top:12px">Hver sag giver dig to træk, ét rigtigt og ét forkert. De ser ens ud, og rækkefølgen skifter, så du må selv vurdere. Bagefter får du at vide, om du valgte rigtigt, og hvad de virkelige personer faktisk gjorde.</p>
        <button class="btn go big" id="start" style="margin-top:18px">📞 Tag telefonen ▸</button>
      </div>
    </div>`;
  document.getElementById('start').onclick = startGame;
}

function startGame(){
  state = { i:0, history:[], rigtige:0, slots:{}, started:true, deck:shuffle([...Array(LEVELS.length).keys()]) };
  recordEl.style.display = 'flex';
  renderRecord();
  showCase();
}

function shuffle(a){ a=a.slice(); for(let i=a.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [a[i],a[j]]=[a[j],a[i]]; } return a; }
function parseBased(b){ const p=b.split('\u00b7').map(s=>s.trim()); return {land:p[0]||'', person:p[1]||'', aar:p[p.length-1]||''}; }

function showCase(){
  const lv = LEVELS[state.deck[state.i]];
  const b = parseBased(lv.based);
  const nr = String(state.i+1).padStart(2,'0');
  const order = Math.random() < 0.5 ? ['rigtige','forkerte'] : ['forkerte','rigtige'];
  state.slots = { 0:order[0], 1:order[1] };
  caseCount.textContent = 'SAG ' + (state.i+1) + ' / 10';
  renderRecord();

  const buttons = [0,1].map(slot=>{
    const o = lv[order[slot]];
    return `<button class="choice" data-slot="${slot}"><span class="key">${SLOTS[slot]}</span><span>${o.tekst}</span></button>`;
  }).join('');

  app.innerHTML = `
    <div class="panel fade">
      <div class="card">
        <div class="stamp">Aktiv sag</div>
        <div class="meta">Sag nr. ${nr}</div>
        <div class="country">${b.land}</div>
        <h2 class="case-title">${lv.titel}</h2>
        <div class="cardsub">${b.person} · ${b.aar}</div>
        <p class="situation">${lv.situation}</p>
        <div class="prompt">Dit træk som konsulent</div>
        <div class="choices">${buttons}</div>
      </div>
    </div>`;
  app.querySelectorAll('.choice').forEach(b=>{ b.onclick = ()=> choose(parseInt(b.dataset.slot,10)); });
}

function choose(slot){
  const lv = LEVELS[state.deck[state.i]];
  const b = parseBased(lv.based);
  const nr = String(state.i+1).padStart(2,'0');
  const role = state.slots[slot];           // 'rigtige' | 'forkerte'
  const opt = lv[role];
  const good = (role === 'rigtige');

  state.history[state.i] = good;
  if(good) state.rigtige++;
  renderRecord();

  // hvad gjorde virkelighedens aktør?
  const realRight = lv.valgteRigtigt;
  const realTag = realRight
    ? `<span class="tag right">Virkeligheden valgte det rigtige</span>`
    : `<span class="tag wrong">Virkeligheden valgte spin</span>`;
  const cmp = (realRight === good) ? 'samme som dit valg' : 'modsat dit valg';

  app.innerHTML = `
    <div class="panel fade">
      <div class="card">
        <div class="stamp land" style="${good?'color:var(--green);border-color:var(--green)':''}">${good ? 'Rigtigt' : 'Forkert'}</div>
        <div class="meta">Sag nr. ${nr} · dit valg</div>
        <div class="country">${b.land}</div>
        <h2 class="case-title">${lv.titel}</h2>
        <div class="verdict ${good?'good':'bad'}"><span class="dot"></span>${good ? 'Rigtigt svar' : 'Forkert svar'}</div>
        <div class="vsub">Du valgte: ${good ? 'det ansvarlige træk' : 'spin-vejen'}</div>
        <p class="consequence">${opt.kon}</p>
        <div class="truth">
          <span class="lab">Sådan gik det i virkeligheden · ${b.aar}</span>
          ${realTag} <span class="cmp">· ${cmp}</span>
          <div style="margin-top:8px">${lv.virkelighed}</div>
        </div>
        <div class="actions" id="act"></div>
      </div>
    </div>`;

  const act = document.getElementById('act');
  if(state.i === LEVELS.length - 1){
    act.innerHTML = `<button class="btn go big" id="next">Se dit jobtilbud ▸</button>`;
    document.getElementById('next').onclick = ending;
  } else {
    act.innerHTML = `<button class="btn big" id="next">Næste sag ▸</button>`;
    document.getElementById('next').onclick = ()=>{ state.i++; showCase(); };
  }
}

const OIL_ART = `<svg width="100%" viewBox="0 0 680 300" role="img" xmlns="http://www.w3.org/2000/svg"><title>Olieboring ud for Grønland med isbjørne der flygter</title><desc>Satirisk nat-arktisk scene med boreplatform, oliepøl og tre isbjørne på revnet is under nordlys.</desc><defs><linearGradient id="oilsky" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#0d141a"/><stop offset="1" stop-color="#16242a"/></linearGradient></defs><rect x="0" y="0" width="680" height="198" fill="url(#oilsky)"/><path d="M0 58 C140 30,260 78,400 52 C520 32,610 70,680 50 L680 96 C600 70,520 104,400 82 C260 60,140 96,0 100 Z" fill="#6b9e78" opacity="0.12"/><path d="M0 72 C160 50,300 88,460 66 C560 52,640 78,680 66 L680 86 C620 72,560 96,460 80 C300 64,160 96,0 96 Z" fill="#7fb98e" opacity="0.08"/><circle cx="96" cy="56" r="30" fill="#e9eeec" opacity="0.10"/><circle cx="96" cy="56" r="21" fill="#e7ecea"/><circle cx="210" cy="30" r="1.3" fill="#cdd6d6" opacity="0.8"/><circle cx="268" cy="48" r="1.1" fill="#cdd6d6" opacity="0.7"/><circle cx="350" cy="26" r="1.3" fill="#cdd6d6" opacity="0.8"/><circle cx="438" cy="42" r="1.1" fill="#cdd6d6" opacity="0.7"/><circle cx="556" cy="30" r="1.2" fill="#cdd6d6" opacity="0.8"/><circle cx="624" cy="120" r="1.1" fill="#cdd6d6" opacity="0.6"/><path d="M0 198 L70 191 L150 196 L230 190 L320 197 L320 199 L0 199 Z" fill="#34474f" opacity="0.55"/><path d="M360 198 L430 192 L520 196 L600 191 L680 197 L680 199 L360 199 Z" fill="#34474f" opacity="0.45"/><rect x="0" y="198" width="680" height="102" fill="#11202a"/><rect x="0" y="197" width="680" height="2" fill="#26424d"/><path d="M470 201 L468 248" stroke="#243842" stroke-width="5" opacity="0.4"/><path d="M516 201 L516 252" stroke="#243842" stroke-width="5" opacity="0.4"/><path d="M562 201 L564 248" stroke="#243842" stroke-width="5" opacity="0.4"/><ellipse cx="514" cy="252" rx="104" ry="14" fill="#0a1014" opacity="0.85"/><ellipse cx="512" cy="249" rx="80" ry="8" fill="#2c5e52" opacity="0.20"/><path d="M448 201 L441 270" stroke="#1b2226" stroke-width="4" fill="none"/><path d="M496 201 L491 270" stroke="#1b2226" stroke-width="4" fill="none"/><path d="M540 201 L545 270" stroke="#1b2226" stroke-width="4" fill="none"/><path d="M586 201 L592 270" stroke="#1b2226" stroke-width="4" fill="none"/><path d="M448 214 L491 248 M496 214 L443 248 M540 214 L592 248 M586 214 L546 248" stroke="#2b343a" stroke-width="1.2" fill="none"/><rect x="432" y="191" width="160" height="10" fill="#1b2226"/><path d="M500 191 L516 78 M548 191 L532 78" stroke="#20282c" stroke-width="2.5" fill="none"/><path d="M500 188 L548 168 L502 150 L546 132 L504 114 L544 96 L516 80" stroke="#283036" stroke-width="1.2" fill="none"/><rect x="513" y="72" width="22" height="7" fill="#20282c"/><path d="M540 96 L612 78" stroke="#20282c" stroke-width="3" fill="none"/><ellipse cx="622" cy="40" rx="8" ry="6" fill="#6a7178" opacity="0.18"/><ellipse cx="632" cy="26" rx="11" ry="8" fill="#6a7178" opacity="0.13"/><ellipse cx="645" cy="12" rx="14" ry="10" fill="#6a7178" opacity="0.09"/><path d="M612 80 C606 64,618 60,614 44 C624 58,622 70,620 80 Z" fill="#d23b2e"/><path d="M613 80 C609 66,617 62,615 50 C621 62,619 72,618 80 Z" fill="#ee7a2e"/><path d="M614 80 C611 70,616 66,615 58 C619 68,617 74,617 80 Z" fill="#f4c64e"/><polygon points="216,260 270,254 330,258 328,273 260,277 218,270" fill="#cdd9dd"/><polygon points="216,260 270,254 330,258 328,261 270,257 218,263" fill="#eef4f5"/><polygon points="218,270 260,277 328,273 328,279 260,283 218,276" fill="#9fb1b7"/><polygon points="8,256 60,250 150,251 200,256 198,270 120,276 30,274 6,266" fill="#cdd9dd"/><polygon points="8,256 60,250 150,251 200,256 196,259 150,255 60,254 10,259" fill="#eef4f5"/><polygon points="6,266 30,274 120,276 198,270 198,277 120,282 30,280 6,272" fill="#9fb1b7"/><path d="M150 251 L156 262 L150 270" stroke="#7e9097" stroke-width="1.4" fill="none" opacity="0.7"/><g transform="translate(36,210)"><ellipse cx="34" cy="40" rx="30" ry="4" fill="#0a1116" opacity="0.35"/><rect x="45" y="24" width="7" height="16" rx="3" fill="#c9d3d2"/><rect x="15" y="24" width="7" height="16" rx="3" fill="#c9d3d2"/><ellipse cx="34" cy="19" rx="26" ry="13" fill="#eef1ec"/><ellipse cx="24" cy="11" rx="13" ry="10" fill="#eef1ec"/><polygon points="12,14 2,21 13,26 21,19" fill="#eef1ec"/><ellipse cx="8" cy="22" rx="8" ry="6.5" fill="#eef1ec"/><ellipse cx="1" cy="24" rx="5" ry="3.6" fill="#e4e9e7"/><circle cx="11" cy="14" r="2.6" fill="#eef1ec"/><rect x="22" y="25" width="7" height="15" rx="3" fill="#f5f7f4"/><rect x="51" y="25" width="7" height="15" rx="3" fill="#f5f7f4"/><ellipse cx="34" cy="27" rx="22" ry="6" fill="#d9e0e0" opacity="0.55"/><circle cx="-3" cy="24" r="1.3" fill="#20272b"/></g><g transform="translate(118,214) scale(0.9)"><ellipse cx="34" cy="40" rx="30" ry="4" fill="#0a1116" opacity="0.32"/><rect x="45" y="24" width="7" height="16" rx="3" fill="#c9d3d2"/><rect x="15" y="24" width="7" height="16" rx="3" fill="#c9d3d2"/><ellipse cx="34" cy="19" rx="26" ry="13" fill="#eef1ec"/><ellipse cx="24" cy="11" rx="13" ry="10" fill="#eef1ec"/><polygon points="12,14 2,21 13,26 21,19" fill="#eef1ec"/><ellipse cx="8" cy="22" rx="8" ry="6.5" fill="#eef1ec"/><ellipse cx="1" cy="24" rx="5" ry="3.6" fill="#e4e9e7"/><circle cx="11" cy="14" r="2.6" fill="#eef1ec"/><rect x="22" y="25" width="7" height="15" rx="3" fill="#f5f7f4"/><rect x="51" y="25" width="7" height="15" rx="3" fill="#f5f7f4"/><ellipse cx="34" cy="27" rx="22" ry="6" fill="#d9e0e0" opacity="0.55"/><circle cx="-3" cy="24" r="1.3" fill="#20272b"/></g><g transform="translate(252,216) scale(0.82)"><ellipse cx="34" cy="40" rx="30" ry="4" fill="#0a1116" opacity="0.30"/><rect x="45" y="24" width="7" height="16" rx="3" fill="#c9d3d2"/><rect x="15" y="24" width="7" height="16" rx="3" fill="#c9d3d2"/><ellipse cx="34" cy="19" rx="26" ry="13" fill="#eef1ec"/><ellipse cx="24" cy="11" rx="13" ry="10" fill="#eef1ec"/><polygon points="12,14 2,21 13,26 21,19" fill="#eef1ec"/><ellipse cx="8" cy="22" rx="8" ry="6.5" fill="#eef1ec"/><ellipse cx="1" cy="24" rx="5" ry="3.6" fill="#e4e9e7"/><circle cx="11" cy="14" r="2.6" fill="#eef1ec"/><rect x="22" y="25" width="7" height="15" rx="3" fill="#f5f7f4"/><rect x="51" y="25" width="7" height="15" rx="3" fill="#f5f7f4"/><ellipse cx="34" cy="27" rx="22" ry="6" fill="#d9e0e0" opacity="0.55"/><circle cx="-3" cy="24" r="1.3" fill="#20272b"/></g></svg>`;

function ending(){
  const r = state.rigtige;
  const recIdx = (r >= 5) ? (10 - r) : 6;   // 10→Rasputin … 5→Judy Smith ; under 5 → Rossen
  const rec = LEGENDS[recIdx];
  const farve  = (r >= 5) ? "var(--green)" : "var(--red)";
  const border = (r >= 5) ? "var(--green-dk)" : "var(--red-dk)";

  let txt;
  if(r >= 5){
    const S = rec.pron==='hun' ? 'Hun' : 'Han';
    const s = rec.pron==='hun' ? 'hun' : 'han';
    txt = `Din telefon ringer. Det er <b>${rec.navn}</b>, ${rec.flavor}. ${S} har fulgt din håndtering af alle ti sager og er imponeret: ${r} ud af 10 reddet. Nu vil ${s} have dig på en opgave. En virksomhed skal have den grønlandske regering til at åbne et ellers fredet område, så der kan suges olie op, og de mangler præcis din slags tæft. Lønnen er astronomisk. Samvittigheden er valgfri.`;
  } else {
    txt = `Din telefon ringer, men det er ikke en af de helt store legender. Det er <b>Martin Rossen</b>. Du imponerede ikke ligaen denne gang: ${r} ud af 10 rakte ikke til de internationale stjerner. Til gengæld kan Rossen bruge dig, han skal have kulkraft tilbage på sporet i EU, og det kræver en, der ikke stiller for mange spørgsmål. Velkommen i maskinrummet. Diskret, som altid.`;
  }

  const banner = (r >= 5) ? '<div class="art-banner">' + OIL_ART + '</div>' : '';
  const leagueRows = LEGENDS.map((L,i)=>`
    <div class="leg${i===recIdx?' me':''}">
      <div class="rk">${i+1}</div>
      <div>
        <div class="nm">${L.navn}${i===recIdx?'<span class="you">Ringede til dig</span>':''}</div>
        <div class="ds">${L.desc}</div>
      </div>
    </div>`).join('');

  caseCount.textContent = 'AUDITION SLUT';
  app.innerHTML = `
    <div class="screen fade" style="border-color:${border}">
      <div class="kicker" style="color:${farve}">Ligaen har set dig</div>
      <div class="bigscore" style="color:${farve}">${r} / 10</div>
      <div class="scoreline">sager reddet</div>
      <h2 class="rank-badge" style="color:${farve};margin-top:18px">${rec.navn} ringer</h2>
      <p class="lede">${txt}</p>
      ${banner}
      <div class="league">
        <h3>Spindoktor-ligaen</h3>
        <div class="lsub">Jo flere sager du redder, jo højere i ligaen rækker du. Her er de andre, du kunne have imponeret, eller skuffet.</div>
        ${leagueRows}
      </div>
      <div class="actions" style="justify-content:flex-start;margin-top:22px"><button class="btn go big" id="again">Tag en ny runde ▸</button></div>
    </div>`;
  document.getElementById('again').onclick = startGame;
}

document.addEventListener('keydown', e=>{
  if(!state.started) return;
  const idx = SLOTS.indexOf(e.key.toUpperCase());
  if(idx >= 0){
    const btn = app.querySelector('.choice[data-slot="'+idx+'"]');
    if(btn) btn.click();
  }
});

intro();
</script>
</body>
</html>
