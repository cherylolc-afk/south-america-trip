<!DOCTYPE html>
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
      --beige-bg: #F4EFEA;
      --beige-card: #FFFFFF;
      --beige-border: #E6DCD3;
      --beige-accent: #C8B29B;
      --terracotta-primary: #8C6D58;
      --warm-dark: #4A3E3D;
      --warm-muted: #7A6F6D;
      --white: #FFFFFF;
      --radius: 16px;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Zen Maru Gothic', sans-serif;
      background: var(--beige-bg);
      color: var(--warm-dark);
      padding-bottom: 85px;
    }

    /* Editable subtle hint state */
    [contenteditable="true"] {
      outline: none;
      transition: background-color 0.2s ease, box-shadow 0.2s ease;
      border-radius: 4px;
    }
    [contenteditable="true"]:hover {
      background-color: rgba(200, 178, 155, 0.15);
    }
    [contenteditable="true"]:focus {
      background-color: rgba(200, 178, 155, 0.25);
      box-shadow: 0 0 0 2px var(--terracotta-primary);
    }

    /* HEADER */
    .app-header {
      background: var(--terracotta-primary);
      color: var(--white);
      padding: 16px 16px 12px;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 4px 12px rgba(140, 109, 88, 0.15);
    }
    .app-header h1 { font-size: 1.2rem; font-weight: 700; }
    .app-header p { font-size: 0.75rem; opacity: 0.9; margin-top: 2px; }

    /* DATE SELECTOR BAR */
    .date-bar-wrapper {
      background: #EBE3DB;
      border-bottom: 1px solid var(--beige-border);
      position: sticky;
      top: 57px;
      z-index: 99;
    }
    .date-bar {
      display: flex;
      flex-wrap: nowrap;
      overflow-x: auto;
      overflow-y: hidden;
      -webkit-overflow-scrolling: touch;
      touch-action: pan-x;
      padding: 10px 14px;
      gap: 8px;
      scrollbar-width: none;
    }
    .date-bar::-webkit-scrollbar { display: none; }
    .date-chip {
      flex: 0 0 auto;
      white-space: nowrap;
      background: var(--white);
      border: 1px solid var(--beige-border);
      color: var(--warm-dark);
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 0.78rem;
      font-weight: 500;
      cursor: pointer;
      user-select: none;
    }
    .date-chip.active {
      background: var(--terracotta-primary);
      color: var(--white);
      border-color: var(--terracotta-primary);
      font-weight: 700;
    }

    /* BOTTOM NAVIGATION TABS */
    .tab-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: var(--white);
      display: flex;
      justify-content: space-around;
      border-top: 1px solid var(--beige-border);
      padding: 8px 0;
      z-index: 100;
    }
    .tab-btn {
      border: none;
      background: none;
      font-family: inherit;
      font-size: 0.7rem;
      font-weight: 500;
      color: var(--warm-muted);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 2px;
      width: 20%;
      cursor: pointer;
    }
    .tab-btn.active { color: var(--terracotta-primary); font-weight: 700; }

    /* CONTENT LAYOUT */
    .tab-content { display: none; padding: 16px; max-width: 600px; margin: 0 auto; }
    .tab-content.active { display: block; }

    /* GUIDE SECTION & CARDS */
    .guide-section {
      background: var(--white);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 16px;
      border: 1px solid var(--beige-border);
    }
    .guide-title {
      font-size: 0.95rem;
      font-weight: 700;
      margin-bottom: 12px;
      color: var(--terracotta-primary);
    }

    /* MASTER OVERVIEW TABLE */
    .overview-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.8rem;
    }
    .overview-table th {
      background: var(--beige-bg);
      color: var(--terracotta-primary);
      text-align: left;
      padding: 8px 10px;
      font-weight: 700;
      border-bottom: 1px solid var(--beige-border);
    }
    .overview-table td {
      padding: 8px 10px;
      border-bottom: 1px dashed var(--beige-border);
      color: var(--warm-dark);
      vertical-align: top;
    }
    .overview-table tr:last-child td { border-bottom: none; }

    /* DAY CARD */
    .day-card {
      display: none;
      background: var(--beige-card);
      border-radius: var(--radius);
      padding: 18px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.03);
      border: 1px solid var(--beige-border);
    }
    .day-card.active { display: block; }
    .day-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid var(--beige-bg);
      padding-bottom: 10px;
      margin-bottom: 14px;
    }
    .day-date { font-weight: 700; color: var(--terracotta-primary); font-size: 1.05rem; }
    .day-dest { font-size: 0.8rem; background: var(--beige-bg); color: var(--terracotta-primary); padding: 4px 10px; border-radius: 20px; font-weight: 500; }

    .time-block {
      margin-bottom: 12px;
      padding-left: 12px;
      border-left: 3px solid var(--terracotta-primary);
    }
    .time-title { font-size: 0.78rem; font-weight: 700; color: var(--terracotta-primary); text-transform: uppercase; margin-bottom: 2px; }
    .time-desc { font-size: 0.85rem; color: var(--warm-dark); line-height: 1.4; }

    .map-btn {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      background: var(--beige-bg);
      color: var(--terracotta-primary);
      text-decoration: none;
      font-size: 0.72rem;
      padding: 2px 7px;
      border-radius: 6px;
      margin-left: 4px;
      font-weight: 500;
      border: 1px solid var(--beige-border);
    }

    .day-map-iframe {
      width: 100%;
      height: 180px;
      border: none;
      border-radius: 12px;
      margin-top: 12px;
      background: #E5E3DF;
    }

    /* WEATHER CARDS */
    .weather-card-link {
      text-decoration: none;
      color: inherit;
      display: block;
      margin-bottom: 10px;
    }
    .weather-card {
      background: var(--white);
      border-radius: var(--radius);
      padding: 14px 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid var(--beige-border);
      transition: border-color 0.2s;
    }
    .weather-card:hover { border-color: var(--terracotta-primary); }
    .weather-left { display: flex; align-items: center; gap: 12px; }
    .weather-icon { font-size: 1.8rem; }
    .weather-date { font-size: 0.75rem; color: var(--warm-muted); font-weight: 500; }
    .weather-city { font-weight: 700; font-size: 0.88rem; color: var(--warm-dark); }
    .weather-desc { font-size: 0.75rem; color: var(--warm-muted); }
    .weather-temp-box { text-align: right; }
    .weather-max { font-size: 1.05rem; font-weight: 700; color: var(--terracotta-primary); }
    .weather-min { font-size: 0.75rem; color: var(--warm-muted); }

    /* CHECKLISTS & CARDS */
    .checklist { list-style: none; }
    .check-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 8px 0;
      border-bottom: 1px dashed var(--beige-border);
      font-size: 0.83rem;
    }
    .check-left { display: flex; align-items: center; gap: 8px; flex: 1; }
    .qty-controls { display: flex; align-items: center; gap: 5px; }
    .qty-btn {
      border: 1px solid var(--beige-border);
      background: var(--beige-bg);
      width: 22px;
      height: 22px;
      border-radius: 4px;
      cursor: pointer;
    }
    .add-form { display: flex; gap: 8px; margin-top: 10px; }
    .add-input {
      flex: 1;
      padding: 6px 10px;
      border: 1px solid var(--beige-border);
      border-radius: 8px;
      font-family: inherit;
      font-size: 0.8rem;
    }
    .btn-action {
      background: var(--terracotta-primary);
      color: var(--white);
      border: none;
      padding: 6px 12px;
      border-radius: 8px;
      font-size: 0.8rem;
      cursor: pointer;
      font-weight: 500;
    }

    .item-card {
      background: var(--beige-bg);
      border-radius: 8px;
      padding: 10px 12px;
      margin-bottom: 10px;
      border: 1px solid var(--beige-border);
    }
    .item-card-header {
      font-weight: 700;
      color: var(--terracotta-primary);
      font-size: 0.88rem;
      margin-bottom: 4px;
    }
    .flight-option {
      font-size: 0.81rem;
      color: var(--warm-dark);
      padding: 3px 0;
      border-bottom: 1px dashed rgba(230, 220, 211, 0.7);
    }
    .flight-option:last-child { border-bottom: none; }
    .pref-tag {
      background: var(--terracotta-primary);
      color: var(--white);
      font-size: 0.65rem;
      padding: 1px 5px;
      border-radius: 4px;
      font-weight: bold;
      margin-left: 4px;
    }

    .tip-category {
      font-weight: 700;
      color: var(--terracotta-primary);
      margin-top: 12px;
      margin-bottom: 4px;
      font-size: 0.88rem;
      border-bottom: 1px solid var(--beige-border);
      padding-bottom: 2px;
    }
    .tip-category:first-child { margin-top: 0; }
    .tip-item {
      font-size: 0.8rem;
      line-height: 1.45;
      color: var(--warm-dark);
      margin-bottom: 6px;
    }
  </style>
</head>
<body>

  <header class="app-header">
    <h1 contenteditable="true">South America Expedition</h1>
    <p contenteditable="true">Oct 2, 2026 – Oct 16, 2026 | Chile • Argentina • Uruguay</p>
  </header>

  <nav class="tab-nav">
    <button class="tab-btn active" onclick="switchTab('todo')">
      <span>☑️</span>
      <span>To-Do List</span>
    </button>
    <button class="tab-btn" onclick="switchTab('weather')">
      <span>🌤️</span>
      <span>Weather</span>
    </button>
    <button class="tab-btn" onclick="switchTab('itinerary')">
      <span>📅</span>
      <span>Itinerary</span>
    </button>
    <button class="tab-btn" onclick="switchTab('flights')">
      <span>✈️</span>
      <span>Flights</span>
    </button>
    <button class="tab-btn" onclick="switchTab('hotels')">
      <span>🏨</span>
      <span>Hotels & Tips</span>
    </button>
  </nav>

  <main id="todo" class="tab-content active">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true">🎟️ Bookings Checklist</div>
      <ul class="checklist" id="tours-list"></ul>
      <div class="add-form">
        <input type="text" id="tours-input" class="add-input" placeholder="Add booking item...">
        <button class="btn-action" onclick="addItem('tours')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title" contenteditable="true">🎒 Carry-On Packing List</div>
      <ul class="checklist" id="carryon-list"></ul>
      <div class="add-form">
        <input type="text" id="carryon-input" class="add-input" placeholder="Add carry-on item...">
        <button class="btn-action" onclick="addItem('carryon')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title" contenteditable="true">🧳 Checked Bag Packing List</div>
      <ul class="checklist" id="checkin-list"></ul>
      <div class="add-form">
        <input type="text" id="checkin-input" class="add-input" placeholder="Add checked item...">
        <button class="btn-action" onclick="addItem('checkin')">Add</button>
      </div>
    </div>
  </main>

  <main id="weather" class="tab-content">
    <a href="https://www.meteoblue.com/en/weather/forecast/week/santiago-de-chile_chile_3871336" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 2</div>
            <div class="weather-city" contenteditable="true">Santiago, Chile ↗</div>
            <div class="weather-desc" contenteditable="true">Clear & Sunny</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">20°C</div>
          <div class="weather-min" contenteditable="true">7°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.meteoblue.com/en/weather/forecast/week/santiago-de-chile_chile_3871336" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 3</div>
            <div class="weather-city" contenteditable="true">Santiago, Chile ↗</div>
            <div class="weather-desc" contenteditable="true">Warm & Pleasant</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">22°C</div>
          <div class="weather-min" contenteditable="true">8°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 4</div>
            <div class="weather-city" contenteditable="true">San Pedro de Atacama ↗</div>
            <div class="weather-desc" contenteditable="true">Dry & Intense Sun</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">20°C</div>
          <div class="weather-min" contenteditable="true">3°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 5</div>
            <div class="weather-city" contenteditable="true">Atacama Salt Flats ↗</div>
            <div class="weather-desc" contenteditable="true">Sunny / Clear Skies</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">21°C</div>
          <div class="weather-min" contenteditable="true">4°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">💨</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 6</div>
            <div class="weather-city" contenteditable="true">Altiplanic Lagoons ↗</div>
            <div class="weather-desc" contenteditable="true">High Altitude Winds</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">14°C</div>
          <div class="weather-min" contenteditable="true">-2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">❄️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 7</div>
            <div class="weather-city" contenteditable="true">El Tatio Geysers → Santiago ↗</div>
            <div class="weather-desc" contenteditable="true">Freezing Sunrise / Mild PM</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">18°C</div>
          <div class="weather-min" contenteditable="true">-4°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 8</div>
            <div class="weather-city" contenteditable="true">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true">Partly Cloudy</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">19°C</div>
          <div class="weather-min" contenteditable="true">11°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/ushuaia/7180/weather-forecast/7180" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌧️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 9</div>
            <div class="weather-city" contenteditable="true">Ushuaia, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true">Chilly / Windy</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">7°C</div>
          <div class="weather-min" contenteditable="true">1°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/ushuaia/7180/weather-forecast/7180" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 10</div>
            <div class="weather-city" contenteditable="true">Ushuaia (Beagle Channel) ↗</div>
            <div class="weather-desc" contenteditable="true">Cool / Coastal Breeze</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">8°C</div>
          <div class="weather-min" contenteditable="true">2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/el-calafate/7123/weather-forecast/7123" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">💨</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 11</div>
            <div class="weather-city" contenteditable="true">El Calafate, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true">Breezy & Cool</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">11°C</div>
          <div class="weather-min" contenteditable="true">2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/el-calafate/7123/weather-forecast/7123" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">❄️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 12</div>
            <div class="weather-city" contenteditable="true">Perito Moreno Glacier ↗</div>
            <div class="weather-desc" contenteditable="true">Cold Glacier Winds</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">9°C</div>
          <div class="weather-min" contenteditable="true">1°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 13</div>
            <div class="weather-city" contenteditable="true">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true">Warm & Sunny</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">21°C</div>
          <div class="weather-min" contenteditable="true">12°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/uy/colonia-del-sacramento/352467/weather-forecast/352467" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 14</div>
            <div class="weather-city" contenteditable="true">Colonia, Uruguay ↗</div>
            <div class="weather-desc" contenteditable="true">Pleasant Coastal Weather</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">20°C</div>
          <div class="weather-min" contenteditable="true">13°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 15</div>
            <div class="weather-city" contenteditable="true">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true">Mostly Clear</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">22°C</div>
          <div class="weather-min" contenteditable="true">13°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date" contenteditable="true">Oct 16</div>
            <div class="weather-city" contenteditable="true">Buenos Aires Departure ↗</div>
            <div class="weather-desc" contenteditable="true">Mild</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true">20°C</div>
          <div class="weather-min" contenteditable="true">12°C</div>
        </div>
      </div>
    </a>
  </main>

  <main id="itinerary" class="tab-content">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true">📍 Master Overview & Quick Summary</div>
      <table class="overview-table">
        <thead>
          <tr>
            <th contenteditable="true">Date / DoW</th>
            <th contenteditable="true">Location</th>
            <th contenteditable="true">Key Highlights & Activities</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td contenteditable="true"><b>Oct 2</b> (Fri)</td>
            <td contenteditable="true">Santiago</td>
            <td contenteditable="true">Long-haul arrival, hotel check-in / rest</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 3</b> (Sat)</td>
            <td contenteditable="true">Santiago</td>
            <td contenteditable="true">Barrio Lastarria, Santa Lucía, Bellavista night</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 4</b> (Sun)</td>
            <td contenteditable="true">Atacama</td>
            <td contenteditable="true">Flight to Calama, Death Valley, Moon Valley sunset</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 5</b> (Mon)</td>
            <td contenteditable="true">Atacama</td>
            <td contenteditable="true">Baltinache salt pools, Cejar floating, Laguna Chaxa</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 6</b> (Tue)</td>
            <td contenteditable="true">Atacama</td>
            <td contenteditable="true">Miscanti & Miñiques Lagoons, Piedras Rojas</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 7</b> (Wed)</td>
            <td contenteditable="true">Transit / Santiago</td>
            <td contenteditable="true">El Tatio Geysers sunrise, fly back to Santiago</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 8</b> (Thu)</td>
            <td contenteditable="true">Buenos Aires</td>
            <td contenteditable="true">Fly to BA, Recoleta neighborhood stroll</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 9</b> (Fri)</td>
            <td contenteditable="true">Ushuaia</td>
            <td contenteditable="true">Fly to Ushuaia, Beagle Channel waterfront</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 10</b> (Sat)</td>
            <td contenteditable="true">Ushuaia</td>
            <td contenteditable="true">Tierra del Fuego National Park, Isla Martillo Penguins</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 11</b> (Sun)</td>
            <td contenteditable="true">El Calafate</td>
            <td contenteditable="true">Fly to El Calafate, Glaciarium Ice Museum</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 12</b> (Mon)</td>
            <td contenteditable="true">El Calafate</td>
            <td contenteditable="true">Full-day Perito Moreno Glacier mini-trekking</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 13</b> (Tue)</td>
            <td contenteditable="true">Buenos Aires</td>
            <td contenteditable="true">Fly to BA, Recoleta Cemetery, Teatro Colón, Tango Show</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 14</b> (Wed)</td>
            <td contenteditable="true">Uruguay Day Trip</td>
            <td contenteditable="true">Day ferry to Colonia del Sacramento, historic tour</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 15</b> (Thu)</td>
            <td contenteditable="true">Buenos Aires</td>
            <td contenteditable="true">La Boca Caminito, San Telmo, Plaza de Mayo, Café Tortoni</td>
          </tr>
          <tr>
            <td contenteditable="true"><b>Oct 16</b> (Fri)</td>
            <td contenteditable="true">Departure</td>
            <td contenteditable="true">Final city sights, souvenir shopping, departure flight</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="date-bar-wrapper">
      <div class="date-bar" id="date-bar">
        <button class="date-chip active" onclick="showDay('day-oct2')">Oct 2</button>
        <button class="date-chip" onclick="showDay('day-oct3')">Oct 3</button>
        <button class="date-chip" onclick="showDay('day-oct4')">Oct 4</button>
        <button class="date-chip" onclick="showDay('day-oct5')">Oct 5</button>
        <button class="date-chip" onclick="showDay('day-oct6')">Oct 6</button>
        <button class="date-chip" onclick="showDay('day-oct7')">Oct 7</button>
        <button class="date-chip" onclick="showDay('day-oct8')">Oct 8</button>
        <button class="date-chip" onclick="showDay('day-oct9')">Oct 9</button>
        <button class="date-chip" onclick="showDay('day-oct10')">Oct 10</button>
        <button class="date-chip" onclick="showDay('day-oct11')">Oct 11</button>
        <button class="date-chip" onclick="showDay('day-oct12')">Oct 12</button>
        <button class="date-chip" onclick="showDay('day-oct13')">Oct 13</button>
        <button class="date-chip" onclick="showDay('day-oct14')">Oct 14</button>
        <button class="date-chip" onclick="showDay('day-oct15')">Oct 15</button>
        <button class="date-chip" onclick="showDay('day-oct16')">Oct 16</button>
      </div>
    </div>

    <div style="height: 14px;"></div>

    <div id="day-oct2" class="day-card active">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 2 (Friday)</span>
        <span class="day-dest" contenteditable="true">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">All Day / Flight Options</div>
        <div class="time-desc">
          <span contenteditable="true">Arrival in Santiago (Long-haul transit). Stay in Santiago if early arrival.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Santiago,+Chile" target="_blank">📍 Santiago Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Santiago,+Chile&output=embed"></iframe>
    </div>

    <div id="day-oct3" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 3 (Saturday)</span>
        <span class="day-dest" contenteditable="true">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Arrive in Santiago and check in to DoubleTree by Hilton Santiago Kennedy.</span>
          <a class="map-btn" href="https://maps.google.com/?q=DoubleTree+by+Hilton+Santiago+Kennedy" target="_blank">📍 Hotel Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Stroll through the cobblestone streets of Barrio Lastarria for lunch, street markets, and outdoor cafés. Optional visit to Santa Lucía Hill, La Moneda Palace, or Plaza de Armas.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Barrio+Lastarria,+Santiago" target="_blank">📍 Lastarria Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc">
          <span contenteditable="true">Walk across the river to Bellavista (Calle Constitución & Patio Bellavista). Optional San Cristóbal Hill funicular.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Patio+Bellavista,+Santiago" target="_blank">📍 Bellavista Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Barrio+Lastarria,+Santiago&output=embed"></iframe>
    </div>

    <div id="day-oct4" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 4 (Sunday)</span>
        <span class="day-dest" contenteditable="true">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Fly SCL → CJC on LA146 (08:23–10:35) [Preferred]. Pick up rental car at Calama Airport and drive 1.5h to San Pedro. Check in at Nueva Lodge La Estacion.</span>
          <a class="map-btn" href="https://maps.google.com/?q=El+Loa+Airport+Calama" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Drive 10 mins to Valley of Death (Valle de la Muerte / Marte) to see red dunes & rock formations. Optional visit to Magic bus or Pukará de Quitor.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Valle+de+la+Muerte,+San+Pedro+de+Atacama" target="_blank">📍 Death Valley Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc">
          <span contenteditable="true">Watch sunset at Valle de la Luna (Duna Mayor & Mirador de Kari). Stargazing tour at night.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Valle+de+la+Luna,+San+Pedro+de+Atacama" target="_blank">📍 Moon Valley Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Valle+de+la+Luna,+San+Pedro+de+Atacama&output=embed"></iframe>
    </div>

    <div id="day-oct5" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 5 (Monday)</span>
        <span class="day-dest" contenteditable="true">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Drive to Lagunas Escondidas de Baltinache (turquoise salt pools).</span>
          <a class="map-btn" href="https://maps.google.com/?q=Lagunas+Escondidas+de+Baltinache" target="_blank">📍 Baltinache Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Swim/float at Lagunas Cejar & Piedra in warm afternoon light. Drive south through Toconao to Laguna Chaxa to see flamingos at dusk.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Laguna+Chaxa" target="_blank">📍 Chaxa Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Relax in town; sample northern Chilean cuisine.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Lagunas+Escondidas+de+Baltinache&output=embed"></iframe>
    </div>

    <div id="day-oct6" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 6 (Tuesday)</span>
        <span class="day-dest" contenteditable="true">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">High-altitude day (~4,200m) visiting Miscanti & Miñiques Lagoons. Hydrate well.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Laguna+Miscanti" target="_blank">📍 Lagoons Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Continue south to Piedras Rojas (Aguas Calientes Salt Flat) across Salar de Talar. Stop at Socaire village and Laguna Tebinquiche on return.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Piedras+Rojas+Atacama" target="_blank">📍 Piedras Rojas Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Prep warm thermals, gloves, and hats for tomorrow's early geysers excursion.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Piedras+Rojas+Atacama&output=embed"></iframe>
    </div>

    <div id="day-oct7" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 7 (Wednesday)</span>
        <span class="day-dest" contenteditable="true">Transit / Santiago</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">04:30 AM drive to El Tatio Geysers for sunrise. Stop at Machuca Village on return drive.</span>
          <a class="map-btn" href="https://maps.google.com/?q=El+Tatio+Geysers" target="_blank">📍 Geysers Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Leave El Tatio ~08:30–09:00 AM back to San Pedro. Return rental car at CJC airport and fly CJC → SCL.</span>
          <a class="map-btn" href="https://maps.google.com/?q=El+Loa+Airport+Calama" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Rest in Santiago before tomorrow's Argentina flight.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=El+Tatio+Geysers&output=embed"></iframe>
    </div>

    <div id="day-oct8" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 8 (Thursday)</span>
        <span class="day-dest" contenteditable="true">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc"><span contenteditable="true">Fly from Santiago to Buenos Aires (EZE or AEP).</span></div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Check in at Up Recoleta Hotel; stroll around Recoleta neighborhood and parks.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Up+Recoleta+Hotel+Buenos+Aires" target="_blank">📍 Recoleta Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Dinner at an Argentine steakhouse (Parrilla).</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Recoleta+Buenos+Aires&output=embed"></iframe>
    </div>

    <div id="day-oct9" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 9 (Friday)</span>
        <span class="day-dest" contenteditable="true">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc"><span contenteditable="true">Fly from Buenos Aires (AEP/EZE) down to Ushuaia. Check in at Alto Andino Hotel.</span></div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Walk along the Beagle Channel waterfront and explore town.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Beagle+Channel+Ushuaia" target="_blank">📍 Waterfront Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Try local King Crab (Centolla) for dinner.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Ushuaia+Argentina&output=embed"></iframe>
    </div>

    <div id="day-oct10" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 10 (Saturday)</span>
        <span class="day-dest" contenteditable="true">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Tierra del Fuego National Park excursion via transfer shuttle (remis) or bus.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Tierra+del+Fuego+National+Park" target="_blank">📍 Park Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Excursion/boat tour to Isla Martillo with Piratour to walk among penguins.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Isla+Martillo+Ushuaia" target="_blank">📍 Isla Martillo Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Relax in Ushuaia town center.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Tierra+del+Fuego+National+Park&output=embed"></iframe>
    </div>

    <div id="day-oct11" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 11 (Sunday)</span>
        <span class="day-dest" contenteditable="true">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc"><span contenteditable="true">Fly from Ushuaia to El Calafate. Check in at Destino Calafate.</span></div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Visit Glaciarium Ice Museum.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Glaciarium+El+Calafate" target="_blank">📍 Glaciarium Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Dinner in town along Av. del Libertador.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=El+Calafate+Argentina&output=embed"></iframe>
    </div>

    <div id="day-oct12" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 12 (Monday)</span>
        <span class="day-dest" contenteditable="true">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning & Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Full-day excursion to Perito Moreno Glacier. Mini-trekking or boat navigation tour with Hielo & Aventura.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Perito+Moreno+Glacier" target="_blank">📍 Glacier Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Farewell Patagonia dinner in El Calafate.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Perito+Moreno+Glacier&output=embed"></iframe>
    </div>

    <div id="day-oct13" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 13 (Tuesday)</span>
        <span class="day-dest" contenteditable="true">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc"><span contenteditable="true">Fly from El Calafate to Buenos Aires. Check in at NH Collection Buenos Aires Crillon.</span></div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Late Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Visit Recoleta Cemetery and stroll down Avenida Santa Fe to browse El Ateneo Grand Splendid.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Recoleta+Cemetery" target="_blank">📍 Recoleta Cemetery Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Take a guided tour at Teatro Colón, then head north to explore Palermo Soho for boutique shopping and cafés.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Teatro+Colon+Buenos+Aires" target="_blank">📍 Teatro Colón Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Attend a live Tango Show with dinner (Gala Tango / El Querandí).</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Recoleta+Cemetery+Buenos+Aires&output=embed"></iframe>
    </div>

    <div id="day-oct14" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 14 (Wednesday)</span>
        <span class="day-dest" contenteditable="true">Buenos Aires / Uruguay</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Take morning ferry across Rio de la Plata to Colonia del Sacramento, Uruguay (Buquebus / Colonia Express).</span>
          <a class="map-btn" href="https://maps.google.com/?q=Puerto+Madero+Ferry+Terminal" target="_blank">📍 Terminal Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Explore historic cobble streets and lighthouse in Colonia del Sacramento.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Colonia+del+Sacramento+Uruguay" target="_blank">📍 Colonia Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Ferry back to Buenos Aires for dinner.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Colonia+del+Sacramento+Uruguay&output=embed"></iframe>
    </div>

    <div id="day-oct15" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 15 (Thursday)</span>
        <span class="day-dest" contenteditable="true">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc">
          <span contenteditable="true">Head south via Uber to Caminito in La Boca for colorful tin houses and street tango performers.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Caminito+La+Boca" target="_blank">📍 Caminito Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Midday & Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true">Explore antique stalls inside Mercado de San Telmo. Visit Plaza de Mayo to view Casa Rosada, then enjoy coffee and churros at Café Tortoni.</span>
          <a class="map-btn" href="https://maps.google.com/?q=Cafe+Tortoni+Buenos+Aires" target="_blank">📍 Café Tortoni Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Evening</div>
        <div class="time-desc"><span contenteditable="true">Final evening celebration dinner in Buenos Aires.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Mercado+de+San+Telmo&output=embed"></iframe>
    </div>

    <div id="day-oct16" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true">Oct 16 (Friday)</span>
        <span class="day-dest" contenteditable="true">Departure</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Morning</div>
        <div class="time-desc"><span contenteditable="true">Check out and final souvenirs/coffee.</span></div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true">Afternoon & Evening</div>
        <div class="time-desc"><span contenteditable="true">Transfer to EZE airport for departure long-haul flight home. In-flight.</span></div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=EZE+Airport+Buenos+Aires&output=embed"></iframe>
    </div>
  </main>

  <main id="flights" class="tab-content">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true">✈️ Flight Options & Route Schedule</div>
      
      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 2: Long-Haul Arrival to Santiago (HKG → SCL)</div>
        <div class="flight-option" contenteditable="true">• Option A: HKG-MAD-SCL (00:45–09:15 on Oct 2, 13:15–21:45)</div>
        <div class="flight-option" contenteditable="true">• Option B: HKG-CDG-SCL (00:05–07:55 on Oct 1, 23:20–08:50+1)</div>
        <div class="flight-option" contenteditable="true">• Option C: HKG-SYD-SCL (00:45–11:45 on Oct 1, 11:45–11:30 on Oct 2)</div>
        <div class="flight-option" contenteditable="true">• Option D: HKG-JFK-SCL (16:30–20:35 on Oct 1, 23:59–06:55+1)</div>
        <div class="flight-option" contenteditable="true">• Option E: HKG-LAX-SCL (00:05–22:00-1 on Oct 1, 14:55–05:35+1)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 4: Santiago to Calama / Atacama (SCL → CJC)</div>
        <div class="flight-option" contenteditable="true">• LA146 (08:23–10:35) <span class="pref-tag">PREFERRED</span></div>
        <div class="flight-option" contenteditable="true">• LA148 (14:05–16:17)</div>
        <div class="flight-option" contenteditable="true">• LA1860 (14:27–16:39)</div>
        <div class="flight-option" contenteditable="true">• LA150 (14:59–17:11)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 7: Calama to Santiago (CJC → SCL)</div>
        <div class="flight-option" contenteditable="true">• LA151 (13:58–16:02)</div>
        <div class="flight-option" contenteditable="true">• LA153 (14:35–16:39)</div>
        <div class="flight-option" contenteditable="true">• LA387 (14:54–16:58)</div>
        <div class="flight-option" contenteditable="true">• LA389 (16:44–18:51)</div>
        <div class="flight-option" contenteditable="true">• LA155 (17:26–19:32)</div>
        <div class="flight-option" contenteditable="true">• LA157 (19:38–21:44)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 8: Santiago to Buenos Aires (SCL → EZE / AEP)</div>
        <div class="flight-option" contenteditable="true">• SCL → EZE: LA542 (09:30–11:30)</div>
        <div class="flight-option" contenteditable="true">• SCL → EZE: KL702 (11:15–13:15)</div>
        <div class="flight-option" contenteditable="true">• SCL → EZE: LA477 (16:20–18:21)</div>
        <div class="flight-option" contenteditable="true">• SCL → AEP: AR1281 (09:15–12:20)</div>
        <div class="flight-option" contenteditable="true">• SCL → AEP: LA455 (12:47–14:50)</div>
        <div class="flight-option" contenteditable="true">• SCL → AEP: AR1283 (14:35–17:40)</div>
        <div class="flight-option" contenteditable="true">• SCL → AEP: LA425 (17:37–19:40)</div>
        <div class="flight-option" contenteditable="true">• SCL → AEP: LA427 (19:27–21:30)</div>
        <div class="flight-option" contenteditable="true">• SCL → AEP: AR1287 (20:35–23:40)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 9: Buenos Aires to Ushuaia (AEP / EZE → USH)</div>
        <div class="flight-option" contenteditable="true">• AEP → USH: AR1872 (03:50–07:30)</div>
        <div class="flight-option" contenteditable="true">• AEP → USH: AR1874 (06:00–09:40)</div>
        <div class="flight-option" contenteditable="true">• AEP → USH: AR1888 (11:15–14:55)</div>
        <div class="flight-option" contenteditable="true">• AEP → USH: AR1876 (17:55–21:35)</div>
        <div class="flight-option" contenteditable="true">• EZE → USH: AR1878 (05:00–08:40)</div>
        <div class="flight-option" contenteditable="true">• EZE → USH: AR1880 (08:30–12:10)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 11: Ushuaia to El Calafate (USH → FTE)</div>
        <div class="flight-option" contenteditable="true">• AR1895 (10:20–11:40)</div>
        <div class="flight-option" contenteditable="true">• AR1897 (16:05–17:25)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 13: El Calafate to Buenos Aires (FTE → AEP)</div>
        <div class="flight-option" contenteditable="true">• AR1839 (08:20–11:20)</div>
        <div class="flight-option" contenteditable="true">• AR1895 (11:40–14:40)</div>
        <div class="flight-option" contenteditable="true">• AR1897 (16:50–19:50)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 14: Ferry Crossing (Buenos Aires ↔ Uruguay)</div>
        <div class="flight-option" contenteditable="true">• Buquebus / Colonia Express (Puerto Madero Terminal)</div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Oct 16: Long-Haul Departure Flight</div>
        <div class="flight-option" contenteditable="true">• EZE Departure Flights (In-flight to HKG)</div>
      </div>
    </div>
  </main>

  <main id="hotels" class="tab-content">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true">🏨 Accommodations & Cancellation Rules</div>
      
      <div class="item-card">
        <div class="item-card-header" contenteditable="true">DoubleTree by Hilton Santiago Kennedy</div>
        <div contenteditable="true">
          <b>Dates:</b> Oct 3 – Oct 4, 2026<br>
          <b>Cost:</b> USD 108.62 (Charge Date: Oct 1)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Nueva Lodge La Estacion (San Pedro de Atacama)</div>
        <div contenteditable="true">
          <b>Dates:</b> Oct 4 – Oct 7, 2026<br>
          <b>Cost:</b> USD 432.00 (Charge Date: Oct 4)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Up Recoleta Hotel (Buenos Aires)</div>
        <div contenteditable="true">
          <b>Dates:</b> Oct 8 – Oct 9, 2026<br>
          <b>Cost:</b> USD 89.80 (Charge Date: Oct 4)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 5, 11:59 PM</span>
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Alto Andino Hotel (Ushuaia)</div>
        <div contenteditable="true">
          <b>Dates:</b> Oct 9 – Oct 11, 2026<br>
          <b>Cost:</b> USD 276.59 (Charge Date: Oct 9)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 10, 11:59 PM</span>
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">Destino Calafate (El Calafate)</div>
        <div contenteditable="true">
          <b>Dates:</b> Oct 11 – Oct 13, 2026<br>
          <b>Cost:</b> USD 283.77 (Charge Date: Oct 8)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 9, 11:59 PM</span>
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true">NH Collection Buenos Aires Crillon</div>
        <div contenteditable="true">
          <b>Dates:</b> Oct 13 – Oct 16, 2026<br>
          <b>Cost:</b> USD 556.03 (Charge Date: Oct 7)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 8, 11:59 PM</span>
        </div>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title" contenteditable="true">💡 Essential Local Travel Notes & Tips</div>
      
      <div class="tip-category" contenteditable="true">🇨🇱 Chile</div>
      <div class="tip-item" contenteditable="true">• <b>Cards:</b> Credit cards (Visa/Mastercard) are universally accepted in Santiago and most established businesses in San Pedro de Atacama (restaurants, hotels, petrol stations).</div>
      <div class="tip-item" contenteditable="true">• <b>Cash Needs:</b> Keep around 20,000 to 40,000 CLP (~$20–$40 USD) in cash for small purchases, national park entry fees in Atacama (some remote checkpoints only accept cash CLP), and small tips.</div>
      <div class="tip-item" contenteditable="true">• <b>Airport Transfers:</b> Use official counter taxis inside the terminal (e.g., <i>TransVIP</i> or <i>Taxi Oficial</i>) rather than accepting rides from unofficial touts in the arrival hall.</div>
      <div class="tip-item" contenteditable="true">• <b>Rideshare:</b> Uber operates reliably across Santiago and is the safest, most convenient option for city transit.</div>
      <div class="tip-item" contenteditable="true">• <b>Metro:</b> Santiago's Metro is modern, clean, and efficient. You will need a reloadable <b>Bip! card</b> to ride.</div>
      <div class="tip-item" contenteditable="true">• <b>Chile Customs (SAG Form):</b> Chile has extremely strict agricultural biosecurity laws. Upon landing at SCL, you must declare <b>all</b> organic matter, fresh food, fruit, wooden items, or snacks via the online SAG (<i>Servicio Agrícola y Ganadero</i>) digital declaration form before reaching customs. Undeclared food leads to steep fines.</div>

      <div class="tip-category" contenteditable="true">🇦🇷 Argentina</div>
      <div class="tip-item" contenteditable="true">• <b>Cards & MEP Rates:</b> International credit cards receive the official <b>MEP exchange rate</b> (<i>Mercado Electrónico de Pagos</i>), which automatically gives you an exchange rate very close to the informal "Blue Dollar" rate without needing to carry stacks of physical currency.</div>
      <div class="tip-item" contenteditable="true">• <b>Cash Needs:</b> While you can pay for hotels, restaurants, and tours with cards, cash is still useful for small tips, small café purchases, and street markets.</div>
      <div class="tip-item" contenteditable="true">• <b>Getting Cash:</b> Avoid using international ATMs in Argentina, as foreign card withdrawal fees are high. If you need cash, send yourself funds via <b>Western Union</b> to pick up pesos locally at market rates, or bring crisp, unmarked $100 USD bills to exchange at official <i>cambios</i>.</div>
      <div class="tip-item" contenteditable="true">• <b>Rideshare:</b> <b>Uber</b> and <b>Cabify</b> are widely used, extremely cheap, and much safer than hailing street taxis at night.</div>
      <div class="tip-item" contenteditable="true">• <b>Public Transit:</b> The subway (<i>Subte</i>) and buses require a <b>SUBE card</b>, which can be purchased at subway stations or <i>kioscos</i> (corner shops) and topped up with pesos.</div>
      <div class="tip-item" contenteditable="true">• <b>Airport Transfers:</b> From EZE or AEP, use pre-paid taxi booths inside the arrival terminal (e.g., <i>Taxi Ezeiza</i>) or book an Uber/Cabify directly from the designated pickup zone.</div>

      <div class="tip-category" contenteditable="true">🏜️ Atacama</div>
      <div class="tip-item" contenteditable="true">• Make sure your rental car in Atacama is a high-clearance SUV (ideally 4WD / AWD). Dirt tracks to Lagunas Escondidas de Baltinache and Piedras Rojas have loose gravel and sharp rocks.</div>
      <div class="tip-item" contenteditable="true">• Always keep a full tank of fuel. Petrol stations are located in Calama and San Pedro de Atacama; there are <b>no gas stations</b> out near the salt flats or geysers.</div>
      <div class="tip-item" contenteditable="true">• High-SPF sunscreen (50+) and UV-blocking sunglasses (the UV index in Atacama and on glacier ice is extremely high).</div>
      <div class="tip-item" contenteditable="true">• Moisturizer, eye drops, and lip balm (the Atacama Desert is one of the driest places on Earth).</div>
    </div>
  </main>

  <script>
    function switchTab(tabId) {
      document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
      
      document.getElementById(tabId).classList.add('active');
      event.currentTarget.classList.add('active');
      window.scrollTo(0, 0);
    }

    function showDay(dayId) {
      document.querySelectorAll('.day-card').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.date-chip').forEach(el => el.classList.remove('active'));

      document.getElementById(dayId).classList.add('active');
      event.currentTarget.classList.add('active');
    }

    let items = {
      tours: [
        { name: 'Piratour Isla Martillo Penguin Walk (Ushuaia)', qty: 1 },
        { name: 'Hielo & Aventura Perito Moreno Mini-Trekking', qty: 1 },
        { name: 'Atacama Stargazing Tour', qty: 1 },
        { name: 'Miscanti & Miñiques Lagoons Park Entry Ticket', qty: 1 },
        { name: 'Buenos Aires Tango Show & Dinner Reservation', qty: 1 },
        { name: 'Buquebus Ferry Buenos Aires ↔ Colonia', qty: 1 }
      ],
      carryon: [
        { name: 'Passport & Visas', qty: 1 },
        { name: 'Credit Cards & Cash (CLP / USD)', qty: 1 },
        { name: 'Moisturizer, Eye Drops & Lip Balm', qty: 2 }
      ],
      checkin: [
        { name: 'High-SPF Sunscreen (50+)', qty: 1 },
        { name: 'Heavy Thermals, Gloves & Warm Hat', qty: 1 },
        { name: 'UV-blocking Sunglasses', qty: 1 }
      ]
    };

    function renderChecklists() {
      ['tours', 'carryon', 'checkin'].forEach(type => {
        const ul = document.getElementById(type + '-list');
        if (!ul) return;
        ul.innerHTML = '';
        items[type].forEach((item, index) => {
          const li = document.createElement('li');
          li.className = 'check-item';
          li.innerHTML = `
            <div class="check-left">
              <input type="checkbox">
              <span contenteditable="true">${item.name}</span>
            </div>
            <div class="qty-controls">
              <button class="qty-btn" onclick="updateQty('${type}', ${index}, -1)">-</button>
              <span contenteditable="true">${item.qty}</span>
              <button class="qty-btn" onclick="updateQty('${type}', ${index}, 1)">+</button>
              <button class="qty-btn" onclick="removeItem('${type}', ${index})" style="color:#B91C1C;">×</button>
            </div>
          `;
          ul.appendChild(li);
        });
      });
    }

    function updateQty(type, index, change) {
      items[type][index].qty += change;
      if (items[type][index].qty <= 0) items[type][index].qty = 1;
      renderChecklists();
    }

    function removeItem(type, index) {
      items[type].splice(index, 1);
      renderChecklists();
    }

    function addItem(type) {
      const input = document.getElementById(type + '-input');
      if (input && input.value.trim() !== '') {
        items[type].push({ name: input.value.trim(), qty: 1 });
        input.value = '';
        renderChecklists();
      }
    }

    renderChecklists();
  </script>
</body>
</html>
