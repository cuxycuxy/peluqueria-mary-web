# DIARIO — peluqueria-mary-web

## 09/07/2026 — Creación del proyecto (fork de barberia-puerto-web)

Web pública de reservas para Peluquería Mary, adaptada desde `barberia-puerto-web` (mismo motor de reservas).

**Funcionalidad:**
- Información del negocio: teléfono, horario (dirección añadida al día siguiente, ver 10/07)
- Formulario de reserva online:
  - Nombre + teléfono
  - Servicios (dropdown dinámico desde `GET /servicios` de `peluqueria-mary-api`)
  - Fecha (calendario inline, mínimo = hoy)
  - Hora (slots dinámicos desde `GET /disponibilidad?fecha=X`, se actualiza al cambiar fecha)
  - Submit → `POST /citas-web` → cita aparece en la app en tiempo real
- Política de privacidad: cuxy.app/privacidad
- **Sin mapa**: a diferencia de Puerto, en el momento del fork Mary no tenía dirección todavía, así que el bloque de mapa (Google Maps embed) no se adaptó. Sigue sin él aunque la dirección se añadió el 10/07 — pendiente si se quiere.

**Diseño:** tema blanco/teal (`#1B5E6E`), distinto del negro/dorado de Puerto.

**Deploy:** Cloudflare Workers (assets) — `wrangler.jsonc` con `name: "peluqueriamary"` (corregido el mismo día, ver abajo, para no pisar el Worker de Puerto).
- Repo: cuxycuxy/peluqueria-mary-web
- URL en producción: **https://peluqueriamary.cuxy.app** (subdominio de Cuxy — Mary no tiene dominio propio, a diferencia de Puerto con `barberiadelpuerto.es`)

**Mismo día — ajustes:**
- `wrangler.jsonc`: `name` corregido a `peluqueriamary` (con el nombre por defecto, heredado del fork, sobrescribía el Worker de `barberia-puerto-web`) — bug real, corregido antes de causar downtime cruzado.
- Logo más grande (440px) y padding del hero ajustado.

## 10/07/2026 — Horario real y dirección

- Horario corregido al real: Lun/Mié–Sáb 09:30–14:00, martes cerrado (el del fork inicial, L-S 08:00-21:00, era provisional/heredado de Puerto).
- Añadida tarjeta de dirección: Carrer Ample, 36, Burriana.
- Calendario JS: bloqueados domingo **y martes** (Puerto solo bloquea domingo — cada web respeta los días cerrados reales de su negocio).
- Favicon ✂️ en la pestaña del navegador.

**Pendiente:**
- Fotos reales del local cuando Mary las proporcione.
- Dominio propio (Mary sigue en `peluqueriamary.cuxy.app`, no se le ha ofrecido/comprado uno propio como a Puerto).

---

## 28/08/2026 — Mapa de Google añadido

Comparando con Puerto salió a la luz que faltaba el mapa aunque la dirección estaba desde el 10/07. Añadido `.map-wrap` + iframe de Google Maps (Carrer Ample, 36, Burriana), mismo patrón que Puerto adaptado al tema claro/teal de Mary. De paso, `DIARIO.md` reescrito con el historial real del proyecto (era una copia sin editar del de Puerto desde el fork).
