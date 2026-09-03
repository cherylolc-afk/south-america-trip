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

    [contenteditable="true"] {
      outline: none;
      transition: background-color 0.2s ease, box-shadow 0.2s ease;
      border-radius: 4px;
    }
    [contenteditable="true"]:hover { background-color: rgba(200, 178, 155, 0.15); }
    [contenteditable="true"]:focus {
      background-color: rgba(200, 178, 155, 0.25);
      box-shadow: 0 0 0 2px var(--terracotta-primary);
    }

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
    }
    .date-chip.active {
      background: var(--terracotta-primary);
      color: var(--white);
      border-color: var(--terracotta-primary);
      font-weight: 700;
    }

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

    .tab-content { display: none; padding: 16px; max-width: 600px; margin: 0 auto; }
    .tab-content.active { display: block; }

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

    .overview-table { width: 100%; border-collapse: collapse; font-size: 0.8rem; }
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

    /* GOOGLE MAP CONTAINER */
    .map-container {
      margin-top: 10px;
      border-radius: 12px;
      overflow: hidden;
      border: 1px solid var(--beige-border);
      height: 200px;
      width: 100%;
    }
    .map-container iframe {
      width: 100%;
      height: 100%;
      border: 0;
    }

    .weather-card-link { text-decoration: none; color: inherit; display: block; margin-bottom: 10px; }
    .weather-card {
      background: var(--white);
      border-radius: var(--radius);
      padding: 14px 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid var(--beige-border);
    }
    .weather-left { display: flex; align-items: center; gap: 12px; }
    .weather-icon { font-size: 1.8rem; }
    .weather-date { font-size: 0.75rem; color: var(--warm-muted); font-weight: 500; }
    .weather-city { font-weight: 700; font-size: 0.88rem; color: var(--warm-dark); }
    .weather-desc { font-size: 0.75rem; color: var(--warm-muted); }
    .weather-temp-box { text-align: right; }
    .weather-max { font-size: 1.05rem; font-weight: 700; color: var(--terracotta-primary); }
    .weather-min { font-size: 0.75rem; color: var(--warm-muted); }

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
  </style>
</head>
<body>

  <header class="app-header">
    <h1 contenteditable="true" data-save-id="header-title">South America Expedition</h1>
    <p contenteditable="true" data-save-id="header-dates">Oct 2, 2026 – Oct 16, 2026 | Chile • Argentina • Uruguay</p>
  </header>

  <nav class="tab-nav">
    <button class="tab-btn active" onclick="switchTab(event, 'todo')">
      <span>☑️</span><span>To-Do List</span>
    </button>
    <button class="tab-btn" onclick="switchTab(event, 'weather')">
      <span>🌤️</span><span>Weather</span>
    </button>
    <button class="tab-btn" onclick="switchTab(event, 'itinerary')">
      <span>📅</span><span>Itinerary</span>
    </button>
    <button class="tab-btn" onclick="switchTab(event, 'flights')">
      <span>✈️</span><span>Flights</span>
    </button>
    <button class="tab-btn" onclick="switchTab(event, 'hotels')">
      <span>🏨</span><span>Hotels & Tips</span>
    </button>
  </nav>

  <main id="todo" class="tab-content active">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true" data-save-id="title-bookings">🎟️ Bookings Checklist</div>
      <ul class="checklist" id="tours-list"></ul>
      <div class="add-form">
        <input type="text" id="tours-input" class="add-input" placeholder="Add booking item...">
        <button class="btn-action" onclick="addItem('tours')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title" contenteditable="true" data-save-id="title-carryon">🎒 Carry-On Packing List</div>
      <ul class="checklist" id="carryon-list"></ul>
      <div class="add-form">
        <input type="text" id="carryon-input" class="add-input" placeholder="Add carry-on item...">
        <button class="btn-action" onclick="addItem('carryon')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title" contenteditable="true" data-save-id="title-checkin">🧳 Checked Bag Packing List</div>
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
            <div class="weather-date" contenteditable="true" data-save-id="w-date-1">Oct 2</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-1">Santiago, Chile ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-1">Clear & Sunny</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-1">20°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-1">7°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.meteoblue.com/en/weather/forecast/week/santiago-de-chile_chile_3871336" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-2">Oct 3</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-2">Santiago, Chile ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-2">Warm & Mild</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-2">22°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-2">8°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-3">Oct 4</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-3">San Pedro de Atacama ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-3">Dry & Intense Sun</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-3">20°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-3">3°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-4">Oct 5</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-4">San Pedro de Atacama ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-4">High UV, Clear Skies</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-4">21°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-4">2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-5">Oct 6</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-5">High Altiplano Lagoons ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-5">Windy & Cold High Alt</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-5">14°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-5">-2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.meteoblue.com/en/weather/forecast/week/santiago-de-chile_chile_3871336" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌬️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-6">Oct 7</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-6">El Tatio / Santiago ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-6">Freezing Dawn / Pleasant Afternoon</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-6">19°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-6">-5°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-7">Oct 8</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-7">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-7">Partly Cloudy & Springlike</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-7">21°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-7">12°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/ushuaia/7180/weather-forecast/7180" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌧️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-8">Oct 9</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-8">Ushuaia, Patagonia ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-8">Chilly & Light Rain</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-8">8°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-8">1°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/ushuaia/7180/weather-forecast/7180" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">💨</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-9">Oct 10</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-9">Ushuaia, Patagonia ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-9">Windy Coastal Breeze</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-9">9°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-9">2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/el-calafate/7123/weather-forecast/7123" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-10">Oct 11</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-10">El Calafate ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-10">Crisp & Gusty</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-10">11°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-10">3°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/el-calafate/7123/weather-forecast/7123" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">❄️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-11">Oct 12</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-11">Perito Moreno Glacier ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-11">Glacial Cold & Wind</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-11">10°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-11">1°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-12">Oct 13</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-12">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-12">Sunny & Mild</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-12">22°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-12">13°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/uy/colonia-del-sacramento/352482/weather-forecast/352482" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-13">Oct 14</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-13">Colonia, Uruguay ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-13">Sunny River Breeze</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-13">21°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-13">12°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-14">Oct 15</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-14">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-14">Pleasant & Clear</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-14">23°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-14">14°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date" contenteditable="true" data-save-id="w-date-15">Oct 16</div>
            <div class="weather-city" contenteditable="true" data-save-id="w-city-15">Buenos Aires / Departure ↗</div>
            <div class="weather-desc" contenteditable="true" data-save-id="w-desc-15">Warm Spring Sun</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max" contenteditable="true" data-save-id="w-max-15">24°C</div>
          <div class="weather-min" contenteditable="true" data-save-id="w-min-15">15°C</div>
        </div>
      </div>
    </a>
  </main>

  <main id="itinerary" class="tab-content">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true" data-save-id="overview-title">📍 Master Overview & Quick Summary</div>
      <table class="overview-table">
        <thead>
          <tr>
            <th contenteditable="true" data-save-id="th-1">Date / DoW</th>
            <th contenteditable="true" data-save-id="th-2">Location</th>
            <th contenteditable="true" data-save-id="th-3">Key Highlights & Activities</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td contenteditable="true" data-save-id="tr-1-d"><b>Oct 2</b> (Fri)</td>
            <td contenteditable="true" data-save-id="tr-1-l">Santiago</td>
            <td contenteditable="true" data-save-id="tr-1-h">Long-haul arrival, hotel check-in / rest</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-2-d"><b>Oct 3</b> (Sat)</td>
            <td contenteditable="true" data-save-id="tr-2-l">Santiago</td>
            <td contenteditable="true" data-save-id="tr-2-h">Barrio Lastarria, Santa Lucía, Bellavista night</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-3-d"><b>Oct 4</b> (Sun)</td>
            <td contenteditable="true" data-save-id="tr-3-l">Atacama</td>
            <td contenteditable="true" data-save-id="tr-3-h">Flight to Calama, Death Valley, Moon Valley sunset</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-4-d"><b>Oct 5</b> (Mon)</td>
            <td contenteditable="true" data-save-id="tr-4-l">Atacama</td>
            <td contenteditable="true" data-save-id="tr-4-h">Baltinache salt pools, Cejar floating, Laguna Chaxa</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-5-d"><b>Oct 6</b> (Tue)</td>
            <td contenteditable="true" data-save-id="tr-5-l">Atacama</td>
            <td contenteditable="true" data-save-id="tr-5-h">Miscanti & Miñiques Lagoons, Piedras Rojas</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-6-d"><b>Oct 7</b> (Wed)</td>
            <td contenteditable="true" data-save-id="tr-6-l">Transit / Santiago</td>
            <td contenteditable="true" data-save-id="tr-6-h">El Tatio Geysers sunrise, fly back to Santiago</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-7-d"><b>Oct 8</b> (Thu)</td>
            <td contenteditable="true" data-save-id="tr-7-l">Buenos Aires</td>
            <td contenteditable="true" data-save-id="tr-7-h">Fly to BA, Palermo neighborhood stroll</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-8-d"><b>Oct 9</b> (Fri)</td>
            <td contenteditable="true" data-save-id="tr-8-l">Ushuaia</td>
            <td contenteditable="true" data-save-id="tr-8-h">Fly to Ushuaia, Beagle Channel waterfront</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-9-d"><b>Oct 10</b> (Sat)</td>
            <td contenteditable="true" data-save-id="tr-9-l">Ushuaia</td>
            <td contenteditable="true" data-save-id="tr-9-h">Tierra del Fuego National Park, Isla Martillo Penguins</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-10-d"><b>Oct 11</b> (Sun)</td>
            <td contenteditable="true" data-save-id="tr-10-l">El Calafate</td>
            <td contenteditable="true" data-save-id="tr-10-h">Fly to El Calafate, Glaciarium Ice Museum</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-11-d"><b>Oct 12</b> (Mon)</td>
            <td contenteditable="true" data-save-id="tr-11-l">El Calafate</td>
            <td contenteditable="true" data-save-id="tr-11-h">Full-day Perito Moreno Glacier mini-trekking</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-12-d"><b>Oct 13</b> (Tue)</td>
            <td contenteditable="true" data-save-id="tr-12-l">Buenos Aires</td>
            <td contenteditable="true" data-save-id="tr-12-h">Fly to BA, Recoleta Cemetery, Teatro Colón, Tango Show</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-13-d"><b>Oct 14</b> (Wed)</td>
            <td contenteditable="true" data-save-id="tr-13-l">Uruguay Day Trip</td>
            <td contenteditable="true" data-save-id="tr-13-h">Day ferry to Colonia del Sacramento, historic tour</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-14-d"><b>Oct 15</b> (Thu)</td>
            <td contenteditable="true" data-save-id="tr-14-l">Buenos Aires</td>
            <td contenteditable="true" data-save-id="tr-14-h">La Boca Caminito, San Telmo, Plaza de Mayo, Café Tortoni</td>
          </tr>
          <tr>
            <td contenteditable="true" data-save-id="tr-15-d"><b>Oct 16</b> (Fri)</td>
            <td contenteditable="true" data-save-id="tr-15-l">Departure</td>
            <td contenteditable="true" data-save-id="tr-15-h">Final city sights, souvenir shopping, departure flight</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="date-bar-wrapper">
      <div class="date-bar" id="date-bar">
        <button class="date-chip active" onclick="showDay(event, 'day-oct2')">Oct 2</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct3')">Oct 3</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct4')">Oct 4</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct5')">Oct 5</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct6')">Oct 6</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct7')">Oct 7</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct8')">Oct 8</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct9')">Oct 9</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct10')">Oct 10</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct11')">Oct 11</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct12')">Oct 12</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct13')">Oct 13</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct14')">Oct 14</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct15')">Oct 15</button>
        <button class="date-chip" onclick="showDay(event, 'day-oct16')">Oct 16</button>
      </div>
    </div>

    <div style="height: 14px;"></div>

    <div id="day-oct2" class="day-card active">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d2-header-date">Oct 2 (Friday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d2-header-dest">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d2-t1-title">All Day / Arrival</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d2-t1-desc">Long-haul transit arrival in Santiago. Check in to DoubleTree by Hilton Santiago Kennedy and rest.</span>
        </div>
      </div>
    </div>

    <div id="day-oct3" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d3-header-date">Oct 3 (Saturday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d3-header-dest">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d3-t1-title">Morning</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d3-t1-desc">Relaxed morning at DoubleTree by Hilton Santiago Kennedy.</span>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d3-t2-title">Afternoon & Evening</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d3-t2-desc">Explore Barrio Lastarria, Santa Lucía Hill, and dinner in Bellavista.</span>
        </div>
      </div>
    </div>

    <div id="day-oct4" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d4-header-date">Oct 4 (Sunday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d4-header-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d4-t1-title">Morning</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d4-t1-desc">Fly from Santiago (SCL) to Calama (CJC). Shuttle transfer to San Pedro de Atacama.</span>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d4-t2-title">Late Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d4-t2-desc">Death Valley & Moon Valley (Valle de la Luna) sunset tour.</span>
          <div class="map-container">
            <iframe src="https://maps.google.com/maps?q=Valle+de+la+Luna+San+Pedro+de+Atacama&t=&z=12&ie=UTF8&iwloc=&output=embed" loading="lazy"></iframe>
          </div>
        </div>
      </div>
    </div>

    <div id="day-oct5" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d5-header-date">Oct 5 (Monday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d5-header-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d5-t1-title">Full Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d5-t1-desc">Baltinache Salt Pools, Laguna Cejar floating experience, and flamingos at Laguna Chaxa.</span>
        </div>
      </div>
    </div>

    <div id="day-oct6" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d6-header-date">Oct 6 (Tuesday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d6-header-dest">Atacama Altiplano</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d6-t1-title">Full Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d6-t1-desc">High altitude expedition: Miscanti & Miñiques Lagoons, Piedras Rojas, and Socaire village.</span>
        </div>
      </div>
    </div>

    <div id="day-oct7" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d7-header-date">Oct 7 (Wednesday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d7-header-dest">Atacama → Santiago</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d7-t1-title">Early Morning</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d7-t1-desc">4:30 AM departure to El Tatio Geysers for geothermal sunrise.</span>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d7-t2-title">Afternoon</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d7-t2-desc">Transfer to Calama airport (CJC) and fly back to Santiago for overnight stay.</span>
        </div>
      </div>
    </div>

    <div id="day-oct8" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d8-header-date">Oct 8 (Thursday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d8-header-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d8-t1-title">All Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d8-t1-desc">Fly from Santiago (SCL) to Buenos Aires (AEP/EZE). Hotel check-in and explore Palermo neighborhood.</span>
        </div>
      </div>
    </div>

    <div id="day-oct9" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d9-header-date">Oct 9 (Friday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d9-header-dest">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d9-t1-title">All Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d9-t1-desc">Fly south to "End of the World" Ushuaia (USH). Stroll Beagle Channel waterfront and sample king crab.</span>
        </div>
      </div>
    </div>

    <div id="day-oct10" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d10-header-date">Oct 10 (Saturday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d10-header-dest">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d10-t1-title">Full Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d10-t1-desc">Tierra del Fuego National Park excursion and Piratour Isla Martillo Penguin Walk.</span>
        </div>
      </div>
    </div>

    <div id="day-oct11" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d11-header-date">Oct 11 (Sunday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d11-header-dest">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d11-t1-title">All Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d11-t1-desc">Fly from Ushuaia (USH) to El Calafate (FTE). Visit Glaciarium Ice Museum and enjoy Patagonian lamb.</span>
        </div>
      </div>
    </div>

    <div id="day-oct12" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d12-header-date">Oct 12 (Monday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d12-header-dest">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d12-t1-title">Full Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d12-t1-desc">Perito Moreno Glacier full-day mini-trekking and boat navigation.</span>
        </div>
      </div>
    </div>

    <div id="day-oct13" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d13-header-date">Oct 13 (Tuesday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d13-header-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d13-t1-title">All Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d13-t1-desc">Fly back to Buenos Aires. Guided walking tour of Recoleta Cemetery, Teatro Colón, and evening Tango Show.</span>
        </div>
      </div>
    </div>

    <div id="day-oct14" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d14-header-date">Oct 14 (Wednesday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d14-header-dest">Uruguay Day Trip</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d14-t1-title">Full Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d14-t1-desc">Buquebus ferry across Río de la Plata to Colonia del Sacramento, Uruguay. Historic Quarter tour.</span>
        </div>
      </div>
    </div>

    <div id="day-oct15" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d15-header-date">Oct 15 (Thursday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d15-header-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d15-t1-title">Full Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d15-t1-desc">La Boca Caminito street art, San Telmo antique markets, Plaza de Mayo, and coffee at Café Tortoni.</span>
        </div>
      </div>
    </div>

    <div id="day-oct16" class="day-card">
      <div class="day-header">
        <span class="day-date" contenteditable="true" data-save-id="d16-header-date">Oct 16 (Friday)</span>
        <span class="day-dest" contenteditable="true" data-save-id="d16-header-dest">Buenos Aires / Departure</span>
      </div>
      <div class="time-block">
        <div class="time-title" contenteditable="true" data-save-id="d16-t1-title">All Day</div>
        <div class="time-desc">
          <span contenteditable="true" data-save-id="d16-t1-desc">Final city shopping, Argentine leather goods, pack up, and head to EZE Airport for international flight.</span>
        </div>
      </div>
    </div>
  </main>

  <main id="flights" class="tab-content">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true" data-save-id="flights-title">✈️ Flight Options & Route Schedule</div>
      
      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-1-head">Oct 2: Long-Haul Arrival to Santiago (HKG → SCL)</div>
        <div contenteditable="true" data-save-id="fl-card-1-body">
          • Option A: HKG-MAD-SCL (00:45–09:15 on Oct 2, 13:15–21:45)<br>
          • Option B: HKG-CDG-SCL (00:05–07:55 on Oct 1, 23:20–08:50+1)
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-2-head">Oct 4: Santiago to Atacama (SCL → CJC)</div>
        <div contenteditable="true" data-save-id="fl-card-2-body">
          • LATAM / SKY Airline direct flights (1h 45m duration)<br>
          • Morning departure recommended to arrive before noon
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-3-head">Oct 7: Atacama to Santiago (CJC → SCL)</div>
        <div contenteditable="true" data-save-id="fl-card-3-body">
          • Evening flight after El Tatio Geysers tour
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-4-head">Oct 8: Santiago to Buenos Aires (SCL → AEP/EZE)</div>
        <div contenteditable="true" data-save-id="fl-card-4-body">
          • LATAM / Aerolíneas Argentinas direct (2h 15m duration)
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-5-head">Oct 9: Buenos Aires to Ushuaia (AEP → USH)</div>
        <div contenteditable="true" data-save-id="fl-card-5-body">
          • Aerolíneas Argentinas non-stop (3h 35m duration)
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-6-head">Oct 11: Ushuaia to El Calafate (USH → FTE)</div>
        <div contenteditable="true" data-save-id="fl-card-6-body">
          • Aerolíneas Argentinas direct (1h 20m duration)
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-7-head">Oct 13: El Calafate to Buenos Aires (FTE → AEP)</div>
        <div contenteditable="true" data-save-id="fl-card-7-body">
          • Morning departure (3h duration) to arrive in BA for afternoon tours
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="fl-card-8-head">Oct 16: Buenos Aires Departure (EZE → HKG)</div>
        <div contenteditable="true" data-save-id="fl-card-8-body">
          • Evening long-haul flight home via Europe or US
        </div>
      </div>
    </div>
  </main>

  <main id="hotels" class="tab-content">
    <div class="guide-section">
      <div class="guide-title" contenteditable="true" data-save-id="hotels-title">🏨 Accommodations & Cancellation Rules</div>
      
      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="hotel-1-name">DoubleTree by Hilton Santiago Kennedy</div>
        <div contenteditable="true" data-save-id="hotel-1-body">
          <b>Dates:</b> Oct 3 – Oct 4, 2026<br>
          <b>Cost:</b> USD 108.62 (Charge Date: Oct 1)<br>
          <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="hotel-2-name">San Pedro de Atacama Hotel / Lodge</div>
        <div contenteditable="true" data-save-id="hotel-2-body">
          <b>Dates:</b> Oct 4 – Oct 7, 2026<br>
          <b>Location:</b> Near Caracoles street town center
        </div>
      </div>

      <div class="item-card">
        <div class="item-card-header" contenteditable="true" data-save-id="hotel-3-name">Buenos Aires Hotel (Palermo / Recoleta)</div>
        <div contenteditable="true" data-save-id="hotel-3-body">
          <b>Dates:</b> Oct 8, Oct 13 – Oct 16, 2026<br>
          <b>Location:</b> Recoleta district recommended for proximity to attractions
        </div>
      </div>
    </div>
  </main>

  <script>
    function switchTab(evt, tabId) {
      document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
      
      document.getElementById(tabId).classList.add('active');
      evt.currentTarget.classList.add('active');
      window.scrollTo(0, 0);
    }

    function showDay(evt, dayId) {
      document.querySelectorAll('.day-card').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.date-chip').forEach(el => el.classList.remove('active'));

      const targetDay = document.getElementById(dayId);
      if (targetDay) targetDay.classList.add('active');
      evt.currentTarget.classList.add('active');
    }

    let defaultItems = {
      tours: [
        { name: 'Piratour Isla Martillo Penguin Walk (Ushuaia)', qty: 1, checked: false },
        { name: 'Hielo & Aventura Perito Moreno Mini-Trekking', qty: 1, checked: false },
        { name: 'Atacama Stargazing Tour', qty: 1, checked: false }
      ],
      carryon: [
        { name: 'Passport & Visas', qty: 1, checked: false },
        { name: 'Credit Cards & Cash (CLP / USD)', qty: 1, checked: false }
      ],
      checkin: [
        { name: 'High-SPF Sunscreen (50+)', qty: 1, checked: false },
        { name: 'Heavy Thermals & Warm Hat', qty: 1, checked: false }
      ]
    };

    let items = JSON.parse(localStorage.getItem('sa_expedition_checklists')) || defaultItems;

    function saveChecklists() {
      localStorage.setItem('sa_expedition_checklists', JSON.stringify(items));
    }

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
              <input type="checkbox" ${item.checked ? 'checked' : ''} onchange="toggleCheck('${type}', ${index}, this.checked)">
              <span contenteditable="true" onblur="updateItemName('${type}', ${index}, this.innerText)">${item.name}</span>
            </div>
            <div class="qty-controls">
              <button class="qty-btn" onclick="updateQty('${type}', ${index}, -1)">-</button>
              <span>${item.qty}</span>
              <button class="qty-btn" onclick="updateQty('${type}', ${index}, 1)">+</button>
              <button class="qty-btn" onclick="removeItem('${type}', ${index})" style="color:#B91C1C;">×</button>
            </div>
          `;
          ul.appendChild(li);
        });
      });
    }

    function toggleCheck(type, index, isChecked) {
      items[type][index].checked = isChecked;
      saveChecklists();
    }

    function updateItemName(type, index, newName) {
      items[type][index].name = newName;
      saveChecklists();
    }

    function updateQty(type, index, change) {
      items[type][index].qty += change;
      if (items[type][index].qty <= 0) items[type][index].qty = 1;
      saveChecklists();
      renderChecklists();
    }

    function removeItem(type, index) {
      items[type].splice(index, 1);
      saveChecklists();
      renderChecklists();
    }

    function addItem(type) {
      const input = document.getElementById(type + '-input');
      if (input && input.value.trim() !== '') {
        items[type].push({ name: input.value.trim(), qty: 1, checked: false });
        input.value = '';
        saveChecklists();
        renderChecklists();
      }
    }

    function initEditableStorage() {
      document.querySelectorAll('[contenteditable="true"][data-save-id]').forEach(el => {
        const saveId = el.getAttribute('data-save-id');
        const savedText = localStorage.getItem('sa_text_' + saveId);
        if (savedText !== null) {
          el.innerHTML = savedText;
        }

        el.addEventListener('input', () => {
          localStorage.setItem('sa_text_' + saveId, el.innerHTML);
        });
      });
    }

    document.addEventListener('DOMContentLoaded', () => {
      renderChecklists();
      initEditableStorage();
    });
  </script>
</body>
</html>
