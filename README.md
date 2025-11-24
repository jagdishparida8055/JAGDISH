<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Modern Weather Dashboard - Get real-time weather forecasts for any city worldwide"
    />
    <meta name="keywords" content="weather, forecast, dashboard, responsive" />
    <title>Weather Dashboard | Real-time Weather Forecast</title>
    <style>
      /* Design System Variables */
      :root {
        --color-white: rgba(255, 255, 255, 1);
        --color-black: rgba(0, 0, 0, 1);
        --color-cream-50: rgba(252, 252, 249, 1);
        --color-cream-100: rgba(255, 255, 253, 1);
        --color-gray-200: rgba(245, 245, 245, 1);
        --color-gray-300: rgba(167, 169, 169, 1);
        --color-gray-400: rgba(119, 124, 124, 1);
        --color-slate-500: rgba(98, 108, 113, 1);
        --color-brown-600: rgba(94, 82, 64, 1);
        --color-charcoal-700: rgba(31, 33, 33, 1);
        --color-charcoal-800: rgba(38, 40, 40, 1);
        --color-slate-900: rgba(19, 52, 59, 1);
        --color-teal-300: rgba(50, 184, 198, 1);
        --color-teal-400: rgba(45, 166, 178, 1);
        --color-teal-500: rgba(33, 128, 141, 1);
        --color-teal-600: rgba(29, 116, 128, 1);
        --color-teal-700: rgba(26, 104, 115, 1);
        --color-red-400: rgba(255, 84, 89, 1);
        --color-red-500: rgba(192, 21, 47, 1);
        --color-orange-400: rgba(230, 129, 97, 1);
        --color-orange-500: rgba(168, 75, 47, 1);

        --color-brown-600-rgb: 94, 82, 64;
        --color-teal-500-rgb: 33, 128, 141;
        --color-slate-900-rgb: 19, 52, 59;
        --color-slate-500-rgb: 98, 108, 113;

        --color-background: var(--color-cream-50);
        --color-surface: var(--color-cream-100);
        --color-text: var(--color-slate-900);
        --color-text-secondary: var(--color-slate-500);
        --color-primary: var(--color-teal-500);
        --color-primary-hover: var(--color-teal-600);
        --color-primary-active: var(--color-teal-700);
        --color-border: rgba(var(--color-brown-600-rgb), 0.2);
        --color-error: var(--color-red-500);
        --color-success: var(--color-teal-500);
        --color-warning: var(--color-orange-500);

        --font-family-base: -apple-system, BlinkMacSystemFont, "Segoe UI",
          Roboto, sans-serif;
        --font-size-sm: 12px;
        --font-size-base: 14px;
        --font-size-lg: 16px;
        --font-size-xl: 18px;
        --font-size-2xl: 20px;
        --font-size-3xl: 24px;
        --font-size-4xl: 30px;
        --font-size-5xl: 36px;
        --font-weight-normal: 400;
        --font-weight-medium: 500;
        --font-weight-semibold: 550;
        --font-weight-bold: 600;

        --space-4: 4px;
        --space-8: 8px;
        --space-12: 12px;
        --space-16: 16px;
        --space-20: 20px;
        --space-24: 24px;
        --space-32: 32px;
        --space-48: 48px;

        --radius-sm: 6px;
        --radius-base: 8px;
        --radius-lg: 12px;
        --radius-xl: 16px;
        --radius-full: 9999px;

        --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.04),
          0 1px 2px rgba(0, 0, 0, 0.02);
        --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.04),
          0 2px 4px -1px rgba(0, 0, 0, 0.02);
        --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.04),
          0 4px 6px -2px rgba(0, 0, 0, 0.02);

        --duration-fast: 150ms;
        --duration-normal: 250ms;

        /* Weather-specific gradients */
        --gradient-hero: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        --gradient-clear: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        --gradient-cloudy: linear-gradient(135deg, #8e9eab 0%, #eef2f3 100%);
        --gradient-rain: linear-gradient(135deg, #5f72bd 0%, #9b23ea 100%);
      }

      @media (prefers-color-scheme: dark) {
        :root {
          --color-background: var(--color-charcoal-700);
          --color-surface: var(--color-charcoal-800);
          --color-text: var(--color-gray-200);
          --color-text-secondary: rgba(167, 169, 169, 0.7);
          --color-primary: var(--color-teal-300);
          --color-primary-hover: var(--color-teal-400);
          --color-border: rgba(119, 124, 124, 0.3);
          --color-error: var(--color-red-400);
          --color-warning: var(--color-orange-400);
        }
      }

      /* Base Styles */
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      html {
        font-size: var(--font-size-base);
        font-family: var(--font-family-base);
        line-height: 1.5;
        color: var(--color-text);
        background-color: var(--color-background);
        -webkit-font-smoothing: antialiased;
      }

      body {
        margin: 0;
        padding: 0;
        min-height: 100vh;
      }

      /* Hero Section */
      .hero {
        background: var(--gradient-hero);
        padding: var(--space-48) var(--space-16) var(--space-32);
        text-align: center;
        color: white;
        position: relative;
        overflow: hidden;
      }

      .hero::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: radial-gradient(
          circle at 50% 50%,
          rgba(255, 255, 255, 0.1) 0%,
          transparent 50%
        );
        pointer-events: none;
      }

      .hero-content {
        max-width: 800px;
        margin: 0 auto;
        position: relative;
        z-index: 1;
      }

      .hero h1 {
        font-size: var(--font-size-5xl);
        font-weight: var(--font-weight-bold);
        margin-bottom: var(--space-16);
        text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      }

      .hero p {
        font-size: var(--font-size-xl);
        margin-bottom: var(--space-32);
        opacity: 0.95;
      }

      /* Search Section */
      .search-container {
        max-width: 600px;
        margin: 0 auto;
        position: relative;
      }

      .search-form {
        display: flex;
        gap: var(--space-12);
        margin-bottom: var(--space-16);
      }

      .search-input {
        flex: 1;
        padding: var(--space-16) var(--space-20);
        border: none;
        border-radius: var(--radius-lg);
        font-size: var(--font-size-lg);
        background: white;
        color: var(--color-slate-900);
        box-shadow: var(--shadow-lg);
        transition: transform var(--duration-fast);
      }

      .search-input:focus {
        outline: 3px solid rgba(255, 255, 255, 0.5);
        transform: translateY(-2px);
      }

      .search-btn {
        padding: var(--space-16) var(--space-32);
        background: white;
        color: #667eea;
        border: none;
        border-radius: var(--radius-lg);
        font-size: var(--font-size-lg);
        font-weight: var(--font-weight-semibold);
        cursor: pointer;
        box-shadow: var(--shadow-lg);
        transition: all var(--duration-normal);
        min-width: 120px;
      }

      .search-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 12px 20px -5px rgba(0, 0, 0, 0.15);
      }

      .search-btn:active {
        transform: translateY(0);
      }

      .search-btn:disabled {
        opacity: 0.6;
        cursor: not-allowed;
      }

      /* Recent Searches */
      .recent-searches {
        display: flex;
        flex-wrap: wrap;
        gap: var(--space-8);
        justify-content: center;
        margin-top: var(--space-16);
      }

      .recent-search-btn {
        padding: var(--space-8) var(--space-16);
        background: rgba(255, 255, 255, 0.2);
        color: white;
        border: 1px solid rgba(255, 255, 255, 0.3);
        border-radius: var(--radius-full);
        font-size: var(--font-size-sm);
        cursor: pointer;
        transition: all var(--duration-fast);
        backdrop-filter: blur(10px);
      }

      .recent-search-btn:hover {
        background: rgba(255, 255, 255, 0.3);
        transform: translateY(-1px);
      }

      /* Main Container */
      .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: var(--space-32) var(--space-16);
      }

      /* Loading Spinner */
      .loading {
        display: none;
        text-align: center;
        padding: var(--space-48);
      }

      .loading.active {
        display: block;
      }

      .spinner {
        width: 50px;
        height: 50px;
        border: 4px solid var(--color-border);
        border-top-color: var(--color-primary);
        border-radius: 50%;
        animation: spin 1s linear infinite;
        margin: 0 auto var(--space-16);
      }

      @keyframes spin {
        to {
          transform: rotate(360deg);
        }
      }

      /* Error Message */
      .error-message {
        display: none;
        max-width: 600px;
        margin: 0 auto var(--space-24);
        padding: var(--space-16);
        background: rgba(var(--color-red-500), 0.1);
        border: 1px solid var(--color-error);
        border-radius: var(--radius-lg);
        color: var(--color-error);
        text-align: center;
      }

      .error-message.active {
        display: block;
      }

      /* Weather Display */
      .weather-display {
        display: none;
      }

      .weather-display.active {
        display: block;
      }

      /* Current Weather Card */
      .current-weather {
        background: var(--color-surface);
        border-radius: var(--radius-xl);
        padding: var(--space-32);
        box-shadow: var(--shadow-lg);
        margin-bottom: var(--space-32);
        border: 1px solid var(--color-border);
      }

      .weather-header {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        margin-bottom: var(--space-24);
        flex-wrap: wrap;
        gap: var(--space-16);
      }

      .location-info h2 {
        font-size: var(--font-size-3xl);
        font-weight: var(--font-weight-bold);
        margin-bottom: var(--space-4);
      }

      .current-time {
        color: var(--color-text-secondary);
        font-size: var(--font-size-base);
      }

      .unit-toggle {
        display: flex;
        gap: var(--space-8);
        background: var(--color-background);
        padding: var(--space-4);
        border-radius: var(--radius-lg);
        border: 1px solid var(--color-border);
      }

      .unit-btn {
        padding: var(--space-8) var(--space-16);
        background: transparent;
        border: none;
        border-radius: var(--radius-base);
        cursor: pointer;
        font-weight: var(--font-weight-medium);
        color: var(--color-text-secondary);
        transition: all var(--duration-fast);
      }

      .unit-btn.active {
        background: var(--color-primary);
        color: white;
      }

      .weather-main {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: var(--space-32);
        margin-bottom: var(--space-32);
      }

      .temperature-display {
        display: flex;
        align-items: center;
        gap: var(--space-16);
      }

      .weather-icon {
        font-size: 80px;
        line-height: 1;
      }

      .temp-info .temperature {
        font-size: 64px;
        font-weight: var(--font-weight-bold);
        line-height: 1;
        margin-bottom: var(--space-8);
      }

      .temp-info .feels-like {
        color: var(--color-text-secondary);
        font-size: var(--font-size-base);
      }

      .weather-description {
        font-size: var(--font-size-xl);
        color: var(--color-text-secondary);
        text-transform: capitalize;
      }

      /* Weather Details Grid */
      .weather-details {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: var(--space-16);
      }

      .detail-item {
        padding: var(--space-16);
        background: var(--color-background);
        border-radius: var(--radius-lg);
        border: 1px solid var(--color-border);
      }

      .detail-item .label {
        display: flex;
        align-items: center;
        gap: var(--space-8);
        color: var(--color-text-secondary);
        font-size: var(--font-size-sm);
        margin-bottom: var(--space-8);
        text-transform: uppercase;
        letter-spacing: 0.5px;
      }

      .detail-item .value {
        font-size: var(--font-size-2xl);
        font-weight: var(--font-weight-semibold);
      }

      /* Forecast Section */
      .forecast-section {
        margin-top: var(--space-32);
      }

      .forecast-section h3 {
        font-size: var(--font-size-2xl);
        font-weight: var(--font-weight-bold);
        margin-bottom: var(--space-20);
      }

      .forecast-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
        gap: var(--space-16);
      }

      .forecast-card {
        background: var(--color-surface);
        border: 1px solid var(--color-border);
        border-radius: var(--radius-lg);
        padding: var(--space-20);
        text-align: center;
        transition: all var(--duration-normal);
        cursor: pointer;
      }

      .forecast-card:hover {
        transform: translateY(-4px);
        box-shadow: var(--shadow-lg);
      }

      .forecast-card .day {
        font-weight: var(--font-weight-semibold);
        margin-bottom: var(--space-8);
        color: var(--color-text);
      }

      .forecast-card .date {
        font-size: var(--font-size-sm);
        color: var(--color-text-secondary);
        margin-bottom: var(--space-12);
      }

      .forecast-card .icon {
        font-size: 40px;
        margin: var(--space-12) 0;
      }

      .forecast-card .temps {
        display: flex;
        justify-content: center;
        gap: var(--space-8);
        font-size: var(--font-size-base);
        margin-top: var(--space-12);
      }

      .forecast-card .temp-max {
        font-weight: var(--font-weight-semibold);
      }

      .forecast-card .temp-min {
        color: var(--color-text-secondary);
      }

      /* Footer */
      .footer {
        background: var(--color-surface);
        border-top: 1px solid var(--color-border);
        padding: var(--space-32) var(--space-16);
        text-align: center;
        color: var(--color-text-secondary);
        margin-top: var(--space-48);
      }

      .footer p {
        margin-bottom: var(--space-8);
      }

      .footer a {
        color: var(--color-primary);
        text-decoration: none;
        font-weight: var(--font-weight-medium);
      }

      .footer a:hover {
        text-decoration: underline;
      }

      /* Responsive Design */
      @media (max-width: 767px) {
        .hero h1 {
          font-size: var(--font-size-3xl);
        }

        .hero p {
          font-size: var(--font-size-base);
        }

        .search-form {
          flex-direction: column;
        }

        .search-btn {
          width: 100%;
        }

        .weather-main {
          grid-template-columns: 1fr;
        }

        .temperature-display {
          flex-direction: column;
          text-align: center;
        }

        .weather-icon {
          font-size: 60px;
        }

        .temp-info .temperature {
          font-size: 48px;
        }

        .weather-details {
          grid-template-columns: 1fr;
        }

        .forecast-grid {
          grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
        }

        .current-weather {
          padding: var(--space-20);
        }
      }

      @media (min-width: 768px) and (max-width: 1023px) {
        .forecast-grid {
          grid-template-columns: repeat(4, 1fr);
        }

        .weather-details {
          grid-template-columns: repeat(2, 1fr);
        }
      }

      @media (min-width: 1024px) {
        .forecast-grid {
          grid-template-columns: repeat(7, 1fr);
        }

        .weather-details {
          grid-template-columns: repeat(3, 1fr);
        }
      }

      /* Accessibility */
      .sr-only {
        position: absolute;
        width: 1px;
        height: 1px;
        padding: 0;
        margin: -1px;
        overflow: hidden;
        clip: rect(0, 0, 0, 0);
        white-space: nowrap;
        border: 0;
      }

      /* Touch-friendly buttons */
      @media (hover: none) and (pointer: coarse) {
        .search-btn,
        .recent-search-btn,
        .unit-btn,
        .forecast-card {
          min-height: 44px;
          min-width: 44px;
        }
      }
    </style>
  </head>
  <body>
    <!-- Hero Section -->
    <header class="hero" role="banner">
      <div class="hero-content">
        <h1>Weather Dashboard</h1>
        <p>Get real-time weather forecasts for any city worldwide</p>

        <!-- Search Form -->
        <div class="search-container">
          <form class="search-form" id="searchForm" role="search">
            <label for="cityInput" class="sr-only">Enter city name</label>
            <input
              type="text"
              id="cityInput"
              class="search-input"
              placeholder="Enter city name (e.g., Mumbai, New York, London)"
              required
              autocomplete="off"
              aria-label="City name"
            />
            <button type="submit" class="search-btn" id="searchBtn">
              Search
            </button>
          </form>

          <!-- Recent Searches -->
          <div
            class="recent-searches"
            id="recentSearches"
            role="navigation"
            aria-label="Recent searches"
          ></div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <main class="container" role="main">
      <!-- Loading Spinner -->
      <div class="loading" id="loading" aria-live="polite" aria-busy="false">
        <div class="spinner" role="status"></div>
        <p>Fetching weather data...</p>
      </div>

      <!-- Error Message -->
      <div
        class="error-message"
        id="errorMessage"
        role="alert"
        aria-live="assertive"
      ></div>

      <!-- Weather Display -->
      <div class="weather-display" id="weatherDisplay">
        <!-- Current Weather -->
        <section class="current-weather" aria-label="Current weather">
          <div class="weather-header">
            <div class="location-info">
              <h2 id="locationName">City Name</h2>
              <p class="current-time" id="currentTime">Loading...</p>
            </div>
            <div
              class="unit-toggle"
              role="group"
              aria-label="Temperature unit toggle"
            >
              <button
                class="unit-btn active"
                data-unit="celsius"
                aria-pressed="true"
              >
                &deg;C
              </button>
              <button
                class="unit-btn"
                data-unit="fahrenheit"
                aria-pressed="false"
              >
                &deg;F
              </button>
            </div>
          </div>

          <div class="weather-main">
            <div class="temperature-display">
              <div class="weather-icon" id="weatherIcon" aria-hidden="true">
                ☀️
              </div>
              <div class="temp-info">
                <div class="temperature" id="temperature">--&deg;</div>
                <div class="feels-like" id="feelsLike">Feels like --&deg;</div>
              </div>
            </div>
            <div>
              <p class="weather-description" id="weatherDescription">
                Loading...
              </p>
            </div>
          </div>

          <!-- Weather Details -->
          <div class="weather-details">
            <div class="detail-item">
              <div class="label">💧 Humidity</div>
              <div class="value" id="humidity">--%</div>
            </div>
            <div class="detail-item">
              <div class="label">💨 Wind Speed</div>
              <div class="value" id="windSpeed">-- km/h</div>
            </div>
            <div class="detail-item">
              <div class="label">🌅 Sunrise</div>
              <div class="value" id="sunrise">--:--</div>
            </div>
            <div class="detail-item">
              <div class="label">🌇 Sunset</div>
              <div class="value" id="sunset">--:--</div>
            </div>
            <div class="detail-item">
              <div class="label">👁️ Visibility</div>
              <div class="value" id="visibility">-- km</div>
            </div>
            <div class="detail-item">
              <div class="label">🌡️ Pressure</div>
              <div class="value" id="pressure">-- hPa</div>
            </div>
          </div>
        </section>

        <!-- 7-Day Forecast -->
        <section class="forecast-section" aria-label="7-day forecast">
          <h3>7-Day Forecast</h3>
          <div class="forecast-grid" id="forecastGrid"></div>
        </section>
      </div>
    </main>

    <script src="app.js"></script>
  </body>
</html>
