# Agenda-Nica
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>AgendaNica — Guía Editorial de Nicaragua</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400;1,600&family=Libre+Franklin:ital,wght@0,300;0,400;0,500;0,600;1,300&family=Playfair+Display:ital,wght@0,700;0,900;1,700&display=swap" rel="stylesheet" />
  <style>
    /* ─── RESET & BASE ──────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--ivory);
      color: var(--black);
      font-family: 'Libre Franklin', sans-serif;
      font-weight: 300;
      line-height: 1.6;
      overflow-x: hidden;
    }
    a { text-decoration: none; color: inherit; }
    img { display: block; width: 100%; height: 100%; object-fit: cover; }
    button { cursor: pointer; border: none; background: none; font-family: inherit; }

    /* ─── TOKENS ────────────────────────────────────── */
    :root {
      --ivory:     #F5F1E8;
      --ivory-dark:#EDE8DC;
      --black:     #1E1E1C;
      --black-soft:#2C2C2A;
      --teal:      #1F6D67;
      --teal-light:#2A8880;
      --terra:     #B85C38;
      --mustard:   #C79A3B;
      --white:     #FDFCF8;
      --gray:      #8A8880;
      --gray-light:#D4D0C8;

      --ff-display: 'Playfair Display', Georgia, serif;
      --ff-serif:   'Cormorant Garamond', Georgia, serif;
      --ff-sans:    'Libre Franklin', sans-serif;

      --transition: 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
      --shadow-sm:  0 2px 12px rgba(30,30,28,0.08);
      --shadow-md:  0 8px 32px rgba(30,30,28,0.14);
      --shadow-lg:  0 20px 60px rgba(30,30,28,0.2);
    }

    /* ─── TYPOGRAPHY UTILITIES ───────────────────────── */
    .label {
      font-family: var(--ff-sans);
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.18em;
      text-transform: uppercase;
    }
    .eyebrow {
      font-family: var(--ff-sans);
      font-size: 0.7rem;
      font-weight: 500;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--terra);
    }
    .section-title {
      font-family: var(--ff-display);
      font-size: clamp(1.8rem, 3vw, 2.8rem);
      font-weight: 700;
      line-height: 1.1;
      letter-spacing: -0.01em;
    }

    /* ─── LAYOUT ─────────────────────────────────────── */
    .container { max-width: 1360px; margin: 0 auto; padding: 0 2rem; }
    .container--narrow { max-width: 900px; margin: 0 auto; padding: 0 2rem; }

    /* ─── DIVIDER ─────────────────────────────────────── */
    .rule {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 2.5rem;
    }
    .rule__line {
      flex: 1;
      height: 1px;
      background: var(--gray-light);
    }

    /* ═══════════════════════════════════════════════════
       HEADER / NAV
    ═══════════════════════════════════════════════════ */
    .site-header {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      background: rgba(245,241,232,0.95);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--gray-light);
      transition: box-shadow var(--transition);
    }
    .site-header.scrolled { box-shadow: var(--shadow-sm); }

    .header-inner {
      display: grid;
      grid-template-columns: 1fr auto 1fr;
      align-items: center;
      height: 68px;
      gap: 1.5rem;
    }

    /* Logo */
    .logo {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      justify-self: center;
      grid-column: 2;
    }
    .logo__mark {
      width: 32px; height: 32px;
      background: var(--teal);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }
    .logo__mark svg { width: 16px; height: 16px; fill: var(--ivory); }
    .logo__text {
      font-family: var(--ff-display);
      font-size: 1.5rem;
      font-weight: 700;
      color: var(--black);
      letter-spacing: -0.02em;
    }
    .logo__text span { color: var(--teal); }

    /* Nav left */
    .nav-primary {
      grid-column: 1;
      display: flex;
      gap: 1.8rem;
      align-items: center;
    }
    .nav-primary a {
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--black-soft);
      position: relative;
      padding-bottom: 2px;
      transition: color var(--transition);
    }
    .nav-primary a::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0;
      width: 0; height: 1px;
      background: var(--teal);
      transition: width var(--transition);
    }
    .nav-primary a:hover { color: var(--teal); }
    .nav-primary a:hover::after { width: 100%; }

    /* Nav right */
    .nav-actions {
      grid-column: 3;
      display: flex;
      gap: 1rem;
      align-items: center;
      justify-content: flex-end;
    }
    .btn-search {
      width: 36px; height: 36px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--black);
      transition: background var(--transition), color var(--transition);
    }
    .btn-search:hover { background: var(--teal); color: var(--ivory); }
    .btn-subscribe {
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.5rem 1.2rem;
      background: var(--teal);
      color: var(--ivory);
      border-radius: 2px;
      transition: background var(--transition), transform var(--transition);
    }
    .btn-subscribe:hover { background: var(--teal-light); transform: translateY(-1px); }

    /* Mobile burger */
    .burger {
      display: none;
      flex-direction: column;
      gap: 5px;
      padding: 6px;
      grid-column: 3;
      justify-self: end;
    }
    .burger span {
      display: block;
      width: 22px; height: 1.5px;
      background: var(--black);
      transition: var(--transition);
    }

    /* Mobile menu */
    .mobile-menu {
      display: none;
      position: fixed;
      top: 68px; left: 0; right: 0;
      background: var(--ivory);
      border-bottom: 1px solid var(--gray-light);
      padding: 1.5rem 2rem;
      flex-direction: column;
      gap: 0.5rem;
      z-index: 99;
      box-shadow: var(--shadow-md);
    }
    .mobile-menu.open { display: flex; }
    .mobile-menu a {
      font-size: 0.9rem;
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      padding: 0.6rem 0;
      border-bottom: 1px solid var(--gray-light);
      color: var(--black);
    }

    /* ─── SEARCH OVERLAY ──────────────────────────────── */
    .search-overlay {
      position: fixed;
      inset: 0;
      z-index: 200;
      background: rgba(30,30,28,0.92);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }
    .search-overlay.open {
      opacity: 1;
      pointer-events: all;
    }
    .search-box {
      width: 100%;
      max-width: 640px;
      padding: 0 2rem;
    }
    .search-label {
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gray);
      margin-bottom: 1rem;
      display: block;
    }
    .search-input {
      width: 100%;
      background: none;
      border: none;
      border-bottom: 1px solid rgba(245,241,232,0.3);
      color: var(--ivory);
      font-family: var(--ff-display);
      font-size: clamp(2rem, 5vw, 3.5rem);
      font-weight: 700;
      padding-bottom: 0.5rem;
      outline: none;
    }
    .search-input::placeholder { color: rgba(245,241,232,0.25); }
    .search-close {
      position: absolute;
      top: 2rem; right: 2rem;
      color: var(--ivory);
      font-size: 0.7rem;
      font-weight: 600;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      opacity: 0.6;
      transition: opacity var(--transition);
    }
    .search-close:hover { opacity: 1; }

    /* ═══════════════════════════════════════════════════
       TICKER
    ═══════════════════════════════════════════════════ */
    .ticker {
      background: var(--teal);
      color: var(--ivory);
      padding: 0.5rem 0;
      overflow: hidden;
      margin-top: 68px;
    }
    .ticker-inner {
      display: flex;
      align-items: center;
      gap: 0;
    }
    .ticker-label {
      font-size: 0.6rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      background: var(--terra);
      padding: 0.25rem 1rem;
      white-space: nowrap;
      flex-shrink: 0;
    }
    .ticker-track {
      display: flex;
      animation: tickerScroll 30s linear infinite;
      white-space: nowrap;
    }
    .ticker-track span {
      font-size: 0.7rem;
      font-weight: 500;
      letter-spacing: 0.08em;
      padding: 0 2.5rem;
      opacity: 0.9;
    }
    .ticker-track span::after {
      content: '·';
      margin-left: 2.5rem;
    }
    @keyframes tickerScroll {
      from { transform: translateX(0); }
      to   { transform: translateX(-50%); }
    }

    /* ═══════════════════════════════════════════════════
       HERO
    ═══════════════════════════════════════════════════ */
    .hero {
      display: grid;
      grid-template-columns: 1fr 380px;
      grid-template-rows: auto auto;
      gap: 1px;
      background: var(--gray-light);
      border-bottom: 1px solid var(--gray-light);
    }

    /* Hero main */
    .hero-main {
      grid-row: 1 / 3;
      position: relative;
      height: 85vh;
      min-height: 580px;
      max-height: 760px;
      overflow: hidden;
    }
    .hero-main .img-wrap {
      position: absolute;
      inset: 0;
    }
    .hero-main .img-wrap::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(
        to top,
        rgba(30,30,28,0.85) 0%,
        rgba(30,30,28,0.3) 55%,
        transparent 100%
      );
    }
    .hero-main .img-wrap img {
      transition: transform 8s ease;
    }
    .hero-main:hover .img-wrap img {
      transform: scale(1.04);
    }
    .hero-main__content {
      position: absolute;
      bottom: 0; left: 0; right: 0;
      padding: 2.5rem;
      z-index: 2;
    }
    .hero-main__eyebrow {
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-bottom: 0.75rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }
    .hero-main__eyebrow::before {
      content: '';
      display: inline-block;
      width: 24px; height: 1px;
      background: var(--mustard);
    }
    .hero-main__title {
      font-family: var(--ff-display);
      font-size: clamp(2rem, 4.5vw, 3.6rem);
      font-weight: 700;
      color: var(--white);
      line-height: 1.08;
      letter-spacing: -0.02em;
      margin-bottom: 1rem;
      max-width: 600px;
    }
    .hero-main__excerpt {
      font-size: 0.9rem;
      font-weight: 300;
      color: rgba(245,241,232,0.8);
      max-width: 480px;
      line-height: 1.65;
      margin-bottom: 1.5rem;
    }
    .hero-main__meta {
      display: flex;
      align-items: center;
      gap: 1rem;
      font-size: 0.65rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: rgba(245,241,232,0.55);
    }
    .hero-main__meta span:first-child { color: var(--terra); }

    /* Hero side cards */
    .hero-side {
      display: flex;
      flex-direction: column;
      gap: 1px;
      background: var(--gray-light);
    }
    .hero-card {
      flex: 1;
      position: relative;
      overflow: hidden;
      min-height: 200px;
    }
    .hero-card .img-wrap {
      position: absolute;
      inset: 0;
    }
    .hero-card .img-wrap::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(
        to top,
        rgba(30,30,28,0.75) 0%,
        transparent 60%
      );
    }
    .hero-card .img-wrap img {
      transition: transform 0.6s ease;
    }
    .hero-card:hover .img-wrap img { transform: scale(1.06); }
    .hero-card__content {
      position: absolute;
      bottom: 0; left: 0; right: 0;
      padding: 1.5rem;
      z-index: 2;
    }
    .hero-card__cat {
      font-size: 0.58rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-bottom: 0.4rem;
    }
    .hero-card__title {
      font-family: var(--ff-serif);
      font-size: clamp(1rem, 2vw, 1.35rem);
      font-weight: 600;
      color: var(--white);
      line-height: 1.2;
    }
    .hero-card__meta {
      font-size: 0.6rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: rgba(245,241,232,0.5);
      margin-top: 0.5rem;
    }

    /* ═══════════════════════════════════════════════════
       DATE STRIP
    ═══════════════════════════════════════════════════ */
    .date-strip {
      background: var(--black);
      color: var(--ivory);
      padding: 0.75rem 0;
    }
    .date-strip-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1rem;
    }
    .date-strip__left {
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      opacity: 0.5;
    }
    .date-strip__cats {
      display: flex;
      gap: 1.5rem;
    }
    .date-strip__cats a {
      font-size: 0.65rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: rgba(245,241,232,0.6);
      transition: color var(--transition);
    }
    .date-strip__cats a:hover { color: var(--mustard); }
    .date-strip__issue {
      font-size: 0.65rem;
      font-weight: 300;
      letter-spacing: 0.1em;
      opacity: 0.4;
    }

    /* ═══════════════════════════════════════════════════
       SECTION HEADER
    ═══════════════════════════════════════════════════ */
    .section-hd {
      display: flex;
      align-items: baseline;
      justify-content: space-between;
      margin-bottom: 2rem;
    }
    .section-hd__group {
      display: flex;
      flex-direction: column;
      gap: 0.3rem;
    }
    .section-hd__link {
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--teal);
      display: flex;
      align-items: center;
      gap: 0.4rem;
      transition: gap var(--transition);
    }
    .section-hd__link:hover { gap: 0.8rem; }
    .section-hd__link::after { content: '→'; }

    /* ═══════════════════════════════════════════════════
       FEATURED STRIP (below hero)
    ═══════════════════════════════════════════════════ */
    .featured-strip {
      padding: 4rem 0;
      background: var(--ivory);
    }
    .featured-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
      background: var(--gray-light);
    }
    .featured-item {
      background: var(--ivory);
      display: flex;
      gap: 1.25rem;
      padding: 1.5rem;
      align-items: flex-start;
      transition: background var(--transition);
    }
    .featured-item:hover { background: var(--ivory-dark); }
    .featured-item__num {
      font-family: var(--ff-display);
      font-size: 3rem;
      font-weight: 700;
      color: var(--gray-light);
      line-height: 1;
      flex-shrink: 0;
      letter-spacing: -0.04em;
    }
    .featured-item__body { flex: 1; }
    .featured-item__cat {
      font-size: 0.6rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--terra);
      margin-bottom: 0.4rem;
    }
    .featured-item__title {
      font-family: var(--ff-serif);
      font-size: 1.1rem;
      font-weight: 600;
      line-height: 1.3;
      color: var(--black);
      margin-bottom: 0.5rem;
    }
    .featured-item__desc {
      font-size: 0.8rem;
      color: var(--gray);
      line-height: 1.6;
    }

    /* ═══════════════════════════════════════════════════
       SECTION: RESTAURANTES
    ═══════════════════════════════════════════════════ */
    .sec-restaurants {
      padding: 5rem 0;
      background: var(--ivory);
    }
    .restaurants-layout {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      grid-template-rows: auto auto;
      gap: 1.5rem;
    }

    /* Card types */
    .card {
      position: relative;
      overflow: hidden;
      background: var(--white);
      border: 1px solid var(--gray-light);
      transition: transform var(--transition), box-shadow var(--transition);
    }
    .card:hover { transform: translateY(-4px); box-shadow: var(--shadow-md); }

    .card--feature {
      grid-column: 1 / 3;
      display: grid;
      grid-template-columns: 1fr 1fr;
    }
    .card--feature .card-img { height: 100%; min-height: 320px; }
    .card--feature .card-body { padding: 2.5rem; display: flex; flex-direction: column; justify-content: center; }

    .card--tall {
      grid-row: 1 / 3;
      grid-column: 3;
    }
    .card--tall .card-img { height: 260px; }

    .card--standard .card-img { height: 220px; }

    .card-img { position: relative; overflow: hidden; }
    .card-img img { transition: transform 0.6s ease; }
    .card:hover .card-img img { transform: scale(1.05); }

    .card-badge {
      position: absolute;
      top: 1rem; left: 1rem;
      font-size: 0.55rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      padding: 0.3rem 0.7rem;
      background: var(--terra);
      color: var(--white);
      z-index: 2;
    }
    .card-badge--teal { background: var(--teal); }
    .card-badge--mustard { background: var(--mustard); color: var(--black); }

    .card-body { padding: 1.5rem; }
    .card-eyebrow {
      font-size: 0.6rem;
      font-weight: 600;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--terra);
      margin-bottom: 0.5rem;
    }
    .card-title {
      font-family: var(--ff-serif);
      font-size: clamp(1.1rem, 2.5vw, 1.45rem);
      font-weight: 600;
      line-height: 1.25;
      color: var(--black);
      margin-bottom: 0.75rem;
    }
    .card-title--sm {
      font-size: 1.05rem;
    }
    .card-desc {
      font-size: 0.82rem;
      color: var(--gray);
      line-height: 1.65;
      margin-bottom: 1rem;
    }
    .card-meta {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      font-size: 0.6rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--gray);
    }
    .card-meta__dot { color: var(--gray-light); }

    .card-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 1rem;
    }
    .tag {
      font-size: 0.58rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.25rem 0.6rem;
      border: 1px solid var(--gray-light);
      color: var(--gray);
      transition: border-color var(--transition), color var(--transition);
    }
    .card:hover .tag { border-color: var(--teal); color: var(--teal); }

    /* Stars */
    .stars {
      display: flex;
      gap: 2px;
      margin-bottom: 0.5rem;
    }
    .stars svg { width: 12px; height: 12px; fill: var(--mustard); }

    /* ═══════════════════════════════════════════════════
       SECTION: EDITORIAL WIDE (Teal bg)
    ═══════════════════════════════════════════════════ */
    .sec-editorial {
      background: var(--teal);
      padding: 5rem 0;
      color: var(--ivory);
    }
    .editorial-inner {
      display: grid;
      grid-template-columns: 1fr 1px 1fr;
      gap: 4rem;
      align-items: center;
    }
    .editorial-divider { background: rgba(245,241,232,0.2); }
    .editorial-text .eyebrow { color: var(--mustard); margin-bottom: 1rem; }
    .editorial-text h2 {
      font-family: var(--ff-display);
      font-size: clamp(2rem, 4vw, 3.2rem);
      font-weight: 700;
      line-height: 1.1;
      letter-spacing: -0.02em;
      margin-bottom: 1.25rem;
    }
    .editorial-text p {
      font-size: 0.9rem;
      line-height: 1.75;
      opacity: 0.8;
      margin-bottom: 1.5rem;
    }
    .btn-outline-ivory {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      padding: 0.8rem 1.8rem;
      border: 1px solid rgba(245,241,232,0.5);
      color: var(--ivory);
      transition: background var(--transition), border-color var(--transition);
    }
    .btn-outline-ivory:hover {
      background: rgba(245,241,232,0.1);
      border-color: var(--ivory);
    }
    .btn-outline-ivory::after { content: '→'; }

    .editorial-cards {
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
    }
    .editorial-card {
      display: flex;
      gap: 1.25rem;
      padding-bottom: 1.5rem;
      border-bottom: 1px solid rgba(245,241,232,0.15);
    }
    .editorial-card:last-child { border-bottom: none; padding-bottom: 0; }
    .editorial-card__img {
      width: 90px; height: 75px;
      flex-shrink: 0;
      overflow: hidden;
    }
    .editorial-card__img img { transition: transform 0.5s; }
    .editorial-card:hover .editorial-card__img img { transform: scale(1.06); }
    .editorial-card__body { flex: 1; }
    .editorial-card__cat {
      font-size: 0.55rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-bottom: 0.3rem;
    }
    .editorial-card__title {
      font-family: var(--ff-serif);
      font-size: 1rem;
      font-weight: 600;
      color: var(--ivory);
      line-height: 1.3;
      margin-bottom: 0.3rem;
    }
    .editorial-card__meta {
      font-size: 0.58rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: rgba(245,241,232,0.45);
    }

    /* ═══════════════════════════════════════════════════
       SECTION: WEEKEND GUIDE
    ═══════════════════════════════════════════════════ */
    .sec-weekend {
      padding: 5rem 0;
      background: var(--ivory-dark);
    }
    .weekend-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1.5rem;
    }
    .weekend-card {
      background: var(--ivory);
      border: 1px solid var(--gray-light);
      overflow: hidden;
      transition: transform var(--transition), box-shadow var(--transition);
    }
    .weekend-card:hover { transform: translateY(-4px); box-shadow: var(--shadow-md); }
    .weekend-card__img { height: 200px; overflow: hidden; position: relative; }
    .weekend-card__img img { transition: transform 0.6s; }
    .weekend-card:hover .weekend-card__img img { transform: scale(1.06); }
    .weekend-card__num {
      position: absolute;
      top: 1rem; right: 1rem;
      width: 36px; height: 36px;
      background: var(--terra);
      color: var(--white);
      font-family: var(--ff-serif);
      font-size: 1.1rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .weekend-card__body { padding: 1.25rem; }
    .weekend-card__time {
      font-size: 0.58rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--teal);
      margin-bottom: 0.4rem;
    }
    .weekend-card__title {
      font-family: var(--ff-serif);
      font-size: 1.05rem;
      font-weight: 600;
      line-height: 1.3;
      color: var(--black);
      margin-bottom: 0.5rem;
    }
    .weekend-card__desc {
      font-size: 0.78rem;
      color: var(--gray);
      line-height: 1.6;
    }

    /* ═══════════════════════════════════════════════════
       SECTION: ESCAPADAS
    ═══════════════════════════════════════════════════ */
    .sec-escapadas {
      padding: 5rem 0;
      background: var(--ivory);
    }
    .escapadas-hero {
      position: relative;
      height: 480px;
      overflow: hidden;
      margin-bottom: 1.5rem;
    }
    .escapadas-hero .img-wrap {
      position: absolute;
      inset: 0;
    }
    .escapadas-hero .img-wrap::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, rgba(30,30,28,0.75) 0%, transparent 60%);
    }
    .escapadas-hero__content {
      position: absolute;
      left: 4rem;
      top: 50%;
      transform: translateY(-50%);
      z-index: 2;
      max-width: 480px;
    }
    .escapadas-hero__eyebrow {
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-bottom: 0.75rem;
    }
    .escapadas-hero__title {
      font-family: var(--ff-display);
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700;
      color: var(--white);
      line-height: 1.08;
      letter-spacing: -0.02em;
      margin-bottom: 1rem;
    }
    .escapadas-hero__desc {
      font-size: 0.88rem;
      color: rgba(245,241,232,0.8);
      line-height: 1.65;
      margin-bottom: 1.5rem;
    }
    .btn-solid {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      padding: 0.8rem 1.8rem;
      background: var(--terra);
      color: var(--white);
      transition: background var(--transition), transform var(--transition);
    }
    .btn-solid:hover { background: #a04d2e; transform: translateX(4px); }
    .btn-solid::after { content: '→'; }

    .escapadas-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1.5rem;
    }
    .escapada-card {
      position: relative;
      height: 260px;
      overflow: hidden;
    }
    .escapada-card .img-wrap {
      position: absolute;
      inset: 0;
    }
    .escapada-card .img-wrap::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(30,30,28,0.8) 0%, transparent 60%);
    }
    .escapada-card .img-wrap img { transition: transform 0.6s; }
    .escapada-card:hover .img-wrap img { transform: scale(1.06); }
    .escapada-card__content {
      position: absolute;
      bottom: 0; left: 0; right: 0;
      padding: 1.5rem;
      z-index: 2;
    }
    .escapada-card__dist {
      font-size: 0.6rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-bottom: 0.4rem;
    }
    .escapada-card__title {
      font-family: var(--ff-serif);
      font-size: 1.25rem;
      font-weight: 600;
      color: var(--white);
      line-height: 1.2;
    }
    .escapada-card__tags {
      display: flex;
      gap: 0.4rem;
      flex-wrap: wrap;
      margin-top: 0.5rem;
    }
    .escapada-tag {
      font-size: 0.55rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.2rem 0.5rem;
      background: rgba(245,241,232,0.15);
      color: rgba(245,241,232,0.8);
      border: 1px solid rgba(245,241,232,0.2);
    }

    /* ═══════════════════════════════════════════════════
       SECTION: CAFÉS
    ═══════════════════════════════════════════════════ */
    .sec-cafes {
      padding: 5rem 0;
      background: var(--black);
      color: var(--ivory);
    }
    .sec-cafes .eyebrow { color: var(--mustard); margin-bottom: 0.5rem; }
    .sec-cafes .section-title { color: var(--ivory); margin-bottom: 0.5rem; }
    .sec-cafes .section-hd__link { color: var(--mustard); }

    .cafes-scroll {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1px;
      background: rgba(245,241,232,0.1);
      margin-top: 2.5rem;
    }
    .cafe-card {
      background: var(--black-soft);
      overflow: hidden;
      position: relative;
    }
    .cafe-card__img {
      height: 260px;
      overflow: hidden;
      position: relative;
    }
    .cafe-card__img::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(30,30,28,0.6) 0%, transparent 50%);
    }
    .cafe-card__img img { transition: transform 0.6s; }
    .cafe-card:hover .cafe-card__img img { transform: scale(1.06); }
    .cafe-card__body {
      padding: 1.5rem;
    }
    .cafe-card__num {
      font-family: var(--ff-serif);
      font-size: 0.75rem;
      color: var(--mustard);
      letter-spacing: 0.08em;
      margin-bottom: 0.3rem;
    }
    .cafe-card__name {
      font-family: var(--ff-serif);
      font-size: 1.2rem;
      font-weight: 600;
      color: var(--ivory);
      margin-bottom: 0.4rem;
      line-height: 1.2;
    }
    .cafe-card__desc {
      font-size: 0.78rem;
      color: rgba(245,241,232,0.55);
      line-height: 1.6;
      margin-bottom: 0.75rem;
    }
    .cafe-card__footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-top: 0.75rem;
      border-top: 1px solid rgba(245,241,232,0.1);
    }
    .cafe-card__zone {
      font-size: 0.6rem;
      font-weight: 600;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--teal-light);
    }
    .cafe-card__icon {
      width: 28px; height: 28px;
      border-radius: 50%;
      background: rgba(245,241,232,0.08);
      display: flex;
      align-items: center;
      justify-content: center;
      color: rgba(245,241,232,0.4);
      font-size: 0.7rem;
      transition: background var(--transition), color var(--transition);
    }
    .cafe-card:hover .cafe-card__icon {
      background: var(--teal);
      color: var(--ivory);
    }

    /* ═══════════════════════════════════════════════════
       SECTION: CULTURA / EVENTS
    ═══════════════════════════════════════════════════ */
    .sec-cultura {
      padding: 5rem 0;
      background: var(--ivory);
    }
    .cultura-layout {
      display: grid;
      grid-template-columns: 1fr 380px;
      gap: 3rem;
      align-items: start;
    }
    .events-list { display: flex; flex-direction: column; }
    .event-item {
      display: grid;
      grid-template-columns: 80px 1fr auto;
      gap: 1.5rem;
      align-items: center;
      padding: 1.5rem 0;
      border-bottom: 1px solid var(--gray-light);
      transition: background var(--transition);
    }
    .event-item:first-child { padding-top: 0; }
    .event-item:last-child { border-bottom: none; }
    .event-item:hover { background: transparent; }
    .event-date {
      text-align: center;
      background: var(--black);
      color: var(--ivory);
      padding: 0.75rem 0.5rem;
    }
    .event-date__day {
      font-family: var(--ff-display);
      font-size: 1.8rem;
      font-weight: 700;
      line-height: 1;
      display: block;
    }
    .event-date__month {
      font-size: 0.55rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--mustard);
    }
    .event-info {}
    .event-cat {
      font-size: 0.58rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--terra);
      margin-bottom: 0.3rem;
    }
    .event-title {
      font-family: var(--ff-serif);
      font-size: 1.05rem;
      font-weight: 600;
      color: var(--black);
      line-height: 1.3;
      margin-bottom: 0.3rem;
    }
    .event-where {
      font-size: 0.72rem;
      color: var(--gray);
    }
    .event-action {
      font-size: 0.6rem;
      font-weight: 600;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--teal);
      white-space: nowrap;
      padding: 0.5rem 0.9rem;
      border: 1px solid var(--teal);
      transition: background var(--transition), color var(--transition);
    }
    .event-action:hover { background: var(--teal); color: var(--ivory); }

    /* Sidebar */
    .cultura-sidebar {}
    .sidebar-widget {
      background: var(--ivory-dark);
      border: 1px solid var(--gray-light);
      padding: 1.75rem;
      margin-bottom: 1.5rem;
    }
    .sidebar-widget__title {
      font-family: var(--ff-display);
      font-size: 1.1rem;
      font-weight: 700;
      margin-bottom: 1rem;
      padding-bottom: 0.75rem;
      border-bottom: 2px solid var(--teal);
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .sidebar-widget__title span {
      font-size: 0.6rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--teal);
    }
    .popular-item {
      display: flex;
      gap: 1rem;
      padding: 0.75rem 0;
      border-bottom: 1px solid var(--gray-light);
    }
    .popular-item:last-child { border-bottom: none; padding-bottom: 0; }
    .popular-item__num {
      font-family: var(--ff-serif);
      font-size: 1.5rem;
      font-weight: 700;
      color: var(--gray-light);
      flex-shrink: 0;
      width: 24px;
      line-height: 1;
    }
    .popular-item__title {
      font-family: var(--ff-serif);
      font-size: 0.9rem;
      font-weight: 600;
      line-height: 1.3;
      color: var(--black);
    }
    .popular-item__cat {
      font-size: 0.58rem;
      font-weight: 600;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--terra);
      margin-top: 0.2rem;
    }

    .social-links {
      display: flex;
      gap: 0.75rem;
      flex-wrap: wrap;
    }
    .social-link {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.6rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.5rem 0.8rem;
      border: 1px solid var(--gray-light);
      color: var(--black-soft);
      transition: border-color var(--transition), color var(--transition), background var(--transition);
    }
    .social-link:hover { background: var(--black); color: var(--ivory); border-color: var(--black); }

    /* ═══════════════════════════════════════════════════
       SECTION: FOTOGÉNICO
    ═══════════════════════════════════════════════════ */
    .sec-photo {
      padding: 5rem 0;
      background: var(--ivory-dark);
    }
    .photo-masonry {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      grid-template-rows: 200px 200px;
      gap: 6px;
    }
    .photo-item {
      position: relative;
      overflow: hidden;
    }
    .photo-item:nth-child(1) { grid-column: 1 / 3; grid-row: 1 / 3; }
    .photo-item:nth-child(4) { grid-column: 4 / 6; }
    .photo-item:nth-child(5) { grid-column: 4 / 6; }

    .photo-item .img-wrap {
      position: absolute;
      inset: 0;
    }
    .photo-item .img-wrap::after {
      content: '';
      position: absolute;
      inset: 0;
      background: rgba(30,30,28,0);
      transition: background 0.4s;
    }
    .photo-item:hover .img-wrap::after { background: rgba(30,30,28,0.5); }
    .photo-item .img-wrap img { transition: transform 0.6s; }
    .photo-item:hover .img-wrap img { transform: scale(1.06); }
    .photo-item__overlay {
      position: absolute;
      inset: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 2;
      opacity: 0;
      transition: opacity 0.4s;
    }
    .photo-item:hover .photo-item__overlay { opacity: 1; }
    .photo-item__place {
      font-family: var(--ff-serif);
      font-size: 1rem;
      font-weight: 600;
      color: var(--white);
      text-align: center;
      padding: 0 1rem;
    }
    .photo-item__tag {
      font-size: 0.58rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-top: 0.4rem;
    }

    /* ═══════════════════════════════════════════════════
       SECTION: NEWSLETTER
    ═══════════════════════════════════════════════════ */
    .sec-newsletter {
      background: var(--terra);
      padding: 5rem 0;
      color: var(--white);
      position: relative;
      overflow: hidden;
    }
    .sec-newsletter::before {
      content: 'NEWSLETTER';
      position: absolute;
      font-family: var(--ff-display);
      font-size: 16vw;
      font-weight: 900;
      color: rgba(255,255,255,0.04);
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      white-space: nowrap;
      pointer-events: none;
      letter-spacing: -0.05em;
    }
    .newsletter-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 5rem;
      align-items: center;
    }
    .newsletter-text .eyebrow { color: rgba(255,255,255,0.6); margin-bottom: 0.75rem; }
    .newsletter-text h2 {
      font-family: var(--ff-display);
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700;
      line-height: 1.1;
      letter-spacing: -0.02em;
      margin-bottom: 1rem;
    }
    .newsletter-text p {
      font-size: 0.9rem;
      line-height: 1.7;
      opacity: 0.8;
    }
    .newsletter-form {}
    .form-group {
      display: flex;
      margin-bottom: 1rem;
    }
    .form-input {
      flex: 1;
      background: rgba(255,255,255,0.12);
      border: 1px solid rgba(255,255,255,0.25);
      border-right: none;
      padding: 0.85rem 1.25rem;
      font-family: var(--ff-sans);
      font-size: 0.85rem;
      color: var(--white);
      outline: none;
      transition: background var(--transition), border-color var(--transition);
    }
    .form-input::placeholder { color: rgba(255,255,255,0.4); }
    .form-input:focus {
      background: rgba(255,255,255,0.18);
      border-color: rgba(255,255,255,0.5);
    }
    .form-submit {
      padding: 0.85rem 1.75rem;
      background: var(--black);
      color: var(--ivory);
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      border: 1px solid var(--black);
      transition: background var(--transition), transform var(--transition);
    }
    .form-submit:hover { background: var(--black-soft); transform: translateX(2px); }
    .form-note {
      font-size: 0.7rem;
      opacity: 0.55;
      line-height: 1.5;
    }
    .newsletter-perks {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      margin-top: 2rem;
    }
    .perk {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      font-size: 0.8rem;
      opacity: 0.8;
    }
    .perk__icon {
      width: 28px; height: 28px;
      border-radius: 50%;
      background: rgba(255,255,255,0.15);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      font-size: 0.8rem;
    }

    /* ═══════════════════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════════════════ */
    .site-footer {
      background: var(--black);
      color: var(--ivory);
      padding: 5rem 0 0;
    }
    .footer-grid {
      display: grid;
      grid-template-columns: 280px 1fr 1fr 1fr;
      gap: 4rem;
      padding-bottom: 4rem;
      border-bottom: 1px solid rgba(245,241,232,0.1);
    }
    .footer-brand .logo { margin-bottom: 1.25rem; }
    .footer-brand p {
      font-size: 0.8rem;
      line-height: 1.7;
      color: rgba(245,241,232,0.5);
      margin-bottom: 1.5rem;
    }
    .footer-socials {
      display: flex;
      gap: 0.5rem;
    }
    .footer-social {
      width: 34px; height: 34px;
      border: 1px solid rgba(245,241,232,0.15);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.7rem;
      font-weight: 600;
      color: rgba(245,241,232,0.5);
      transition: border-color var(--transition), color var(--transition), background var(--transition);
    }
    .footer-social:hover {
      border-color: var(--teal);
      color: var(--teal);
      background: rgba(31,109,103,0.1);
    }

    .footer-col h4 {
      font-family: var(--ff-sans);
      font-size: 0.62rem;
      font-weight: 700;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--mustard);
      margin-bottom: 1.25rem;
    }
    .footer-links {
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
    }
    .footer-links a {
      font-size: 0.82rem;
      color: rgba(245,241,232,0.55);
      transition: color var(--transition), padding-left var(--transition);
    }
    .footer-links a:hover { color: var(--ivory); padding-left: 4px; }

    .footer-recent { display: flex; flex-direction: column; gap: 1rem; }
    .footer-post {
      display: flex;
      gap: 0.75rem;
      padding-bottom: 1rem;
      border-bottom: 1px solid rgba(245,241,232,0.08);
    }
    .footer-post:last-child { border-bottom: none; padding-bottom: 0; }
    .footer-post__img {
      width: 56px; height: 48px;
      flex-shrink: 0;
      overflow: hidden;
    }
    .footer-post__img img { transition: transform 0.4s; }
    .footer-post:hover .footer-post__img img { transform: scale(1.08); }
    .footer-post__title {
      font-family: var(--ff-serif);
      font-size: 0.82rem;
      font-weight: 600;
      color: rgba(245,241,232,0.8);
      line-height: 1.3;
    }
    .footer-post__date {
      font-size: 0.58rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: rgba(245,241,232,0.3);
      margin-top: 0.3rem;
    }

    .footer-bottom {
      padding: 1.5rem 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1rem;
    }
    .footer-bottom__copy {
      font-size: 0.68rem;
      color: rgba(245,241,232,0.3);
      letter-spacing: 0.06em;
    }
    .footer-bottom__links {
      display: flex;
      gap: 1.5rem;
    }
    .footer-bottom__links a {
      font-size: 0.65rem;
      color: rgba(245,241,232,0.3);
      letter-spacing: 0.08em;
      transition: color var(--transition);
    }
    .footer-bottom__links a:hover { color: rgba(245,241,232,0.7); }

    /* ═══════════════════════════════════════════════════
       SCROLL TO TOP
    ═══════════════════════════════════════════════════ */
    .scroll-top {
      position: fixed;
      bottom: 2rem;
      right: 2rem;
      width: 44px;
      height: 44px;
      background: var(--teal);
      color: var(--ivory);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 50;
      opacity: 0;
      transform: translateY(8px);
      transition: opacity var(--transition), transform var(--transition);
      pointer-events: none;
    }
    .scroll-top.visible {
      opacity: 1;
      transform: translateY(0);
      pointer-events: all;
    }
    .scroll-top:hover { background: var(--teal-light); }
    .scroll-top svg { width: 16px; height: 16px; fill: none; stroke: currentColor; stroke-width: 2; }

    /* ═══════════════════════════════════════════════════
       REVEAL ANIMATIONS
    ═══════════════════════════════════════════════════ */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }

    /* ═══════════════════════════════════════════════════
       RESPONSIVE
    ═══════════════════════════════════════════════════ */
    @media (max-width: 1100px) {
      .restaurants-layout { grid-template-columns: 1fr 1fr; }
      .card--feature { grid-column: 1 / 3; }
      .card--tall { grid-column: unset; grid-row: unset; }
      .weekend-grid { grid-template-columns: repeat(2, 1fr); }
      .cafes-scroll { grid-template-columns: repeat(2, 1fr); }
      .footer-grid { grid-template-columns: 1fr 1fr; gap: 2.5rem; }
      .editorial-inner { grid-template-columns: 1fr; gap: 2.5rem; }
      .editorial-divider { display: none; }
      .photo-masonry { grid-template-columns: repeat(3, 1fr); grid-template-rows: 180px 180px; }
      .photo-item:nth-child(1) { grid-column: 1 / 2; grid-row: 1 / 3; }
      .photo-item:nth-child(4) { grid-column: unset; }
      .photo-item:nth-child(5) { grid-column: unset; }
    }

    @media (max-width: 900px) {
      .hero { grid-template-columns: 1fr; }
      .hero-main { height: 70vw; min-height: 420px; grid-row: 1; }
      .hero-side { flex-direction: row; }
      .hero-card { min-height: 220px; }
      .cultura-layout { grid-template-columns: 1fr; }
      .newsletter-inner { grid-template-columns: 1fr; gap: 2.5rem; }
      .escapadas-grid { grid-template-columns: repeat(2, 1fr); }
      .nav-primary { display: none; }
      .nav-actions .btn-subscribe { display: none; }
      .burger { display: flex; }
    }

    @media (max-width: 640px) {
      .container { padding: 0 1.25rem; }
      .header-inner { grid-template-columns: auto 1fr auto; }
      .logo { grid-column: 2; justify-self: center; }
      .burger { grid-column: 3; }
      .hero-main__title { font-size: 1.8rem; }
      .hero-side { flex-direction: column; }
      .featured-grid { grid-template-columns: 1fr; }
      .restaurants-layout { grid-template-columns: 1fr; }
      .card--feature { grid-template-columns: 1fr; }
      .card--feature .card-img { height: 220px; }
      .weekend-grid { grid-template-columns: 1fr; }
      .cafes-scroll { grid-template-columns: 1fr; }
      .escapadas-grid { grid-template-columns: 1fr; }
      .photo-masonry { grid-template-columns: repeat(2, 1fr); }
      .photo-item:nth-child(1) { grid-column: 1 / 3; grid-row: 1; }
      .footer-grid { grid-template-columns: 1fr; gap: 2rem; }
      .footer-bottom { flex-direction: column; text-align: center; }
      .event-item { grid-template-columns: 60px 1fr; gap: 1rem; }
      .event-action { display: none; }
      .date-strip-inner { flex-direction: column; gap: 0.5rem; text-align: center; }
      .date-strip__cats { justify-content: center; flex-wrap: wrap; gap: 1rem; }
      .escapadas-hero__content { left: 1.5rem; right: 1.5rem; }
      .newsletter-inner { gap: 2rem; }
      .form-group { flex-direction: column; }
      .form-input { border-right: 1px solid rgba(255,255,255,0.25); border-bottom: none; }
    }
  </style>
</head>
<body>

<!-- ═══════════════════════════════════════════════════
     SEARCH OVERLAY
═══════════════════════════════════════════════════ -->
<div class="search-overlay" id="searchOverlay">
  <div class="search-box">
    <span class="search-label">¿Qué estás buscando?</span>
    <input type="text" class="search-input" placeholder="Buscar lugares, eventos…" id="searchInput" />
  </div>
  <button class="search-close" id="searchClose">Cerrar ×</button>
</div>

<!-- ═══════════════════════════════════════════════════
     HEADER
═══════════════════════════════════════════════════ -->
<header class="site-header" id="siteHeader">
  <div class="container">
    <div class="header-inner">

      <nav class="nav-primary">
        <a href="#">Restaurantes</a>
        <a href="#">Cultura</a>
        <a href="#">Escapadas</a>
        <a href="#">Cafés</a>
        <a href="#">Agenda</a>
      </nav>

      <a href="#" class="logo">
        <div class="logo__mark">
          <svg viewBox="0 0 16 16"><path d="M8 1.5C4.4 1.5 1.5 4.4 1.5 8c0 1.8.7 3.5 1.8 4.7L8 8l4.7 4.7c1.1-1.2 1.8-2.9 1.8-4.7 0-3.6-2.9-6.5-6.5-6.5z"/></svg>
        </div>
        <span class="logo__text">Agenda<span>Nica</span></span>
      </a>

      <div class="nav-actions">
        <button class="btn-search" id="searchBtn" title="Buscar">
          <svg width="17" height="17" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="7"/><path d="m21 21-4.35-4.35"/></svg>
        </button>
        <a href="#newsletter" class="btn-subscribe">Suscríbete</a>
      </div>

      <button class="burger" id="burgerBtn" aria-label="Menú">
        <span></span><span></span><span></span>
      </button>

    </div>
  </div>
</header>

<!-- Mobile menu -->
<div class="mobile-menu" id="mobileMenu">
  <a href="#">Restaurantes</a>
  <a href="#">Cultura</a>
  <a href="#">Escapadas</a>
  <a href="#">Cafés y Bares</a>
  <a href="#">Agenda de Eventos</a>
  <a href="#">Rincones Fotogénicos</a>
  <a href="#">Guía de Managua</a>
</div>

<!-- ═══════════════════════════════════════════════════
     TICKER
═══════════════════════════════════════════════════ -->
<div class="ticker">
  <div class="container">
    <div class="ticker-inner">
      <span class="ticker-label">Hoy en Managua</span>
      <div class="ticker-track" id="tickerTrack">
        <span>Festival de Jazz en el Malecón de Managua</span>
        <span>Nuevo restaurante Tawa abre en Altamira</span>
        <span>Muestra de arte en la Galería Códice este sábado</span>
        <span>Rutas de café de especialidad en la Colonia Centroamérica</span>
        <span>Escapada de fin de semana: Isletas de Granada</span>
        <span>Feria gastronómica en el Parque Luis Alfonso Velásquez</span>
        <span>Concierto de marimba en el Teatro Nacional Rubén Darío</span>
        <span>Guía definitiva del Paseo Xolotlán en temporada seca</span>
        <span>Festival de Jazz en el Malecón de Managua</span>
        <span>Nuevo restaurante Tawa abre en Altamira</span>
        <span>Muestra de arte en la Galería Códice este sábado</span>
        <span>Rutas de café de especialidad en la Colonia Centroamérica</span>
        <span>Escapada de fin de semana: Isletas de Granada</span>
        <span>Feria gastronómica en el Parque Luis Alfonso Velásquez</span>
        <span>Concierto de marimba en el Teatro Nacional Rubén Darío</span>
        <span>Guía definitiva del Paseo Xolotlán en temporada seca</span>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════════════
     DATE STRIP
═══════════════════════════════════════════════════ -->
<div class="date-strip">
  <div class="container">
    <div class="date-strip-inner">
      <span class="date-strip__left">AgendaNica — Managua, Nicaragua</span>
      <nav class="date-strip__cats">
        <a href="#">🍽 Comer</a>
        <a href="#">🎭 Cultura</a>
        <a href="#">☕ Cafés</a>
        <a href="#">🌋 Escapadas</a>
        <a href="#">📸 Fotogénico</a>
        <a href="#">🎶 Música</a>
        <a href="#">🛍 Compras</a>
      </nav>
      <span class="date-strip__issue">Edición N° 28 · Verano 2025</span>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════════════
     HERO
═══════════════════════════════════════════════════ -->
<section class="hero">

  <!-- Main feature -->
  <article class="hero-main">
    <div class="img-wrap">
      <img src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=1400&q=80&auto=format" alt="Managua hero" loading="eager" />
    </div>
    <div class="hero-main__content">
      <div class="hero-main__eyebrow">Portada de la Semana</div>
      <h1 class="hero-main__title">La nueva cocina nicaragüense que está reinventando Managua</h1>
      <p class="hero-main__excerpt">Una generación de chefs locales está recuperando ingredientes ancestrales — cacao, chiltoma, jocote — para crear una propuesta gastronómica que ya mira al mundo.</p>
      <div class="hero-main__meta">
        <span>Gastronomía</span>
        <span class="hero-main__meta--dot">·</span>
        <span>12 min de lectura</span>
        <span class="hero-main__meta--dot">·</span>
        <span>Por Andrea Solís</span>
      </div>
    </div>
  </article>

  <!-- Side cards -->
  <aside class="hero-side">
    <article class="hero-card">
      <div class="img-wrap">
        <img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?w=800&q=80&auto=format" alt="Café de especialidad" loading="lazy" />
      </div>
      <div class="hero-card__content">
        <div class="hero-card__cat">Cafés · Guía</div>
        <h2 class="hero-card__title">Los 7 cafés más bonitos de Managua para trabajar y soñar</h2>
        <div class="hero-card__meta">5 min · Esta semana</div>
      </div>
    </article>
    <article class="hero-card">
      <div class="img-wrap">
        <img src="https://images.unsplash.com/photo-1473116763249-2faaef81ccda?w=800&q=80&auto=format" alt="Volcán Momotombo" loading="lazy" />
      </div>
      <div class="hero-card__content">
        <div class="hero-card__cat">Escapadas · Naturaleza</div>
        <h2 class="hero-card__title">Momotombo: ascenso al volcán más imponente del Pacífico</h2>
        <div class="hero-card__meta">8 min · Guía completa</div>
      </div>
    </article>
    <article class="hero-card">
      <div class="img-wrap">
        <img src="https://images.unsplash.com/photo-1414235077428-338989a2e8c0?w=800&q=80&auto=format" alt="Evento cultural" loading="lazy" />
      </div>
      <div class="hero-card__content">
        <div class="hero-card__cat">Eventos · Cultura</div>
        <h2 class="hero-card__title">Teatro, marimba y arte callejero: agenda cultural del mes</h2>
        <div class="hero-card__meta">3 min · Agenda</div>
      </div>
    </article>
  </aside>

</section>

<!-- ═══════════════════════════════════════════════════
     FEATURED STRIP — Top 3
═══════════════════════════════════════════════════ -->
<section class="featured-strip">
  <div class="container">
    <div class="featured-grid reveal">
      <div class="featured-item">
        <span class="featured-item__num">01</span>
        <div class="featured-item__body">
          <div class="featured-item__cat">Recomendación</div>
          <h3 class="featured-item__title">Qué hacer este fin de semana en Managua sin salir de la ciudad</h3>
          <p class="featured-item__desc">Mercados de diseño, pop-ups gastronómicos y noches de jazz en el Malecón.</p>
        </div>
      </div>
      <div class="featured-item">
        <span class="featured-item__num">02</span>
        <div class="featured-item__body">
          <div class="featured-item__cat">Guía Local</div>
          <h3 class="featured-item__title">Los barrios más interesantes de Managua que no están en las guías convencionales</h3>
          <p class="featured-item__desc">Desde las galerías emergentes de Linda Vista hasta los murales de Jorge Dimitrov.</p>
        </div>
      </div>
      <div class="featured-item">
        <span class="featured-item__num">03</span>
        <div class="featured-item__body">
          <div class="featured-item__cat">Naturaleza</div>
          <h3 class="featured-item__title">Laguna de Apoyo: la reserva natural favorita de los que ya lo saben todo</h3>
          <p class="featured-item__desc">El cráter volcánico con agua termal donde Managua va a desconectarse de verdad.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: RESTAURANTES DE MANAGUA
═══════════════════════════════════════════════════ -->
<section class="sec-restaurants">
  <div class="container">
    <div class="section-hd reveal">
      <div class="section-hd__group">
        <span class="eyebrow">Gastronomía</span>
        <h2 class="section-title">Restaurantes que debes conocer</h2>
      </div>
      <a href="#" class="section-hd__link">Ver todos</a>
    </div>

    <div class="restaurants-layout">

      <!-- Feature card -->
      <article class="card card--feature reveal">
        <div class="card-img">
          <div class="card-badge">Editor's Pick</div>
          <img src="https://images.unsplash.com/photo-1544025162-d76694265947?w=800&q=80&auto=format" alt="Tawa Restaurante" loading="lazy" />
        </div>
        <div class="card-body">
          <div class="card-eyebrow">Apertura · Altamira</div>
          <h3 class="card-title">Tawa: la propuesta nicaragüense de autor que está agotando mesas cada noche</h3>
          <div class="stars">
            <svg viewBox="0 0 16 16"><path d="M8 1l1.8 3.6L14 5.3l-3 3 .7 4.1L8 10.6l-3.7 1.8.7-4.1-3-3 4.2-.7z"/></svg>
            <svg viewBox="0 0 16 16"><path d="M8 1l1.8 3.6L14 5.3l-3 3 .7 4.1L8 10.6l-3.7 1.8.7-4.1-3-3 4.2-.7z"/></svg>
            <svg viewBox="0 0 16 16"><path d="M8 1l1.8 3.6L14 5.3l-3 3 .7 4.1L8 10.6l-3.7 1.8.7-4.1-3-3 4.2-.7z"/></svg>
            <svg viewBox="0 0 16 16"><path d="M8 1l1.8 3.6L14 5.3l-3 3 .7 4.1L8 10.6l-3.7 1.8.7-4.1-3-3 4.2-.7z"/></svg>
            <svg viewBox="0 0 16 16"><path d="M8 1l1.8 3.6L14 5.3l-3 3 .7 4.1L8 10.6l-3.7 1.8.7-4.1-3-3 4.2-.7z"/></svg>
          </div>
          <p class="card-desc">El chef Marco Espinoza fusiona técnicas de alta cocina con ingredientes de mercado local: cacao de Waslala, chiltoma ahumada y mariscos del Pacífico. Menú de temporada que cambia cada mes.</p>
          <div class="card-meta">
            <span>Cocina de autor</span>
            <span class="card-meta__dot">·</span>
            <span>$$$</span>
            <span class="card-meta__dot">·</span>
            <span>Reservas requeridas</span>
          </div>
          <div class="card-tags">
            <span class="tag">Cacao</span>
            <span class="tag">Fusión</span>
            <span class="tag">Terraza</span>
          </div>
        </div>
      </article>

      <!-- Tall card -->
      <article class="card card--tall reveal reveal-delay-1">
        <div class="card-img">
          <div class="card-badge card-badge--teal">Favorito Local</div>
          <img src="https://images.unsplash.com/photo-1424847651672-bf20a4b0982b?w=600&q=80&auto=format" alt="El Rancho" loading="lazy" />
        </div>
        <div class="card-body">
          <div class="card-eyebrow">Tradicional · Carretera Masaya</div>
          <h3 class="card-title card-title--sm">La Plancha: parrilla de leña y sabor nicaragüense que nunca falla</h3>
          <p class="card-desc">Cortes premium de res local a las brasas, nacatamales del domingo y la mejor sopa de queso de la ciudad.</p>
          <div class="card-meta">
            <span>Parrilla</span>
            <span class="card-meta__dot">·</span>
            <span>$$</span>
          </div>
        </div>
      </article>

      <!-- Standard card -->
      <article class="card card--standard reveal reveal-delay-2">
        <div class="card-img">
          <img src="https://images.unsplash.com/photo-1565299585323-38d6b0865b47?w=600&q=80&auto=format" alt="Sushi Nica" loading="lazy" />
        </div>
        <div class="card-body">
          <div class="card-eyebrow">Asiático-Nica · Bolonia</div>
          <h3 class="card-title card-title--sm">Nikkei Managua: ceviche de corvina con toques japoneses</h3>
          <p class="card-desc">La fusión nikkei llega a Managua con resultados sorprendentes. Tiradito de corvina, nigiris y pisco sour artesanal.</p>
          <div class="card-meta">
            <span>Fusión</span>
            <span class="card-meta__dot">·</span>
            <span>$$$</span>
          </div>
        </div>
      </article>

      <!-- Standard card -->
      <article class="card card--standard reveal reveal-delay-3">
        <div class="card-img">
          <div class="card-badge card-badge--mustard">Nuevo</div>
          <img src="https://images.unsplash.com/photo-1528605248644-14dd04022da1?w=600&q=80&auto=format" alt="Vegano" loading="lazy" />
        </div>
        <div class="card-body">
          <div class="card-eyebrow">Plant-Based · Los Robles</div>
          <h3 class="card-title card-title--sm">Verde Raíz: gastronomía vegetal de temporada en el corazón de Los Robles</h3>
          <p class="card-desc">Ensaladas únicas con hierbas del huerto propio, bowls de quinua nica y jugos de frutas tropicales poco conocidas.</p>
          <div class="card-meta">
            <span>Vegano</span>
            <span class="card-meta__dot">·</span>
            <span>$$</span>
          </div>
        </div>
      </article>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: EDITORIAL TEAL — "Lo que define a Managua"
═══════════════════════════════════════════════════ -->
<section class="sec-editorial">
  <div class="container">
    <div class="editorial-inner">
      <div class="editorial-text reveal">
        <div class="eyebrow">Nota Editorial</div>
        <h2>Managua siempre ha sido una ciudad que se cuenta desde adentro</h2>
        <p>No hay guías turísticas que capturen lo que un managuero siente al ver el Lago Xolotlán al atardecer, o la energía de los mercados Huembes al amanecer. AgendaNica nació para contar esas historias con la precisión y el amor que merecen.</p>
        <p>Cada recomendación, cada restaurante, cada rincón fotogénico que encontrarás aquí ha sido visitado y verificado por nuestro equipo. Nada de listas genéricas. Solo lo que vale la pena.</p>
        <a href="#" class="btn-outline-ivory">Nuestra filosofía</a>
      </div>

      <div class="editorial-divider"></div>

      <div class="editorial-cards reveal reveal-delay-2">
        <div class="editorial-card">
          <div class="editorial-card__img">
            <img src="https://images.unsplash.com/photo-1455619452474-d2be8b1e70cd?w=200&q=80&auto=format" alt="Comida" loading="lazy" />
          </div>
          <div class="editorial-card__body">
            <div class="editorial-card__cat">Gastronomía</div>
            <div class="editorial-card__title">Los ingredientes olvidados que los nuevos chefs nicaragüenses están rescatando</div>
            <div class="editorial-card__meta">8 minutos · Esta semana</div>
          </div>
        </div>
        <div class="editorial-card">
          <div class="editorial-card__img">
            <img src="https://images.unsplash.com/photo-1468276311594-df7cb65d8df6?w=200&q=80&auto=format" alt="Arte" loading="lazy" />
          </div>
          <div class="editorial-card__body">
            <div class="editorial-card__cat">Arte Urbano</div>
            <div class="editorial-card__title">El mural de 300 metros que convirtió a Jorge Dimitrov en galería a cielo abierto</div>
            <div class="editorial-card__meta">6 minutos · Fotoreportaje</div>
          </div>
        </div>
        <div class="editorial-card">
          <div class="editorial-card__img">
            <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=200&q=80&auto=format" alt="Naturaleza" loading="lazy" />
          </div>
          <div class="editorial-card__body">
            <div class="editorial-card__cat">Naturaleza</div>
            <div class="editorial-card__title">Cerro Negro: la experiencia más adrenalínica a dos horas de Managua</div>
            <div class="editorial-card__meta">10 minutos · Guía de viaje</div>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: QUÉ HACER ESTE FIN DE SEMANA
═══════════════════════════════════════════════════ -->
<section class="sec-weekend">
  <div class="container">
    <div class="section-hd reveal">
      <div class="section-hd__group">
        <span class="eyebrow">Fin de Semana</span>
        <h2 class="section-title">¿Qué hacer este sábado y domingo?</h2>
      </div>
      <a href="#" class="section-hd__link">Agenda completa</a>
    </div>

    <div class="weekend-grid">
      <article class="weekend-card reveal">
        <div class="weekend-card__img">
          <img src="https://images.unsplash.com/photo-1541532713592-79a0317b6b77?w=600&q=80&auto=format" alt="Jazz" loading="lazy" />
          <div class="weekend-card__num">01</div>
        </div>
        <div class="weekend-card__body">
          <div class="weekend-card__time">Sábado · 7:00 PM</div>
          <h3 class="weekend-card__title">Jazz en el Malecón: concierto al aire libre con vista al lago</h3>
          <p class="weekend-card__desc">La quinta edición del festival que llena de música el Paseo Xolotlán. Entrada libre. Lleva tu picnic.</p>
        </div>
      </article>
      <article class="weekend-card reveal reveal-delay-1">
        <div class="weekend-card__img">
          <img src="https://images.unsplash.com/photo-1555396273-367ea4eb4db5?w=600&q=80&auto=format" alt="Feria" loading="lazy" />
          <div class="weekend-card__num">02</div>
        </div>
        <div class="weekend-card__body">
          <div class="weekend-card__time">Sábado · 9:00 AM — 4:00 PM</div>
          <h3 class="weekend-card__title">Feria de Diseñadores Locales en Plaza Inter</h3>
          <p class="weekend-card__desc">Más de 40 emprendedores con moda sostenible, artesanías contemporáneas y gastronomía de autor.</p>
        </div>
      </article>
      <article class="weekend-card reveal reveal-delay-2">
        <div class="weekend-card__img">
          <img src="https://images.unsplash.com/photo-1571902943202-507ec2618e8f?w=600&q=80&auto=format" alt="Yoga" loading="lazy" />
          <div class="weekend-card__num">03</div>
        </div>
        <div class="weekend-card__body">
          <div class="weekend-card__time">Domingo · 6:30 AM</div>
          <h3 class="weekend-card__title">Yoga al amanecer en la Laguna de Tiscapa</h3>
          <p class="weekend-card__desc">Una práctica colectiva gratuita frente al cráter volcánico. Vista de la ciudad incluida.</p>
        </div>
      </article>
      <article class="weekend-card reveal reveal-delay-3">
        <div class="weekend-card__img">
          <img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?w=600&q=80&auto=format" alt="Galería" loading="lazy" />
          <div class="weekend-card__num">04</div>
        </div>
        <div class="weekend-card__body">
          <div class="weekend-card__time">Domingo · 11:00 AM — 6:00 PM</div>
          <h3 class="weekend-card__title">Inauguración: "Volcanes de Papel" en la Galería Códice</h3>
          <p class="weekend-card__desc">La artista Sofía Rugama presenta su primera exposición individual de escultura y técnica mixta.</p>
        </div>
      </article>
    </div>

  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: ESCAPADAS
═══════════════════════════════════════════════════ -->
<section class="sec-escapadas">
  <div class="container">
    <div class="section-hd reveal">
      <div class="section-hd__group">
        <span class="eyebrow">Escapadas</span>
        <h2 class="section-title">Cerca de Managua, lejos del ruido</h2>
      </div>
      <a href="#" class="section-hd__link">Explorar rutas</a>
    </div>

    <div class="escapadas-hero reveal">
      <div class="img-wrap">
        <img src="https://images.unsplash.com/photo-1510414842594-a61c69b5ae57?w=1400&q=80&auto=format" alt="Laguna de Apoyo" loading="lazy" />
      </div>
      <div class="escapadas-hero__content">
        <div class="escapadas-hero__eyebrow">Destino de la Semana</div>
        <h3 class="escapadas-hero__title">Laguna de Apoyo: la piscina natural más perfecta de Centroamérica</h3>
        <p class="escapadas-hero__desc">A 45 minutos de Managua, este cráter volcánico lleno de agua termal y transparente es el secreto mejor guardado de Nicaragua. Guía completa para un día perfecto.</p>
        <a href="#" class="btn-solid">Leer guía completa</a>
      </div>
    </div>

    <div class="escapadas-grid">
      <article class="escapada-card reveal">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=800&q=80&auto=format" alt="Granada" loading="lazy" />
        </div>
        <div class="escapada-card__content">
          <div class="escapada-card__dist">45 min · Colonial</div>
          <div class="escapada-card__title">Granada: la ciudad más fotogénica de Nicaragua</div>
          <div class="escapada-card__tags">
            <span class="escapada-tag">Colonial</span>
            <span class="escapada-tag">Gastronomía</span>
            <span class="escapada-tag">Cultura</span>
          </div>
        </div>
      </article>
      <article class="escapada-card reveal reveal-delay-1">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1439853949212-36689e2b29f1?w=800&q=80&auto=format" alt="Playa" loading="lazy" />
        </div>
        <div class="escapada-card__content">
          <div class="escapada-card__dist">2h 30min · Playa</div>
          <div class="escapada-card__title">Playa Poneloya: olas, surf y ceviche al atardecer</div>
          <div class="escapada-card__tags">
            <span class="escapada-tag">Surf</span>
            <span class="escapada-tag">Playa</span>
            <span class="escapada-tag">Relax</span>
          </div>
        </div>
      </article>
      <article class="escapada-card reveal reveal-delay-2">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1546500840-ae38253aba9b?w=800&q=80&auto=format" alt="Montaña" loading="lazy" />
        </div>
        <div class="escapada-card__content">
          <div class="escapada-card__dist">1h 15min · Senderismo</div>
          <div class="escapada-card__title">Volcán Masaya: el cráter activo más accesible del mundo</div>
          <div class="escapada-card__tags">
            <span class="escapada-tag">Volcán</span>
            <span class="escapada-tag">Naturaleza</span>
            <span class="escapada-tag">Aventura</span>
          </div>
        </div>
      </article>
    </div>

  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: CAFÉS FAVORITOS
═══════════════════════════════════════════════════ -->
<section class="sec-cafes">
  <div class="container">
    <div class="section-hd reveal">
      <div class="section-hd__group">
        <span class="eyebrow">Cafés &amp; Tercera Ola</span>
        <h2 class="section-title">Los mejores cafés de Managua</h2>
      </div>
      <a href="#" class="section-hd__link">Ver guía completa</a>
    </div>

    <div class="cafes-scroll">
      <article class="cafe-card reveal">
        <div class="cafe-card__img">
          <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=600&q=80&auto=format" alt="Café 1" loading="lazy" />
        </div>
        <div class="cafe-card__body">
          <div class="cafe-card__num">01 —</div>
          <div class="cafe-card__name">Café Solaz</div>
          <p class="cafe-card__desc">Espresso de alta calidad con granos de Matagalpa y Jinotega. Ambiente indie, terraza con buganvilias y playlist de culto.</p>
          <div class="cafe-card__footer">
            <span class="cafe-card__zone">Bolonia</span>
            <span class="cafe-card__icon">→</span>
          </div>
        </div>
      </article>
      <article class="cafe-card reveal reveal-delay-1">
        <div class="cafe-card__img">
          <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=600&q=80&auto=format" alt="Café 2" loading="lazy" />
        </div>
        <div class="cafe-card__body">
          <div class="cafe-card__num">02 —</div>
          <div class="cafe-card__name">La Ceiba Specialty</div>
          <p class="cafe-card__desc">La primera cafetería de especialidad con proceso propio en Managua. Cata de origen todos los sábados a las 10am.</p>
          <div class="cafe-card__footer">
            <span class="cafe-card__zone">Los Robles</span>
            <span class="cafe-card__icon">→</span>
          </div>
        </div>
      </article>
      <article class="cafe-card reveal reveal-delay-2">
        <div class="cafe-card__img">
          <img src="https://images.unsplash.com/photo-1442512595331-e89e73853f31?w=600&q=80&auto=format" alt="Café 3" loading="lazy" />
        </div>
        <div class="cafe-card__body">
          <div class="cafe-card__num">03 —</div>
          <div class="cafe-card__name">Estudio Café</div>
          <p class="cafe-card__desc">Café con galería de arte y espacio coworking en una casona colonial restaurada. El más instagrameable de la ciudad sin dudas.</p>
          <div class="cafe-card__footer">
            <span class="cafe-card__zone">Altamira</span>
            <span class="cafe-card__icon">→</span>
          </div>
        </div>
      </article>
      <article class="cafe-card reveal reveal-delay-3">
        <div class="cafe-card__img">
          <img src="https://images.unsplash.com/photo-1511920170033-f8396924c348?w=600&q=80&auto=format" alt="Café 4" loading="lazy" />
        </div>
        <div class="cafe-card__body">
          <div class="cafe-card__num">04 —</div>
          <div class="cafe-card__name">El Patio del Cacao</div>
          <p class="cafe-card__desc">Chocolate artesanal de Waslala, bebidas calientes de cacao con canela y menta. También tienen el mejor croissant de la ciudad.</p>
          <div class="cafe-card__footer">
            <span class="cafe-card__zone">Colonia Centroamérica</span>
            <span class="cafe-card__icon">→</span>
          </div>
        </div>
      </article>
    </div>

  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: AGENDA CULTURAL + SIDEBAR
═══════════════════════════════════════════════════ -->
<section class="sec-cultura">
  <div class="container">
    <div class="section-hd reveal">
      <div class="section-hd__group">
        <span class="eyebrow">Cultura &amp; Ocio</span>
        <h2 class="section-title">Agenda de la ciudad</h2>
      </div>
      <a href="#" class="section-hd__link">Ver todos los eventos</a>
    </div>

    <div class="cultura-layout">
      <div class="events-list reveal">
        <div class="event-item">
          <div class="event-date">
            <span class="event-date__day">18</span>
            <span class="event-date__month">Ene</span>
          </div>
          <div class="event-info">
            <div class="event-cat">Música</div>
            <div class="event-title">Concierto de Marimba y Gaita: Raíces del Pacifico</div>
            <div class="event-where">Teatro Nacional Rubén Darío · 8:00 PM</div>
          </div>
          <a href="#" class="event-action">Más info</a>
        </div>
        <div class="event-item">
          <div class="event-date">
            <span class="event-date__day">21</span>
            <span class="event-date__month">Ene</span>
          </div>
          <div class="event-info">
            <div class="event-cat">Arte</div>
            <div class="event-title">Inauguración: "Volcanes de Papel" — Sofía Rugama</div>
            <div class="event-where">Galería Códice, Altamira · 6:00 PM</div>
          </div>
          <a href="#" class="event-action">Reservar</a>
        </div>
        <div class="event-item">
          <div class="event-date">
            <span class="event-date__day">24</span>
            <span class="event-date__month">Ene</span>
          </div>
          <div class="event-info">
            <div class="event-cat">Gastronomía</div>
            <div class="event-title">Cena de Cacao: mesa única con 8 tiempos de chocolate</div>
            <div class="event-where">Tawa Restaurante · 7:30 PM · Solo 20 cupos</div>
          </div>
          <a href="#" class="event-action">Últimas plazas</a>
        </div>
        <div class="event-item">
          <div class="event-date">
            <span class="event-date__day">25</span>
            <span class="event-date__month">Ene</span>
          </div>
          <div class="event-info">
            <div class="event-cat">Cine</div>
            <div class="event-title">Cineclub al Aire Libre: ciclo de cine latinoamericano contemporáneo</div>
            <div class="event-where">Parque Luis Alfonso Velásquez · 7:00 PM</div>
          </div>
          <a href="#" class="event-action">Gratis</a>
        </div>
        <div class="event-item">
          <div class="event-date">
            <span class="event-date__day">28</span>
            <span class="event-date__month">Ene</span>
          </div>
          <div class="event-info">
            <div class="event-cat">Mercado</div>
            <div class="event-title">Mercado de Diseñadores: edición especial de verano</div>
            <div class="event-where">Plaza Inter, Managua · 9:00 AM — 5:00 PM</div>
          </div>
          <a href="#" class="event-action">Más info</a>
        </div>
      </div>

      <aside class="cultura-sidebar reveal reveal-delay-2">
        <div class="sidebar-widget">
          <div class="sidebar-widget__title">
            Lo más leído
            <span>Esta semana</span>
          </div>
          <div class="popular-item">
            <span class="popular-item__num">1</span>
            <div>
              <div class="popular-item__title">Los 7 cafés más bonitos de Managua para trabajar o soñar</div>
              <div class="popular-item__cat">Cafés · Guía</div>
            </div>
          </div>
          <div class="popular-item">
            <span class="popular-item__num">2</span>
            <div>
              <div class="popular-item__title">Laguna de Apoyo: guía completa para el día perfecto</div>
              <div class="popular-item__cat">Escapadas</div>
            </div>
          </div>
          <div class="popular-item">
            <span class="popular-item__num">3</span>
            <div>
              <div class="popular-item__title">Tawa: el restaurante de autor que está agotando mesas</div>
              <div class="popular-item__cat">Gastronomía</div>
            </div>
          </div>
          <div class="popular-item">
            <span class="popular-item__num">4</span>
            <div>
              <div class="popular-item__title">Granada en un día: el itinerario que no falla</div>
              <div class="popular-item__cat">Escapadas</div>
            </div>
          </div>
        </div>

        <div class="sidebar-widget">
          <div class="sidebar-widget__title">Síguenos</div>
          <div class="social-links">
            <a href="#" class="social-link">📸 Instagram</a>
            <a href="#" class="social-link">🎵 TikTok</a>
            <a href="#" class="social-link">📘 Facebook</a>
            <a href="#" class="social-link">📧 Newsletter</a>
          </div>
        </div>

        <div class="sidebar-widget" style="background: var(--teal); border-color: var(--teal); color: var(--ivory);">
          <div class="sidebar-widget__title" style="color: var(--ivory); border-color: rgba(245,241,232,0.3);">
            ¿Conoces un rincón especial?
          </div>
          <p style="font-size: 0.82rem; line-height: 1.65; opacity: 0.85; margin-bottom: 1.25rem;">Envianos tu recomendación. Las mejores sugerencias aparecen en nuestra edición semanal.</p>
          <a href="#" class="btn-outline-ivory" style="width: 100%; justify-content: center; text-align: center;">Enviar sugerencia</a>
        </div>
      </aside>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: RINCONES FOTOGÉNICOS
═══════════════════════════════════════════════════ -->
<section class="sec-photo">
  <div class="container">
    <div class="section-hd reveal">
      <div class="section-hd__group">
        <span class="eyebrow">Fotogénico</span>
        <h2 class="section-title">Rincones que tienes que fotografiar</h2>
      </div>
      <a href="#" class="section-hd__link">Ver todos</a>
    </div>

    <div class="photo-masonry reveal">
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1501854140801-50d01698950b?w=800&q=80&auto=format" alt="Lago Xolotlán" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Lago Xolotlán al atardecer</div>
          <div class="photo-item__tag">Malecón de Managua</div>
        </div>
      </div>
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1525625293386-3f8f99389edd?w=600&q=80&auto=format" alt="Colonial" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Calle de los Poetas</div>
          <div class="photo-item__tag">Ciudad Jardín</div>
        </div>
      </div>
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1441974231531-c6227db76b6e?w=600&q=80&auto=format" alt="Naturaleza" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Reserva Chocoyero</div>
          <div class="photo-item__tag">35 min de Managua</div>
        </div>
      </div>
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1519682577862-22b62b24e493?w=600&q=80&auto=format" alt="Mercado" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Mercado Huembes</div>
          <div class="photo-item__tag">Sur de Managua</div>
        </div>
      </div>
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1470252649378-9c29740c9fa8?w=600&q=80&auto=format" alt="Amanecer" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Volcán Masaya al amanecer</div>
          <div class="photo-item__tag">30 min de Managua</div>
        </div>
      </div>
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1539650116574-8efeb43e2750?w=600&q=80&auto=format" alt="Cafetal" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Cafetales de Matagalpa</div>
          <div class="photo-item__tag">2h de Managua</div>
        </div>
      </div>
      <div class="photo-item">
        <div class="img-wrap">
          <img src="https://images.unsplash.com/photo-1508739773434-c26b3d09e071?w=600&q=80&auto=format" alt="Playa" loading="lazy" />
        </div>
        <div class="photo-item__overlay">
          <div class="photo-item__place">Playa San Juan del Sur</div>
          <div class="photo-item__tag">3h de Managua</div>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     SECTION: NEWSLETTER
═══════════════════════════════════════════════════ -->
<section class="sec-newsletter" id="newsletter">
  <div class="container">
    <div class="newsletter-inner">
      <div class="newsletter-text reveal">
        <div class="eyebrow">Newsletter Semanal</div>
        <h2>Lo mejor de Managua, en tu bandeja de entrada</h2>
        <p>Cada viernes, una selección curada de restaurantes nuevos, eventos del fin de semana, escapadas cercanas y rincones que aún no conoces. Sin spam. Solo lo que vale.</p>
        <div class="newsletter-perks">
          <div class="perk">
            <div class="perk__icon">📍</div>
            Recomendaciones geolocalizadas por barrio
          </div>
          <div class="perk">
            <div class="perk__icon">🎟</div>
            Acceso anticipado a eventos y aforos limitados
          </div>
          <div class="perk">
            <div class="perk__icon">☕</div>
            Guías exclusivas para suscriptores cada mes
          </div>
        </div>
      </div>
      <div class="newsletter-form reveal reveal-delay-2">
        <div class="form-group">
          <input type="email" class="form-input" placeholder="tu@correo.com" id="emailInput" />
          <button class="form-submit" id="subBtn">Suscribirse</button>
        </div>
        <p class="form-note">Más de 12,000 managuenses ya están suscritos. Cancela cuando quieras.</p>
        <p id="subMsg" style="margin-top:1rem; font-size:0.82rem; font-weight:600; display:none;">¡Perfecto! Ya estás dentro 🎉</p>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════
     FOOTER
═══════════════════════════════════════════════════ -->
<footer class="site-footer">
  <div class="container">
    <div class="footer-grid">
      <div class="footer-brand">
        <a href="#" class="logo">
          <div class="logo__mark">
            <svg viewBox="0 0 16 16"><path d="M8 1.5C4.4 1.5 1.5 4.4 1.5 8c0 1.8.7 3.5 1.8 4.7L8 8l4.7 4.7c1.1-1.2 1.8-2.9 1.8-4.7 0-3.6-2.9-6.5-6.5-6.5z"/></svg>
          </div>
          <span class="logo__text">Agenda<span>Nica</span></span>
        </a>
        <p>La guía editorial de ocio, cultura y gastronomía de Managua y Nicaragua. Hecho con amor desde la capital.</p>
        <div class="footer-socials">
          <a href="#" class="footer-social">IG</a>
          <a href="#" class="footer-social">TK</a>
          <a href="#" class="footer-social">FB</a>
          <a href="#" class="footer-social">YT</a>
          <a href="#" class="footer-social">📧</a>
        </div>
      </div>

      <div class="footer-col">
        <h4>Explorar</h4>
        <div class="footer-links">
          <a href="#">Restaurantes de Managua</a>
          <a href="#">Cafés y Tercera Ola</a>
          <a href="#">Bares y Vida Nocturna</a>
          <a href="#">Escapadas Cercanas</a>
          <a href="#">Mercados y Artesanías</a>
          <a href="#">Naturaleza y Aventura</a>
          <a href="#">Arte y Cultura</a>
          <a href="#">Música y Festivales</a>
        </div>
      </div>

      <div class="footer-col">
        <h4>Guías</h4>
        <div class="footer-links">
          <a href="#">Guía de Managua</a>
          <a href="#">Guía de Granada</a>
          <a href="#">Guía de León</a>
          <a href="#">Volcanes de Nicaragua</a>
          <a href="#">Playas del Pacífico</a>
          <a href="#">Ruta del Café</a>
          <a href="#">Turismo Gastronómico</a>
          <a href="#">Fin de Semana Perfecto</a>
        </div>
      </div>

      <div class="footer-col">
        <h4>Recientes</h4>
        <div class="footer-recent">
          <div class="footer-post">
            <div class="footer-post__img">
              <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=120&q=80&auto=format" alt="" loading="lazy" />
            </div>
            <div>
              <div class="footer-post__title">La ruta del café que no te puedes perder este verano</div>
              <div class="footer-post__date">14 Ene 2025</div>
            </div>
          </div>
          <div class="footer-post">
            <div class="footer-post__img">
              <img src="https://images.unsplash.com/photo-1544025162-d76694265947?w=120&q=80&auto=format" alt="" loading="lazy" />
            </div>
            <div>
              <div class="footer-post__title">Tawa: la cocina de autor que está reinventando Managua</div>
              <div class="footer-post__date">10 Ene 2025</div>
            </div>
          </div>
          <div class="footer-post">
            <div class="footer-post__img">
              <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=120&q=80&auto=format" alt="" loading="lazy" />
            </div>
            <div>
              <div class="footer-post__title">Granada en 24 horas: el itinerario definitivo</div>
              <div class="footer-post__date">7 Ene 2025</div>
            </div>
          </div>
        </div>
      </div>

    </div>

    <div class="footer-bottom">
      <span class="footer-bottom__copy">© 2025 AgendaNica. Todos los derechos reservados. Managua, Nicaragua.</span>
      <div class="footer-bottom__links">
        <a href="#">Privacidad</a>
        <a href="#">Términos</a>
        <a href="#">Publicidad</a>
        <a href="#">Contacto</a>
        <a href="#">Colaborar</a>
      </div>
    </div>
  </div>
</footer>

<!-- Scroll to top -->
<button class="scroll-top" id="scrollTop" title="Volver arriba">
  <svg viewBox="0 0 24 24"><path d="M18 15l-6-6-6 6"/></svg>
</button>

<!-- ═══════════════════════════════════════════════════
     JAVASCRIPT
═══════════════════════════════════════════════════ -->
<script>
  // ─── Header scroll ───────────────────────────────
  const header = document.getElementById('siteHeader');
  const scrollTopBtn = document.getElementById('scrollTop');

  window.addEventListener('scroll', () => {
    const y = window.scrollY;
    header.classList.toggle('scrolled', y > 40);
    scrollTopBtn.classList.toggle('visible', y > 400);
  });

  scrollTopBtn.addEventListener('click', () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  });

  // ─── Mobile menu ─────────────────────────────────
  const burgerBtn = document.getElementById('burgerBtn');
  const mobileMenu = document.getElementById('mobileMenu');

  burgerBtn.addEventListener('click', () => {
    mobileMenu.classList.toggle('open');
    const spans = burgerBtn.querySelectorAll('span');
    const isOpen = mobileMenu.classList.contains('open');
    spans[0].style.transform = isOpen ? 'rotate(45deg) translate(4.5px, 4.5px)' : '';
    spans[1].style.opacity   = isOpen ? '0' : '1';
    spans[2].style.transform = isOpen ? 'rotate(-45deg) translate(4.5px, -4.5px)' : '';
  });

  // ─── Search overlay ───────────────────────────────
  const searchBtn     = document.getElementById('searchBtn');
  const searchOverlay = document.getElementById('searchOverlay');
  const searchClose   = document.getElementById('searchClose');
  const searchInput   = document.getElementById('searchInput');

  searchBtn.addEventListener('click', () => {
    searchOverlay.classList.add('open');
    setTimeout(() => searchInput.focus(), 200);
  });
  searchClose.addEventListener('click', () => searchOverlay.classList.remove('open'));
  searchOverlay.addEventListener('click', e => {
    if (e.target === searchOverlay) searchOverlay.classList.remove('open');
  });
  document.addEventListener('keydown', e => {
    if (e.key === 'Escape') searchOverlay.classList.remove('open');
  });

  // ─── Newsletter ───────────────────────────────────
  document.getElementById('subBtn').addEventListener('click', () => {
    const val = document.getElementById('emailInput').value.trim();
    if (val && val.includes('@')) {
      document.getElementById('subMsg').style.display = 'block';
      document.getElementById('emailInput').value = '';
    }
  });

  // ─── Scroll reveal ────────────────────────────────
  const revealEls = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.08, rootMargin: '0px 0px -40px 0px' });

  revealEls.forEach(el => observer.observe(el));

  // ─── Ticker clone for seamless loop ──────────────
  const track = document.getElementById('tickerTrack');
  if (track) {
    // Already doubled in HTML for seamless scroll
  }
</script>

</body>
</html>
