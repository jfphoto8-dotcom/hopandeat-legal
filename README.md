<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Hop&Eat — Encuentra los mejores restaurantes y bares cerca de ti. Disponible en iOS y Android.">
  <meta property="og:title" content="Hop&Eat — Encuentra dónde comer">
  <meta property="og:description" content="Descubre restaurantes y bares cercanos, lee reseñas con IA y comparte tus favoritos.">
  <meta property="og:image" content="https://hopandeat.app/og-image.png">
  <title>Hop&Eat — Encuentra dónde comer</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; background: #FBF7F4; color: #2C1A0E; }

    /* HERO */
    .hero {
      background: linear-gradient(160deg, #3E1F0D 0%, #5C3317 60%, #7D4A2A 100%);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 40px 24px;
      position: relative;
      overflow: hidden;
    }
    .hero::before {
      content: '';
      position: absolute;
      width: 400px; height: 400px;
      background: #C47A2B;
      border-radius: 50%;
      opacity: 0.08;
      top: -100px; right: -100px;
    }
    .hero::after {
      content: '';
      position: absolute;
      width: 300px; height: 300px;
      background: #C47A2B;
      border-radius: 50%;
      opacity: 0.06;
      bottom: -80px; left: -80px;
    }
    .logo-emoji { font-size: 72px; margin-bottom: 16px; }
    .hero h1 {
      font-size: clamp(36px, 8vw, 64px);
      font-weight: 800;
      color: white;
      letter-spacing: -1px;
      margin-bottom: 8px;
    }
    .hero h1 span { color: #C47A2B; }
    .hero p {
      font-size: clamp(16px, 3vw, 20px);
      color: rgba(255,255,255,0.75);
      max-width: 520px;
      margin: 0 auto 40px;
      line-height: 1.6;
    }
    .badges {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 48px;
    }
    .badge-btn {
      display: flex;
      align-items: center;
      gap: 10px;
      background: rgba(255,255,255,0.1);
      border: 1.5px solid rgba(255,255,255,0.2);
      color: white;
      padding: 12px 24px;
      border-radius: 14px;
      text-decoration: none;
      font-size: 15px;
      font-weight: 500;
      backdrop-filter: blur(10px);
      transition: all 0.2s;
    }
    .badge-btn:hover {
      background: rgba(255,255,255,0.2);
      transform: translateY(-2px);
    }
    .badge-btn .icon { font-size: 24px; }
    .badge-btn .sub { font-size: 11px; opacity: 0.7; display: block; }
    .scroll-hint {
      color: rgba(255,255,255,0.4);
      font-size: 13px;
      margin-top: 16px;
    }

    /* FEATURES */
    .features {
      padding: 80px 24px;
      max-width: 1000px;
      margin: 0 auto;
      text-align: center;
    }
    .section-label {
      color: #C47A2B;
      font-size: 13px;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 2px;
      margin-bottom: 12px;
    }
    .features h2 {
      font-size: clamp(28px, 5vw, 42px);
      font-weight: 800;
      color: #3E1F0D;
      margin-bottom: 16px;
    }
    .features > p {
      color: #7D4A2A;
      font-size: 17px;
      max-width: 500px;
      margin: 0 auto 56px;
      line-height: 1.6;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 20px;
    }
    .card {
      background: white;
      border-radius: 20px;
      padding: 28px 24px;
      text-align: left;
      border: 1px solid #eeddd4;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    .card:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 40px rgba(92,51,23,0.1);
    }
    .card-icon { font-size: 36px; margin-bottom: 16px; }
    .card h3 { font-size: 18px; font-weight: 700; color: #3E1F0D; margin-bottom: 8px; }
    .card p { color: #7D4A2A; font-size: 14px; line-height: 1.6; }
    .card .badge-pro {
      display: inline-block;
      background: #C47A2B;
      color: white;
      font-size: 10px;
      font-weight: 700;
      padding: 2px 8px;
      border-radius: 20px;
      margin-left: 6px;
      vertical-align: middle;
    }

    /* PRICING */
    .pricing {
      background: #3E1F0D;
      padding: 80px 24px;
      text-align: center;
    }
    .pricing .section-label { color: #C47A2B; }
    .pricing h2 { color: white; font-size: clamp(28px, 5vw, 42px); font-weight: 800; margin-bottom: 16px; }
    .pricing > p { color: rgba(255,255,255,0.65); font-size: 17px; max-width: 500px; margin: 0 auto 48px; }
    .plans {
      display: flex;
      gap: 20px;
      justify-content: center;
      flex-wrap: wrap;
      max-width: 700px;
      margin: 0 auto;
    }
    .plan {
      background: rgba(255,255,255,0.06);
      border: 1.5px solid rgba(255,255,255,0.12);
      border-radius: 20px;
      padding: 32px 28px;
      flex: 1;
      min-width: 220px;
      text-align: center;
      backdrop-filter: blur(10px);
    }
    .plan.featured {
      background: #C47A2B;
      border-color: #C47A2B;
      transform: scale(1.04);
    }
    .plan .plan-name { color: rgba(255,255,255,0.7); font-size: 13px; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 12px; }
    .plan.featured .plan-name { color: rgba(255,255,255,0.85); }
    .plan .price { font-size: 42px; font-weight: 800; color: white; }
    .plan .price span { font-size: 16px; font-weight: 400; opacity: 0.7; }
    .plan .save { color: rgba(255,255,255,0.6); font-size: 13px; margin: 8px 0 20px; }
    .plan.featured .save { color: rgba(255,255,255,0.8); }
    .plan ul { list-style: none; text-align: left; margin-bottom: 24px; }
    .plan ul li { color: rgba(255,255,255,0.8); font-size: 14px; padding: 5px 0; }
    .plan ul li::before { content: '✓ '; color: #C47A2B; font-weight: 700; }
    .plan.featured ul li::before { color: white; }
    .plan-cta {
      display: block;
      background: rgba(255,255,255,0.15);
      color: white;
      padding: 12px;
      border-radius: 12px;
      text-decoration: none;
      font-weight: 600;
      font-size: 15px;
    }
    .plan.featured .plan-cta { background: white; color: #C47A2B; }

    /* FOOTER */
    footer {
      background: #2C1A0E;
      padding: 40px 24px;
      text-align: center;
    }
    footer .logo { font-size: 24px; font-weight: 800; color: white; margin-bottom: 8px; }
    footer p { color: rgba(255,255,255,0.4); font-size: 13px; margin-bottom: 16px; }
    footer .links { display: flex; gap: 20px; justify-content: center; flex-wrap: wrap; }
    footer .links a { color: rgba(255,255,255,0.5); font-size: 13px; text-decoration: none; }
    footer .links a:hover { color: #C47A2B; }
  </style>
</head>
<body>

  <!-- HERO -->
  <section class="hero">
    <img src="logo.png" alt="Hop&Eat" style="width:120px;height:120px;object-fit:contain;margin-bottom:16px;">
    <h1>Hop<span>&Eat</span></h1>
    <p>Encuentra los mejores restaurantes y bares cerca de ti. Con reseñas reales, resúmenes de IA y mucho más.</p>
    <div class="badges">
      <a href="#"><img src="appstore.svg" alt="Download on the App Store" style="height:52px;"></a>
      <a href="#"><img src="googleplay.png" alt="Get it on Google Play" style="height:52px;"></a>
    </div>
    <p class="scroll-hint">↓ Descubre más</p>
  </section>

  <!-- FEATURES -->
  <section class="features">
    <div class="section-label">Funcionalidades</div>
    <h2>Todo lo que necesitas para salir a comer</h2>
    <p>Hop&Eat combina datos reales de Google Places con inteligencia artificial para darte la mejor experiencia.</p>
    <div class="grid">
      <div class="card">
        <div class="card-icon">📍</div>
        <h3>Cerca de ti</h3>
        <p>Detecta tu ubicación automáticamente y muestra los mejores sitios en segundos.</p>
      </div>
      <div class="card">
        <div class="card-icon">⭐</div>
        <h3>Reseñas reales</h3>
        <p>Valoraciones y reseñas reales de Google Places, siempre actualizadas.</p>
      </div>
      <div class="card">
        <div class="card-icon">✨</div>
        <h3>Resumen IA <span class="badge-pro">PRO</span></h3>
        <p>Inteligencia artificial analiza las reseñas y te da un resumen claro de lo mejor y lo peor.</p>
      </div>
      <div class="card">
        <div class="card-icon">❤️</div>
        <h3>Favoritos <span class="badge-pro">PRO</span></h3>
        <p>Guarda tus sitios favoritos y crea listas personalizadas para cada ocasión.</p>
      </div>
      <div class="card">
        <div class="card-icon">🔍</div>
        <h3>Filtros avanzados <span class="badge-pro">PRO</span></h3>
        <p>Filtra por tipo de cocina, precio, valoración mínima y radio de búsqueda.</p>
      </div>
      <div class="card">
        <div class="card-icon">📱</div>
        <h3>Compartir</h3>
        <p>Comparte restaurantes por WhatsApp con un solo toque.</p>
      </div>
    </div>
  </section>

  <!-- PRICING -->
  <section class="pricing">
    <div class="section-label">Precios</div>
    <h2>Simple y transparente</h2>
    <p>Empieza gratis y desbloquea todo con Premium por menos de 1€ al mes.</p>
    <div class="plans">
      <div class="plan">
        <div class="plan-name">Gratuito</div>
        <div class="price">0€</div>
        <div class="save">Para siempre</div>
        <ul>
          <li>5 restaurantes por búsqueda</li>
          <li>2 reseñas por sitio</li>
          <li>Radio de 1 km</li>
          <li>Compartir básico</li>
        </ul>
        <a href="#" class="plan-cta">Descargar gratis</a>
      </div>
      <div class="plan featured">
        <div class="plan-name">⭐ Premium Anual</div>
        <div class="price">9,99€<span>/año</span></div>
        <div class="save">Menos de 1€ al mes · Ahorra un 58%</div>
        <ul>
          <li>Resultados ilimitados</li>
          <li>Resumen IA de reseñas</li>
          <li>Filtros avanzados</li>
          <li>Favoritos y listas</li>
          <li>Radio hasta 5 km</li>
          <li>Alertas de ofertas</li>
        </ul>
        <a href="#" class="plan-cta">Activar Premium</a>
      </div>
      <div class="plan">
        <div class="plan-name">Premium Mensual</div>
        <div class="price">1,99€<span>/mes</span></div>
        <div class="save">&nbsp;</div>
        <ul>
          <li>Todo lo de Premium anual</li>
          <li>Cancela cuando quieras</li>
        </ul>
        <a href="#" class="plan-cta">Empezar ahora</a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="logo">🍺 Hop&Eat</div>
    <p>Encuentra dónde comer, ahora mismo.</p>
    <div class="links">
      <a href="/privacy.html">Política de Privacidad</a>
      <a href="/terms.html">Términos y Condiciones</a>
      <a href="mailto:support@hopandeat.app">Contacto</a>
    </div>
    <p style="margin-top:20px;">© 2026 Hop&Eat · España</p>
  </footer>

</body>
</html>
