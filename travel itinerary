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
        <div class="time-desc">
          Arrive in Santiago and check in to hotel.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=DoubleTree+by+Hilton+Santiago+Kennedy" target="_blank">📍 Hotel Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Stroll through Barrio Lastarria for lunch, street markets, and outdoor cafés. Optional visit to Santa Lucía Hill.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Barrio+Lastarria+Santiago" target="_blank">📍 Lastarria Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">
          Walk across the river to Bellavista (Calle Constitución & Patio Bellavista). Optional San Cristóbal Hill funicular.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Patio+Bellavista+Santiago" target="_blank">📍 Bellavista Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Barrio+Lastarria,Patio+Bellavista,Santiago&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 4 (Sun)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Fly SCL → CJC (LA146 08:23–10:35). Pick up rental car at Calama Airport and drive 1.5h to San Pedro.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Calama+Airport+Chile" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Check in at hotel; drive 10 mins to Valley of Death (Valle de la Muerte) for red dunes and rock formations.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Valle+de+la+Muerte+San+Pedro+de+Atacama" target="_blank">📍 Death Valley Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">
          Watch sunset at Valle de la Luna (Duna Mayor & Mirador de Kari). Stargazing tour at night.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Valle+de+la+Luna+San+Pedro+de+Atacama" target="_blank">📍 Moon Valley Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Valle+de+la+Muerte,Valle+de+la+Luna,San+Pedro+de+Atacama&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 5 (Mon)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Drive to Lagunas Escondidas de Baltinache (turquoise salt pools).
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Lagunas+Escondidas+de+Baltinache" target="_blank">📍 Baltinache Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Swim/float at Lagunas Cejar & Piedra. Drive south through Toconao to Laguna Chaxa to see flamingos at dusk.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Laguna+Chaxa" target="_blank">📍 Chaxa Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Relax in town and sample northern Chilean cuisine.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Lagunas+Escondidas+de+Baltinache,Laguna+Chaxa,San+Pedro+de+Atacama&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 6 (Tue)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          High-altitude day (~4,200m) visiting Miscanti & Miñiques Lagoons (reserve tickets ahead).
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Lagunas+Miscanti+y+Mi%C3%B1iques" target="_blank">📍 Lagoons Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Continue south to Piedras Rojas (Aguas Calientes Salt Flat). Stop at Socaire village and Laguna Tebinquiche on return.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Piedras+Rojas+Atacama" target="_blank">📍 Piedras Rojas Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Prep warm layers for tomorrow morning's geysers.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Lagunas+Miscanti,Piedras+Rojas+Atacama&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 7 (Wed)</span>
        <span class="day-dest">Transit / Santiago</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          04:30 AM drive to El Tatio Geysers for sunrise. Stop at Machuca Village on return drive.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=El+Tatio+Geysers" target="_blank">📍 Geysers Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Leave El Tatio ~08:30–09:00 AM back to San Pedro (~10:30 AM). Drive to CJC airport (~1.5h), drop car, fly CJC → SCL.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Calama+Airport" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Rest in Santiago before tomorrow's flight to Argentina.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=El+Tatio+Geysers,Machuca,Calama+Airport&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 8 (Thu)</span>
        <span class="day-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from Santiago to Buenos Aires (EZE or AEP).</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Check in at hotel; stroll around Recoleta neighborhood and surrounding parks.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Recoleta+Buenos+Aires" target="_blank">📍 Recoleta Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Dinner at an Argentine steakhouse (Parrilla).</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Recoleta,Buenos+Aires&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 9 (Fri)</span>
        <span class="day-dest">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from Buenos Aires down to Ushuaia.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Walk along the Beagle Channel waterfront and explore town.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Beagle+Channel+Ushuaia" target="_blank">📍 Waterfront Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Try local King Crab (Centolla) for dinner.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Ushuaia,Tierra+del+Fuego&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 10 (Sat)</span>
        <span class="day-dest">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Tierra del Fuego National Park excursion via transfer shuttle (remis) or bus.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Tierra+del+Fuego+National+Park" target="_blank">📍 Park Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Excursion/boat tour to Isla Martillo with Piratour to walk among penguins.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Isla+Martillo+Ushuaia" target="_blank">📍 Isla Martillo Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Relax in Ushuaia town center.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Tierra+del+Fuego+National+Park,Isla+Martillo&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 11 (Sun)</span>
        <span class="day-dest">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from Ushuaia to El Calafate.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Check in and visit Glaciarium Museum.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Glaciarium+El+Calafate" target="_blank">📍 Glaciarium Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Dinner in town along Av. del Libertador.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Glaciarium,El+Calafate&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 12 (Mon)</span>
        <span class="day-dest">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Full-day excursion to Perito Moreno Glacier.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Glacier mini-trekking or boat navigation tour with Hielo & Aventura.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Perito+Moreno+Glacier" target="_blank">📍 Glacier Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Farewell Patagonia dinner.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Perito+Moreno+Glacier,El+Calafate&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 13 (Tue)</span>
        <span class="day-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from El Calafate back to Buenos Aires.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Late Morning / Afternoon</div>
        <div class="time-desc">
          Visit Recoleta Cemetery and El Ateneo Grand Splendid. Guided tour at Teatro Colón, then explore Palermo Soho.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Teatro+Colon+Buenos+Aires" target="_blank">📍 Teatro Colón Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Attend a live Tango Show with dinner (Gala Tango, El Querandí, or Café de los Angelitos).</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Teatro+Colon,Recoleta+Cemetery,Palermo+Soho,Buenos+Aires&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 14 (Wed)</span>
        <span class="day-dest">Buenos Aires / Uruguay</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Ferry across Rio de la Plata to Colonia del Sacramento, Uruguay. Arrive at Puerto Madero ferry terminal 90 mins prior.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Buquebus+Puerto+Madero" target="_blank">📍 Ferry Terminal Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Explore historic cobble streets and lighthouse in Colonia.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Colonia+del+Sacramento+Uruguay" target="_blank">📍 Colonia Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Ferry back to Buenos Aires for dinner.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Colonia+del+Sacramento,Uruguay&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 15 (Thu)</span>
        <span class="day-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Uber to Caminito in La Boca for colorful tin houses and street tango performers.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Caminito+La+Boca" target="_blank">📍 Caminito Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Midday & Afternoon</div>
        <div class="time-desc">
          Explore Mercado de San Telmo. Visit Plaza de Mayo (Casa Rosada) and enjoy coffee & churros at Café Tortoni.
          <a class="map-btn" href="https://www.google.com/maps/search/?api=1&query=Cafe+Tortoni+Buenos+Aires" target="_blank">📍 Café Tortoni Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Final evening celebration dinner in Buenos Aires.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Caminito+La+Boca,Mercado+de+San+Telmo,Cafe+Tortoni&output=embed"></iframe>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 16 (Fri)</span>
        <span class="day-dest">Departure</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Check out and final souvenirs/coffee.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon & Evening</div>
        <div class="time-desc">Transfer to EZE airport for departure flight home. In-flight.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=EZE+Airport+Buenos+Aires&output=embed"></iframe>
    </div>

  </main>

  <main id="weather" class="tab-content">
    <div class="weather-card">
      <div>
        <div class="weather-city">📍 Santiago, Chile</div>
        <div class="weather-details">Oct 2 – Oct 4 | Mostly Sunny</div>
      </div>
      <div class="weather-temp">21°C</div>
    </div>

    <div class="weather-card">
      <div>
        <div class="weather-city">📍 San Pedro de Atacama</div>
        <div class="weather-details">Oct 4 – Oct 7 | Sunny / Lows -2°C at Geysers</div>
      </div>
      <div class="weather-temp">19°C</div>
    </div>

    <div class="weather-card">
      <div>
        <div class="weather-city">📍 Buenos Aires, Argentina</div>
        <div class="weather-details">Oct 8 & Oct 13 – Oct 16 | Mild / Pleasant</div>
      </div>
      <div class="weather-temp">19°C</div>
    </div>

    <div class="weather-card">
      <div>
        <div class="weather-city">📍 Ushuaia, Argentina</div>
        <div class="weather-details">Oct 9 – Oct 11 | Cold / Windy / Shower Risk</div>
      </div>
      <div class="weather-temp">7°C</div>
    </div>

    <div class="weather-card">
      <div>
        <div class="weather-city">📍 El Calafate, Argentina</div>
        <div class="weather-details">Oct 11 – Oct 13 | Cool Glacier Winds</div>
      </div>
      <div class="weather-temp">11°C</div>
    </div>

    <div class="weather-card">
      <div>
        <div class="weather-city">📍 Colonia del Sacramento, Uruguay</div>
        <div class="weather-details">Oct 14 | Coastal Breeze</div>
      </div>
      <div class="weather-temp">20°C</div>
    </div>
  </main>

  <main id="guide" class="tab-content">
    
    <div class="guide-section">
      <div class="guide-title">🧳 Packing Checklist</div>
      
      <p style="font-size:0.8rem; font-weight:700; color:var(--fuji-blue);">Carry-On Bag</p>
      <ul class="checklist" id="carryon-list"></ul>
      <div class="add-form">
        <input type="text" id="carryon-input" class="add-input" placeholder="Add carry-on item...">
        <button class="btn-action" onclick="addItem('carryon')">Add</button>
      </div>

      <p style="font-size:0.8rem; font-weight:700; margin-top:16px; color:var(--fuji-blue);">Checked Bag</p>
      <ul class="checklist" id="checkin-list"></ul>
      <div class="add-form">
        <input type="text" id="checkin-input" class="add-input" placeholder="Add checked item...">
        <button class="btn-action" onclick="addItem('checkin')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title">🧰 Travel Details & Accommodations</div>

      <details open>
        <summary>🏨 Hotel Bookings & Cancellation Policies</summary>
        <div class="details-content">
          
          <div class="hotel-card">
            <div class="hotel-name">DoubleTree by Hilton Santiago Kennedy</div>
            <b>Check-In:</b> Oct 3, 2026 | <b>Check-Out:</b> Oct 4, 2026<br>
            <b>Cost:</b> USD 108.62 (to be charged Oct 1)<br>
            <b>Cancellation Policy:</b> <span style="color:red; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Nueva Lodge La Estacion (San Pedro)</div>
            <b>Check-In:</b> Oct 4, 2026 | <b>Check-Out:</b> Oct 7, 2026<br>
            <b>Cost:</b> USD 432.00 (to be charged Oct 4)<br>
            <b>Cancellation Policy:</b> <span style="color:red; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Up Recoleta Hotel (Buenos Aires)</div>
            <b>Check-In:</b> Oct 8, 2026 | <b>Check-Out:</b> Oct 9, 2026<br>
            <b>Cost:</b> USD 89.80 (to be charged Oct 4)<br>
            <b>Cancellation Policy:</b> <span style="color:red; font-weight:700;">Free cancellation until Oct 5, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Alto Andino Hotel (Ushuaia)</div>
            <b>Check-In:</b> Oct 9, 2026 | <b>Check-Out:</b> Oct 11, 2026<br>
            <b>Cost:</b> USD 276.59 (to be charged Oct 9)<br>
            <b>Cancellation Policy:</b> <span style="color:red; font-weight:700;">Free cancellation until Oct 10, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Destino Calafate (El Calafate)</div>
            <b>Check-In:</b> Oct 11, 2026 | <b>Check-Out:</b> Oct 13, 2026<br>
            <b>Cost:</b> USD 283.77 (to be charged Oct 8)<br>
            <b>Cancellation Policy:</b> <span style="color:red; font-weight:700;">Free cancellation until Oct 9, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">NH Collection Buenos Aires Crillon</div>
            <b>Check-In:</b> Oct 13, 2026 | <b>Check-Out:</b> Oct 16, 2026<br>
            <b>Cost:</b> USD 556.03 (to be charged Oct 7)<br>
            <b>Cancellation Policy:</b> <span style="color:red; font-weight:700;">Free cancellation until Oct 8, 11:59 PM</span>
          </div>

        </div>
      </details>

      <details>
        <summary>✈️ Flight Details & Schedule</summary>
        <div class="details-content">
          <b>Oct 4 (SCL → CJC):</b> LA146 (08:23–10:35) [Preferred]<br>
          <i>Options: LA148 (14:05–16:17), LA1860 (14:27–16:39), LA150 (14:59–17:11)</i><br><br>
          
          <b>Oct 7 (CJC → SCL):</b> LA151 (13:58–16:02)<br>
          <i>Options: LA153 (14:35–16:39), LA387 (14:54–16:58), LA389 (16:44–18:51), LA155 (17:26–19:32), LA157 (19:38–21:44)</i><br><br>

          <b>Oct 8 (SCL → EZE / AEP):</b> LA542 (09:30–11:30 EZE) / AR1281 (09:15–12:20 AEP)<br><br>
          <b>Oct 9 (AEP → USH):</b> AR1874 (06:00–09:40) / AR1888 (11:15–14:55)<br><br>
          <b>Oct 11 (USH → FTE):</b> AR1895 (10:20–11:40) / AR1897 (16:05–17:25)<br><br>
          <b>Oct 13 (FTE → AEP):</b> AR1839 (08:20–11:20) / AR1895 (11:40–14:40)
        </div>
      </details>

      <details>
        <summary>💡 Local Tips & Customs</summary>
        <div class="details-content">
          • <b>Chile Customs (SAG Form):</b> Declare all food/organic items before reaching customs line at SCL.<br>
          • <b>Chile Cash:</b> Keep 20,000–40,000 CLP in cash for national park entry and small tips.<br>
          • <b>Argentina MEP Rate:</b> Foreign credit cards get the official MEP rate (close to informal Blue Dollar rate).<br>
          • <b>Argentina Transit:</b> Use official prepaid taxi booths inside arrival terminal (e.g. Taxi Ezeiza) or Uber.
        </div>
      </details>

      <details>
        <summary>🚗 Car Rental (Atacama)</summary>
        <div class="details-content">
          • High-clearance SUV (4WD/AWD) mandatory for dirt tracks to Baltinache and Piedras Rojas.<br>
          • No gas stations near salt flats or geysers; always keep fuel tank full in Calama or San Pedro.
        </div>
      </details>
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

    let items = {
      carryon: [
        { name: 'Passport & Visas', qty: 1 },
        { name: 'Credit Cards & Cash (CLP / USD)', qty: 1 },
        { name: 'Moisturizer & Lip Balm', qty: 2 }
      ],
      checkin: [
        { name: 'High-SPF Sunscreen (50+)', qty: 1 },
        { name: 'Heavy Thermals, Gloves & Warm Hat', qty: 1 },
        { name: 'UV-blocking Sunglasses', qty: 1 }
      ]
    };

    function renderChecklist() {
      ['carryon', 'checkin'].forEach(type => {
        const ul = document.getElementById(type + '-list');
        ul.innerHTML = '';
        items[type].forEach((item, index) => {
          const li = document.createElement('li');
          li.className = 'check-item';
          li.innerHTML = `
            <div class="check-left">
              <input type="checkbox">
              <span>${item.name}</span>
            </div>
            <div class="qty-controls">
              <button class="qty-btn" onclick="updateQty('${type}', ${index}, -1)">-</button>
              <span>${item.qty}</span>
              <button class="qty-btn" onclick="updateQty('${type}', ${index}, 1)">+</button>
              <button class="qty-btn" onclick="removeItem('${type}', ${index})" style="color:red;">×</button>
            </div>
          `;
          ul.appendChild(li);
        });
      });
    }

    function updateQty(type, index, change) {
      items[type][index].qty += change;
      if (items[type][index].qty <= 0) items[type][index].qty = 1;
      renderChecklist();
    }

    function removeItem(type, index) {
      items[type].splice(index, 1);
      renderChecklist();
    }

    function addItem(type) {
      const input = document.getElementById(type + '-input');
      if (input.value.trim() !== '') {
        items[type].push({ name: input.value.trim(), qty: 1 });
        input.value = '';
        renderChecklist();
      }
    }

    renderChecklist();
  </script>
</body>
</html>
