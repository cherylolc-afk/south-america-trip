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

    /* DATE SELECTOR BAR (FIXED SCROLLING) */
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

    /* CHECKLISTS & FORMS */
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

    .hotel-card {
      background: var(--beige-bg);
      border-radius: 8px;
      padding: 10px;
      margin-bottom: 10px;
      border: 1px solid var(--beige-border);
    }
    .hotel-name { font-weight: 700; color: var(--terracotta-primary); margin-bottom: 4px; font-size: 0.88rem; }
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
    <button class="tab-btn" onclick="switchTab('todo')">
      <span>☑️</span>
      <span>To-Do List</span>
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

  <main id="itinerary" class="tab-content active">

    <div class="date-bar-wrapper">
      <div class="date-bar" id="date-bar">
        <button class="date-chip active" onclick="showDay('day-oct2')">Oct 2 (Fri)</button>
        <button class="date-chip" onclick="showDay('day-oct3')">Oct 3 (Sat)</button>
        <button class="date-chip" onclick="showDay('day-oct4')">Oct 4 (Sun)</button>
        <button class="date-chip" onclick="showDay('day-oct5')">Oct 5 (Mon)</button>
        <button class="date-chip" onclick="showDay('day-oct6')">Oct 6 (Tue)</button>
        <button class="date-chip" onclick="showDay('day-oct7')">Oct 7 (Wed)</button>
        <button class="date-chip" onclick="showDay('day-oct8')">Oct 8 (Thu)</button>
        <button class="date-chip" onclick="showDay('day-oct9')">Oct 9 (Fri)</button>
        <button class="date-chip" onclick="showDay('day-oct10')">Oct 10 (Sat)</button>
        <button class="date-chip" onclick="showDay('day-oct11')">Oct 11 (Sun)</button>
        <button class="date-chip" onclick="showDay('day-oct12')">Oct 12 (Mon)</button>
        <button class="date-chip" onclick="showDay('day-oct13')">Oct 13 (Tue)</button>
        <button class="date-chip" onclick="showDay('day-oct14')">Oct 14 (Wed)</button>
        <button class="date-chip" onclick="showDay('day-oct15')">Oct 15 (Thu)</button>
        <button class="date-chip" onclick="showDay('day-oct16')">Oct 16 (Fri)</button>
      </div>
    </div>

    <div style="height: 14px;"></div>

    <div id="day-oct2" class="day-card active">
      <div class="day-header">
        <span class="day-date">Oct 2 (Fri)</span>
        <span class="day-dest">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title">All Day / Flight Options</div>
        <div class="time-desc">
          Arrival in Santiago (Long-haul transit). Stay in Santiago if early arrival.
          <a class="map-btn" href="https://maps.google.com/?q=Santiago,+Chile" target="_blank">📍 Santiago Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Santiago,+Chile&output=embed"></iframe>
    </div>

    <div id="day-oct3" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 3 (Sat)</span>
        <span class="day-dest">Santiago, Chile</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Arrive in Santiago and check in to DoubleTree by Hilton Santiago Kennedy.
          <a class="map-btn" href="https://maps.google.com/?q=DoubleTree+by+Hilton+Santiago+Kennedy" target="_blank">📍 Hotel Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Stroll through the cobblestone streets of Barrio Lastarria for lunch, street markets, and outdoor cafés. Optional visit to Santa Lucía Hill, La Moneda Palace, or Plaza de Armas.
          <a class="map-btn" href="https://maps.google.com/?q=Barrio+Lastarria,+Santiago" target="_blank">📍 Lastarria Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">
          Walk across the river to Bellavista (Calle Constitución & Patio Bellavista). Optional San Cristóbal Hill funicular.
          <a class="map-btn" href="https://maps.google.com/?q=Patio+Bellavista,+Santiago" target="_blank">📍 Bellavista Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Barrio+Lastarria,+Santiago&output=embed"></iframe>
    </div>

    <div id="day-oct4" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 4 (Sun)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Fly SCL → CJC on LA146 (08:23–10:35) [Preferred]. Pick up rental car at Calama Airport and drive 1.5h to San Pedro. Check in at Nueva Lodge La Estacion.
          <a class="map-btn" href="https://maps.google.com/?q=El+Loa+Airport+Calama" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Drive 10 mins to Valley of Death (Valle de la Muerte / Marte) to see red dunes & rock formations. Optional visit to Magic bus or Pukará de Quitor.
          <a class="map-btn" href="https://maps.google.com/?q=Valle+de+la+Muerte,+San+Pedro+de+Atacama" target="_blank">📍 Death Valley Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">
          Watch sunset at Valle de la Luna (Duna Mayor & Mirador de Kari). Stargazing tour at night.
          <a class="map-btn" href="https://maps.google.com/?q=Valle+de+la+Luna,+San+Pedro+de+Atacama" target="_blank">📍 Moon Valley Map</a>
        </div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Valle+de+la+Luna,+San+Pedro+de+Atacama&output=embed"></iframe>
    </div>

    <div id="day-oct5" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 5 (Mon)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Drive to Lagunas Escondidas de Baltinache (turquoise salt pools).
          <a class="map-btn" href="https://maps.google.com/?q=Lagunas+Escondidas+de+Baltinache" target="_blank">📍 Baltinache Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Swim/float at Lagunas Cejar & Piedra in warm afternoon light. Drive south through Toconao to Laguna Chaxa to see flamingos at dusk.
          <a class="map-btn" href="https://maps.google.com/?q=Laguna+Chaxa" target="_blank">📍 Chaxa Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Relax in town; sample northern Chilean cuisine.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Lagunas+Escondidas+de+Baltinache&output=embed"></iframe>
    </div>

    <div id="day-oct6" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 6 (Tue)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          High-altitude day (~4,200m) visiting Miscanti & Miñiques Lagoons. Hydrate well.
          <a class="map-btn" href="https://maps.google.com/?q=Laguna+Miscanti" target="_blank">📍 Lagoons Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Continue south to Piedras Rojas (Aguas Calientes Salt Flat) across Salar de Talar. Stop at Socaire village and Laguna Tebinquiche on return.
          <a class="map-btn" href="https://maps.google.com/?q=Piedras+Rojas+Atacama" target="_blank">📍 Piedras Rojas Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Prep warm thermals, gloves, and hats for tomorrow's early geysers excursion.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Piedras+Rojas+Atacama&output=embed"></iframe>
    </div>

    <div id="day-oct7" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 7 (Wed)</span>
        <span class="day-dest">Transit / Santiago</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          04:30 AM drive to El Tatio Geysers for sunrise. Stop at Machuca Village on return drive.
          <a class="map-btn" href="https://maps.google.com/?q=El+Tatio+Geysers" target="_blank">📍 Geysers Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Leave El Tatio ~08:30–09:00 AM back to San Pedro. Return rental car at CJC airport and fly CJC → SCL.
          <a class="map-btn" href="https://maps.google.com/?q=El+Loa+Airport+Calama" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Rest in Santiago before tomorrow's Argentina flight.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=El+Tatio+Geysers&output=embed"></iframe>
    </div>

    <div id="day-oct8" class="day-card">
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
          Check in at Up Recoleta Hotel; stroll around Recoleta neighborhood and parks.
          <a class="map-btn" href="https://maps.google.com/?q=Up+Recoleta+Hotel+Buenos+Aires" target="_blank">📍 Recoleta Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Dinner at an Argentine steakhouse (Parrilla).</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Recoleta+Buenos+Aires&output=embed"></iframe>
    </div>

    <div id="day-oct9" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 9 (Fri)</span>
        <span class="day-dest">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from Buenos Aires (AEP/EZE) down to Ushuaia. Check in at Alto Andino Hotel.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Walk along the Beagle Channel waterfront and explore town.
          <a class="map-btn" href="https://maps.google.com/?q=Beagle+Channel+Ushuaia" target="_blank">📍 Waterfront Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Try local King Crab (Centolla) for dinner.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Ushuaia+Argentina&output=embed"></iframe>
    </div>

    <div id="day-oct10" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 10 (Sat)</span>
        <span class="day-dest">Ushuaia, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Tierra del Fuego National Park excursion via transfer shuttle (remis) or bus.
          <a class="map-btn" href="https://maps.google.com/?q=Tierra+del+Fuego+National+Park" target="_blank">📍 Park Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Excursion/boat tour to Isla Martillo with Piratour to walk among penguins.
          <a class="map-btn" href="https://maps.google.com/?q=Isla+Martillo+Ushuaia" target="_blank">📍 Isla Martillo Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Relax in Ushuaia town center.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Tierra+del+Fuego+National+Park&output=embed"></iframe>
    </div>

    <div id="day-oct11" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 11 (Sun)</span>
        <span class="day-dest">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from Ushuaia to El Calafate. Check in at Destino Calafate.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Visit Glaciarium Ice Museum.
          <a class="map-btn" href="https://maps.google.com/?q=Glaciarium+El+Calafate" target="_blank">📍 Glaciarium Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Dinner in town along Av. del Libertador.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=El+Calafate+Argentina&output=embed"></iframe>
    </div>

    <div id="day-oct12" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 12 (Mon)</span>
        <span class="day-dest">El Calafate, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning & Afternoon</div>
        <div class="time-desc">
          Full-day excursion to Perito Moreno Glacier. Mini-trekking or boat navigation tour with Hielo & Aventura.
          <a class="map-btn" href="https://maps.google.com/?q=Perito+Moreno+Glacier" target="_blank">📍 Glacier Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Farewell Patagonia dinner in El Calafate.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Perito+Moreno+Glacier&output=embed"></iframe>
    </div>

    <div id="day-oct13" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 13 (Tue)</span>
        <span class="day-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">Fly from El Calafate to Buenos Aires. Check in at NH Collection Buenos Aires Crillon.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Late Morning</div>
        <div class="time-desc">
          Visit Recoleta Cemetery and stroll down Avenida Santa Fe to browse El Ateneo Grand Splendid.
          <a class="map-btn" href="https://maps.google.com/?q=Recoleta+Cemetery" target="_blank">📍 Recoleta Cemetery Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Take a guided tour at Teatro Colón, then head north to explore Palermo Soho for boutique shopping and cafés.
          <a class="map-btn" href="https://maps.google.com/?q=Teatro+Colon+Buenos+Aires" target="_blank">📍 Teatro Colón Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Attend a live Tango Show with dinner (Gala Tango / El Querandí).</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Recoleta+Cemetery+Buenos+Aires&output=embed"></iframe>
    </div>

    <div id="day-oct14" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 14 (Wed)</span>
        <span class="day-dest">Buenos Aires / Uruguay</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Take morning ferry across Rio de la Plata to Colonia del Sacramento, Uruguay (Buquebus / Colonia Express).
          <a class="map-btn" href="https://maps.google.com/?q=Puerto+Madero+Ferry+Terminal" target="_blank">📍 Terminal Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Explore historic cobble streets and lighthouse in Colonia del Sacramento.
          <a class="map-btn" href="https://maps.google.com/?q=Colonia+del+Sacramento+Uruguay" target="_blank">📍 Colonia Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Ferry back to Buenos Aires for dinner.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Colonia+del+Sacramento+Uruguay&output=embed"></iframe>
    </div>

    <div id="day-oct15" class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 15 (Thu)</span>
        <span class="day-dest">Buenos Aires, Argentina</span>
      </div>
      <div class="time-block">
        <div class="time-title">Morning</div>
        <div class="time-desc">
          Head south via Uber to Caminito in La Boca for colorful tin houses and street tango performers.
          <a class="map-btn" href="https://maps.google.com/?q=Caminito+La+Boca" target="_blank">📍 Caminito Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Midday & Afternoon</div>
        <div class="time-desc">
          Explore antique stalls inside Mercado de San Telmo. Visit Plaza de Mayo to view Casa Rosada, then enjoy coffee and churros at Café Tortoni.
          <a class="map-btn" href="https://maps.google.com/?q=Cafe+Tortoni+Buenos+Aires" target="_blank">📍 Café Tortoni Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Final evening celebration dinner in Buenos Aires.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=Mercado+de+San+Telmo&output=embed"></iframe>
    </div>

    <div id="day-oct16" class="day-card">
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
        <div class="time-desc">Transfer to EZE airport for departure long-haul flight home. In-flight.</div>
      </div>
      <iframe class="day-map-iframe" src="https://maps.google.com/maps?q=EZE+Airport+Buenos+Aires&output=embed"></iframe>
    </div>

  </main>

  <main id="weather" class="tab-content">
    <a href="https://www.meteoblue.com/en/weather/forecast/week/santiago-de-chile_chile_3871336" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date">Oct 2 (Fri)</div>
            <div class="weather-city">Santiago, Chile ↗</div>
            <div class="weather-desc">Clear & Sunny</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">20°C</div>
          <div class="weather-min">7°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.meteoblue.com/en/weather/forecast/week/santiago-de-chile_chile_3871336" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date">Oct 3 (Sat)</div>
            <div class="weather-city">Santiago, Chile ↗</div>
            <div class="weather-desc">Warm & Pleasant</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">22°C</div>
          <div class="weather-min">8°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date">Oct 4 (Sun)</div>
            <div class="weather-city">San Pedro de Atacama ↗</div>
            <div class="weather-desc">Dry & Intense Sun</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">20°C</div>
          <div class="weather-min">3°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date">Oct 5 (Mon)</div>
            <div class="weather-city">Atacama Salt Flats ↗</div>
            <div class="weather-desc">Sunny / Clear Skies</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">21°C</div>
          <div class="weather-min">4°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">💨</span>
          <div>
            <div class="weather-date">Oct 6 (Tue)</div>
            <div class="weather-city">Altiplanic Lagoons ↗</div>
            <div class="weather-desc">High Altitude Winds</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">14°C</div>
          <div class="weather-min">-2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/cl/san-pedro-de-atacama/106346/weather-forecast/106346" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">❄️</span>
          <div>
            <div class="weather-date">Oct 7 (Wed)</div>
            <div class="weather-city">El Tatio Geysers → Santiago ↗</div>
            <div class="weather-desc">Freezing Sunrise / Mild PM</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">18°C</div>
          <div class="weather-min">-4°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date">Oct 8 (Thu)</div>
            <div class="weather-city">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc">Partly Cloudy</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">19°C</div>
          <div class="weather-min">11°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/ushuaia/7180/weather-forecast/7180" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌧️</span>
          <div>
            <div class="weather-date">Oct 9 (Fri)</div>
            <div class="weather-city">Ushuaia, Argentina ↗</div>
            <div class="weather-desc">Chilly / Windy</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">7°C</div>
          <div class="weather-min">1°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/ushuaia/7180/weather-forecast/7180" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date">Oct 10 (Sat)</div>
            <div class="weather-city">Ushuaia (Beagle Channel) ↗</div>
            <div class="weather-desc">Cool / Coastal Breeze</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">8°C</div>
          <div class="weather-min">2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/el-calafate/7123/weather-forecast/7123" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">💨</span>
          <div>
            <div class="weather-date">Oct 11 (Sun)</div>
            <div class="weather-city">El Calafate, Argentina ↗</div>
            <div class="weather-desc">Breezy & Cool</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">11°C</div>
          <div class="weather-min">2°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/el-calafate/7123/weather-forecast/7123" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">❄️</span>
          <div>
            <div class="weather-date">Oct 12 (Mon)</div>
            <div class="weather-city">Perito Moreno Glacier ↗</div>
            <div class="weather-desc">Cold Glacier Winds</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">9°C</div>
          <div class="weather-min">1°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date">Oct 13 (Tue)</div>
            <div class="weather-city">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc">Warm & Sunny</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">21°C</div>
          <div class="weather-min">12°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/uy/colonia-del-sacramento/352467/weather-forecast/352467" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">🌤️</span>
          <div>
            <div class="weather-date">Oct 14 (Wed)</div>
            <div class="weather-city">Colonia, Uruguay ↗</div>
            <div class="weather-desc">Pleasant Coastal Weather</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">20°C</div>
          <div class="weather-min">13°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">☀️</span>
          <div>
            <div class="weather-date">Oct 15 (Thu)</div>
            <div class="weather-city">Buenos Aires, Argentina ↗</div>
            <div class="weather-desc">Mostly Clear</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">22°C</div>
          <div class="weather-min">13°C</div>
        </div>
      </div>
    </a>

    <a href="https://www.accuweather.com/en/ar/buenos-aires/7894/weather-forecast/7894" target="_blank" class="weather-card-link">
      <div class="weather-card">
        <div class="weather-left">
          <span class="weather-icon">⛅</span>
          <div>
            <div class="weather-date">Oct 16 (Fri)</div>
            <div class="weather-city">Buenos Aires Departure ↗</div>
            <div class="weather-desc">Mild</div>
          </div>
        </div>
        <div class="weather-temp-box">
          <div class="weather-max">20°C</div>
          <div class="weather-min">12°C</div>
        </div>
      </div>
    </a>
  </main>

  <main id="todo" class="tab-content">
    
    <div class="guide-section">
      <div class="guide-title">🎟️ Advance Tour Bookings Checklist</div>
      <ul class="checklist" id="tours-list"></ul>
      <div class="add-form">
        <input type="text" id="tours-input" class="add-input" placeholder="Add tour to book...">
        <button class="btn-action" onclick="addItem('tours')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title">🎒 Carry-On Packing List</div>
      <ul class="checklist" id="carryon-list"></ul>
      <div class="add-form">
        <input type="text" id="carryon-input" class="add-input" placeholder="Add carry-on item...">
        <button class="btn-action" onclick="addItem('carryon')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title">🧳 Checked Bag Packing List</div>
      <ul class="checklist" id="checkin-list"></ul>
      <div class="add-form">
        <input type="text" id="checkin-input" class="add-input" placeholder="Add checked item...">
        <button class="btn-action" onclick="addItem('checkin')">Add</button>
      </div>
    </div>

  </main>

  <main id="flights" class="tab-content">
    <div class="guide-section">
      <div class="guide-title">✈️ Flight Options & Schedules</div>
      <p style="font-size:0.78rem; color:var(--warm-muted); margin-bottom:12px;">Check off flights once booked or selected:</p>
      
      <ul class="checklist" id="flights-list"></ul>

      <div class="add-form">
        <input type="text" id="flights-input" class="add-input" placeholder="Add custom flight option...">
        <button class="btn-action" onclick="addItem('flights')">Add</button>
      </div>
    </div>
  </main>

  <main id="hotels" class="tab-content">
    <div class="guide-section">
      <div class="guide-title">🏨 Accommodations & Cancellation Rules</div>
      
      <div class="hotel-card">
        <div class="hotel-name">DoubleTree by Hilton Santiago Kennedy</div>
        <b>Dates:</b> Oct 3 – Oct 4, 2026<br>
        <b>Cost:</b> USD 108.62 (Charge Date: Oct 1)<br>
        <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
      </div>

      <div class="hotel-card">
        <div class="hotel-name">Nueva Lodge La Estacion (San Pedro de Atacama)</div>
        <b>Dates:</b> Oct 4 – Oct 7, 2026<br>
        <b>Cost:</b> USD 432.00 (Charge Date: Oct 4)<br>
        <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
      </div>

      <div class="hotel-card">
        <div class="hotel-name">Up Recoleta Hotel (Buenos Aires)</div>
        <b>Dates:</b> Oct 8 – Oct 9, 2026<br>
        <b>Cost:</b> USD 89.80 (Charge Date: Oct 4)<br>
        <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 5, 11:59 PM</span>
      </div>

      <div class="hotel-card">
        <div class="hotel-name">Alto Andino Hotel (Ushuaia)</div>
        <b>Dates:</b> Oct 9 – Oct 11, 2026<br>
        <b>Cost:</b> USD 276.59 (Charge Date: Oct 9)<br>
        <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 10, 11:59 PM</span>
      </div>

      <div class="hotel-card">
        <div class="hotel-name">Destino Calafate (El Calafate)</div>
        <b>Dates:</b> Oct 11 – Oct 13, 2026<br>
        <b>Cost:</b> USD 283.77 (Charge Date: Oct 8)<br>
        <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 9, 11:59 PM</span>
      </div>

      <div class="hotel-card">
        <div class="hotel-name">NH Collection Buenos Aires Crillon</div>
        <b>Dates:</b> Oct 13 – Oct 16, 2026<br>
        <b>Cost:</b> USD 556.03 (Charge Date: Oct 7)<br>
        <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 8, 11:59 PM</span>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title">💡 Essential Local Tips</div>
      <p style="font-size:0.82rem; line-height:1.5; color:var(--warm-dark);">
        • <b>Chile SAG Customs Declaration:</b> Fill out online before entry at Santiago Airport.<br>
        • <b>Atacama Cash:</b> Carry 30,000 CLP for park entry fees.<br>
        • <b>Argentina MEP Exchange Rate:</b> Paying with foreign credit cards applies the favorable MEP rate.<br>
        • <b>Uruguay Ferry:</b> Arrive at Puerto Madero ferry terminal 90 mins prior with passport for cross-border immigration.
      </p>
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
      ],
      flights: [
        { name: 'Oct 2: HKG-MAD-SCL (00:45–09:15, 13:15–21:45)', qty: 1 },
        { name: 'Oct 2: HKG-CDG-SCL (00:05–07:55, 23:20–08:50+1)', qty: 1 },
        { name: 'Oct 4: SCL → CJC LA146 (08:23–10:35) [Preferred]', qty: 1 },
        { name: 'Oct 4: SCL → CJC LA148 (14:05–16:17)', qty: 1 },
        { name: 'Oct 7: CJC → SCL LA151 (13:58–16:02)', qty: 1 },
        { name: 'Oct 7: CJC → SCL LA153 (14:35–16:39)', qty: 1 },
        { name: 'Oct 8: SCL → EZE LA542 (09:30–11:30)', qty: 1 },
        { name: 'Oct 8: SCL → EZE KL702 (11:15–13:15)', qty: 1 },
        { name: 'Oct 8: SCL → AEP AR1281 (09:15–12:20)', qty: 1 },
        { name: 'Oct 8: SCL → AEP LA455 (12:47–14:50)', qty: 1 },
        { name: 'Oct 8: SCL → AEP AR1283 (14:35–17:40)', qty: 1 },
        { name: 'Oct 9: AEP → USH AR1872 (03:50–07:30)', qty: 1 },
        { name: 'Oct 9: EZE → USH AR1878 (05:00–08:40)', qty: 1 },
        { name: 'Oct 11: USH → FTE AR1895 (10:20–11:40)', qty: 1 },
        { name: 'Oct 11: USH → FTE AR1897 (16:05–17:25)', qty: 1 },
        { name: 'Oct 13: FTE → AEP AR1839 (08:20–11:20)', qty: 1 },
        { name: 'Oct 13: FTE → AEP AR1895 (11:40–14:40)', qty: 1 }
      ]
    };

    function renderChecklists() {
      ['tours', 'carryon', 'checkin', 'flights'].forEach(type => {
        const ul = document.getElementById(type + '-list');
        if (!ul) return;
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
              ${type !== 'flights' ? `<button class="qty-btn" onclick="updateQty('${type}', ${index}, -1)">-</button><span>${item.qty}</span><button class="qty-btn" onclick="updateQty('${type}', ${index}, 1)">+</button>` : ''}
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
