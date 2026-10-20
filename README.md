# <!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="theme-color" content="#11161c" />
  <meta name="color-scheme" content="light" />
  <title>TEMPO INSTRUMENTS — Precision Timing Test Bench</title>
  <meta name="description" content="TEMPO INSTRUMENTS is an interactive horological test bench. Open the calibre, sign off four modules, file a build order and hold the escapement in spec. Every interaction makes its own sound." />
  <meta property="og:title" content="TEMPO INSTRUMENTS — Precision Timing Test Bench" />
  <meta property="og:description" content="Every tick is a test. An interactive calibre, four modules, a build order and an escapement rig — all scored, all sounding live." />
  <meta property="og:type" content="website" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Archivo+Black&family=Archivo:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="css/style.css" />
  <link rel="stylesheet" href="css/industrial.css" />
  <link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'%3E%3Crect width='64' height='64' fill='%2311161c'/%3E%3Crect x='8' y='8' width='48' height='48' fill='none' stroke='%23e23326' stroke-width='3'/%3E%3Cpath d='M20 20h24M32 20v26' stroke='%23e7e2d6' stroke-width='4'/%3E%3C/svg%3E" />
</head>
<body class="is-locked">

  <div class="grain" aria-hidden="true"></div>
  <div class="vignette" aria-hidden="true"></div>
  <div class="loupe" id="loupe" aria-hidden="true"><span></span></div>

  <!-- ══════════════════════ GATE ══════════════════════ -->
  <div class="gate" id="gate" role="dialog" aria-modal="true" aria-labelledby="gate-title">
    <div class="gate__bg" aria-hidden="true">
      <div class="gate__orbit gate__orbit--1"></div>
      <div class="gate__orbit gate__orbit--2"></div>
      <div class="gate__orbit gate__orbit--3"></div>
      <div class="gate__gear" id="gate-gear"></div>
    </div>
    <div class="gate__inner">
      <div class="gate__copy-col">
        <div class="gate__mark">
          <span class="gate__monogram"><i>T</i></span>
          <span class="gate__since">TEMPO INSTRUMENTS<br />PRECISION TIMING DIVISION</span>
        </div>
        <p class="eyebrow gate__eyebrow"><i></i> Flight clearance · Bench 001</p>
        <h1 class="gate__title" id="gate-title">EVERY TICK<br /><em>IS A TEST.</em></h1>
        <p class="gate__copy">A mechanical chronograph on the bench. Open the calibre, sign off its modules, file a build order, and hold the escapement in spec. Every switch makes its own sound.</p>
        <div class="gate__actions">
          <button class="btn btn--gold" id="enter-sound" type="button">
            <span class="btn__label">Power on + audio</span>
            <span class="btn__arrow" aria-hidden="true">→</span>
          </button>
          <button class="btn btn--ghost" id="enter-mute" type="button">
            <span class="btn__label">Run silent</span>
          </button>
        </div>
        <p class="gate__note"><span class="pulse-dot"></span> Audio synthesised in-browser. No samples. Calibrate your headphones.</p>
        <div class="gate__foot">
          <span>CAL. T-01</span><span>28,800 A/H</span><span>11 MODULES</span><span>BENCH NO. 001</span>
        </div>
      </div>

      <div class="gate__console" aria-hidden="true">
        <div class="console__top"><span>BENCH POWER / CTRL-01</span><span class="console__led"></span></div>
        <div class="console__display" id="gate-display">----</div>
        <div class="console__keypad">
          <button type="button" data-key="1">1</button>
          <button type="button" data-key="2">2</button>
          <button type="button" data-key="3">3</button>
          <button type="button" data-key="4">4</button>
          <button type="button" data-key="5">5</button>
          <button type="button" data-key="6">6</button>
          <button type="button" data-key="7">7</button>
          <button type="button" data-key="8">8</button>
          <button type="button" data-key="9">9</button>
          <button type="button" data-key="*">*</button>
          <button type="button" data-key="0">0</button>
          <button type="button" data-key="enter" class="is-enter">ENTER</button>
        </div>
        <p class="console__hint">ENTER CODE 1897 FOR SERVICE</p>
        <div class="console__stripe"></div>
        <span class="console__tag">REMOVE BEFORE FLIGHT</span>
      </div>
    </div>
  </div>

  <!-- ══════════════════════ CHROME ══════════════════════ -->
  <header class="topbar" id="topbar">
    <a class="brand" href="#top" aria-label="TEMPO INSTRUMENTS — back to top">
      <span class="brand__word">TEMPO</span>
      <span class="brand__sub">INSTRUMENTS</span>
      <span class="brand__reg">®</span>
    </a>
    <nav class="nav" aria-label="Sections">
      <a href="#anatomy" data-nav="anatomy"><b>01</b> Teardown</a>
      <a href="#complications" data-nav="complications"><b>02</b> Modules</a>
      <a href="#commission" data-nav="commission"><b>03</b> Build</a>
      <a href="#trial" data-nav="trial"><b>04</b> Test</a>
      <a href="#ledger" data-nav="ledger"><b>05</b> Log</a>
    </nav>
    <div class="hud">
      <div class="hud__rank">
        <span class="hud__lv" id="level-num">I</span>
        <span class="hud__meta">
          <span class="hud__label">CLEARANCE</span>
          <span class="hud__name" id="level-name">Cadet</span>
        </span>
      </div>
      <div class="hud__xp">
        <div class="hud__bar" aria-hidden="true"><i id="xp-fill"></i></div>
        <span class="hud__xp-text" id="xp-text">0 / 90 TP</span>
      </div>
      <button class="sound-toggle" id="sound-toggle" type="button" aria-pressed="false" aria-label="Toggle sound">
        <span class="sound-bars" aria-hidden="true"><i></i><i></i><i></i><i></i></span>
        <span class="sound-label" aria-hidden="true">AUDIO</span>
      </button>
    </div>
    <div class="progress" aria-hidden="true"><i id="progress-fill"></i></div>
  </header>

  <main id="top">

    <!-- ══════════════════════ HERO ══════════════════════ -->
    <section class="hero" id="hero">
      <div class="hero__grid" aria-hidden="true"></div>
      <div class="hero__watermark" aria-hidden="true">T</div>
      <div class="hero__orbit" aria-hidden="true">
        <div class="orbit-ring orbit-ring--a"></div>
        <div class="orbit-ring orbit-ring--b"></div>
        <div class="orbit-ring orbit-ring--c"></div>
      </div>

      <div class="hero__copy">
        <p class="eyebrow"><i></i> A horological arcade · six movements</p>
        <h1 class="hero__title"><span>TEM</span><span>PO</span></h1>
        <p class="hero__lede">A watch is a <em>game of microseconds.</em> Here, it is also a game of points. Scroll to take the calibre apart. Hover or tap to hear it. Keep the beat to earn your rank.</p>
        <div class="hero__actions">
          <a class="btn btn--gold" href="#anatomy" data-cta="begin">
            <span class="btn__label">Enter the calibre</span><span class="btn__arrow" aria-hidden="true">↓</span>
          </a>
          <button class="text-link" type="button" id="how-it-scores">How it scores <span aria-hidden="true">↗</span></button>
        </div>
        <dl class="hero__stats">
          <div><dt>Components</dt><dd>312</dd></div>
          <div><dt>Beat rate</dt><dd>28,800<span> a/h</span></dd></div>
          <div><dt>Reserve</dt><dd>72<span> h</span></dd></div>
          <div><dt>Your rank</dt><dd class="gold" id="hero-rank">I — Apprentice</dd></div>
        </dl>
      </div>

      <div class="hero__stage">
        <div class="hero__watch" id="hero-watch" aria-label="A live mechanical watch showing the current time"></div>
        <div class="hero__tag hero__tag--a"><b>01</b><span>Calibre T-01</span></div>
        <div class="hero__tag hero__tag--b"><b>N° 001</b><span>Genève</span></div>
        <p class="hero__hint"><span class="pulse-dot"></span> The dial is live · Calibre T-01</p>
      </div>

      <div class="hero__scroll" aria-hidden="true">
        <span>Scroll to disassemble</span>
        <i></i>
      </div>
    </section>

    <!-- ══════════════════════ TICKER ══════════════════════ -->
    <div class="ticker" aria-hidden="true">
      <div class="ticker__track">
        <span>28,800 vibrations per hour <b>✦</b> 312 components <b>✦</b> 72-hour power reserve <b>✦</b> free-sprung balance <b>✦</b> hand-finished in Genève <b>✦</b> every tick is a point <b>✦</b></span>
        <span>28,800 vibrations per hour <b>✦</b> 312 components <b>✦</b> 72-hour power reserve <b>✦</b> free-sprung balance <b>✦</b> hand-finished in Genève <b>✦</b> every tick is a point <b>✦</b></span>
      </div>
    </div>

    <!-- ══════════════════════ ANATOMY ══════════════════════ -->
    <section class="anatomy" id="anatomy" data-section="anatomy">
      <div class="anatomy__sticky">
        <div class="anatomy__copy">
          <p class="eyebrow"><i></i> Trial II — The Anatomy</p>
          <h2 class="section-title">Take it apart.<br /><em>Every part sings.</em></h2>
          <p class="section-copy">A calibre is a city of 312 components. Scroll to explode the T-01 and log its eleven vital organs — each one has its own note, its own job, its own way of failing beautifully.</p>

          <div class="parts">
            <div class="parts__head">
              <span>Assembly log</span>
              <span class="parts__count"><b id="anatomy-count">00</b> / 11</span>
            </div>
            <ol class="parts__list" id="parts-list">
              <li data-part="mainplate"><span class="parts__idx">01</span><span class="parts__name">Mainplate</span><span class="parts__spec">German silver</span></li>
              <li data-part="caseback"><span class="parts__idx">02</span><span class="parts__name">Sapphire caseback</span><span class="parts__spec">N° 001</span></li>
              <li data-part="rotor"><span class="parts__idx">03</span><span class="parts__name">Rotor</span><span class="parts__spec">22k gold</span></li>
              <li data-part="barrel"><span class="parts__idx">04</span><span class="parts__name">Mainspring barrel</span><span class="parts__spec">72 h reserve</span></li>
              <li data-part="bridge"><span class="parts__idx">05</span><span class="parts__name">Barrel bridge</span><span class="parts__spec">Côtes de Genève</span></li>
              <li data-part="train"><span class="parts__idx">06</span><span class="parts__name">Gear train</span><span class="parts__spec">Four wheels</span></li>
              <li data-part="escape"><span class="parts__idx">07</span><span class="parts__name">Escape wheel</span><span class="parts__spec">Swiss lever</span></li>
              <li data-part="balance"><span class="parts__idx">08</span><span class="parts__name">Balance wheel</span><span class="parts__spec">4 Hz · free-sprung</span></li>
              <li data-part="dial"><span class="parts__idx">09</span><span class="parts__name">Dial</span><span class="parts__spec">Grand feu</span></li>
              <li data-part="hands"><span class="parts__idx">10</span><span class="parts__name">Hands</span><span class="parts__spec">Dauphine · 18k</span></li>
              <li data-part="crystal"><span class="parts__idx">11</span><span class="parts__name">Crystal</span><span class="parts__spec">Box-domed sapphire</span></li>
            </ol>
          </div>
        </div>

        <div class="anatomy__stage">
          <div class="movement" id="movement">
            <div class="movement__frame">
              <div class="movement__svg" id="movement-svg"></div>
              <div class="movement__corner movement__corner--tl" aria-hidden="true"></div>
              <div class="movement__corner movement__corner--tr" aria-hidden="true"></div>
              <div class="movement__corner movement__corner--bl" aria-hidden="true"></div>
              <div class="movement__corner movement__corner--br" aria-hidden="true"></div>
              <div class="movement__scale" aria-hidden="true"><span>Ø 31.2 mm</span><span>SCALE 4:1</span></div>
            </div>
            <div class="movement__readout">
              <span class="movement__readout-idx" id="part-index">00</span>
              <span class="movement__readout-body">
                <b id="part-name">Scroll to disassemble</b>
                <span id="part-spec">11 components · 312 parts in total</span>
              </span>
              <span class="movement__readout-tick" aria-hidden="true"><i></i><i></i><i></i></span>
            </div>
            <div class="movement__progress" aria-hidden="true"><i id="anatomy-fill"></i></div>
          </div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════ COMPLICATIONS ══════════════════════ -->
    <section class="complications section" id="complications" data-section="complications">
      <div class="section__head">
        <div>
          <p class="eyebrow"><i></i> Trial III — The Complications</p>
          <h2 class="section-title">Four ways to<br /><em>lose track of time.</em></h2>
        </div>
        <div class="section__aside">
          <p class="section-copy">Complications are mechanisms that do more than tell the time — they argue with gravity, remember leap years, chart the moon, and speak the hour. Hover to wake them. Click to log them and hear their signature.</p>
          <span class="logged-count"><b id="comp-count">0</b> / 4 logged</span>
        </div>
      </div>

      <div class="comp-grid">
        <article class="comp-card" data-complication="tourbillon" data-tone="high" tabindex="0" role="button" aria-pressed="false" aria-label="Log the Tourbillon complication">
          <div class="comp-card__top">
            <span class="comp-card__no">01</span>
            <span class="comp-card__status">Tap to log</span>
          </div>
          <div class="comp-card__visual">
            <svg viewBox="0 0 220 220" aria-hidden="true">
              <circle cx="110" cy="110" r="90" class="cx-ring cx-ring--dim" />
              <circle cx="110" cy="110" r="78" class="cx-ring" />
              <circle cx="110" cy="110" r="70" class="cx-ring cx-ring--teeth" />
              <g class="cx-tourbillon">
                <circle cx="110" cy="110" r="60" class="cx-ring cx-ring--gold" />
                <circle cx="110" cy="110" r="46" class="cx-ring cx-ring--dim" />
                <line x1="110" y1="50" x2="110" y2="170" class="cx-line" />
                <line x1="58" y1="80" x2="162" y2="140" class="cx-line" />
                <line x1="58" y1="140" x2="162" y2="80" class="cx-line" />
                <circle cx="110" cy="110" r="30" class="cx-ring" />
                <circle cx="110" cy="110" r="20" class="cx-ring cx-ring--dim" />
                <circle cx="110" cy="110" r="8" class="cx-fill-gold" />
                <circle cx="110" cy="84" r="5" class="cx-fill-cream" />
                <circle cx="130" cy="122" r="3" class="cx-fill-cream" opacity=".7" />
              </g>
              <circle cx="110" cy="110" r="3.5" class="cx-fill-cream" />
            </svg>
          </div>
          <div class="comp-card__body">
            <h3>Tourbillon</h3>
            <p class="comp-card__sub">Gravity, corrected.</p>
            <p class="comp-card__desc">A cage rotates the escapement once a minute so that positional error averages itself out of existence.</p>
            <div class="comp-card__foot"><span>60 s / rotation</span><span class="comp-card__action">Log <b>+40</b></span></div>
          </div>
          <span class="comp-card__stamp">Logged</span>
        </article>

        <article class="comp-card" data-complication="perpetual" data-tone="mid" tabindex="0" role="button" aria-pressed="false" aria-label="Log the Perpetual Calendar complication">
          <div class="comp-card__top">
            <span class="comp-card__no">02</span>
            <span class="comp-card__status">Tap to log</span>
          </div>
          <div class="comp-card__visual">
            <svg viewBox="0 0 220 220" aria-hidden="true">
              <circle cx="110" cy="110" r="90" class="cx-ring cx-ring--dim" />
              <circle cx="110" cy="110" r="78" class="cx-ring" />
              <circle cx="110" cy="110" r="72" class="cx-ring cx-ring--teeth" />
              <circle cx="110" cy="110" r="64" class="cx-ring cx-ring--dash" />
              <text x="110" y="54" class="cx-micro">PERPETUAL</text>
              <rect x="62" y="76" width="96" height="68" rx="4" class="cx-aperture" />
              <text x="110" y="124" class="cx-digit cx-digit--big" data-today="day">19</text>
              <rect x="31" y="96" width="23" height="18" rx="2" class="cx-aperture cx-aperture--small" />
              <text x="42.5" y="108" class="cx-mini" data-today="weekday">THU</text>
              <rect x="166" y="96" width="23" height="18" rx="2" class="cx-aperture cx-aperture--small" />
              <text x="177.5" y="108" class="cx-mini" data-today="month">OCT</text>
            </svg>
          </div>
          <div class="comp-card__body">
            <h3>Perpetual Calendar</h3>
            <p class="comp-card__sub">Time, remembered.</p>
            <p class="comp-card__desc">A mechanical memory of every 28-, 30- and 31-day month — and of February, even when it forgets itself.</p>
            <div class="comp-card__foot"><span>Until 2100</span><span class="comp-card__action">Log <b>+40</b></span></div>
          </div>
          <span class="comp-card__stamp">Logged</span>
        </article>

        <article class="comp-card" data-complication="moonphase" data-tone="airy" tabindex="0" role="button" aria-pressed="false" aria-label="Log the Moonphase complication">
          <div class="comp-card__top">
            <span class="comp-card__no">03</span>
            <span class="comp-card__status">Tap to log</span>
          </div>
          <div class="comp-card__visual">
            <svg viewBox="0 0 220 220" aria-hidden="true">
              <defs>
                <clipPath id="moon-aperture"><rect x="44" y="78" width="132" height="74" rx="37" /></clipPath>
              </defs>
              <circle cx="110" cy="110" r="90" class="cx-ring cx-ring--dim" />
              <circle cx="110" cy="110" r="78" class="cx-ring" />
              <circle cx="110" cy="110" r="70" class="cx-ring cx-ring--teeth" />
              <g clip-path="url(#moon-aperture)">
                <rect x="44" y="78" width="132" height="74" fill="#101623" />
                <circle cx="110" cy="112" r="45" fill="#c9a86a" opacity=".07" />
                <circle cx="70" cy="98" r="1.6" fill="#efe9dc" opacity=".7" />
                <circle cx="158" cy="112" r="1.2" fill="#efe9dc" opacity=".45" />
                <circle cx="140" cy="92" r="1" fill="#efe9dc" opacity=".7" />
                <circle cx="90" cy="142" r="1.3" fill="#efe9dc" opacity=".35" />
                <circle cx="126" cy="136" r="1.1" fill="#efe9dc" opacity=".55" />
                <circle cx="152" cy="132" r="1.5" fill="#efe9dc" opacity=".4" />
                <circle cx="60" cy="126" r="1" fill="#efe9dc" opacity=".35" />
                <g class="cx-moon">
                  <circle cx="108" cy="116" r="28" fill="#efe9dc" />
                  <circle cx="120" cy="107" r="26" fill="#101623" opacity=".94" />
                </g>
              </g>
              <rect x="44" y="78" width="132" height="74" rx="37" class="cx-aperture-frame" />
              <circle cx="110" cy="110" r="98" class="cx-ring cx-ring--dash" />
            </svg>
          </div>
          <div class="comp-card__body">
            <h3>Moonphase</h3>
            <p class="comp-card__sub">The night, mechanised.</p>
            <p class="comp-card__desc">A 59-tooth wheel charts the lunar cycle with such patience that it drifts by a single day every 122 years.</p>
            <div class="comp-card__foot"><span>29.53 days</span><span class="comp-card__action">Log <b>+40</b></span></div>
          </div>
          <span class="comp-card__stamp">Logged</span>
        </article>

        <article class="comp-card" data-complication="repeater" data-tone="low" tabindex="0" role="button" aria-pressed="false" aria-label="Log the Minute Repeater complication">
          <div class="comp-card__top">
            <span class="comp-card__no">04</span>
            <span class="comp-card__status">Tap to log</span>
          </div>
          <div class="comp-card__visual">
            <svg viewBox="0 0 220 220" aria-hidden="true">
              <circle cx="110" cy="110" r="90" class="cx-ring cx-ring--dim" />
              <circle cx="110" cy="110" r="78" class="cx-ring" />
              <circle cx="110" cy="110" r="70" class="cx-ring cx-ring--teeth" />
              <circle cx="110" cy="110" r="34" class="cx-ring cx-ring--dim" />
              <path d="M58 132a52 52 0 0 1 104 0" class="cx-gong" />
              <path d="M76 132a34 34 0 0 1 68 0" class="cx-gong cx-gong--2" />
              <g class="cx-hammer cx-hammer--l">
                <line x1="76" y1="112" x2="54" y2="132" class="cx-line" />
                <circle cx="54" cy="132" r="7" class="cx-hammer-head" />
                <circle cx="76" cy="112" r="2.5" class="cx-fill-cream" />
              </g>
              <g class="cx-hammer cx-hammer--r">
                <line x1="144" y1="112" x2="166" y2="132" class="cx-line" />
                <circle cx="166" cy="132" r="7" class="cx-hammer-head" />
                <circle cx="144" cy="112" r="2.5" class="cx-fill-cream" />
              </g>
              <circle cx="110" cy="110" r="12" class="cx-ring cx-ring--gold" />
              <circle cx="110" cy="110" r="4" class="cx-fill-gold" />
              <text x="110" y="160" class="cx-micro">MINUTE REPEATER</text>
            </svg>
          </div>
          <div class="comp-card__body">
            <h3>Minute Repeater</h3>
            <p class="comp-card__sub">Time, spoken.</p>
            <p class="comp-card__desc">Two hammers strike two gongs to chime the hours, the quarters and the minutes — time you can hear in the dark.</p>
            <div class="comp-card__foot"><span>2 gongs · 4 notes</span><span class="comp-card__action">Log <b>+40</b></span></div>
          </div>
          <span class="comp-card__stamp">Logged</span>
        </article>
      </div>
    </section>

    <!-- ══════════════════════ COMMISSION ══════════════════════ -->
    <section class="commission section" id="commission" data-section="commission">
      <div class="section__head">
        <div>
          <p class="eyebrow"><i></i> Trial IV — The Commission</p>
          <h2 class="section-title">Build your<br /><em>own calibre.</em></h2>
        </div>
        <div class="section__aside">
          <p class="section-copy">Case, dial, strap: three decisions, each with its own material voice. Every change updates the piece and the ledger. When it is right, seal it.</p>
          <span class="logged-count"><b id="commission-count">0</b> / 3 decisions</span>
        </div>
      </div>

      <div class="commission__grid">
        <div class="commission__preview">
          <div class="commission__plinth">
            <div class="commission__watch" id="commission-watch"></div>
          </div>
          <div class="commission__specsheet">
            <div class="spec-row"><span>Reference</span><b id="spec-ref">T-01 / ST / IV</b></div>
            <div class="spec-row"><span>Case</span><b id="spec-case">Brushed steel</b></div>
            <div class="spec-row"><span>Dial</span><b id="spec-dial">Ivory guilloché</b></div>
            <div class="spec-row"><span>Strap</span><b id="spec-strap">Black calf</b></div>
            <div class="spec-row spec-row--price"><span>Commission</span><b id="spec-price">CHF 24,800</b></div>
          </div>
        </div>

        <div class="commission__builder">
          <div class="builder__group" data-group="case">
            <div class="builder__head"><span class="builder__no">01</span><h3>The case</h3><span class="builder__val" data-value-label="case">Brushed steel</span></div>
            <div class="swatches">
              <button class="swatch is-active" type="button" data-group="case" data-value="steel" data-label="Brushed steel" aria-pressed="true"><span class="swatch__chip" style="--sw:#c9ced4; --sw2:#7e858c"></span><span class="swatch__name">Steel</span></button>
              <button class="swatch" type="button" data-group="case" data-value="gold" data-label="Yellow gold" aria-pressed="false"><span class="swatch__chip" style="--sw:#dcb871; --sw2:#8d6b31"></span><span class="swatch__name">Gold</span></button>
              <button class="swatch" type="button" data-group="case" data-value="rose" data-label="Rose gold" aria-pressed="false"><span class="swatch__chip" style="--sw:#c98d74; --sw2:#7d4e3d"></span><span class="swatch__name">Rose</span></button>
              <button class="swatch" type="button" data-group="case" data-value="dlc" data-label="Black DLC" aria-pressed="false"><span class="swatch__chip" style="--sw:#3a3b3f; --sw2:#111113"></span><span class="swatch__name">DLC</span></button>
            </div>
          </div>

          <div class="builder__group" data-group="dial">
            <div class="builder__head"><span class="builder__no">02</span><h3>The dial</h3><span class="builder__val" data-value-label="dial">Ivory guilloché</span></div>
            <div class="swatches">
              <button class="swatch is-active" type="button" data-group="dial" data-value="ivory" data-label="Ivory guilloché" aria-pressed="true"><span class="swatch__chip" style="--sw:#ece2ce; --sw2:#bfb29a"></span><span class="swatch__name">Ivory</span></button>
              <button class="swatch" type="button" data-group="dial" data-value="onyx" data-label="Onyx sunburst" aria-pressed="false"><span class="swatch__chip" style="--sw:#232326; --sw2:#08080a"></span><span class="swatch__name">Onyx</span></button>
              <button class="swatch" type="button" data-group="dial" data-value="salmon" data-label="Salmon guilloché" aria-pressed="false"><span class="swatch__chip" style="--sw:#d99b83; --sw2:#a96650"></span><span class="swatch__name">Salmon</span></button>
              <button class="swatch" type="button" data-group="dial" data-value="midnight" data-label="Midnight blue" aria-pressed="false"><span class="swatch__chip" style="--sw:#1d2c46; --sw2:#0c1424"></span><span class="swatch__name">Blue</span></button>
            </div>
          </div>

          <div class="builder__group" data-group="strap">
            <div class="builder__head"><span class="builder__no">03</span><h3>The strap</h3><span class="builder__val" data-value-label="strap">Black calf</span></div>
            <div class="swatches">
              <button class="swatch is-active" type="button" data-group="strap" data-value="black" data-label="Black calf" aria-pressed="true"><span class="swatch__chip" style="--sw:#202022; --sw2:#0b0b0c"></span><span class="swatch__name">Black</span></button>
              <button class="swatch" type="button" data-group="strap" data-value="cognac" data-label="Cognac calf" aria-pressed="false"><span class="swatch__chip" style="--sw:#8a5632; --sw2:#4d2c18"></span><span class="swatch__name">Cognac</span></button>
              <button class="swatch" type="button" data-group="strap" data-value="oxblood" data-label="Oxblood calf" aria-pressed="false"><span class="swatch__chip" style="--sw:#63222b; --sw2:#331016"></span><span class="swatch__name">Oxblood</span></button>
              <button class="swatch" type="button" data-group="strap" data-value="bracelet" data-label="Steel bracelet" aria-pressed="false"><span class="swatch__chip" style="--sw:#c3c9d0; --sw2:#767e86"></span><span class="swatch__name">Bracelet</span></button>
            </div>
          </div>

          <div class="builder__total">
            <div>
              <span class="builder__total-label">Your commission</span>
              <span class="builder__total-value" id="total-price">CHF 24,800</span>
            </div>
            <button class="btn btn--gold btn--wide" id="seal-btn" type="button">
              <span class="btn__label">Seal the commission</span><span class="btn__arrow" aria-hidden="true">→</span>
            </button>
            <p class="builder__note" id="builder-note">Each material has a voice. Listen as you choose.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════ TRIAL ══════════════════════ -->
    <section class="trial section" id="trial" data-section="trial">
      <div class="section__head">
        <div>
          <p class="eyebrow"><i></i> Trial V — The Escapement</p>
          <h2 class="section-title">Keep the<br /><em>beat.</em></h2>
        </div>
        <div class="section__aside">
          <p class="section-copy">The balance swings through the target twelve times. Press <b class="kbd">BEAT</b> — or the space bar — as the needle crosses the top mark. Every clean pass raises the pitch. Miss, and the room goes quiet.</p>
          <span class="logged-count">Best combo <b id="game-best-stat">x0</b></span>
        </div>
      </div>

      <div class="game" id="game">
        <div class="game__panel">
          <div class="game__dial" id="game-dial">
            <div class="game__ticks" id="game-ticks" aria-hidden="true"></div>
            <div class="game__target" aria-hidden="true">
              <svg viewBox="0 0 480 480">
                <circle class="game__target-track" cx="240" cy="240" r="222" />
                <circle class="game__target-arc" cx="240" cy="240" r="210" pathLength="100" stroke-dasharray="17.22 82.78" transform="rotate(-121 240 240)" />
              </svg>
            </div>
            <div class="game__progress" aria-hidden="true">
              <svg viewBox="0 0 480 480">
                <circle id="game-progress" class="game__progress-arc" cx="240" cy="240" r="233" pathLength="100" stroke-dasharray="0 100" transform="rotate(-90 240 240)" />
              </svg>
            </div>
            <div class="game__needle" id="game-needle" aria-hidden="true"><span></span></div>
            <div class="game__center" aria-hidden="true">
              <div class="game__balance"><i></i><i></i></div>
              <div class="game__combo"><b id="game-combo">x1</b><span>combo</span></div>
            </div>
            <div class="game__flash" id="game-flash" aria-hidden="true"></div>
            <div class="game__veil" id="game-veil">
              <span class="game__veil-eyebrow">Calibre T-01 · 4 Hz</span>
              <h3>Twelve clean beats.</h3>
              <p>Hit inside the gold arc. No points for guessing.</p>
              <button class="btn btn--gold" id="game-start" type="button"><span class="btn__label">Start the escapement</span><span class="btn__arrow" aria-hidden="true">→</span></button>
            </div>
            <div class="game__veil game__veil--result" id="game-result" hidden>
              <span class="game__veil-eyebrow">Escapement complete</span>
              <h3 id="result-rank">Tempo kept.</h3>
              <p id="result-copy">12 beats · 100% accuracy</p>
              <div class="game__result-stats">
                <div><b id="result-hits">12</b><span>hits</span></div>
                <div><b id="result-best">x12</b><span>best combo</span></div>
                <div><b id="result-acc">100%</b><span>accuracy</span></div>
              </div>
              <button class="btn btn--gold" id="game-replay" type="button"><span class="btn__label">Run it again</span><span class="btn__arrow" aria-hidden="true">↻</span></button>
            </div>
          </div>

          <div class="game__hud">
            <div class="game__hud-item"><span>Hits</span><b><i id="game-hits">0</i> / 12</b></div>
            <div class="game__hud-item"><span>Combo</span><b id="game-hud-combo">x1</b></div>
            <div class="game__hud-item"><span>Accuracy</span><b id="game-acc">—</b></div>
            <div class="game__hud-item"><span>Best</span><b id="game-best">x0</b></div>
          </div>

          <button class="beat-btn" id="beat-btn" type="button" disabled>
            <span class="beat-btn__ring" aria-hidden="true"></span>
            <span class="beat-btn__label">BEAT</span>
            <span class="beat-btn__key">SPACE</span>
          </button>
          <p class="game__hint" id="game-hint">The trial begins at 33⅓ beats per minute. It will not stay that slow.</p>
        </div>

        <aside class="game__side">
          <p class="game__side-eyebrow">How the escapement works</p>
          <p>The balance wheel swings freely, but the pallet fork only lets one tooth of the escape wheel pass at a time. Tick. Tock. That is the whole trick of mechanical time — a controlled loss.</p>
          <ol class="game__rules">
            <li><span>01</span> Press as the needle enters the gold arc.</li>
            <li><span>02</span> One clean pass per swing. No double-dipping.</li>
            <li><span>03</span> Twelve hits completes the trial. Combo raises the note.</li>
          </ol>
          <div class="game__award" id="game-award">
            <span class="game__award-label">Trial reward</span>
            <span class="game__award-value">+90 XP on first clear · Metronome at x8</span>
          </div>
        </aside>
      </div>
    </section>

    <!-- ══════════════════════ LEDGER ══════════════════════ -->
    <section class="ledger section" id="ledger" data-section="ledger">
      <div class="ledger__head">
        <p class="eyebrow"><i></i> Trial VI — The Ledger</p>
        <h2 class="section-title">Your rank<br /><em>awaits.</em></h2>
      </div>

      <div class="ledger__grid">
        <div class="ledger__rank">
          <div class="ledger__seal" aria-hidden="true">
            <span class="ledger__seal-ring"></span>
            <span class="ledger__seal-letter" id="rank-initial">A</span>
            <span class="ledger__seal-small">TEMPO<br />GENÈVE</span>
          </div>
          <div class="ledger__rank-copy">
            <span class="ledger__rank-label" id="rank-label">Rank I</span>
            <h3 id="rank-title">Apprentice</h3>
            <p id="rank-desc">The bench is clean, the loupe is on. There is a long way to go, and every second counts.</p>
            <div class="ledger__xp">
              <div class="ledger__xp-bar"><i id="ledger-xp-fill"></i></div>
              <div class="ledger__xp-meta"><span id="ledger-xp">0 XP</span><span id="ledger-next">120 XP to Journeyman</span></div>
            </div>
          </div>
        </div>

        <div class="ledger__badges">
          <div class="badges__head"><span>Marks of the bench</span><span id="badge-count">0 / 6</span></div>
          <div class="badge-grid" id="badge-grid">
            <div class="badge" data-badge="first-wind"><span class="badge__num">I</span><span class="badge__body"><b>First Wind</b><span>Enter the atelier</span></span><span class="badge__lock">Locked</span></div>
            <div class="badge" data-badge="anatomist"><span class="badge__num">II</span><span class="badge__body"><b>Anatomist</b><span>Log all 11 components</span></span><span class="badge__lock">Locked</span></div>
            <div class="badge" data-badge="complicationist"><span class="badge__num">III</span><span class="badge__body"><b>Complicationist</b><span>Log all 4 complications</span></span><span class="badge__lock">Locked</span></div>
            <div class="badge" data-badge="commissioner"><span class="badge__num">IV</span><span class="badge__body"><b>Commissioner</b><span>Seal a commission</span></span><span class="badge__lock">Locked</span></div>
            <div class="badge" data-badge="metronome"><span class="badge__num">V</span><span class="badge__body"><b>Metronome</b><span>Reach a x8 combo</span></span><span class="badge__lock">Locked</span></div>
            <div class="badge" data-badge="grand"><span class="badge__num">VI</span><span class="badge__body"><b>Grand Complication</b><span>Reach Rank V</span></span><span class="badge__lock">Locked</span></div>
          </div>
        </div>

        <div class="ledger__stats">
          <div class="lstat"><span>Components logged</span><b id="stat-parts">0 / 11</b></div>
          <div class="lstat"><span>Complications logged</span><b id="stat-comps">0 / 4</b></div>
          <div class="lstat"><span>Best escapement combo</span><b id="stat-combo">x0</b></div>
          <div class="lstat"><span>Commissions sealed</span><b id="stat-commissions">0</b></div>
          <div class="lstat"><span>Total XP</span><b id="stat-xp">0</b></div>
        </div>
      </div>

      <div class="ledger__cta">
        <div>
          <span class="ledger__cta-label">The archive is yours to reset</span>
          <p>Sound settings and progress are stored on this device. Wipe the ledger and start the trial again.</p>
        </div>
        <button class="btn btn--ghost" id="reset-btn" type="button"><span class="btn__label">Reset the ledger</span></button>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="footer__brand">
      <span class="brand__word">TEMPO</span>
      <p>A watchmaker's arcade. Built as one page, played in six movements.</p>
    </div>
    <div class="footer__controls">
      <label class="volume" for="volume">
        <span>Volume</span>
        <input type="range" id="volume" min="0" max="100" value="72" aria-label="Sound volume" />
        <output id="volume-out">72</output>
      </label>
      <button class="text-link" id="replay-overture" type="button">Replay overture <span aria-hidden="true">↻</span></button>
    </div>
    <div class="footer__base">
      <span>© MMXXVI TEMPO · Genève</span>
      <span>Every sound synthesised with the Web Audio API. No samples. No watches harmed.</span>
      <a href="#top">Back to the top ↑</a>
    </div>
  </footer>

  <div class="toasts" id="toasts" aria-live="polite" aria-atomic="false"></div>
  <div class="confetti" id="confetti" aria-hidden="true"></div>

  <script src="js/audio.js"></script>
  <script src="js/watch.js"></script>
  <script src="js/movement.js"></script>
  <script src="js/game.js"></script>
  <script src="js/main.js"></script>
</body>
</html>
