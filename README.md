<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Invitación — Majo & Facundo</title>
  <meta name="description" content="Tarjeta digital de boda con flores en tonos lila: portada animada, cuenta regresiva, ubicación, agenda y confirmación de asistencia." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
  <style>
    :root{
      --lila-50:#f6f2fb; /* fondo suave */
      --lila-100:#eee8f8;
      --lila-200:#e0d3f3;
      --lila-300:#ccb3ec;
      --lila-400:#b78fe3;
      --lila-500:#a06bd9; /* principal */
      --lila-600:#8c55c7;
      --lila-700:#7647a5;
      --lila-800:#5d3781;
      --lila-900:#472a62;
      --text:#2b2533;
      --muted:#6b6473;
      --white:#fff;
      --shadow: 0 10px 25px rgba(70, 32, 102, .15);
    }

    html,body{margin:0;padding:0;font-family:Poppins,system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,"Helvetica Neue",Arial,sans-serif;color:var(--text);background:var(--lila-50);}
    img{max-width:100%;display:block}
    a{text-decoration:none;color:inherit}
    .container{width:min(1000px,92%);margin-inline:auto}
    .btn{display:inline-flex;align-items:center;gap:.6rem;padding:.9rem 1.1rem;border-radius:999px;border:1px solid transparent;background:var(--lila-500);color:var(--white);box-shadow:var(--shadow);font-weight:600;transition:.25s}
    .btn:hover{transform:translateY(-1px);filter:brightness(1.04)}
    .btn-outline{background:transparent;color:var(--lila-700);border-color:var(--lila-300)}
    .btn-outline:hover{background:var(--lila-100)}
    .pill{display:inline-block;background:var(--lila-100);color:var(--lila-700);padding:.35rem .8rem;border-radius:999px;border:1px solid var(--lila-200);font-size:.85rem}

    /* --- HERO --- */
    .hero{position:relative;min-height:100dvh;display:grid;place-items:center;overflow:hidden;background:linear-gradient(180deg, var(--lila-100), var(--lila-50));}
    .hero-card{position:relative;isolation:isolate;text-align:center;padding:2.2rem 1.5rem;border-radius:28px;background:rgba(255,255,255,.75);backdrop-filter:blur(8px);box-shadow:var(--shadow)}
    .hero h1{font-family:"Playfair Display",serif;font-size:clamp(2.2rem,6vw,3.6rem);line-height:1.05;margin:.6rem 0 .2rem;color:var(--lila-800)}
    .amp{letter-spacing:.06em;color:var(--lila-500)}
    .date{font-weight:500;color:var(--muted);margin-bottom:1rem}
    .actions{display:flex;gap:.8rem;justify-content:center;flex-wrap:wrap;margin-top:1.2rem}
    .scroll-ind{position:absolute;bottom:22px;left:50%;translate:-50% 0;color:var(--muted);font-size:.9rem;display:flex;align-items:center;gap:.5rem}

    /* Florales decorativos */
    .floral{position:absolute;inset:0;pointer-events:none}
    .floral svg{position:absolute;opacity:.65;filter:drop-shadow(0 6px 12px rgba(96,51,133,.18))}
    .floral .tl{top:-30px;left:-20px;max-width:180px;}
    .floral .br{bottom:-30px;right:-10px;max-width:200px;}

    /* --- COUNTDOWN --- */
    .countdown{padding:3rem 0 2.2rem}
    .count-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:.8rem}
    .counter{background:var(--white);border:1px solid var(--lila-200);padding:1.1rem;border-radius:18px;text-align:center;box-shadow:var(--shadow)}
    .counter .num{font-family:"Playfair Display",serif;font-size:clamp(1.6rem,5vw,2.2rem);color:var(--lila-800)}
    .counter .lab{font-size:.9rem;color:var(--muted)}

    /* --- SECTIONS --- */
    section{padding:3.8rem 0}
    .card{background:var(--white);border:1px solid var(--lila-200);border-radius:24px;padding:1.6rem;box-shadow:var(--shadow)}
    h2{font-family:"Playfair Display",serif;color:var(--lila-800);font-size:clamp(1.6rem,4.5vw,2.2rem);margin:.2rem 0 1rem}
    .sub{color:var(--muted);margin-top:-.6rem;margin-bottom:1.2rem}

    /* Ubicación */
    .grid-2{display:grid;grid-template-columns:1.2fr 1fr;gap:1.2rem}
    @media (max-width: 860px){.grid-2{grid-template-columns:1fr}}
    .map{aspect-ratio:16/10;border:0;width:100%;border-radius:16px}

    /* Galería simple */
    .gallery{display:grid;grid-template-columns:repeat(3,1fr);gap:.6rem}
    .gallery img{border-radius:14px}
    @media (max-width:720px){.gallery{grid-template-columns:repeat(2,1fr)}}

    /* Música */
    .music{position:fixed;right:16px;bottom:16px;z-index:50}
    .music button{border-radius:999px;border:1px solid var(--lila-300);background:var(--white);box-shadow:var(--shadow);padding:.7rem 1rem;font-weight:600;color:var(--lila-800)}

    /* Footer */
    footer{padding:2.2rem 0 3.2rem;color:var(--muted);text-align:center}

    /* Suavizar desplazamiento */
    html{scroll-behavior:smooth}
  </style>
</head>
<body>
  <!-- Música de fondo (reemplazar src por tu pista .mp3) -->
  <audio id="song" src="musica.mp3" preload="auto" loop></audio>
  <div class="music">
    <button id="toggleMusic" aria-pressed="false">♪ Música</button>
  </div>

  <!-- HERO -->
  <header class="hero">
    <div class="floral" aria-hidden="true">
      <!-- Esquina superior izquierda -->
      <svg class="tl" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="g1" x1="0" x2="1" y1="0" y2="1">
            <stop offset="0%" stop-color="var(--lila-300)"/>
            <stop offset="100%" stop-color="var(--lila-500)"/>
          </linearGradient>
        </defs>
        <g fill="url(#g1)">
          <path d="M30 220c40-50 60-100 120-140 30-20 70-30 90-25-20 25-60 45-80 70-22 29-30 66-75 100-18 14-40 16-55-5z" opacity=".8"/>
          <circle cx="85" cy="90" r="14"/>
          <circle cx="110" cy="65" r="9" opacity=".7"/>
          <circle cx="135" cy="95" r="6" opacity=".5"/>
        </g>
      </svg>
      <!-- Esquina inferior derecha -->
      <svg class="br" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="g2" x1="0" x2="1" y1="1" y2="0">
            <stop offset="0%" stop-color="var(--lila-400)"/>
            <stop offset="100%" stop-color="var(--lila-600)"/>
          </linearGradient>
        </defs>
        <g fill="url(#g2)">
          <path d="M270 60c-35 40-54 82-110 120-34 24-82 38-104 34 24-22 66-44 88-74 25-34 31-72 76-106 18-13 40-13 50 26z" opacity=".8"/>
          <circle cx="210" cy="200" r="12"/>
          <circle cx="230" cy="175" r="8" opacity=".7"/>
          <circle cx="250" cy="210" r="6" opacity=".5"/>
        </g>
      </svg>
    </div>

    <div class="container hero-card">
      <span class="pill">¡Nos casamos!</span>
      <h1><span id="n1">Nombres</span> <span class="amp">&amp;</span> <span id="n2">Nombres</span></h1>
      <p class="date" id="dateText">Sábado 28 de Febrero de 2026 · 12:00 hs</p>
      <div class="actions">
        <a class="btn" href="#rsvp">Confirmar asistencia</a>
        <a class="btn btn-outline" href="#info">Ver detalles</a>
      </div>
      <div class="scroll-ind">▼ Deslizá para ver más</div>
    </div>
  </header>

  <!-- COUNTDOWN -->
  <section class="countdown container">
    <h2>Falta muy poquito</h2>
    <p class="sub">Acompañanos en este día especial. Activá el recordatorio y confirmá tu asistencia.</p>
    <div class="count-grid" id="countdown">
      <div class="counter"><div class="num" id="d">00</div><div class="lab">Días</div></div>
      <div class="counter"><div class="num" id="h">00</div><div class="lab">Horas</div></div>
      <div class="counter"><div class="num" id="m">00</div><div class="lab">Minutos</div></div>
      <div class="counter"><div class="num" id="s">00</div><div class="lab">Segundos</div></div>
    </div>
    <div class="actions">
      <button class="btn" id="addToCalendar">Agregar al calendario</button>
      <a class="btn btn-outline" href="#ubicacion">Cómo llegar</a>
    </div>
  </section>

  <!-- INFO + UBICACIÓN -->
  <section id="info" class="container">
    <div class="grid-2">
      <div class="card">
        <h2>Ceremonia & Fiesta</h2>
        <p><strong>Ceremonia:</strong> Parroquia Ejemplo, 19:00 hs</p>
        <p><strong>Fiesta:</strong> Salón Lila, 20:30 hs</p>
        <p class="sub">Dress code: Elegante. Sugerimos tonos claros y pasteles.</p>
        <div class="actions">
          <a class="btn" href="#rsvp">Confirmar asistencia</a>
          <a class="btn btn-outline" href="#regalos">Lista de regalos</a>
        </div>
      </div>
      <div id="ubicacion" class="card">
        <h2>Ubicación</h2>
        <p class="sub">Tocá el mapa para abrir en Google Maps</p>
        <a target="_blank" rel="noopener" href="https://maps.google.com/?q=Sal%C3%B3n%20Lila%20Salta">
          <img class="map" alt="Mapa del salón" src="https://maps.googleapis.com/maps/api/staticmap?center=-24.7883,-65.4106&zoom=13&size=800x500&maptype=roadmap&markers=color:purple|-24.7883,-65.4106&key=AIzaSyDUMMY"/>
        </a>
      </div>
    </div>
  </section>

  <!-- GALERÍA -->
  <section class="container">
    <div class="card">
      <h2>Momentos</h2>
      <p class="sub">Algunas fotos nuestras. ¡Etiquetanos con <strong>#BodaLila</strong>!</p>
      <div class="gallery">
        <img src="https://images.unsplash.com/photo-1522673607200-164d1b6ce486?q=80&w=1200&auto=format&fit=crop" alt="Flores lila 1"/>
        <img src="https://images.unsplash.com/photo-1504196606672-aef5c9cefc92?q=80&w=1200&auto=format&fit=crop" alt="Flores lila 2"/>
        <img src="https://images.unsplash.com/photo-1491002052546-bf38f186af2f?q=80&w=1200&auto=format&fit=crop" alt="Flores lila 3"/>
        <img src="https://images.unsplash.com/photo-1504196606672-aef5c9cefc92?q=80&w=1200&auto=format&fit=crop" alt="Flores lila 4"/>
        <img src="https://images.unsplash.com/photo-1522673607200-164d1b6ce486?q=80&w=1200&auto=format&fit=crop" alt="Flores lila 5"/>
        <img src="https://images.unsplash.com/photo-1491002052546-bf38f186af2f?q=80&w=1200&auto=format&fit=crop" alt="Flores lila 6"/>
      </div>
    </div>
  </section>

  <!-- REGALOS -->
  <section id="regalos" class="container">
    <div class="card">
      <h2>Regalos</h2>
      <p class="sub">Tu presencia es lo más importante. Si querés hacernos un regalo:</p>
      <ul>
        <li>Alias: <strong>BODA.LILA.2025</strong></li>
        <li>CBU: <strong>00000000 0000000000000000</strong></li>
        <li>Lista en Tienda: <a class="pill" href="#">Ver lista online</a></li>
      </ul>
    </div>
  </section>

  <!-- RSVP / CONFIRMACIÓN -->
  <section id="rsvp" class="container">
    <div class="card">
      <h2>Confirmación de asistencia</h2>
      <p class="sub">Por favor, completá tus datos. ¡Gracias!</p>
      <!-- Opción A: Formulario nativo con Formspree (reemplazar action por tu endpoint) -->
      <form action="https://formspree.io/f/tu-endpoint" method="POST" class="rsvpf" onsubmit="this.querySelector('button[type=submit]').disabled=true">
        <div style="display:grid;gap:.8rem;grid-template-columns:1fr 1fr;">
          <label>Nombre y apellido<br>
            <input required name="nombre" type="text" placeholder="Nombre" style="width:100%;padding:.8rem;border:1px solid var(--lila-200);border-radius:12px">
          </label>
          <label>Teléfono<br>
            <input required name="telefono" type="tel" placeholder="11 2345 6789" style="width:100%;padding:.8rem;border:1px solid var(--lila-200);border-radius:12px">
          </label>
          <label style="grid-column:1/-1">¿Asistís?<br>
            <select required name="asistencia" style="width:100%;padding:.8rem;border:1px solid var(--lila-200);border-radius:12px">
              <option value="Sí">Sí, confirmo</option>
              <option value="No">No puedo</option>
              <option value="Duda">Lo confirmo más cerca</option>
            </select>
          </label>
          <label style="grid-column:1/-1">Mensaje (opcional)<br>
            <textarea name="mensaje" rows="3" placeholder="Dejanos un mensajito" style="width:100%;padding:.8rem;border:1px solid var(--lila-200);border-radius:12px"></textarea>
          </label>
        </div>
        <div class="actions" style="margin-top:1rem">
          <button class="btn" type="submit">Enviar confirmación</button>
          <!-- Opción B: Link a Google Forms (si preferís) -->
          <a class="btn btn-outline" target="_blank" rel="noopener" href="https://forms.gle/tu-form">Usar Google Forms</a>
        </div>
      </form>
    </div>
  </section>

  <footer>
    Hecho con ♥ en tonos lila · <a href="#" onclick="window.scrollTo({top:0,behavior:'smooth'})">Volver arriba</a>
  </footer>

  <script>
    // ===== Configuración rápida (editá estos datos) =====
    const NOMBRE_1 = "Majo";   // reemplazar
    const NOMBRE_2 = "Facundo";    // reemplazar
    // Fecha y hora del evento (zona: América/Argentina/Buenos_Aires)
    const EVENTO = new Date("2026-02-28T12:00:00-03:00");
    const LUGAR = "Salón Lila, Salta"; // se usa para el .ics

    // Inyectar nombres y fecha legible
    document.getElementById('n1').textContent = NOMBRE_1;
    document.getElementById('n2').textContent = NOMBRE_2;
    const dateFmt = new Intl.DateTimeFormat('es-AR', {weekday:'long', day:'2-digit', month:'long', year:'numeric', hour:'2-digit', minute:'2-digit'});
    document.getElementById('dateText').textContent =
      dateFmt.format(EVENTO).replace(/\b\w/g, c => c.toUpperCase());

    // ===== Countdown =====
    function updateCountdown(){
      const now = new Date();
      let diff = Math.max(0, EVENTO - now);
      const d = Math.floor(diff / (1000*60*60*24)); diff -= d*(1000*60*60*24);
      const h = Math.floor(diff / (1000*60*60)); diff -= h*(1000*60*60);
      const m = Math.floor(diff / (1000*60)); diff -= m*(1000*60);
      const s = Math.floor(diff / 1000);
      document.getElementById('d').textContent = String(d).padStart(2,'0');
      document.getElementById('h').textContent = String(h).padStart(2,'0');
      document.getElementById('m').textContent = String(m).padStart(2,'0');
      document.getElementById('s').textContent = String(s).padStart(2,'0');
    }
    updateCountdown();
    setInterval(updateCountdown, 1000);

    // ===== Agregar al calendario (.ics) =====
    document.getElementById('addToCalendar').addEventListener('click', () => {
      // Evento de 5 horas por defecto
      const end = new Date(EVENTO.getTime() + 5*60*60*1000);
      function toICS(dt){
        const pad = n => String(n).padStart(2,'0');
        const y = dt.getUTCFullYear();
        const mo = pad(dt.getUTCMonth()+1);
        const d = pad(dt.getUTCDate());
        const h = pad(dt.getUTCHours());
        const mi = pad(dt.getUTCMinutes());
        const s = pad(dt.getUTCSeconds());
        return `${y}${mo}${d}T${h}${mi}${s}Z`;
      }
      const ics = `BEGIN:VCALENDAR\nVERSION:2.0\nPRODID:-//Tarjeta Lila//ES\nBEGIN:VEVENT\nUID:${Date.now()}@tarjeta-lila\nDTSTAMP:${toICS(new Date())}\nDTSTART:${toICS(EVENTO)}\nDTEND:${toICS(end)}\nSUMMARY:Boda ${NOMBRE_1} & ${NOMBRE_2}\nLOCATION:${LUGAR}\nDESCRIPTION:¡Nos casamos!\nEND:VEVENT\nEND:VCALENDAR`;
      const blob = new Blob([ics], {type:'text/calendar'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url; a.download = `Boda-${NOMBRE_1}-${NOMBRE_2}.ics`;
      document.body.appendChild(a); a.click(); a.remove();
      URL.revokeObjectURL(url);
    });

    // ===== Música de fondo (control simple) =====
    const song = document.getElementById('song');
    const btn = document.getElementById('toggleMusic');
    let playing = false;
    btn.addEventListener('click', async ()=>{
      try{
        if(!playing){await song.play(); playing = true; btn.textContent = '❚❚ Pausar música'; btn.setAttribute('aria-pressed','true');}
        else{song.pause(); playing = false; btn.textContent = '♪ Música'; btn.setAttribute('aria-pressed','false');}
      }catch(e){alert('Para reproducir la música, tocá de nuevo.');}
    });
  </script>
</body>
</html>
