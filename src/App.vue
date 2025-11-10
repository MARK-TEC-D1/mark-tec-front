<template>
  <div class="site">
    <!-- Header -->
    <header class="nav">
      <div class="container nav__inner">
        <a class="brand" href="#">
          <span class="brand__logo">M</span>
          <span class="brand__text">MARK-TECS</span>
        </a>

        <button class="hamburger" :aria-expanded="menuOpen" @click="menuOpen = !menuOpen">
          <span></span><span></span><span></span>
        </button>

        <nav class="menu" :class="{ 'menu--open': menuOpen }" @click.self="menuOpen=false">
          <a href="#servicios" @click="menuOpen=false">Servicios</a>
          <a href="#caracteristicas" @click="menuOpen=false">Características</a>
          <a href="#contacto" class="btn btn--sm btn--primary" @click="menuOpen=false">Contacto</a>
        </nav>
      </div>
    </header>

    <!-- Hero con imagen -->
    <section class="hero hero--img">
      <div class="hero__overlay"></div>
      <img
        class="hero__bg"
        src="https://images.unsplash.com/photo-1519389950473-47ba0277781c?q=80&w=1600&auto=format&fit=crop"
        alt="Panel de analytics y campañas"
        loading="eager"
      />
      <div class="container hero__grid">
        <div class="hero__copy">
          <h1>
            Campañas y <span class="grad">automatizaciones</span>
            <span class="break">multicanal</span>
          </h1>
          <p>WhatsApp, SMS, Email y Ads con flujos automáticos y medición end-to-end.</p>
          <div class="actions">
            <a :href="waLink" target="_blank" rel="noopener" class="btn btn--primary">Escríbeme por WhatsApp</a>
            <a href="#servicios" class="btn btn--ghost">Ver servicios</a>
          </div>
          <p class="meta">* Sitio informativo para verificación de negocios de Meta.</p>
        </div>

        <div class="hero__panel">
          <div class="kpi">
            <div class="kpi__val">98.6%</div>
            <div class="kpi__lbl">Entregabilidad</div>
          </div>
          <div class="kpi">
            <div class="kpi__val">x3.1</div>
            <div class="kpi__lbl">ROAS campañas</div>
          </div>
          <div class="kpi">
            <div class="kpi__val">~1.2s</div>
            <div class="kpi__lbl">LAT toques</div>
          </div>
          <div class="chips">
            <span class="chip">WhatsApp</span>
            <span class="chip">SMS</span>
            <span class="chip">Email</span>
            <span class="chip">Ads</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Servicios con imágenes -->
    <section id="servicios" class="section">
      <div class="container">
        <h2 class="sec__title">Lo que hacemos</h2>
        <div class="grid cards">
          <article class="card card--media">
            <img src="https://images.unsplash.com/photo-1556157382-97eda2d62296?q=80&w=1200&auto=format&fit=crop" alt="Campañas multicanal" />
            <div class="card__body">
              <h3>Campañas multicanal</h3>
              <p>Orquestación en varios canales con segmentación dinámica y calendarización.</p>
            </div>
          </article>

          <article class="card card--media">
            <img src="https://images.unsplash.com/photo-1551281044-8d8d4e86b513?q=80&w=1200&auto=format&fit=crop" alt="Toques y notificaciones" />
            <div class="card__body">
              <h3>Toques y notificaciones</h3>
              <p>Mensajes transaccionales y recordatorios con plantillas aprobadas.</p>
            </div>
          </article>

          <article class="card card--media">
            <img src="https://images.unsplash.com/photo-1515879218367-8466d910aaa4?q=80&w=1200&auto=format&fit=crop" alt="Automatizaciones" />
            <div class="card__body">
              <h3>Automatizaciones</h3>
              <p>Flujos por eventos (alta, compra, abandono) y pruebas A/B.</p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Características -->
    <section id="caracteristicas" class="section section--alt">
      <div class="container">
        <h2 class="sec__title">Características clave</h2>
        <ul class="grid features">
          <li class="feature">Consentimiento y opt-out en todos los canales.</li>
          <li class="feature">Cumplimiento de políticas de Meta y WhatsApp Business.</li>
          <li class="feature">Medición de entregabilidad y conversiones.</li>
          <li class="feature">Integración con CRMs y catálogos.</li>
        </ul>
      </div>
    </section>

    <!-- Contacto + Form -->
    <section id="contacto" class="section">
      <div class="container contact__grid">
        <div class="contact__copy">
          <h2 class="sec__title">Contacto</h2>

          <a :href="waLink" target="_blank" rel="noopener" class="wa-cta">
            <img src="https://static.whatsapp.net/rsrc.php/ym/r/36B424nhiZf.svg" alt="WhatsApp" />
            <div>
              <strong>Escríbeme a WhatsApp</strong>
              <span class="legend">Respuesta breve. Click para abrir el chat.</span>
              <span class="number">{{ phoneDisplay }}</span>
            </div>
          </a>

          <div class="legal-mini">
            <details>
              <summary>Política de WhatsApp Business</summary>
              <ul>
                <li>Solo contactamos con consentimiento previo.</li>
                <li>Plantillas aprobadas para notificaciones proactivas.</li>
                <li>Escribe <b>ALTO</b> para dejar de recibir mensajes.</li>
              </ul>
            </details>
            <details>
              <summary>Aviso de Privacidad</summary>
              <p>Tratamos datos de contacto y metadatos de interacción para brindar el servicio.</p>
            </details>
          </div>
        </div>

        <!-- Form que envía a tu API -->
        <form class="form" @submit.prevent="sendEmail" novalidate>
          <div class="row">
            <label class="field">
              <span>Nombre</span>
              <input v-model.trim="form.name" type="text" placeholder="Tu nombre" />
            </label>
            <label class="field">
              <span>Email*</span>
              <input v-model.trim="form.email" type="email" required placeholder="tucorreo@dominio.com" />
            </label>
          </div>

          <label class="field">
            <span>Asunto*</span>
            <input v-model.trim="form.subject" type="text" required placeholder="Quiero una demo" />
          </label>

          <label class="field">
            <span>Mensaje*</span>
            <textarea v-model.trim="form.message" rows="5" required placeholder="Cuéntanos qué necesitas"></textarea>
          </label>

          <div class="form__footer">
            <button class="btn btn--primary" :disabled="loading">
              <span v-if="!loading">Enviar</span>
              <span v-else class="spinner" aria-hidden="true"></span>
            </button>
          </div>

          <p v-if="status === 'ok'" class="alert alert--ok">¡Gracias! Recibimos tu mensaje.</p>
          <p v-if="status === 'error'" class="alert alert--error">No pudimos enviar. Intenta de nuevo.</p>
        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container footer__inner">
        <p>© {{ year }} MARK-TECS</p>
        <p class="tiny muted">Stack: Vue + Python (API) · Sitio estático para verificación</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    const phone = "+527713034047";
    const text = encodeURIComponent("Hola, me interesa MARK-TECS. ¿Podemos hablar?");
    return {
      menuOpen: false,
      year: new Date().getFullYear(),
      endpoint: "https://kz-media-backend-python-production.up.railway.app/email",
      defaults: { to: "mark-tec-v1@outlook.com", from: "onboarding@resend.dev" },
      form: { name: "", email: "", subject: "", message: "" },
      loading: false,
      status: null,
      phoneRaw: phone,
      waLink: `https://wa.me/${phone.replace(/[^0-9]/g,"")}?text=${text}`,
    };
  },
  computed: {
    phoneDisplay() {
      return this.phoneRaw.replace(/^\+52/, "+52 ").replace(/(\d{3})(\d{3})(\d{4})$/, "$1 $2 $3");
    },
  },
  methods: {
    async sendEmail() {
      this.status = null;
      if (!this.form.email || !this.form.subject || !this.form.message) {
        this.status = "error";
        return;
      }
      const payload = {
        to: this.defaults.to,
        from: this.defaults.from,
        subject: `[Landing] ${this.form.subject} — ${this.form.name || "Sin nombre"} <${this.form.email}>`,
        text: this.form.message,
      };
      this.loading = true;
      try {
        const res = await fetch(this.endpoint, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(payload),
        });
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        this.status = "ok";
        this.form = { name: "", email: "", subject: "", message: "" };
      } catch (e) {
        console.error(e);
        this.status = "error";
      } finally {
        this.loading = false;
      }
    },
  },
};
</script>

<style scoped>
/* ==== Tokens ==== */
:root {
  --bg: hsl(225 15% 10%);
  --bg-2: hsl(225 15% 12%);
  --surface: hsl(225 16% 16%);
  --surface-2: hsl(225 16% 18%);
  --text: hsl(220 20% 95%);
  --muted: hsl(220 10% 70%);
  --primary: hsl(255 88% 70%);
  --primary-2: hsl(255 88% 64%);
  --border: hsl(225 15% 24%);
  --ok: #2aa06a;
  --error: #e45454;
}

* { box-sizing: border-box; }
html, body, .site { height: 100%; }
body {
  margin: 0;
  background: var(--bg);
  color: var(--text);
  font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Inter, Roboto, "Helvetica Neue", Arial;
}

/* Helpers */
.container { max-width: 1120px; margin: 0 auto; padding: 0 20px; }
.tiny { font-size: 12px; }
.muted { color: var(--muted); }

/* Header */
.nav { position: sticky; top: 0; z-index: 20; backdrop-filter: blur(10px);
  background: color-mix(in hsl, var(--bg), black 20%); border-bottom: 1px solid var(--border); }
.nav__inner { display: flex; align-items: center; justify-content: space-between; padding: 14px 0; }
.brand { display: inline-flex; align-items: center; gap: 10px; color: var(--text); text-decoration: none; font-weight: 800; letter-spacing: .3px; }
.brand__logo { width: 28px; height: 28px; display: grid; place-items: center; border-radius: 8px;
  background: linear-gradient(135deg, var(--primary), #b98bff); color: #0d0d12; font-weight: 900; }
.brand__text { opacity: .95; }
.menu { display: flex; align-items: center; gap: 18px; }
.menu a { color: var(--muted); text-decoration: none; font-size: 14px; }
.menu a:hover { color: var(--text); }
.hamburger { display: none; background: transparent; border: 0; cursor: pointer; padding: 6px; margin-left: auto; }
.hamburger span { display: block; width: 22px; height: 2px; margin: 5px 0; background: var(--text); transition: .2s; }

/* Hero */
.hero { position: relative; padding: clamp(56px, 7vw, 96px) 0 72px; overflow: hidden; }
.hero--img { isolation: isolate; }
.hero__bg { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; z-index: -2; transform: scale(1.05); filter: saturate(90%); }
.hero__overlay { position: absolute; inset: 0; z-index: -1;
  background: radial-gradient(1200px 600px at 10% -10%, hsl(255 30% 18% / .5), transparent),
              radial-gradient(1000px 600px at 100% 10%, hsl(200 40% 20% / .45), transparent),
              color-mix(in hsl, var(--bg), black 35%); }
.hero__grid { display: grid; align-items: center; gap: 36px; grid-template-columns: 1.1fr .9fr; }
.hero__copy h1 { font-size: clamp(32px, 6vw, 56px); line-height: 1.05; margin: 0 0 12px; }
.break { display: block; }
.hero__copy p { margin: 0; color: var(--text); opacity: .9; font-size: clamp(16px, 2.2vw, 18px); }
.actions { display: flex; gap: 12px; margin-top: 18px; flex-wrap: wrap; }
.meta { margin-top: 10px; color: var(--muted); font-size: 12px; }
.grad { background: linear-gradient(135deg, var(--primary), #b98bff 60%, #7cf7ff); -webkit-background-clip: text; background-clip: text; color: transparent; }

.hero__panel {
  background: linear-gradient(180deg, color-mix(in hsl, var(--surface), white 4%), var(--surface-2));
  border: 1px solid var(--border); border-radius: 18px; padding: 18px;
  display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px;
  box-shadow: 0 10px 30px hsl(220 40% 2% / .45);
}
.kpi { background: #0f1220; border: 1px solid var(--border); border-radius: 14px; padding: 14px; }
.kpi__val { font-weight: 900; font-size: clamp(20px, 4vw, 28px); }
.kpi__lbl { color: var(--muted); font-size: 12px; margin-top: 2px; }
.chips { grid-column: 1 / -1; display: flex; gap: 8px; flex-wrap: wrap; }
.chip { padding: 8px 12px; border: 1px solid var(--border); border-radius: 999px; background: #0f111a; font-size: 13px; }

/* Sections */
.section { padding: clamp(48px, 6vw, 80px) 0; }
.section--alt { background: color-mix(in hsl, var(--bg-2), black 8%); border-block: 1px solid var(--border); }
.sec__title { font-size: clamp(22px, 3.2vw, 28px); margin: 0 0 18px; letter-spacing: .2px; }

/* Cards con imagen */
.grid { display: grid; gap: 16px; }
.cards { grid-template-columns: repeat(3, 1fr); }
.card { border-radius: 16px; overflow: hidden; border: 1px solid var(--border); background: var(--surface-2); }
.card--media img { width: 100%; height: 160px; object-fit: cover; display: block; }
.card__body { padding: 16px 16px 18px; }
.card h3 { margin: 0 0 6px; }
.card p { color: var(--muted); margin: 0; }

/* Features */
.features { grid-template-columns: repeat(2, 1fr); padding: 0; list-style: none; }
.feature { padding: 14px; border-radius: 12px; border: 1px solid var(--border); background: #0f111a; }

/* Contact */
.contact__grid { display: grid; grid-template-columns: .95fr 1.05fr; gap: 24px; align-items: start; }
.wa-cta {
  display: grid; grid-template-columns: 40px 1fr; gap: 12px; align-items: center;
  text-decoration: none; color: var(--text);
  background: linear-gradient(180deg, var(--surface), var(--surface-2));
  border: 1px solid var(--border); border-radius: 14px; padding: 12px 14px; margin: 6px 0 14px;
}
.wa-cta:hover { outline: 2px solid color-mix(in hsl, var(--primary), white 10%); }
.wa-cta img { width: 40px; height: 40px; filter: drop-shadow(0 2px 6px rgba(0,0,0,.3)); }
.legend { display: block; color: var(--muted); font-size: 13px; }
.number { display: block; font-size: 13px; opacity: .9; margin-top: 2px; }

.legal-mini details { background: #0f111a; border: 1px solid var(--border); border-radius: 12px; padding: 10px 12px; margin-top: 10px; }
.legal-mini summary { cursor: pointer; color: var(--text); }

.form { background: linear-gradient(180deg, var(--surface), var(--surface-2));
  border: 1px solid var(--border); border-radius: 16px; padding: 18px; }
.row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.field { display: grid; gap: 8px; margin-bottom: 12px; }
.field > span { font-size: 13px; color: var(--muted); }
input, textarea { width: 100%; padding: 12px 12px; border-radius: 12px;
  border: 1px solid var(--border); outline: none; background: #0e111a; color: var(--text); }
input:focus, textarea:focus { border-color: var(--primary); box-shadow: 0 0 0 3px hsl(255 88% 70% / .18); }
.form__footer { display: flex; align-items: center; justify-content: space-between; gap: 12px; flex-wrap: wrap; }
.alert { margin-top: 12px; padding: 10px 12px; border-radius: 10px; border: 1px solid; }
.alert--ok { color: #c7ffea; background: rgba(42,160,106,.12); border-color: var(--ok); }
.alert--error { color: #ffd0d0; background: rgba(228,84,84,.12); border-color: var(--error); }

/* Buttons */
.btn { appearance: none; border: 1px solid transparent; border-radius: 14px; padding: 12px 16px;
  text-decoration: none; color: white; display: inline-flex; gap: 8px; align-items: center; justify-content: center; font-weight: 600; }
.btn--sm { padding: 8px 12px; font-size: 14px; }
.btn--primary { background: var(--primary); }
.btn--primary:hover { background: var(--primary-2); }
.btn--ghost { border-color: var(--border); color: var(--text); background: transparent; }
.btn[disabled] { opacity: .6; cursor: not-allowed; }
.spinner { width: 16px; height: 16px; border-radius: 50%; border: 2px solid rgba(255,255,255,.35); border-top-color: #fff; animation: spin .9s linear infinite; }
@keyframes spin { to { transform: rotate(360deg); } }

/* Footer */
.footer { border-top: 1px solid var(--border); background: color-mix(in hsl, var(--bg), black 12%); }
.footer__inner { display: flex; justify-content: space-between; gap: 10px; padding: 18px 0; color: var(--muted); flex-wrap: wrap; }

/* Responsive */
@media (max-width: 980px) {
  .hero__grid { grid-template-columns: 1fr; }
  .cards { grid-template-columns: 1fr; }
  .features { grid-template-columns: 1fr; }
  .contact__grid { grid-template-columns: 1fr; }
  .row { grid-template-columns: 1fr; }
  .menu { display: none; }
  .menu.menu--open {
    display: grid; position: absolute; top: 56px; right: 16px; gap: 10px; padding: 12px;
    background: var(--surface); border: 1px solid var(--border); border-radius: 14px;
  }
  .hamburger { display: inline-block; }
}
</style>
