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
      --bg: #f5f7fb;
      --card-bg: #ffffff;
      --primary: #2d5be3;
      --primary-light: #eef2ff;
      --text: #1e293b;
      --muted: #64748b;
      --border: #e2e8f0;
      --radius: 16px;
      
      --food: #f59e0b;
      --activity: #10b981;
      --shopping: #ec4899;
      --sight: #8b5cf6;
      --hotel: #06b6d4;
      --transit: #3b82f6;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Zen Maru Gothic', sans-serif;
      background: var(--bg);
      color: var(--text);
      padding-bottom: 80px;
    }

    .app-header {
      background: linear-gradient(135deg, #1e3a8a, #3b82f6);
      color: white;
      padding: 24px 20px 20px;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    .app-header h1 { font-size: 1.4rem; font-weight: 700; }
    .app-header p { font-size: 0.85rem; opacity: 0.85; margin-top: 4px; }

    .tab-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: var(--card-bg);
      display: flex;
      justify-content: space-around;
      border-top: 1px solid var(--border);
      padding: 10px 0;
      z-index: 100;
    }
    .tab-btn {
      border: none;
      background: none;
      font-family: inherit;
      font-size: 0.8rem;
      font-weight: 500;
      color: var(--muted);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      width: 33%;
      cursor: pointer;
    }
    .tab-btn.active { color: var(--primary); font-weight: 700; }

    .tab-content { display: none; padding: 16px; max-width: 600px; margin: 0 auto; }
    .tab-content.active { display: block; }

    .day-card {
      background: var(--card-bg);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 20px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.04);
      border: 1px solid var(--border);
    }
    .day-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid var(--bg);
      padding-bottom: 8px;
      margin-bottom: 12px;
    }
    .day-date { font-weight: 700; color: var(--primary); font-size: 1.05rem; }
    .day-dest { font-size: 0.85rem; background: var(--primary-light); color: var(--primary); padding: 4px 10px; border-radius: 20px; font-weight: 500; }

    .spot-card {
      border: 1px solid var(--border);
      border-radius: 12px;
      overflow: hidden;
      margin-top: 12px;
      background: #fafafa;
    }
    .spot-img { width: 100%; height: 160px; object-fit: cover; }
    .spot-body { padding: 12px; }
    
    .badge {
      display: inline-block;
      font-size: 0.7rem;
      font-weight: 700;
      padding: 2px 8px;
      border-radius: 6px;
      color: white;
      text-transform: uppercase;
      margin-bottom: 6px;
    }
    .badge.food { background: var(--food); }
    .badge.activity { background: var(--activity); }
    .badge.shopping { background: var(--shopping); }
    .badge.sight { background: var(--sight); }
    .badge.hotel { background: var(--hotel); }
    .badge.transit { background: var(--transit); }

    .tag {
      display: inline-block;
      font-size: 0.7rem;
      padding: 2px 8px;
      border-radius: 12px;
      margin-right: 4px;
      margin-top: 6px;
      font-weight: 500;
    }
    .tag-eat { background: #fef3c7; color: #b45309; }
    .tag-buy { background: #fce7f3; color: #be185d; }
    .tag-photo { background: #ede9fe; color: #6d28d9; }

    .spot-title { font-size: 0.95rem; font-weight: 700; margin-bottom: 4px; }
    .spot-desc { font-size: 0.82rem; color: var(--muted); line-height: 1.4; margin-bottom: 8px; }

    .info-box {
      background: #eff6ff;
      border-left: 3px solid var(--primary);
      padding: 8px;
      font-size: 0.75rem;
      color: #1e40af;
      margin-top: 8px;
      border-radius: 4px;
    }

    .btn-nav {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      background: var(--primary);
      color: white;
      text-decoration: none;
      font-size: 0.75rem;
      padding: 6px 12px;
      border-radius: 8px;
      margin-top: 8px;
      font-weight: 500;
    }

    .weather-card {
      background: var(--card-bg);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid var(--border);
    }
    .weather-info { display: flex; flex-direction: column; gap: 2px; }
    .weather-city { font-weight: 700; font-size: 0.9rem; }
    .weather-temp { font-size: 1.1rem; font-weight: 700; color: var(--primary); }
    .weather-details { font-size: 0.75rem; color: var(--muted); }

    .guide-section {
      background: var(--card-bg);
      border-radius: var(--radius);
      padding: 16px;
      margin-bottom: 16px;
      border: 1px solid var(--border);
    }
    .guide-title {
      font-size: 1rem;
      font-weight: 700;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 6px;
      color: var(--primary);
    }

    .checklist { list-style: none; }
    .check-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 8px 0;
      border-bottom: 1px dashed var(--border);
      font-size: 0.85rem;
    }
    .check-left { display: flex; align-items: center; gap: 8px; }
    .qty-controls { display: flex; align-items: center; gap: 6px; }
    .qty-btn {
      border: 1px solid var(--border);
      background: #f8fafc;
      width: 22px;
      height: 22px;
      border-radius: 4px;
      cursor: pointer;
    }
    .add-form { display: flex; gap: 8px; margin-top: 12px; }
    .add-input {
      flex: 1;
      padding: 6px 10px;
      border: 1px solid var(--border);
      border-radius: 8px;
      font-family: inherit;
      font-size: 0.8rem;
    }

    details { margin-bottom: 10px; border-bottom: 1px solid var(--border); padding-bottom: 8px; }
    summary { font-weight: 700; font-size: 0.85rem; cursor: pointer; padding: 4px 0; }
    .details-content { font-size: 0.8rem; color: var(--muted); padding: 8px 0; line-height: 1.5; }
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
        <span class="day-dest">Santiago</span>
      </div>
      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1589802829985-817e51171b92?auto=format&fit=crop&w=600&q=80" alt="Santiago Flight Arrival">
        <div class="spot-body">
          <span class="badge transit">Transit</span>
          <div class="spot-title">Arrival in Santiago</div>
          <p class="spot-desc">Arrival day options depending on selected long-haul flight routing.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Arturo+Merino+Benitez+Airport" target="_blank">📍 Navigate Airport</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 3 (Sat)</span>
        <span class="day-dest">Santiago</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1541872703-74c5e44368f9?auto=format&fit=crop&w=600&q=80" alt="Barrio Lastarria">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <span class="tag tag-eat">Must Eat</span>
          <div class="spot-title">Barrio Lastarria & Bellavista</div>
          <p class="spot-desc">Stroll cobblestone streets, local street markets, outdoor cafés, and vibrant bohemian avenues.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Barrio+Lastarria+Santiago" target="_blank">📍 Navigate</a>
        </div>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1512917774080-9991f1c4c750?auto=format&fit=crop&w=600&q=80" alt="DoubleTree Hilton Santiago">
        <div class="spot-body">
          <span class="badge hotel">Hotel</span>
          <div class="spot-title">DoubleTree by Hilton Santiago Kennedy</div>
          <p class="spot-desc">Overnight stay. Free cancellation until Oct 2, 11:59 PM.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=DoubleTree+by+Hilton+Santiago+Kennedy" target="_blank">📍 Navigate Hotel</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 4 (Sun)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1509316975850-ff9c5deb0cd9?auto=format&fit=crop&w=600&q=80" alt="Valle de la Luna">
        <div class="spot-body">
          <span class="badge activity">Activity</span>
          <span class="tag tag-photo">Must Photo</span>
          <div class="spot-title">Valle de la Muerte & Valle de la Luna</div>
          <p class="spot-desc">Explore red dunes, rock formations, and watch sunset at Duna Mayor / Mirador de Kari. Stargazing at night.</p>
          
          <div class="info-box">
            ⛽ <b>Gas Info:</b> Fill tank at Calama (CJC) or San Pedro town. No fuel available near salt flats.
            <br>🅿️ <b>Parking:</b> Parking lots available at designated national reserve entry points.
          </div>

          <a class="btn-nav" href="https://maps.google.com/?q=Valle+de+la+Luna+San+Pedro+de+Atacama" target="_blank">📍 Navigate</a>
        </div>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1566073771259-6a8506099945?auto=format&fit=crop&w=600&q=80" alt="Nueva Lodge La Estacion">
        <div class="spot-body">
          <span class="badge hotel">Hotel</span>
          <div class="spot-title">Nueva Lodge La Estacion</div>
          <p class="spot-desc">Overnight stay in San Pedro de Atacama.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Nueva+Lodge+La+Estacion+San+Pedro+de+Atacama" target="_blank">📍 Navigate Hotel</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 5 (Mon)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1518709268805-4e9042af9f23?auto=format&fit=crop&w=600&q=80" alt="Baltinache Salt Pools">
        <div class="spot-body">
          <span class="badge activity">Activity</span>
          <span class="tag tag-photo">Must Photo</span>
          <div class="spot-title">Lagunas Escondidas de Baltinache & Laguna Chaxa</div>
          <p class="spot-desc">Turquoise salt pools for floating. Drive south through Toconao to Laguna Chaxa for flamingos at dusk.</p>
          
          <div class="info-box">
            🚙 <b>Drive Note:</b> High-clearance SUV (4WD/AWD) recommended for loose gravel and sharp rocks on dirt tracks.
          </div>

          <a class="btn-nav" href="https://maps.google.com/?q=Lagunas+Escondidas+de+Baltinache" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 6 (Tue)</span>
        <span class="day-dest">San Pedro de Atacama</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=600&q=80" alt="Miscanti Lagoons">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <span class="tag tag-photo">Must Photo</span>
          <div class="spot-title">Miscanti & Miñiques Lagoons & Piedras Rojas</div>
          <p class="spot-desc">High altitude day (~4,200m). Scenic route extension across Salar de Talar and Aguas Calientes Salt Flat. Stop at Socaire village.</p>

          <div class="info-box">
            ☕ <b>Altitude Warning:</b> Limit alcohol, drink plenty of water, and consider coca tea or soroche pills.
          </div>

          <a class="btn-nav" href="https://maps.google.com/?q=Piedras+Rojas+San+Pedro+de+Atacama" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 7 (Wed)</span>
        <span class="day-dest">Transit / Santiago</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&w=600&q=80" alt="El Tatio Geysers">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <div class="spot-title">El Tatio Geysers & Machuca Village</div>
          <p class="spot-desc">04:30 AM early drive to geysers for sunrise. Stop at Machuca Village on return drive before flying back to Santiago.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=El+Tatio+Geysers" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 8 (Thu)</span>
        <span class="day-dest">Buenos Aires</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1589909202802-8f4aadce1849?auto=format&fit=crop&w=600&q=80" alt="Buenos Aires Steakhouse">
        <div class="spot-body">
          <span class="badge food">Food</span>
          <span class="tag tag-eat">Must Eat</span>
          <div class="spot-title">Recoleta Stroll & Argentine Steakhouse</div>
          <p class="spot-desc">Fly from Santiago to Buenos Aires. Explore Recoleta parks and enjoy a traditional Parrilla dinner.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Recoleta+Buenos+Aires" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 9 (Fri)</span>
        <span class="day-dest">Ushuaia</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1544735716-392fe2489ffa?auto=format&fit=crop&w=600&q=80" alt="Ushuaia Waterfront">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <span class="tag tag-eat">Must Eat</span>
          <div class="spot-title">Beagle Channel Waterfront</div>
          <p class="spot-desc">Fly to Ushuaia. Walk along the waterfront and try local King Crab (Centolla) for dinner.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Ushuaia+Waterfront" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 10 (Sat)</span>
        <span class="day-dest">Ushuaia</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1598439210625-5067c578f3f6?auto=format&fit=crop&w=600&q=80" alt="Isla Martillo Penguins">
        <div class="spot-body">
          <span class="badge activity">Activity</span>
          <span class="tag tag-photo">Must Photo</span>
          <div class="spot-title">Isla Martillo Penguin Walk</div>
          <p class="spot-desc">Excursion with Piratour to walk among penguins on Isla Martillo. Morning trip to Tierra del Fuego National Park.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Isla+Martillo+Ushuaia" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 11 (Sun)</span>
        <span class="day-dest">El Calafate</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1520962922320-2038eebab146?auto=format&fit=crop&w=600&q=80" alt="Glaciarium Museum">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <div class="spot-title">Glaciarium Museum & El Calafate Town</div>
          <p class="spot-desc">Fly from Ushuaia to El Calafate. Visit Glaciarium Museum and enjoy dinner along Av. del Libertador.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Glaciarium+El+Calafate" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 12 (Mon)</span>
        <span class="day-dest">El Calafate</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1517411032315-54ef2cb783bb?auto=format&fit=crop&w=600&q=80" alt="Perito Moreno Glacier">
        <div class="spot-body">
          <span class="badge activity">Activity</span>
          <span class="tag tag-photo">Must Photo</span>
          <div class="spot-title">Perito Moreno Glacier Mini-Trekking</div>
          <p class="spot-desc">Full-day excursion to Perito Moreno Glacier. Ice trekking / boat tour with Hielo & Aventura.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Perito+Moreno+Glacier" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 13 (Tue)</span>
        <span class="day-dest">Buenos Aires</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?auto=format&fit=crop&w=600&q=80" alt="Teatro Colon">
        <div class="spot-body">
          <span class="badge activity">Activity</span>
          <span class="tag tag-eat">Must Eat</span>
          <div class="spot-title">Recoleta, Teatro Colón & Tango Show</div>
          <p class="spot-desc">Visit Recoleta Cemetery, El Ateneo Grand Splendid, Teatro Colón, and attend a live Tango Show dinner.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Teatro+Colon+Buenos+Aires" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 14 (Wed)</span>
        <span class="day-dest">Buenos Aires / Uruguay</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1508672019048-805479760c23?auto=format&fit=crop&w=600&q=80" alt="Colonia del Sacramento">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <span class="tag tag-buy">Must Buy</span>
          <div class="spot-title">Day Trip to Colonia del Sacramento, Uruguay</div>
          <p class="spot-desc">Ferry across Rio de la Plata. Explore historic cobble streets, lighthouse, and artisan stores.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Colonia+del+Sacramento+Uruguay" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 15 (Thu)</span>
        <span class="day-dest">Buenos Aires</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1612294037637-ec328d0e075e?auto=format&fit=crop&w=600&q=80" alt="La Boca Caminito">
        <div class="spot-body">
          <span class="badge sight">Sightseeing</span>
          <span class="tag tag-photo">Must Photo</span>
          <span class="tag tag-eat">Must Eat</span>
          <div class="spot-title">La Boca, San Telmo & Plaza de Mayo</div>
          <p class="spot-desc">Visit Caminito tin houses, Mercado de San Telmo, Plaza de Mayo, and coffee & churros at Café Tortoni.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=Caminito+La+Boca+Buenos+Aires" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

    <div class="day-card">
      <div class="day-header">
        <span class="day-date">Oct 16 (Fri)</span>
        <span class="day-dest">Departure</span>
      </div>

      <div class="spot-card">
        <img class="spot-img" src="https://images.unsplash.com/photo-1436491865332-7a61a109cc05?auto=format&fit=crop&w=600&q=80" alt="EZE Airport Departure">
        <div class="spot-body">
          <span class="badge transit">Transit</span>
          <div class="spot-title">EZE Airport Transfer</div>
          <p class="spot-desc">Check out, final souvenirs and coffee, then transfer to EZE airport for departure flight home.</p>
          <a class="btn-nav" href="https://maps.google.com/?q=EZE+Airport" target="_blank">📍 Navigate</a>
        </div>
      </div>
    </div>

  </main>

  <main id="weather" class="tab-content">
    <div class="weather-card">
      <div class="weather-info">
        <div class="weather-city">📍 Santiago, Chile (Oct 2 - Oct 4)</div>
        <div class="weather-details">Feels like 22°C | Mostly Sunny</div>
      </div>
      <div class="weather-temp">21°C</div>
    </div>

    <div class="weather-card">
      <div class="weather-info">
        <div class="weather-city">📍 San Pedro de Atacama (Oct 4 - Oct 7)</div>
        <div class="weather-details">High UV | Lows -2°C at Geysers | Sunny</div>
      </div>
      <div class="weather-temp">19°C</div>
    </div>

    <div class="weather-card">
      <div class="weather-info">
        <div class="weather-city">📍 Buenos Aires (Oct 8, Oct 13 - Oct 16)</div>
        <div class="weather-details">Feels like 20°C | Mild / Breezy</div>
      </div>
      <div class="weather-temp">19°C</div>
    </div>

    <div class="weather-card">
      <div class="weather-info">
        <div class="weather-city">📍 Ushuaia (Oct 9 - Oct 11)</div>
        <div class="weather-details">Feels like 4°C | Windy / Shower Risk</div>
      </div>
      <div class="weather-temp">7°C</div>
    </div>

    <div class="weather-card">
      <div class="weather-info">
        <div class="weather-city">📍 El Calafate (Oct 11 - Oct 13)</div>
        <div class="weather-details">Feels like 8°C | Cool Glacier Winds</div>
      </div>
      <div class="weather-temp">11°C</div>
    </div>

    <div class="weather-card">
      <div class="weather-info">
        <div class="weather-city">📍 Colonia del Sacramento (Oct 14)</div>
        <div class="weather-details">Feels like 21°C | Coastal Breeze</div>
      </div>
      <div class="weather-temp">20°C</div>
    </div>
  </main>

  <main id="guide" class="tab-content">
    
    <div class="guide-section">
      <div class="guide-title">🧳 Packing Checklist</div>
      
      <p style="font-size:0.8rem; font-weight:700; margin-top:8px; color:var(--primary);">Carry-On Bag</p>
      <ul class="checklist" id="carryon-list"></ul>
      <div class="add-form">
        <input type="text" id="carryon-input" class="add-input" placeholder="Add item...">
        <button class="btn-nav" onclick="addItem('carryon')">Add</button>
      </div>

      <p style="font-size:0.8rem; font-weight:700; margin-top:16px; color:var(--primary);">Checked Bag</p>
      <ul class="checklist" id="checkin-list"></ul>
      <div class="add-form">
        <input type="text" id="checkin-input" class="add-input" placeholder="Add item...">
        <button class="btn-nav" onclick="addItem('checkin')">Add</button>
      </div>
    </div>

    <div class="guide-section">
      <div class="guide-title">🧰 Travel Details & Toolbox</div>

      <details>
        <summary>💡 Travel Tips (Chile & Argentina)</summary>
        <div class="details-content">
          <b>Chile Cash & Cards:</b> Credit cards universally accepted in Santiago & San Pedro. Keep 20,000–40,000 CLP cash for park entry and tips.
          <br><br>
          <b>Chile SAG Form:</b> Must declare all organic matter/food online before reaching customs at SCL.
          <br><br>
          <b>Argentina MEP Exchange Rate:</b> International cards get official MEP rate close to Blue Dollar rate. Avoid international ATMs due to fees.
          <br><br>
          <b>Transit:</b> Use official taxi booths inside airport arrival halls (TransVIP, Taxi Ezeiza) or Uber/Cabify.
        </div>
      </details>

      <details>
        <summary>✈️ Flight Details</summary>
        <div class="details-content">
          <b>Preferred Flights:</b>
          <br>• Oct 4: SCL → CJC (LA146 08:23–10:35)
          <br>• Oct 7: CJC → SCL (LA151 13:58–16:02 / LA153 14:35–16:39)
          <br>• Oct 8: SCL → EZE/AEP (LA542 09:30–11:30)
          <br>• Oct 9: AEP → USH (AR1874 06:00–09:40)
          <br>• Oct 11: USH → FTE (AR1895 10:20–11:40)
          <br>• Oct 13: FTE → AEP (AR1839 08:20–11:20)
        </div>
      </details>

      <details>
        <summary>🏨 Hotel Reservations</summary>
        <div class="details-content">
          • <b>Santiago:</b> DoubleTree by Hilton Santiago Kennedy ($108.62)
          <br>• <b>San Pedro:</b> Nueva Lodge La Estacion ($432.00)
          <br>• <b>Buenos Aires:</b> Up Recoleta Hotel ($89.80) / NH Collection Crillon ($556.03)
          <br>• <b>Ushuaia:</b> Alto Andino Hotel ($276.59)
          <br>• <b>El Calafate:</b> Destino Calafate ($283.77)
        </div>
      </details>

      <details>
        <summary>🚗 Car Rental Details (Atacama)</summary>
        <div class="details-content">
          • Pick-up at Calama Airport (CJC).
          <br>• Requires high-clearance SUV (4WD / AWD).
          <br>• Loose gravel on tracks to Baltinache & Piedras Rojas.
          <br>• Always maintain full fuel; no petrol stations near salt flats.
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
        { name: 'Credit Cards & Cash', qty: 1 },
        { name: 'Lip Balm & Eye Drops', qty: 2 }
      ],
      checkin: [
        { name: 'High-SPF Sunscreen (50+)', qty: 1 },
        { name: 'Heavy Thermals & Warm Hat', qty: 1 },
        { name: 'Trekking Boots', qty: 1 }
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
