<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>South America Expedition 2026</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Zen+Maru+Gothic:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --fuji-blue: #1D4ED8;
      --fuji-light: #EFF6FF;
      --snow-white: #FFFFFF;
      --warm-gray-bg: #F8FAFC;
      --warm-gray-card: #FFFFFF;
      --warm-gray-border: #E2E8F0;
      --warm-gray-text: #1E293B;
      --warm-gray-muted: #64748B;
      --radius: 16px;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Zen Maru Gothic', sans-serif;
      background: var(--warm-gray-bg);
      color: var(--warm-gray-text);
      padding-bottom: 80px;
    }

    /* HEADER */
    .app-header {
      background: var(--fuji-blue);
      color: var(--snow-white);
      padding: 24px 20px 20px;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 4px 12px rgba(29, 78, 216, 0.15);
    }
    .app-header h1 { font-size: 1.35rem; font-weight: 700; }
    .app-header p { font-size: 0.85rem; opacity: 0.9; margin-top: 4px; }

    /* NAVIGATION TABS */
    .tab-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: var(--snow-white);
      display: flex;
      justify-content: space-around;
      border-top: 1px solid var(--warm-gray-border);
      padding: 10px 0;
      z-index: 100;
    }
    .tab-btn {
      border: none;
      background: none;
      font-family: inherit;
      font-size: 0.8rem;
      font-weight: 500;
      color: var(--warm-gray-muted);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      width: 33%;
      cursor: pointer;
    }
    .tab-btn.active { color: var(--fuji-blue); font-weight: 700; }

    /* CONTENT LAYOUT */
    .tab-content { display: none; padding: 16px; max-width: 600px; margin: 0 auto; }
    .tab-content.active { display: block; }

    /* DAY CARD */
    .day-card {
      background: var(--warm-gray-card);
      border-radius: var(--radius);
      padding: 18px;
      margin-bottom: 20px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.03);
      border: 1px solid var(--warm-gray-border);
    }
    .day-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid var(--warm-gray-bg);
      padding-bottom: 10px;
      margin-bottom: 14px;
    }
    .day-date { font-weight: 700; color: var(--fuji-blue); font-size: 1.05rem; }
    .day-dest { font-size: 0.85rem; background: var(--fuji-light); color: var(--fuji-blue); padding: 4px 10px; border-radius: 20px; font-weight: 500; }

    /* TIME BLOCKS */
    .time-block {
      margin-bottom: 12px;
      padding-left: 12px;
      border-left: 3px solid var(--fuji-blue);
    }
    .time-title { font-size: 0.8rem; font-weight: 700; color: var(--fuji-blue); text-transform: uppercase; margin-bottom: 2px; }
    .time-desc { font-size: 0.85rem; color: var(--warm-gray-text); line-height: 1.4; }

    .map-btn {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      background: var(--fuji-light);
      color: var(--fuji-blue);
      text-decoration: none;
      font-size: 0.72rem;
      padding: 3px 8px;
      border-radius: 6px;
      margin-left: 6px;
      font-weight: 500;
    }

    .info-box {
      background: #F1F5F9;
      border-radius: 8px;
      padding: 10px;
      font-size: 0.78rem;
      color: var(--warm-gray-muted);
      margin-top: 10px;
      line-height: 1.4;
    }

    .day-map-iframe {
      width: 100%;
      height: 200px;
      border: none;
      border-radius: 12px;
      margin-top: 14px;
      background: #e5e3df;
    }

    /* WEATHER CARD */
    .weather-card {
      background: var(--snow-white);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid var(--warm-gray-border);
    }
    .weather-city { font-weight: 700; font-size: 0.9rem; }
    .weather-temp { font-size: 1.1rem; font-weight: 700; color: var(--fuji-blue); }
    .weather-details { font-size: 0.75rem; color: var(--warm-gray-muted); }

    /* GUIDE SECTION */
    .guide-section {
      background: var(--snow-white);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 16px;
      border: 1px solid var(--warm-gray-border);
    }
    .guide-title {
      font-size: 1rem;
      font-weight: 700;
      margin-bottom: 12px;
      color: var(--fuji-blue);
    }

    .checklist { list-style: none; }
    .check-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 8px 0;
      border-bottom: 1px dashed var(--warm-gray-border);
      font-size: 0.85rem;
    }
    .check-left { display: flex; align-items: center; gap: 8px; }
    .qty-controls { display: flex; align-items: center; gap: 6px; }
    .qty-btn {
      border: 1px solid var(--warm-gray-border);
      background: var(--warm-gray-bg);
      width: 22px;
      height: 22px;
      border-radius: 4px;
      cursor: pointer;
    }
    .add-form { display: flex; gap: 8px; margin-top: 12px; }
    .add-input {
      flex: 1;
      padding: 6px 10px;
      border: 1px solid var(--warm-gray-border);
      border-radius: 8px;
      font-family: inherit;
      font-size: 0.8rem;
    }
    .btn-action {
      background: var(--fuji-blue);
      color: var(--snow-white);
      border: none;
      padding: 6px 12px;
      border-radius: 8px;
      font-size: 0.8rem;
      cursor: pointer;
      font-weight: 500;
    }

    details { margin-bottom: 12px; border-bottom: 1px solid var(--warm-gray-border); padding-bottom: 8px; }
    summary { font-weight: 700; font-size: 0.85rem; cursor: pointer; padding: 4px 0; color: var(--warm-gray-text); }
    .details-content { font-size: 0.8rem; color: var(--warm-gray-muted); padding: 8px 0; line-height: 1.5; }

    .hotel-card {
      background: var(--warm-gray-bg);
      border-radius: 8px;
      padding: 10px;
      margin-bottom: 8px;
    }
    .hotel-name { font-weight: 700; color: var(--fuji-blue); margin-bottom: 4px; }
  </style>
</head>
<body>

  <header class="app-header">
    <h1>South America Expedition</h1>
    <p>Oct 2, 2026 – Oct 16, 2026 | Chile • Argentina • Uruguay</p>
  </header>

  <nav class="tab-nav">
    <button class="tab-btn active" onclick="switchTab('itinerary')">
      <span>📅</span>
      <span>Itinerary</span>
    </button>
    <button class="tab-btn" onclick="switchTab('weather')">
      <span>🌤️</span>
      <span>Weather</span>
    </button>
    <button class="tab-btn" onclick="switchTab('guide')">
      <span>🧰</span>
      <span>Guide</span>
    </button>
  </nav>

  <main id="itinerary" class="tab-content active">

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 2 (Fri)</span>
        <span class="day-dest">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title">All Day / Flight Options</div>
        <div class="time-desc">
          Arrival in Santiago (Flight options A–E). Stay in Santiago if arriving early.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Santiago+Chile" target="_blank">📍 Santiago Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Santiago,Chile&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 3 (Sat)</span>
        <span class="day-dest">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc
