<template>
  <div class="site">
    <!-- Header -->
    <header class="nav">
      <div class="container nav__inner">
        <a class="brand" href="#">MARK-TECS</a>
        <nav class="menu">
          <a href="#servicios">Servicios</a>
          <a href="#caracteristicas">Características</a>
          <a href="#contacto">Contacto</a>
        </nav>
      </div>
    </header>

    <!-- Hero -->
    <section class="hero">
      <div class="container hero__grid">
        <div class="hero__copy">
          <h1>Campañas, <span class="grad">toques</span> y automatizaciones</h1>
          <p>Activamos audiencias por WhatsApp, SMS, Email y Ads con flujos automatizados y medición end-to-end.</p>
          <div class="cta">
            <a href="#contacto" class="btn btn--primary">Habla con nosotros</a>
            <a href="#servicios" class="btn btn--ghost">Ver servicios</a>
          </div>
          <p class="footnote">* Sitio informativo para verificación de negocios de Meta.</p>
        </div>
        <div class="hero__card">
          <div class="feature">
            <h4>WhatsApp</h4>
            <p>Conversaciones, catálogos y flujos.</p>
          </div>
          <div class="feature">
            <h4>SMS</h4>
            <p>Toques transaccionales y masivos.</p>
          </div>
          <div class="feature">
            <h4>Email</h4>
            <p>Campañas y newsletters medibles.</p>
          </div>
          <div class="feature">
            <h4>Ads</h4>
            <p>Audiencias y remarketing.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Servicios -->
    <section id="servicios" class="section">
      <div class="container cards">
        <div class="card">
          <h3>Campañas multicanal</h3>
          <p>Orquestación coordinada en varios canales con segmentación y calendario.</p>
        </div>
        <div class="card">
          <h3>Toques y notificaciones</h3>
          <p>Recordatorios y mensajes transaccionales con plantillas aprobadas.</p>
        </div>
        <div class="card">
          <h3>Automatizaciones</h3>
          <p>Flujos por eventos (alta, compra, abandono) con reglas y A/B.</p>
        </div>
      </div>
    </section>

    <!-- Características -->
    <section id="caracteristicas" class="section alt">
      <div class="container">
        <h2>Lo esencial</h2>
        <ul class="list">
          <li>Consentimiento y opt-out en todos los canales.</li>
          <li>Cumplimiento de políticas de Meta y WhatsApp Business.</li>
          <li>Medición de entregabilidad y conversiones.</li>
          <li>Integración con CRMs y catálogos.</li>
        </ul>
        <div class="links">
          <a href="#politicas">Política de WhatsApp</a>
          <span>·</span>
          <a href="#privacidad">Aviso de Privacidad</a>
          <span>·</span>
          <a href="#terminos">Términos</a>
        </div>
      </div>
    </section>

    <!-- Contacto + Form API -->
    <section id="contacto" class="section">
      <div class="container contact">
        <div class="contact__copy">
          <h2>Contacto</h2>
          <p>Escríbenos a <a href="mailto:hola@mark-tecs.com">hola@mark-tecs.com</a> o por WhatsApp al
            <a href="https://wa.me/5215555555555" target="_blank" rel="noopener">+52 1 55 5555 5555</a>.
          </p>
          <p class="muted">Al contactarnos aceptas nuestro Aviso de Privacidad.</p>
        </div>

        <form class="form" @submit.prevent="sendEmail">
          <div class="form__row">
            <div class="field">
              <label for="name">Nombre</label>
              <input id="name" v-model.trim="form.name" type="text" placeholder="Tu nombre" />
            </div>
            <div class="field">
              <label for="email">Email</label>
              <input id="email" v-model.trim="form.email" type="email" placeholder="tucorreo@dominio.com" required />
            </div>
          </div>
          <div class="field">
            <label for="subject">Asunto</label>
            <input id="subject" v-model.trim="form.subject" type="text" placeholder="Quiero una demo" required />
          </div>
          <div class="field">
            <label for="message">Mensaje</label>
            <textarea id="message" v-model.trim="form.message" rows="5" placeholder="Cuéntanos qué necesitas" required></textarea>
          </div>

          <div class="form__footer">
            <div class="tiny muted">
              Se enviará vía API a {{ endpoint }}  
              <br />
              <code>{ "to": "{{ defaults.to }}", "from": "{{ defaults.from }}" }</code>
            </div>
            <button class="btn btn--primary" :disabled="loading">
              <span v-if="!loading">Enviar mensaje</span>
              <span v-else class="spinner" aria-hidden="true"></span>
            </button>
          </div>

          <p v-if="status === 'ok'" class="alert alert--ok">¡Listo! Recibimos tu mensaje.</p>
          <p v-if="status === 'error'" class="alert alert--error">Ocurrió un problema al enviar. Intenta de nuevo.</p>
        </form>
      </div>
    </section>

    <!-- Legales "ancla" (contenido mínimo para verificación) -->
    <section id="politicas" class="section alt">
      <div class="container legal">
        <h3>Política de WhatsApp Business</h3>
        <ul>
          <li>Solo contactamos a personas con consentimiento previo.</li>
          <li>Usamos plantillas aprobadas para notificaciones proactivas.</li>
          <li>Escribe <b>ALTO</b> para dejar de recibir mensajes.</li>
        </ul>
      </div>
    </section>

    <section id="privacidad" class="section">
      <div class="container legal">
        <h3>Aviso de Privacidad</h3>
        <p>Tratamos datos de contacto y metadatos de interacción para brindar el servicio. Para ejercer derechos ARCO,
          escríbenos a <a href="mailto:privacidad@mark-tecs.com">privacidad@mark-tecs.com</a>.</p>
      </div>
    </section>

    <section id="terminos" class="section alt">
      <div class="container legal">
        <h3>Términos y Condiciones</h3>
        <p>El uso de los servicios implica aceptación de políticas por canal (Meta/WhatsApp/SMS/Email) y de la legislación aplicable.</p>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container footer__inner">
        <p>© {{ year }} MARK-TECS. Todos los derechos reservados.</p>
        <p class="tiny">Stack: Vue + Python (API) · Sitio estático para verificación de Meta</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      year: new Date().getFullYear(),
      endpoint: "https://kz-media-backend-python-production.up.railway.app/email",
      defaults: {
        to: "mark-tec-v1@outlook.com",
        from: "onboarding@resend.dev",
      },
      form: {
        name: "",
        email: "",
        subject: "",
        message: "",
      },
      loading: false,
      status: null, // 'ok' | 'error' | null
    };
  },
  methods: {
    async sendEmail() {
      this.status = null;

      // Validación simple
      if (!this.form.email || !this.form.subject || !this.form.message) {
        this.status = "error";
        return;
      }

      // Armado del payload solicitado
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
/* ====== Design tokens ====== */
:root {
  --bg: #0b0c10;
  --surface: #0f1117;
  --surface-2: #151824;
  --text: #e9ecf1;
  --muted: #a7b0be;
  --primary: #6d7cff;
  --primary-2: #5b6af0;
  --border: #252a36;
  --ok: #2aa06a;
  --error: #e45454;
}

* { box-sizing: border-box; }
html, body, .site { height: 100%; }
body { margin: 0; background: var(--bg); color: var(--text); font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Inter, "Helvetica Neue", Arial, "Noto Sans", "Apple Color Emoji", "Segoe UI Emoji"; }

/* Layout helpers */
.container { max-width: 1100px; margin: 0 auto; padding: 0 20px; }
.section { padding: 64px 0; }
.section.alt { background: var(--surface); }
.grad { background: linear-gradient(135deg, var(--primary), #9c7cff 60%, #c77dff); -webkit-background-clip: text; background-clip: text; color: transparent; }

/* Header */
.nav { position: sticky; top: 0; z-index: 10; backdrop-filter: saturate(120%) blur(8px); background: rgba(11,12,16,0.6); border-bottom: 1px solid var(--border); }
.nav__inner { display: flex; align-items: center; justify-content: space-between; padding: 14px 0; }
.brand { font-weight: 900; letter-spacing: .5px; color: var(--text); text-decoration: none; }
.menu a { color: var(--muted); text-decoration: none; margin-left: 18px; font-size: 14px; }
.menu a:hover { color: var(--text); }

/* Hero */
.hero { padding: 72px 0 48px; }
.hero__grid { display: grid; grid-template-columns: 1.1fr 0.9fr; gap: 36px; }
.hero__copy h1 { font-size: clamp(28px, 5vw, 48px); line-height: 1.05; margin: 0 0 14px; }
.hero__copy p { color: var(--muted); font-size: 18px; }
.cta { display: flex; gap: 12px; margin-top: 18px; }
.footnote { color: var(--muted); font-size: 12px; margin-top: 10px; }

.hero__card { background: linear-gradient(180deg, var(--surface), var(--surface-2)); border: 1px solid var(--border); border-radius: 18px; padding: 18px; display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.feature { border: 1px solid var(--border); border-radius: 14px; padding: 16px; background: #0f121b; }
.feature h4 { margin: 0 0 6px; font-size: 16px; }

/* Cards */
.cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
.card { background: var(--surface-2); border: 1px solid var(--border); border-radius: 16px; padding: 18px; }
.card h3 { margin: 0 0 6px; }
.card p { color: var(--muted); }

/* List + links */
.list { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; margin: 16px 0 8px; padding: 0; list-style: none; }
.list li { background: var(--surface-2); border: 1px solid var(--border); border-radius: 12px; padding: 12px 14px; color: var(--text); }
.links { display: flex; align-items: center; gap: 8px; color: var(--muted); }
.links a { color: var(--primary); text-decoration: none; }
.links a:hover { text-decoration: underline; }

/* Contact + form */
.contact { display: grid; grid-template-columns: 0.9fr 1.1fr; gap: 24px; align-items: start; }
.contact__copy p { color: var(--muted); }
.contact__copy a { color: var(--primary); text-decoration: none; }
.contact__copy a:hover { text-decoration: underline; }
.muted { color: var(--muted); }
.tiny { font-size: 12px; }

.form { background: var(--surface-2); border: 1px solid var(--border); border-radius: 16px; padding: 18px; }
.form__row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.field { display: grid; gap: 8px; margin-bottom: 12px; }
label { font-size: 13px; color: var(--muted); }
input, textarea {
  width: 100%; padding: 12px 12px; border-radius: 12px;
  border: 1px solid var(--border); outline: none; background: #0e111a; color: var(--text);
}
input:focus, textarea:focus { border-color: var(--primary); box-shadow: 0 0 0 3px rgba(109,124,255,0.15); }

.form__footer { display: flex; align-items: center; justify-content: space-between; gap: 12px; }
.alert { margin-top: 12px; padding: 10px 12px; border-radius: 10px; border: 1px solid; }
.alert--ok { color: #c7ffea; background: rgba(42,160,106,.12); border-color: var(--ok); }
.alert--error { color: #ffd0d0; background: rgba(228,84,84,.12); border-color: var(--error); }

/* Buttons */
.btn {
  appearance: none; border: 1px solid transparent; border-radius: 14px; padding: 12px 16px;
  text-decoration: none; color: white; display: inline-flex; gap: 8px; align-items: center; justify-content: center;
}
.btn--primary { background: var(--primary); }
.btn--primary:hover { background: var(--primary-2); }
.btn--ghost { border-color: var(--border); color: var(--text); background: transparent; }
.btn[disabled] { opacity: .6; cursor: not-allowed; }

.spinner {
  width: 16px; height: 16px; border-radius: 50%;
  border: 2px solid rgba(255,255,255,.35); border-top-color: #fff; animation: spin 0.9s linear infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }

/* Legal blocks */
.legal { background: var(--surface-2); border: 1px solid var(--border); border-radius: 16px; padding: 18px; }
.legal h3 { margin-top: 0; }

/* Footer */
.footer { border-top: 1px solid var(--border); background: rgba(11,12,16,0.6); }
.footer__inner { display: flex; flex-direction: column; gap: 6px; padding: 18px 0; color: var(--muted); }

/* Responsive */
@media (max-width: 980px) {
  .hero__grid { grid-template-columns: 1fr; }
  .cards { grid-template-columns: 1fr; }
  .list { grid-template-columns: 1fr; }
  .contact { grid-template-columns: 1fr; }
  .form__row { grid-template-columns: 1fr; }
}
</style>
