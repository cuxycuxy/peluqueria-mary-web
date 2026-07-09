# DIARIO — barberia-puerto-web

## 08/07/2026 — Creación del proyecto

Web pública de reservas para La Barberia del Puerto (Raúl Giménez, Burriana).

**Funcionalidad:**
- Información del negocio: dirección, teléfono, horario
- Google Maps embed (Avinguda Mediterrània, 27, Burriana)
- Formulario de reserva online:
  - Nombre + teléfono
  - Servicios (dropdown dinámico desde `GET /servicios` de barberia-puerto-api)
  - Fecha (picker con mínimo = hoy)
  - Hora (slots dinámicos desde `GET /disponibilidad?fecha=X`, se actualiza al cambiar fecha)
  - Submit → `POST /citas-web` → cita aparece en app en tiempo real
- Política de privacidad: cuxy.app/privacidad

**Diseño:** tema negro/dorado, coherente con el logo de Raúl.

**Deploy:** Cloudflare Pages
- Repo: cuxycuxy/barberia-puerto-web (público)
- Workers & Pages → Create → Connect to Git → barberia-puerto-web → rama main → sin build command → directorio raíz /

## 09/07/2026 — Rediseño web completo + dominio + prueba reserva

- Nav eliminada (nombre y teléfono ya están en hero e info)
- Hero: logo de Raúl (PNG 1024x1024, fondo #000 exacto), ancho hasta 680px, sin recuadro visible
- Formulario de reserva: `<input type="date">` reemplazado por **calendario inline** en CSS/JS puro — muestra el mes actual, hoy seleccionado por defecto con slots ya cargados, domingos y días pasados deshabilitados, navegación con flechas
- Calendario compacto (celdas 34px) para no desproporcionarse respecto al resto del formulario
- **Dominio personalizado**: `labarberiadelpuerto.cuxy.app` activo en Cloudflare Workers
- **Prueba real**: reserva hecha desde la web → cita apareció en tiempo real en la app de Raúl (Expo Go)

**Pendiente:**
- Fotos reales del local cuando Raúl las proporcione
