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
      padding-bottom: 80px;
    }

    /* HEADER */
    .app-header {
      background: var(--terracotta-primary);
      color: var(--white);
      padding: 20px 16px 16px;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 4px 12px rgba(140, 109, 88, 0.15);
    }
    .app-header h1 { font-size: 1.3rem; font-weight: 700; letter-spacing: 0.5px; }
    .app-header p { font-size: 0.8rem; opacity: 0.9; margin-top: 4px; }

    /* DATE SELECTOR BAR */
    .date-bar {
      display: flex;
      gap: 8px;
      overflow-x: auto;
      padding: 12px 16px;
      background: #EBE3DB;
      border-bottom: 1px solid var(--beige-border);
      scrollbar-width: none;
    }
    .date-bar::-webkit-scrollbar { display: none; }
    .date-chip {
      flex: 0 0 auto;
      background: var(--white);
      border: 1px solid var(--beige-border);
      color: var(--warm-dark);
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 0.78rem;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.2s ease;
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
      padding: 10px 0;
      z-index: 100;
    }
    .tab-btn {
      border: none;
      background: none;
      font-family: inherit;
      font-size: 0.75rem;
      font-weight: 500;
      color: var(--warm-muted);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 3px;
      width: 25%;
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
      margin-bottom: 20px;
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

    /* TIME BLOCKS */
    .time-block {
      margin-bottom: 12px;
      padding-left: 12px;
      border-left: 3px solid var(--terracotta-primary);
    }
    .time-title { font-size: 0.8rem; font-weight: 700; color: var(--terracotta-primary); text-transform: uppercase; margin-bottom: 2px; }
    .time-desc { font-size: 0.85rem; color: var(--warm-dark); line-height: 1.4; }

    .map-btn {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      background: var(--beige-bg);
      color: var(--terracotta-primary);
      text-decoration: none;
      font-size: 0.72rem;
      padding: 3px 8px;
      border-radius: 6px;
      margin-left: 6px;
      font-weight: 500;
      border: 1px solid var(--beige-border);
    }

    .day-map-iframe {
      width: 100%;
      height: 200px;
      border: none;
      border-radius: 12px;
      margin-top: 14px;
      background: #E5E3DF;
    }

    /* WEATHER CARDS */
    .weather-card {
      background: var(--white);
      border-radius: var(--radius);
      padding: 14px 16px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid var(--beige-border);
    }
    .weather-date { font-size: 0.75rem; color: var(--warm-muted); font-weight: 500; }
    .weather-city { font-weight: 700; font-size: 0.9rem; color: var(--warm-dark); }
    .weather-temp { font-size: 1.1rem; font-weight: 700; color: var(--terracotta-primary); }
    .weather-details { font-size: 0.75rem; color: var(--warm-muted); margin-top: 2px; }

    /* GUIDE & TO-DO SECTIONS */
    .guide-section {
      background: var(--white);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 16px;
      border: 1px solid var(--beige-border);
    }
    .guide-title {
      font-size: 1rem;
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
      font-size: 0.85rem;
    }
    .check-left { display: flex; align-items: center; gap: 8px; }
    .qty-controls { display: flex; align-items: center; gap: 6px; }
    .qty-btn {
      border: 1px solid var(--beige-border);
      background: var(--beige-bg);
      width: 22px;
      height: 22px;
      border-radius: 4px;
      cursor: pointer;
    }
    .add-form { display: flex; gap: 8px; margin-top: 12px; }
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

    details { margin-bottom: 12px; border-bottom: 1px solid var(--beige-border); padding-bottom: 8px; }
    summary { font-weight: 700; font-size: 0.85rem; cursor: pointer; padding: 4px 0; color: var(--warm-dark); }
    .details-content { font-size: 0.8rem; color: var(--warm-muted); padding: 8px 0; line-height: 1.5; }

    .hotel-card {
      background: var(--beige-bg);
      border-radius: 8px;
      padding: 10px;
      margin-bottom: 8px;
      border: 1px solid var(--beige-border);
    }
    .hotel-name { font-weight: 700; color: var(--terracotta-primary); margin-bottom: 4px; }
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
    <button class="tab-btn" onclick="switchTab('guide')">
      <span>🧰</span>
      <span>Guide & Hotels</span>
    </button>
  </nav>

  <main id="itinerary" class="tab-content active">

    <div class="date-bar">
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
          Arrive in Santiago and check in to hotel.
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
          Walk across the river to Bellavista (Calle Constitución & Patio Bellavista). Optional San Cristóbal Hill funicular. Dinner in Santiago.
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
          Fly SCL → CJC on LA146 (08:23–10:35) [Preferred]. Pick up rental car at Calama Airport and drive 1.5h to San Pedro.
          <a class="map-btn" href="https://maps.google.com/?q=El+Loa+Airport+Calama" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Check in at hotel; drive 10 mins to Valley of Death (Valle de la Muerte / Marte) to see red dunes & rock formations. Optional visit to Magic bus or Pukará de Quitor.
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
          High-altitude day (~4,200m) visiting Miscanti & Miñiques Lagoons (reserve tickets ahead). Drink plenty of water and limit alcohol.
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
        <div class="time-desc">Prep warm layers (heavy thermals, gloves, warm hat) for tomorrow's early geysers excursion.</div>
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
          Leave El Tatio ~08:30–09:00 AM back to San Pedro (~10:30 AM). Return rental car at CJC airport (~1.5h drive) and fly CJC → SCL.
          <a class="map-btn" href="https://maps.google.com/?q=El+Loa+Airport+Calama" target="_blank">📍 Airport Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Rest in Santiago before tomorrow's Argentina flight. Optional: Puritama Hot Springs if time permits earlier.</div>
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
          Check in at Up Recoleta Hotel; stroll around Recoleta neighborhood and surrounding parks.
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
        <div class="time-desc">Fly from Buenos Aires (AEP/EZE) down to Ushuaia.</div>
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
          Excursion/boat tour to Isla Martillo with Piratour (the only licensed company allowed to step foot on the island) to walk among penguins.
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
        <div class="time-desc">Fly from Ushuaia to El Calafate.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Check in at Destino Calafate and visit Glaciarium Museum.
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
        <div class="time-title">Morning</div>
        <div class="time-desc">Full-day excursion to Perito Moreno Glacier.</div>
      </div>
      <div class="time-block">
        <div class="time-title">Afternoon</div>
        <div class="time-desc">
          Glacier mini-trekking or boat navigation tour with Hielo & Aventura (strict daily participant limits).
          <a class="map-btn" href="https://maps.google.com/?q=Perito+Moreno+Glacier" target="_blank">📍 Glacier Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Farewell Patagonia dinner.</div>
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
        <div class="time-desc">Fly from El Calafate back to Buenos Aires.</div>
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
          Take a guided tour at Teatro Colón, then head north to explore Palermo Soho for boutique shopping, cafés, and street art.
          <a class="map-btn" href="https://maps.google.com/?q=Teatro+Colon+Buenos+Aires" target="_blank">📍 Teatro Colón Map</a>
        </div>
      </div>
      <div class="time-block">
        <div class="time-title">Evening</div>
        <div class="time-desc">Attend a live Tango Show with dinner (Gala Tango, El Querandí, or Café de los Angelitos).</div>
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
          Take morning ferry across Rio de la Plata to Colonia del Sacramento, Uruguay (Buquebus / Colonia Express). Arrive at Puerto Madero terminal 90 mins prior.
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
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 2 (Fri)</div>
        <div class="weather-city">📍 Santiago, Chile</div>
        <div class="weather-details">Clear / Mild</div>
      </div>
      <div class="weather-temp">20°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 3 (Sat)</div>
        <div class="weather-city">📍 Santiago, Chile</div>
        <div class="weather-details">Sunny & Pleasant</div>
      </div>
      <div class="weather-temp">22°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 4 (Sun)</div>
        <div class="weather-city">📍 San Pedro de Atacama</div>
        <div class="weather-details">Sunny / High UV</div>
      </div>
      <div class="weather-temp">20°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 5 (Mon)</div>
        <div class="weather-city">📍 Atacama Salt Flats</div>
        <div class="weather-details">Dry / Clear Skies</div>
      </div>
      <div class="weather-temp">21°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 6 (Tue)</div>
        <div class="weather-city">📍 Altiplanic Lagoons</div>
        <div class="weather-details">High Altitude Breeze</div>
      </div>
      <div class="weather-temp">14°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 7 (Wed)</div>
        <div class="weather-city">📍 El Tatio Geysers → Santiago</div>
        <div class="weather-details">Early Freezing (-3°C) / Mild PM</div>
      </div>
      <div class="weather-temp">18°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 8 (Thu)</div>
        <div class="weather-city">📍 Buenos Aires, Argentina</div>
        <div class="weather-details">Partly Cloudy</div>
      </div>
      <div class="weather-temp">19°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 9 (Fri)</div>
        <div class="weather-city">📍 Ushuaia, Argentina</div>
        <div class="weather-details">Patagonian Wind & Cold</div>
      </div>
      <div class="weather-temp">7°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 10 (Sat)</div>
        <div class="weather-city">📍 Ushuaia (Beagle Channel)</div>
        <div class="weather-details">Chilly / Possible Showers</div>
      </div>
      <div class="weather-temp">8°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 11 (Sun)</div>
        <div class="weather-city">📍 El Calafate, Argentina</div>
        <div class="weather-details">Breezy & Cool</div>
      </div>
      <div class="weather-temp">11°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 12 (Mon)</div>
        <div class="weather-city">📍 Perito Moreno Glacier</div>
        <div class="weather-details">Glacier Winds / Cold</div>
      </div>
      <div class="weather-temp">9°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 13 (Tue)</div>
        <div class="weather-city">📍 Buenos Aires, Argentina</div>
        <div class="weather-details">Warm & Sunny</div>
      </div>
      <div class="weather-temp">21°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 14 (Wed)</div>
        <div class="weather-city">📍 Colonia, Uruguay</div>
        <div class="weather-details">Coastal Breeze / Pleasant</div>
      </div>
      <div class="weather-temp">20°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 15 (Thu)</div>
        <div class="weather-city">📍 Buenos Aires, Argentina</div>
        <div class="weather-details">Mostly Clear</div>
      </div>
      <div class="weather-temp">22°C</div>
    </div>
    <div class="weather-card">
      <div>
        <div class="weather-date">Oct 16 (Fri)</div>
        <div class="weather-city">📍 Buenos Aires Departure</div>
        <div class="weather-details">Mild</div>
      </div>
      <div class="weather-temp">20°C</div>
    </div>
  </main>

  <main id="todo" class="tab-content">
    <div class="guide-section">
      <div class="guide-title">☑️ Packing & Pre-Trip Checklist</div>
      
      <p style="font-size:0.8rem; font-weight:700; color:var(--terracotta-primary);">Carry-On Bag</p>
      <ul class="checklist" id="carryon-list"></ul>
      <div class="add-form">
        <input type="text" id="carryon-input" class="add-input" placeholder="Add carry-on item...">
        <button class="btn-action" onclick="addItem('carryon')">Add</button>
      </div>

      <p style="font-size:0.8rem; font-weight:700; margin-top:16px; color:var(--terracotta-primary);">Checked Bag</p>
      <ul class="checklist" id="checkin-list"></ul>
      <div class="add-form">
        <input type="text" id="checkin-input" class="add-input" placeholder="Add checked item...">
        <button class="btn-action" onclick="addItem('checkin')">Add</button>
      </div>
    </div>
  </main>

  <main id="guide" class="tab-content">
    <div class="guide-section">
      <div class="guide-title">🧰 Travel Details & Accommodations</div>

      <details open>
        <summary>🏨 Hotel Bookings & Cancellation Policies</summary>
        <div class="details-content">
          
          <div class="hotel-card">
            <div class="hotel-name">DoubleTree by Hilton Santiago Kennedy</div>
            <b>Check-In:</b> Oct 3, 2026 | <b>Check-Out:</b> Oct 4, 2026<br>
            <b>Cost:</b> USD 108.62 (to be charged Oct 1)<br>
            <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Nueva Lodge La Estacion (San Pedro de Atacama)</div>
            <b>Check-In:</b> Oct 4, 2026 | <b>Check-Out:</b> Oct 7, 2026<br>
            <b>Cost:</b> USD 432.00 (to be charged Oct 4)<br>
            <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 2, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Up Recoleta Hotel (Buenos Aires)</div>
            <b>Check-In:</b> Oct 8, 2026 | <b>Check-Out:</b> Oct 9, 2026<br>
            <b>Cost:</b> USD 89.80 (to be charged Oct 4)<br>
            <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 5, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Alto Andino Hotel (Ushuaia)</div>
            <b>Check-In:</b> Oct 9, 2026 | <b>Check-Out:</b> Oct 11, 2026<br>
            <b>Cost:</b> USD 276.59 (to be charged Oct 9)<br>
            <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 10, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">Destino Calafate (El Calafate)</div>
            <b>Check-In:</b> Oct 11, 2026 | <b>Check-Out:</b> Oct 13, 2026<br>
            <b>Cost:</b> USD 283.77 (to be charged Oct 8)<br>
            <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 9, 11:59 PM</span>
          </div>

          <div class="hotel-card">
            <div class="hotel-name">NH Collection Buenos Aires Crillon</div>
            <b>Check-In:</b> Oct 13, 2026 | <b>Check-Out:</b> Oct 16, 2026<br>
            <b>Cost:</b> USD 556.03 (to be charged Oct 7)<br>
            <b>Cancellation Policy:</b> <span style="color:#B91C1C; font-weight:700;">Free cancellation until Oct 8, 11:59 PM</span>
          </div>

        </div>
      </details>

      <details>
        <summary>✈️ Complete Flight Options & Schedules</summary>
        <div class="details-content">
          <b>Oct 2 Long-Haul Arrivals to SCL:</b><br>
          • Option A: HKG-MAD-SCL 00:45–09:15 on 2 Oct, 13:15–21:45 or 13:20–21:40<br>
          • Option B: HKG-CDG-SCL 00:05–07:55 on 1 Oct, 23:20–08:50+1<br>
          • Option C: HKG-SYD-SCL 00:45–11:45 on 1 Oct, 11:45–11:30 on 2 Oct<br>
          • Option D: HKG-JFK-SCL 16:30–20:35 on 1 Oct, 23:59–06:55+1<br>
          • Option E: HKG-LAX-SCL 00:05–22:00-1 on 1 Oct, 14:55–05:35+1<br><br>

          <b>Oct 4 (Santiago SCL → Calama CJC):</b><br>
          • LA146 (08:23–10:35) [Preferred]<br>
          • LA148 (14:05–16:17)<br>
          • LA1860 (14:27–16:39)<br>
          • LA150 (14:59–17:11)<br><br>
          
          <b>Oct 7 (Calama CJC → Santiago SCL):</b><br>
          • LA151 (13:58–16:02)<br>
          • LA153 (14:35–16:39)<br>
          • LA387 (14:54–16:58)<br>
          • LA389 (16:44–18:51)<br>
          • LA155 (17:26–19:32)<br>
          • LA157 (19:38–21:44)<br><br>

          <b>Oct 8 (Santiago SCL → Buenos Aires EZE / AEP):</b><br>
          <i>SCL → EZE:</i><br>
          • LA542 (09:30–11:30)<br>
          • KL702 (11:15–13:15)<br>
          • LA477 (16:20–18:21)<br>
          <i>SCL → AEP:</i><br>
          • AR1281 (09:15–12:20)<br>
          • LA455 (12:47–14:50)<br>
          • AR1283 (14:35–17:40)<br>
          • LA425 (17:37–19:40)<br>
          • LA427 (19:27–21:30)<br>
          • AR1287 (20:35–23:40)<br><br>

          <b>Oct 9 (Buenos Aires AEP/EZE → Ushuaia USH):</b><br>
          <i>AEP → USH:</i><br>
          • AR1872 (03:50–07:30)<br>
          • AR1874 (06:00–09:40)<br>
          • AR1888 (11:15–14:55)<br>
          • AR1876 (17:55–21:35)<br>
          <i>EZE → USH:</i><br>
          • AR1878 (05:00–08:40)<br>
          • AR1880 (08:30–12:10)<br><br>

          <b>Oct 11 (Ushuaia USH → El Calafate FTE):</b><br>
          • AR1895 (10:20–11:40)<br>
          • AR1897 (16:05–17:25)<br><br>

          <b>Oct 13 (El Calafate FTE → Buenos Aires AEP):</b><br>
          • AR1839 (08:20–11:20)<br>
          • AR1895 (11:40–14:40)<br>
          • AR1897 (16:50–19:50)
        </div>
      </details>

      <details>
        <summary>💡 Local Tips & Country Regulations</summary>
        <div class="details-content">
          • <b>Chile Customs (SAG Form):</b> Chile has strict agricultural biosecurity laws. Declare all organic matter, fresh food, or fruit on the online SAG digital form before customs at SCL.<br>
          • <b>Chile Cash:</b> Keep 20,000–40,000 CLP (~$20–$40 USD) in cash for small purchases, park entries, and tips.<br>
          • <b>Santiago Transit:</b> Metro requires a reloadable Bip! card. Use official counter taxis (TransVIP or Taxi Oficial) inside arrival terminal.<br>
          • <b>Argentina Exchange Rates:</b> Foreign cards receive the official MEP exchange rate (close to Blue Dollar rate). Avoid international ATMs due to high withdrawal fees.<br>
          • <b>Argentina Transit:</b> Subway (Subte) and buses require a SUBE card. Use pre-paid taxi booths (Taxi Ezeiza) or Uber/Cabify.<br>
          • <b>Atacama Driving:</b> High-clearance 4WD/AWD SUV mandatory for dirt tracks to Baltinache and Piedras Rojas. Keep full fuel tank as there are no gas stations near salt flats or geysers.
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

    function showDay(dayId) {
      document.querySelectorAll('.day-card').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.date-chip').forEach(el => el.classList.remove('active'));

      document.getElementById(dayId).classList.add('active');
      event.currentTarget.classList.add('active');
    }

    let items = {
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

    function renderChecklist() {
      ['carryon', 'checkin'].forEach(type => {
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
      if (input && input.value.trim() !== '') {
        items[type].push({ name: input.value.trim(), qty: 1 });
        input.value = '';
        renderChecklist();
      }
    }

    renderChecklist();
  </script>
</body>
</html>
