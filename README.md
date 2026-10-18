<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>TICo · Asistente de TicsEducación</title>
<meta name="description" content="Asistente virtual de TicsEducación: formación, servicios, herramientas digitales y blog.">
<style>
  html,body{margin:0;min-height:100%;background:#e9f1f3}
  .tico-volver{display:block;max-width:720px;margin:16px auto 0;padding:0 16px;font:600 14px system-ui,sans-serif;color:#0f5c6e}
  @media (max-width:520px){.tico-volver{display:none}}
</style>
</head>
<body>
<a class="tico-volver" href="https://ticseducaciondotcom.wordpress.com/">← Volver a TicsEducación</a>
<script>window.TICO_MODO_PAGINA = true;</script>
<!-- ================================================================
     CHATBOT «TICo» · Asistente virtual de TicsEducación
     Versión 1.0 · Widget autocontenido (HTML + CSS + JavaScript)
     Funciona sin servidor, sin claves de API y sin coste.
     Dónde pegarlo: bloque «HTML personalizado» de WordPress o plugin
     WPCode → «Pie de página» (solo planes con plugins activados).
     ================================================================ -->
<div id="tico-root" class="tico" aria-live="off">
  <button id="tico-launcher" class="tico-launcher" type="button" aria-label="Abrir el asistente virtual de TicsEducación" aria-expanded="false" aria-controls="tico-panel">
    <svg viewBox="0 0 24 24" width="28" height="28" aria-hidden="true"><path fill="currentColor" d="M4 4h16a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H9l-4.5 3.6A.6.6 0 0 1 3.5 21v-3H4a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2Zm4 6.2a1.3 1.3 0 1 0 0 2.6 1.3 1.3 0 0 0 0-2.6Zm4 0a1.3 1.3 0 1 0 0 2.6 1.3 1.3 0 0 0 0-2.6Zm4 0a1.3 1.3 0 1 0 0 2.6 1.3 1.3 0 0 0 0-2.6Z"/></svg>
    <span class="tico-badge" aria-hidden="true">1</span>
  </button>

  <section id="tico-panel" class="tico-panel" role="dialog" aria-modal="false" aria-labelledby="tico-title" hidden>
    <header class="tico-header">
      <div class="tico-avatar" aria-hidden="true">T</div>
      <div class="tico-head-text">
        <h2 id="tico-title">TICo</h2>
        <p><span class="tico-dot" aria-hidden="true"></span>Asistente de TicsEducación · en línea</p>
      </div>
      <button class="tico-icon-btn" id="tico-reset" type="button" aria-label="Reiniciar la conversación" title="Reiniciar">
        <svg viewBox="0 0 24 24" width="18" height="18" aria-hidden="true"><path fill="currentColor" d="M12 5V2L7 6l5 4V7a5 5 0 1 1-5 5H5a7 7 0 1 0 7-7Z"/></svg>
      </button>
      <button class="tico-icon-btn" id="tico-close" type="button" aria-label="Cerrar el asistente" title="Cerrar">
        <svg viewBox="0 0 24 24" width="18" height="18" aria-hidden="true"><path fill="currentColor" d="M6.4 5 12 10.6 17.6 5 19 6.4 13.4 12l5.6 5.6-1.4 1.4L12 13.4 6.4 19 5 17.6 10.6 12 5 6.4Z"/></svg>
      </button>
    </header>

    <div id="tico-log" class="tico-log" role="log" aria-live="polite" aria-relevant="additions"></div>

    <div id="tico-chips" class="tico-chips" aria-label="Sugerencias"></div>

    <form id="tico-form" class="tico-form" autocomplete="off">
      <label for="tico-input" class="tico-sr">Escribe tu pregunta</label>
      <input id="tico-input" type="text" maxlength="300" placeholder="Escribe tu pregunta…" />
      <button type="submit" class="tico-send" aria-label="Enviar">
        <svg viewBox="0 0 24 24" width="20" height="20" aria-hidden="true"><path fill="currentColor" d="M3.4 20.4 21 12 3.4 3.6 3.4 10l12.6 2-12.6 2Z"/></svg>
      </button>
    </form>
    <p class="tico-legal">Asistente automático. No guarda tus datos. Para consultas personales escribe a <a href="mailto:victordelafuente@ticseducacion.com">victordelafuente@ticseducacion.com</a>.</p>
  </section>
</div>

<style>
/* ---------- 1. Variables de diseño (cámbialas para adaptar la marca) ---------- */
#tico-root{
  --tico-main:#0f5c6e;      /* color principal (cabecera, botones)   */
  --tico-main-2:#1b8aa0;    /* degradado del botón flotante           */
  --tico-accent:#f2a33a;    /* acento (notificación, enlaces activos) */
  --tico-bg:#ffffff;        /* fondo del panel                        */
  --tico-surface:#f2f6f7;   /* burbujas del bot                       */
  --tico-text:#1d2a2e;      /* texto principal                        */
  --tico-muted:#5b6b70;     /* texto secundario                       */
  --tico-line:#dbe4e6;      /* bordes                                 */
  --tico-radius:16px;
  font-family:system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  font-size:15px; line-height:1.45; color:var(--tico-text);
}
#tico-root *,#tico-root *::before,#tico-root *::after{box-sizing:border-box}
#tico-root [hidden]{display:none!important}
/* ---------- 0. Escudo frente a estilos del tema de WordPress ---------- */
#tico-root button,#tico-root input{font-family:inherit;text-transform:none;letter-spacing:normal;margin:0;box-shadow:none;min-height:0;text-shadow:none}
#tico-root button{padding:0;line-height:1}
#tico-root h2,#tico-root p,#tico-root ul,#tico-root li,#tico-root a,#tico-root strong,#tico-root em{font-family:inherit;font-size:inherit;line-height:inherit;letter-spacing:normal;text-transform:none}
#tico-root p,#tico-root li{color:inherit}

#tico-root .tico-sr{position:absolute!important;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap}

/* ---------- 2. Botón flotante (lanzador) ---------- */
#tico-root .tico-launcher{position:fixed;right:20px;bottom:20px;z-index:99998;width:60px;height:60px;border:0;border-radius:50%;
  background:linear-gradient(135deg,var(--tico-main),var(--tico-main-2));color:#fff;cursor:pointer;
  box-shadow:0 8px 24px rgba(15,92,110,.35);display:grid;place-items:center;transition:transform .2s ease}
#tico-root .tico-launcher:hover{transform:scale(1.06)}
#tico-root .tico-launcher:focus-visible{outline:3px solid var(--tico-accent);outline-offset:3px}
#tico-root .tico-badge{position:absolute;top:2px;right:2px;min-width:20px;height:20px;border-radius:10px;background:var(--tico-accent);
  color:#1d2a2e;font:700 12px/20px system-ui,sans-serif;text-align:center;padding:0 5px}

/* ---------- 3. Panel de conversación ---------- */
#tico-root .tico-panel{position:fixed;right:20px;bottom:92px;z-index:99999;width:370px;max-width:calc(100vw - 32px);
  height:560px;max-height:calc(100vh - 120px);background:var(--tico-bg);border:1px solid var(--tico-line);
  border-radius:var(--tico-radius);box-shadow:0 18px 50px rgba(0,0,0,.18);display:flex;flex-direction:column;overflow:hidden;
  animation:tico-in .22s ease-out}
@keyframes tico-in{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:none}}
#tico-root .tico-header{display:flex;align-items:center;gap:10px;padding:12px 12px 12px 14px;background:var(--tico-main);color:#fff}
#tico-root .tico-avatar{flex:none;width:38px;height:38px;border-radius:50%;background:#fff;color:var(--tico-main);
  display:grid;place-items:center;font-weight:800;font-size:18px}
#tico-root .tico-head-text{flex:1;min-width:0}
#tico-root .tico-head-text h2{margin:0;font-size:15px;font-weight:700;color:#fff;line-height:1.2;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
#tico-root .tico-head-text p{margin:2px 0 0;font-size:12px;line-height:1.3;opacity:.85}
#tico-root .tico-dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:#5ee08c;margin-right:6px;vertical-align:1px}
#tico-root .tico-icon-btn{flex:none;width:34px;height:34px;border:0;border-radius:8px;background:transparent;color:#fff;cursor:pointer;display:grid;place-items:center}
#tico-root .tico-icon-btn:hover{background:rgba(255,255,255,.15)}
#tico-root .tico-icon-btn:focus-visible{outline:2px solid #fff}

/* ---------- 4. Mensajes ---------- */
#tico-root .tico-log{position:relative;flex:1;overflow-y:auto;padding:16px 14px 8px;display:flex;flex-direction:column;gap:10px;background:var(--tico-bg);scroll-behavior:smooth}
#tico-root .tico-msg{max-width:86%;padding:10px 13px;border-radius:14px;word-wrap:break-word;overflow-wrap:anywhere}
#tico-root .tico-msg p{margin:0 0 6px}#tico-root .tico-msg p:last-child{margin-bottom:0}
#tico-root .tico-msg ul{margin:4px 0 6px;padding-left:18px}#tico-root .tico-msg li{margin:2px 0}
#tico-root .tico-bot{align-self:flex-start;background:var(--tico-surface);border-bottom-left-radius:4px}
#tico-root .tico-user{align-self:flex-end;background:var(--tico-main);color:#fff;border-bottom-right-radius:4px}
#tico-root .tico-msg a{color:var(--tico-main);font-weight:600;text-decoration:underline}
#tico-root .tico-user a{color:#fff}
#tico-root .tico-typing{display:inline-flex;gap:4px;padding:12px 14px}
#tico-root .tico-typing span{width:7px;height:7px;border-radius:50%;background:var(--tico-muted);animation:tico-b 1s infinite ease-in-out}
#tico-root .tico-typing span:nth-child(2){animation-delay:.15s}#tico-root .tico-typing span:nth-child(3){animation-delay:.3s}
@keyframes tico-b{0%,80%,100%{opacity:.3;transform:translateY(0)}40%{opacity:1;transform:translateY(-3px)}}

/* ---------- 5. Botones de respuesta rápida ---------- */
#tico-root .tico-chips{display:flex;flex-wrap:wrap;gap:6px;padding:4px 14px 10px}
#tico-root .tico-chips:empty{display:none}
#tico-root .tico-chip{border:1px solid var(--tico-main);background:#fff;color:var(--tico-main);border-radius:999px;padding:6px 12px;
  font-weight:600;font-size:13px;line-height:1.2;font-family:inherit;text-transform:none;letter-spacing:normal;margin:0;cursor:pointer}
#tico-root .tico-chip:hover,#tico-root .tico-chip:focus-visible{background:var(--tico-main);color:#fff;outline:none}

/* ---------- 6. Caja de escritura ---------- */
#tico-root .tico-form{display:flex;gap:8px;padding:10px 12px;border-top:1px solid var(--tico-line);background:#fff}
#tico-root .tico-form input{flex:1;min-width:0;border:1px solid var(--tico-line);border-radius:999px;padding:10px 14px;font:inherit;color:var(--tico-text);background:#fff}
#tico-root .tico-form input:focus{outline:2px solid var(--tico-main-2);outline-offset:0;border-color:transparent}
#tico-root .tico-send{flex:none;width:42px;height:42px;border:0;border-radius:50%;background:var(--tico-main);color:#fff;cursor:pointer;display:grid;place-items:center}
#tico-root .tico-send:focus-visible{outline:3px solid var(--tico-accent)}
#tico-root .tico-legal{margin:0;line-height:1.35;padding:0 14px 10px;font-size:11px;color:var(--tico-muted);background:#fff}
#tico-root .tico-legal a{color:var(--tico-muted)}

/* ---------- 7. Móvil: el panel ocupa toda la pantalla ---------- */
@media (max-width:520px){
  #tico-root .tico-panel{right:0;bottom:0;width:100vw;max-width:100vw;height:100%;max-height:100%;border-radius:0;border:0}
  #tico-root .tico-launcher{right:16px;bottom:16px}
}

/* ---------- 8. Modo página completa (versión independiente) ---------- */
#tico-root.tico-fullpage .tico-launcher{display:none}
#tico-root.tico-fullpage .tico-panel{position:relative;right:auto;bottom:auto;width:100%;max-width:720px;height:min(760px,calc(100vh - 32px));
  max-height:none;margin:16px auto;animation:none}
@media (max-width:520px){#tico-root.tico-fullpage .tico-panel{margin:0;height:100vh;height:100dvh;border-radius:0}}
@media (prefers-reduced-motion:reduce){#tico-root *{animation:none!important;transition:none!important}}
</style>

<script>
(function () {
  "use strict";

  /* =============================================================
     A. CONFIGURACIÓN GENERAL
     ============================================================= */
  var CONFIG = {
    nombreBot: "TICo",
    web: "https://ticseducaciondotcom.wordpress.com",
    email: "victordelafuente@ticseducacion.com",
    umbral: 2,            // puntuación mínima para dar una respuesta por intención
    maxFallos: 2,         // nº de «no entiendo» seguidos antes de ofrecer contacto
    modoPagina: !!window.TICO_MODO_PAGINA, // true = ocupa toda la página
    abrirAlCargar: !!window.TICO_MODO_PAGINA
  };
  var W = CONFIG.web;

  function a(texto, url) {
    var externo = url.indexOf("mailto:") !== 0;
    return '<a href="' + url + '"' + (externo ? ' target="_blank" rel="noopener"' : "") + ">" + texto + "</a>";
  }
  var MAIL = a(CONFIG.email, "mailto:" + CONFIG.email + "?subject=" + encodeURIComponent("Consulta desde el asistente de TicsEducación"));

  /* =============================================================
     B. BASE DE CONOCIMIENTO (intenciones)
     - claves: palabras o frases que activan la intención.
       «palabra^3» = peso 3 (por defecto, peso 1).
     - respuesta: texto HTML que mostrará el bot.
     - chips: botones de respuesta rápida que se ofrecen después.
     Para AÑADIR una pregunta nueva: copia un bloque { … } y edítalo.
     ============================================================= */
  var INTENCIONES = [
    { id: "saludo",
      claves: ["hola^3", "buenas^3", "buenos dias^4", "buenas tardes^4", "buenas noches^4", "hey^2", "saludos^3", "que tal^2"],
      respuesta: "<p>¡Hola! 👋 Soy <strong>TICo</strong>, el asistente virtual de TicsEducación.</p><p>Puedo informarte sobre la <strong>formación</strong>, los <strong>servicios</strong>, las <strong>herramientas digitales</strong> y el <strong>blog</strong>. ¿Qué te interesa?",
      chips: ["Formación", "Servicios", "Herramientas", "Blog", "Contacto"] },

    { id: "despedida",
      claves: ["adios^3", "hasta luego^4", "chao^3", "nos vemos^3", "hasta pronto^4", "bye^2"],
      respuesta: "<p>¡Hasta pronto! Si te surge otra duda, aquí estaré. 😊</p>",
      chips: [] },

    { id: "gracias",
      claves: ["gracias^3", "muchas gracias^4", "genial^2", "perfecto^2", "vale^1", "ok^1", "estupendo^2"],
      respuesta: "<p>¡A ti! ¿Te puedo ayudar con algo más?</p>",
      chips: ["Formación", "Servicios", "Contacto"] },

    { id: "ayuda",
      claves: ["ayuda^3", "que puedo preguntar^4", "que sabes^3", "que haces^3", "opciones^2", "menu^2", "como funciona^2"],
      respuesta: "<p>Puedes preguntarme, por ejemplo:</p><ul><li>«¿Qué cursos ofrecéis?»</li><li>«¿Qué es SCORM?»</li><li>«¿Quién está detrás de la web?»</li><li>«¿Cómo contacto?»</li></ul><p>O pulsa uno de los botones de abajo.</p>",
      chips: ["Formación", "Servicios", "Herramientas", "Blog", "¿Quién está detrás?"] },

    { id: "bot",
      claves: ["quien eres^4", "eres un robot^4", "eres humano^4", "eres una persona^4", "chatbot^3", "bot^2", "inteligencia artificial^3", "como estas hecho^4", "como funcionas^4"],
      respuesta: "<p>Soy un <strong>chatbot basado en reglas</strong>: analizo las palabras clave de tu mensaje, las comparo con mi base de conocimiento y elijo la respuesta con mayor puntuación. Tolero tildes y algunas faltas de ortografía.</p><p>No soy una persona ni guardo tus datos. Para consultas personales te pongo en contacto con el responsable de la web.</p>",
      chips: ["Contacto", "Formación"] },

    { id: "web",
      claves: ["ticseducacion^3", "que es esta web^4", "de que va^3", "que ofreceis^3", "a que os dedicais^4", "que haceis^3", "pagina^1", "web^1", "sobre nosotros^3"],
      respuesta: "<p><strong>TicsEducación</strong> es un espacio sobre <strong>innovación y herramientas digitales aplicadas a la educación</strong>.</p><p>Se organiza en tres áreas:</p><ul><li><strong>Formación para el Empleo</strong>: cursos, talleres, seminarios y webinars.</li><li><strong>Herramientas</strong>: orientación sobre recursos digitales para cada metodología o materia.</li><li><strong>Servicios</strong>: asesoramiento y diseño de cursos (SCORM, eXeLearning…).</li></ul>",
      chips: ["Formación", "Herramientas", "Servicios"] },

    { id: "autor",
      claves: ["quien esta detras^4", "quien eres tu^2", "autor^3", "victor^4", "fuente montero^4", "responsable^2", "quien soy^3", "docente^1", "formador^2", "profesor^2", "trayectoria^3", "experiencia^2"],
      respuesta: "<p>La web la dirige <strong>Víctor de la Fuente Montero</strong>, licenciado en Geografía e Historia, con unos <strong>25 años</strong> dedicados a la docencia y la investigación.</p><p>Su objetivo es compartir la aplicación de las nuevas tecnologías a la educación, con especial atención a la <strong>teleformación</strong> y la <strong>Formación Profesional para el Empleo</strong>.</p><p>Más información en " + a("¿Quién soy?", W + "/acercademi/") + ".</p>",
      chips: ["Formación", "Contacto"] },

    { id: "formacion",
      claves: ["formacion^3", "curso^3", "cursos^3", "taller^3", "talleres^3", "pildora^3", "pildoras formativas^4", "seminario^3", "webinar^3", "aprender^2", "estudiar^2", "oferta formativa^4", "catalogo^3", "que cursos^4", "formarme^3", "actualizacion^2"],
      respuesta: "<p>TicsEducación propone <strong>talleres, cursos y píldoras formativas</strong> para la actualización docente. Ahora mismo destacan dos líneas:</p><ul><li>📡 <strong>Herramientas de comunicación en la e-Educación</strong></li><li>☁️ <strong>Trabajar en la nube</strong></li></ul><p>Modalidades: cursos, talleres, seminarios y webinars. Mira el detalle en " + a("Formación", W + "/formacion/") + ".</p>",
      chips: ["Comunicación en la e-Educación", "Trabajar en la nube", "Precios y fechas"] },

    { id: "curso_comunicacion",
      claves: ["comunicacion^3", "e-educacion^4", "eeducacion^4", "herramientas de comunicacion^5", "videoconferencia^2", "foro^2", "correo^1", "mensajeria^2"],
      respuesta: "<p>📡 <strong>Herramientas de comunicación en la e-Educación</strong> se centra en las herramientas que permiten comunicarse con el alumnado en entornos digitales de aprendizaje.</p><p>El programa detallado, la duración y las fechas no están publicados en la web: pídelos por correo a " + MAIL + ".</p>",
      chips: ["Trabajar en la nube", "Precios y fechas", "Contacto"] },

    { id: "curso_nube",
      claves: ["nube^4", "cloud^3", "trabajar en la nube^5", "drive^3", "google drive^4", "dropbox^3", "almacenamiento^2", "onedrive^2", "colaborativo^2", "compartir archivos^3"],
      respuesta: "<p>☁️ <strong>Trabajar en la nube</strong> aborda el uso de servicios en línea para guardar, compartir y editar documentos de forma colaborativa en la actividad formativa.</p><p>Para conocer contenidos, duración y fechas, escribe a " + MAIL + ".</p>",
      chips: ["Comunicación en la e-Educación", "Precios y fechas", "Contacto"] },

    { id: "precios",
      claves: ["precio^4", "precios^4", "cuanto cuesta^5", "cuesta^3", "coste^3", "tarifa^3", "gratis^3", "gratuito^3", "pagar^2", "fecha^3", "fechas^3", "cuando empieza^4", "calendario^3", "horario^3", "inscripcion^4", "inscribirme^4", "matricula^4", "apuntarme^4", "plazas^3", "certificado^3", "titulo^2", "duracion^3", "horas^2", "online^2", "presencial^3", "modalidad^3"],
      respuesta: "<p>Los <strong>precios, fechas, duración, modalidad y certificación</strong> de cada acción formativa no están publicados en la web porque se adaptan a cada grupo.</p><p>Solicítalos directamente a " + MAIL + " indicando qué formación te interesa y cuántas personas sois.</p>",
      chips: ["Formación", "Contacto"] },

    { id: "fpe",
      claves: ["formacion para el empleo^5", "fpe^4", "empleo^3", "trabajo^1", "desempleado^3", "parado^2", "ocupados^2", "certificado de profesionalidad^5", "sepe^3", "teleformacion^3"],
      respuesta: "<p>La <strong>Formación Profesional para el Empleo</strong> es uno de los ejes de TicsEducación: acciones formativas para actualizar contenidos y competencias tecnológicas aplicadas a la educación.</p><p>También hay una reflexión sobre la docencia en teleformación en el blog: " + a("La docencia en función de los principios de la teleformación", W + "/2020/09/13/la-docencia-en-funcion-de-los-principios-de-la-teleformacion/") + ".</p>",
      chips: ["Formación", "Blog", "Contacto"] },

    { id: "herramientas",
      claves: ["herramientas^4", "herramienta^4", "recursos^3", "recurso^3", "aplicaciones^3", "apps^3", "programas^2", "tic^3", "tics^3", "digital^2", "digitales^2", "metodologia^2", "materia^2", "que herramienta^4"],
      respuesta: "<p>En el área de <strong>Herramientas</strong> se orienta sobre qué recursos digitales son más adecuados para cada acción, metodología o materia.</p><p>Algunos ejemplos tratados en el blog:</p><ul><li>" + a("Infografías interactivas con Genially", W + "/2020/09/13/infografias-interactivas-un-recurso-genially/") + "</li><li>" + a("El blog como herramienta educativa", W + "/2020/09/13/blog-como-herramienta-educativa/") + "</li><li>" + a("Competencias digitales básicas", W + "/2021/03/28/competencias-digitales-basicas/") + "</li></ul>",
      chips: ["Genially", "Blog", "Servicios"] },

    { id: "servicios",
      claves: ["servicios^4", "servicio^4", "asesoramiento^4", "asesoria^4", "consultoria^3", "diseno de cursos^5", "disenar un curso^5", "crear un curso^4", "accion formativa^3", "acciones formativas^3", "plataforma^3", "moodle^4", "disenar^3", "diseno^3", "diseneis^3", "disenen^3", "disenamos^3", "lms^3", "contratar^3", "empresa^2", "academia^2", "contenidos^2"],
      respuesta: "<p>TicsEducación ofrece <strong>servicios de asesoramiento y diseño de cursos y acciones formativas</strong>, adaptados a la plataforma y a las exigencias de cada actividad.</p><p>Se trabaja con formatos estándar como <strong>SCORM</strong> y herramientas de autor como <strong>eXeLearning</strong>.</p><p>Para pedir presupuesto escribe a " + MAIL + ".</p>",
      chips: ["¿Qué es SCORM?", "¿Qué es eXeLearning?", "Contacto"] },

    { id: "scorm",
      claves: ["scorm^5", "paquete scorm^5", "estandar^2", "empaquetar^3"],
      respuesta: "<p><strong>SCORM</strong> (<em>Sharable Content Object Reference Model</em>) es un <strong>estándar de e-learning</strong>: empaqueta un curso en un archivo .zip que cualquier plataforma compatible (Moodle, por ejemplo) puede importar.</p><p>Ventaja clave: la plataforma registra el progreso, el tiempo y las calificaciones del alumnado. TicsEducación diseña contenidos en este formato.</p>",
      chips: ["¿Qué es eXeLearning?", "Servicios", "Contacto"] },

    { id: "exelearning",
      claves: ["exelearning^5", "exe learning^5", "exe^3", "excelearning^5", "herramienta de autor^4"],
      respuesta: "<p><strong>eXeLearning</strong> es una <strong>herramienta de autor libre y gratuita</strong> para crear contenidos educativos web (textos, actividades, cuestionarios…) sin saber programar.</p><p>Permite exportar el resultado como página web o como paquete <strong>SCORM</strong> para subirlo a una plataforma de formación.</p>",
      chips: ["¿Qué es SCORM?", "Servicios"] },

    { id: "genially",
      claves: ["genially^5", "genialy^5", "infografia^4", "infografias^4", "interactiva^3", "interactivas^3", "presentacion interactiva^4"],
      respuesta: "<p>En el blog hay una entrada dedicada a las <strong>infografías interactivas con Genially</strong>, una herramienta muy versátil para docentes: " + a("Infografías interactivas: un recurso genial(ly)", W + "/2020/09/13/infografias-interactivas-un-recurso-genially/") + ".</p>",
      chips: ["Herramientas", "Blog"] },

    { id: "competencias",
      claves: ["competencias digitales^5", "competencia digital^5", "competencias^3", "alfabetizacion digital^4", "basicas^1"],
      respuesta: "<p>La entrada " + a("Competencias Digitales Básicas", W + "/2021/03/28/competencias-digitales-basicas/") + " (marzo de 2021) enlaza una presentación interactiva sobre este tema.</p>",
      chips: ["Herramientas", "Blog"] },

    { id: "rural",
      claves: ["rural^5", "pueblo^3", "despoblacion^5", "escuela rural^5", "escuelas rurales^5", "espana vaciada^4"],
      respuesta: "<p>La entrada " + a("TIC y educación rural", W + "/2020/09/13/tics-y-educacion-rural/") + " analiza cómo la despoblación provoca el cierre de escuelas rurales y qué papel pueden jugar las tecnologías.</p>",
      chips: ["Blog", "Formación"] },

    { id: "blog_herramienta",
      claves: ["blog educativo^5", "blog como herramienta^5", "crear un blog^4", "ventajas del blog^5", "blog en clase^5"],
      respuesta: "<p>Según la entrada " + a("Blog como herramienta educativa", W + "/2020/09/13/blog-como-herramienta-educativa/") + ", un blog aporta:</p><ul><li>Un <strong>entorno de trabajo</strong> con recursos y enlaces permanentes.</li><li><strong>Organización</strong> cronológica del contenido.</li><li><strong>Seguimiento</strong> del progreso del alumnado.</li><li><strong>Debate</strong> y participación.</li><li><strong>Autoevaluación</strong> e investigación.</li></ul>",
      chips: ["Blog", "Herramientas"] },

    { id: "blog",
      claves: ["blog^4", "articulos^3", "articulo^3", "entradas^3", "entrada^2", "publicaciones^3", "noticias^2", "leer^2", "ultimas^2", "novedades^2"],
      respuesta: "<p>Entradas publicadas en el " + a("blog", W + "/blog/") + ":</p><ul><li>" + a("Competencias Digitales Básicas", W + "/2021/03/28/competencias-digitales-basicas/") + "</li><li>" + a("Infografías interactivas con Genially", W + "/2020/09/13/infografias-interactivas-un-recurso-genially/") + "</li><li>" + a("La docencia y la teleformación", W + "/2020/09/13/la-docencia-en-funcion-de-los-principios-de-la-teleformacion/") + "</li><li>" + a("TIC y educación rural", W + "/2020/09/13/tics-y-educacion-rural/") + "</li><li>" + a("Blog como herramienta educativa", W + "/2020/09/13/blog-como-herramienta-educativa/") + "</li></ul>",
      chips: ["Suscribirme", "Herramientas"] },

    { id: "suscripcion",
      claves: ["suscribirme^5", "suscribir^4", "suscripcion^5", "newsletter^4", "boletin^4", "avisos^3", "seguir el blog^5", "notificaciones^3"],
      respuesta: "<p>Puedes recibir las nuevas entradas en tu correo: entra en el " + a("blog", W + "/blog/") + ", busca el apartado <strong>«Sigue mi blog»</strong>, escribe tu correo y pulsa <strong>«Registrarse»</strong>.</p>",
      chips: ["Blog", "Formación"] },

    { id: "contacto",
      claves: ["contacto^4", "contactar^4", "contacta^3", "email^4", "e-mail^4", "correo electronico^4", "mail^3", "telefono^3", "llamar^3", "hablar con alguien^5", "persona^2", "escribir^2", "direccion^2", "donde estais^3", "informacion^1", "presupuesto^3", "duda^1"],
      respuesta: function () {
        return "<p>Puedes escribir directamente a <strong>Víctor de la Fuente</strong>:</p><p>✉️ " + MAIL + "</p><p>Cuéntale qué necesitas (formación, asesoramiento o diseño de un curso) y te responderá personalmente.</p>";
      },
      chips: ["Formación", "Servicios"] }
  ];

  /* Sinónimos: convierten palabras equivalentes en una sola forma */
  var SINONIMOS = {
    "precio": ["coste", "costo", "importe", "pasta", "dinero", "euros"],
    "curso": ["cursillo", "clase", "clases", "formaciones", "capacitacion"],
    "contacto": ["contactaros", "contactarte", "escribiros", "llamaros"],
    "herramientas": ["utilidades", "software"],
    "hola": ["holi", "ola", "buenas!", "hello"]
  };

  /* Palabras vacías que no aportan significado */
  var VACIAS = ("a al algo algun alguna como con cual cuales de del el ella ellos en es esa ese eso esta este esto estoy hay la las le les lo los me mi mis muy no nos o os para pero por puede puedo que se si sin sobre su sus te tengo ti tu tus un una uno unos unas y ya yo vosotros vuestro vuestra quiero querria queria saber podrias podeis puedes dime decir me gustaria").split(" ");

  /* =============================================================
     C. MOTOR DE PROCESAMIENTO DEL LENGUAJE (PLN ligero)
     1) Normalizar → 2) Tokenizar → 3) Raíz (stem) → 4) Comparar
     ============================================================= */
  function normalizar(t) {
    return String(t).toLowerCase()
      .normalize("NFD").replace(/[̀-ͯ]/g, "")   // quita tildes
      .replace(/[^a-z0-9ñ\s-]/g, " ")                      // quita signos
      .replace(/\s+/g, " ").trim();
  }
  function raiz(p) {                                       // stemming muy simple
    if (p.length > 6 && /mente$/.test(p)) p = p.slice(0, -5);
    if (p.length > 5 && /(ciones|siones)$/.test(p)) return p.slice(0, -5);
    if (p.length > 4 && /(cion|sion)$/.test(p)) return p.slice(0, -4);
    if (p.length > 4 && /es$/.test(p)) return p.slice(0, -2);
    if (p.length > 3 && /s$/.test(p)) return p.slice(0, -1);
    return p;
  }
  function levenshtein(x, y) {                              // distancia de edición
    if (x === y) return 0;
    var m = x.length, n = y.length, prev = [], cur = [], i, j;
    for (j = 0; j <= n; j++) prev[j] = j;
    for (i = 1; i <= m; i++) {
      cur = [i];
      for (j = 1; j <= n; j++) {
        cur[j] = Math.min(prev[j] + 1, cur[j - 1] + 1, prev[j - 1] + (x[i - 1] === y[j - 1] ? 0 : 1));
      }
      prev = cur;
    }
    return prev[n];
  }
  var MAPA_SIN = {};
  Object.keys(SINONIMOS).forEach(function (k) {
    SINONIMOS[k].forEach(function (s) { MAPA_SIN[normalizar(s)] = k; });
  });
  function tokens(texto) {
    return normalizar(texto).split(" ").filter(function (w) { return w && VACIAS.indexOf(w) === -1; })
      .map(function (w) { return MAPA_SIN[w] || w; });
  }
  function coincide(palabra, clave) {                     // ¿la palabra del usuario equivale a la clave?
    if (palabra === clave) return 1;
    var rp = raiz(palabra), rc = raiz(clave);
    if (rp === rc) return 1;
    var tol = rc.length >= 8 ? 2 : (rc.length >= 5 ? 1 : 0);  // tolerancia a faltas
    if (tol && Math.abs(rp.length - rc.length) <= tol && levenshtein(rp, rc) <= tol) return 0.8;
    return 0;
  }

  /* Pre-procesa las claves de cada intención una sola vez */
  INTENCIONES.forEach(function (it) {
    it._claves = it.claves.map(function (c) {
      var partes = c.split("^");
      var frase = normalizar(partes[0]);
      return { frase: frase, palabras: frase.split(" "), peso: partes[1] ? parseFloat(partes[1]) : 1 };
    });
  });

  function analizar(texto) {
    var norm = " " + normalizar(texto) + " ";
    var toks = tokens(texto);
    var ranking = INTENCIONES.map(function (it) {
      var puntos = 0, usadas = {};                         // cada raíz puntúa una sola vez
      it._claves.forEach(function (c) {
        if (c.palabras.length > 1) {                       // frase de varias palabras
          if (norm.indexOf(" " + c.frase + " ") !== -1) puntos += c.peso;
        } else {                                           // palabra suelta
          var r = raiz(c.frase);
          if (usadas[r]) return;
          var mejor = 0;
          for (var i = 0; i < toks.length; i++) mejor = Math.max(mejor, coincide(toks[i], c.frase));
          if (mejor) usadas[r] = true;
          puntos += mejor * c.peso;
        }
      });
      return { id: it.id, intencion: it, puntos: Math.round(puntos * 100) / 100 };
    }).sort(function (x, y) { return y.puntos - x.puntos; });
    return ranking;
  }

  /* =============================================================
     D. GESTOR DE DIÁLOGO (decide qué contestar)
     ============================================================= */
  var estado = { fallos: 0, ultimo: null };

  function responder(texto) {
    var ranking = analizar(texto);
    var mejor = ranking[0];
    if (mejor && mejor.puntos >= CONFIG.umbral) {
      estado.fallos = 0;
      estado.ultimo = mejor.id;
      var r = mejor.intencion.respuesta;
      return { id: mejor.id, puntos: mejor.puntos, html: typeof r === "function" ? r() : r, chips: mejor.intencion.chips };
    }
    estado.fallos++;
    if (estado.fallos >= CONFIG.maxFallos) {
      estado.fallos = 0;
      return { id: "fallback_contacto", puntos: mejor ? mejor.puntos : 0,
        html: "<p>Creo que tu consulta necesita una respuesta personal. 🙂</p><p>Escríbela a " + MAIL + " y te contestarán directamente.</p>",
        chips: ["Formación", "Servicios", "Blog"] };
    }
    return { id: "fallback", puntos: mejor ? mejor.puntos : 0,
      html: "<p>No estoy seguro de haberte entendido. ¿Puedes decírmelo con otras palabras?</p><p>También puedes elegir un tema:</p>",
      chips: ["Formación", "Servicios", "Herramientas", "Blog", "Contacto"] };
  }

  /* =============================================================
     E. INTERFAZ (pinta mensajes, botones y eventos)
     ============================================================= */
  var root = document.getElementById("tico-root");
  if (!root) return;
  var $ = function (id) { return document.getElementById(id); };
  var panel = $("tico-panel"), launcher = $("tico-launcher"), log = $("tico-log"),
      chipsBox = $("tico-chips"), form = $("tico-form"), input = $("tico-input");
  var ocupado = false;

  if (CONFIG.modoPagina) root.classList.add("tico-fullpage");

  function bajar() { log.scrollTop = log.scrollHeight; }

  function pintarUsuario(texto) {
    var d = document.createElement("div");
    d.className = "tico-msg tico-user";
    d.textContent = texto;            // textContent: nunca interpreta HTML del usuario (seguridad XSS)
    log.appendChild(d); bajar();
  }
  function pintarBot(html) {
    var d = document.createElement("div");
    d.className = "tico-msg tico-bot";
    d.innerHTML = html;               // HTML de confianza: procede de la base de conocimiento
    log.appendChild(d);
    // si la respuesta es larga, se muestra desde su primera línea
    if (d.offsetHeight > log.clientHeight - 40) log.scrollTop = d.offsetTop - 12; else bajar();
  }
  function pintarChips(lista) {
    chipsBox.innerHTML = "";
    (lista || []).forEach(function (txt) {
      var b = document.createElement("button");
      b.type = "button"; b.className = "tico-chip"; b.textContent = txt;
      b.addEventListener("click", function () { enviar(txt); });
      chipsBox.appendChild(b);
    });
  }
  function escribiendo(on) {
    var t = $("tico-typing");
    if (on && !t) {
      t = document.createElement("div");
      t.id = "tico-typing"; t.className = "tico-msg tico-bot tico-typing";
      t.setAttribute("aria-label", "TICo está escribiendo");
      t.innerHTML = "<span></span><span></span><span></span>";
      log.appendChild(t); bajar();
    } else if (!on && t) { t.remove(); }
  }

  function enviar(texto) {
    texto = String(texto || "").trim();
    if (!texto || ocupado) return;
    ocupado = true;
    pintarUsuario(texto);
    pintarChips([]);
    input.value = "";
    var res = responder(texto);
    escribiendo(true);
    var espera = Math.min(1200, 350 + res.html.length * 1.2);   // simula tiempo de escritura
    setTimeout(function () {
      escribiendo(false);
      pintarBot(res.html);
      pintarChips(res.chips);
      ocupado = false;
      if (window.matchMedia("(pointer:fine)").matches) input.focus();
    }, espera);
  }

  function bienvenida() {
    log.innerHTML = "";
    estado.fallos = 0; estado.ultimo = null;
    pintarBot("<p>¡Hola! 👋 Soy <strong>TICo</strong>, el asistente virtual de <strong>TicsEducación</strong>.</p><p>Te ayudo con información sobre formación, servicios, herramientas digitales y el blog. ¿Qué necesitas?</p>");
    pintarChips(["Formación", "Servicios", "Herramientas", "Blog", "¿Quién está detrás?", "Contacto"]);
  }

  function abrir() {
    panel.hidden = false;
    launcher.setAttribute("aria-expanded", "true");
    var badge = launcher.querySelector(".tico-badge"); if (badge) badge.remove();
    if (!log.children.length) bienvenida();
    setTimeout(function () { input.focus(); }, 50);
  }
  function cerrar() {
    if (CONFIG.modoPagina) return;
    panel.hidden = true;
    launcher.setAttribute("aria-expanded", "false");
    launcher.focus();
  }

  launcher.addEventListener("click", function () { panel.hidden ? abrir() : cerrar(); });
  $("tico-close").addEventListener("click", cerrar);
  $("tico-reset").addEventListener("click", bienvenida);
  form.addEventListener("submit", function (e) { e.preventDefault(); enviar(input.value); });
  document.addEventListener("keydown", function (e) { if (e.key === "Escape" && !panel.hidden) cerrar(); });
  if (CONFIG.modoPagina) $("tico-close").hidden = true;
  if (CONFIG.abrirAlCargar) abrir();

  /* API mínima para pruebas desde la consola del navegador:
     TICo.analizar("¿cuánto cuesta el curso?")  → ranking de intenciones */
  window.TICo = { analizar: analizar, responder: responder, abrir: abrir, cerrar: cerrar, version: "1.0" };
})();
</script>
<!-- ===================== FIN DEL CHATBOT TICo ===================== -->

</body>
</html>
