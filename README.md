<p align="center">
  <img src="assets/logo_grillout.png" alt="Grillout Logo" width="220" />
</p>

<h1 align="center">GRILLOUT 🦗</h1>

<p align="center">
  <strong>Motor de Colas Asíncronas, Mensajería Efímera & Notificaciones Multicanal ($0)</strong><br>
  <em>Parte del Ecosistema Terra — Infraestructura Fantasma Serverless e Inmutable sobre GitHub Engine</em>
</p>

<p align="center">
  <a href="https://github.com/amglogicalis/Terra"><strong>Ecosistema Terra</strong></a> •
  <a href="https://amglogicalis.github.io/grillout-repo-public/"><strong>Gryllus Studio Console</strong></a> •
  <a href="#-características-principales"><strong>Características</strong></a> •
  <a href="#-instalación-y-uso"><strong>Instalación</strong></a>
</p>

---

## 🦗 Visión y Filosofía

**GRILLOUT** es el 12º Titán del Ecosistema Terra. Inspirado en la comunicación rítmica y eficiente de los grillos (*Gryllus*), reemplaza plataformas de colas y mensajería de pago (SQS, BullMQ, RabbitMQ, SendGrid) operando **100% a coste $0 e independencia total para el usuario final**.

No mantiene ningún servidor "escuchando" o consumiendo cómputo en reposo. Las aplicaciones encolan intenciones (*Chirps*) en milisegundos escribiendo en almacenes de estado pasivos (`.grillout-storage` en Git DB), y el enjambre de ejecutores efímeros sólo se despierta (canta) cuando hay un lote de notificaciones que entregar.

---

## ⚡ Características Principales

1. **📢 Stridulation Echo & Multicast Fanout**: Difusión de un solo payload JSON a múltiples destinos en paralelo: Discord Webhooks, Slack Webhooks, Telegram Bot API, Custom HTTP Webhooks, Email ($0 via Actions/SMTP) y GitHub Issues.
2. **⚡ Auto-Tuning Stridulation Batcher**: Gateway inteligente que dispara un `repository_dispatch` inmediato ante ráfagas de tráfico, o acumula los Chirps pasivamente en tráfico bajo para optimizar los minutos de Actions a cero.
3. **🎯 Gryllus FIFO & Chirp Deduplicator**: Deduplicación por `dedupKey` (SHA-256) + ventana temporal (`dedupWindowSec`) y secuenciación FIFO estricta por partición `groupKey`.
4. **🔓 Gryllus Lease Locks & Partial Batch Verdicts**: Bloqueos anti-colisiones (`leasedUntil`) y veredictos parciales de lote para purgar únicamente los mensajes procesados con éxito.
5. **⏳ Temporal Chirp Delays & Priority Swarms**: Mensajes programados a futuro (`deliverAt`) y priorización VIP para alertas de seguridad críticas.
6. **🛡️ HoneyChirp Poison Shield**: Detección pasiva anti-bots y cuarentena de payloads maliciosos sin falsos positivos.
7. **🎨 Gryllus Template Synthesizer & Studio Visual**: Motor de plantillas Markdown/HTML integrado con vista previa en vivo y consola web Glassmorphic 24/7 en GitHub Pages en tono **Verde Bosque Oscuro** (`#1b4332`).

---

## 🛠️ Instalación y Uso

### Instalación del SDK o CLI
```bash
npm install @terra/grillout
# o instalar el CLI global:
npm install -g grillout-cli
```

### Publicar un Chirp desde Node.js TypeScript
```typescript
import { Grillout } from '@terra/grillout';

const grillout = new Grillout();

await grillout.publish({
  channel: 'user-onboarding',
  payload: {
    subject: '¡Bienvenido a bordo!',
    message: 'Tu cuenta ha sido activada con éxito.',
    userId: 99
  },
  priority: 'VIP',
  groupKey: 'user_99',
  targets: [
    { type: 'discord', endpoint: 'https://discord.com/api/webhooks/...' },
    { type: 'slack', endpoint: 'https://hooks.slack.com/services/...' }
  ]
});
```

### Uso desde la CLI
```bash
# Publicar un mensaje
grillout pub user-onboarding '{"subject":"Alerta","message":"Hola"}' --priority VIP

# Listar canales activos
grillout list

# Arrancar la consola web local
grillout studio
```

---

## 🎨 Gryllus Studio Web Console
Accede a la consola web interactiva 24/7 alojada en GitHub Pages:  
👉 **[amglogicalis.github.io/grillout-repo-public/](https://amglogicalis.github.io/grillout-repo-public/)**

---

*Desarrollado con rigor técnico y pasión por el Ecosistema Terra.* 🦗
