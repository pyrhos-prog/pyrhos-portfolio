# Portfolio de Pyrhos ⚡

Portfolio profesional y blog de ciberseguridad ofensiva, writeups de máquinas (Hack The Box, TryHackMe, CTFs), análisis de vulnerabilidades, herramientas y seguimiento del **Roadmap hacia la certificación CPTS (Certified Penetration Testing Specialist)**.

Construido sobre **Jekyll** con el tema **Chirpy** y una capa visual y funcional de estilo hacker y HackTheBox.

---

## Características principales

- **Terminal interactiva:** Hero de bienvenida con prompt estilo Linux, `whoami`, avatar en arte ASCII e insignias dinámicas de progreso.
- **Efectos Cyber:** Lluvia Matrix interactiva sobre canvas en el panel lateral, animaciones glitch y transiciones fluidas.
- **Roadmap CPTS:** Seguimiento de progreso con cálculo porcentual automático, contador de resueltas y tabla interactiva de máquinas ordenadas por dominios clave de la CPTS (Easy, Medium, Active Directory y Pivoting/Redes corporativas).
- **Filtrado dinámico en tiempo real:** Filtros combinados por Sistema Operativo, Nivel de dificultad y búsqueda en vivo sin recargar la página.
- **Dashboard analítico de máquinas:** Gráficas interactivas (donut, barras y timeline) del historial de retos resueltos.
- **Sección de Herramientas y Proyectos:** Fichas interactivas desplegables para proyectos como el ESP32 Marauder o utilidades de automatización.
- **Acreditaciones y Formación:** Credenciales verificadas (eJPTv2) y seguimiento formativo reglado y práctico.

---

## Estructura del proyecto

- `_posts/` — Write-ups y artículos publicados (formato Markdown con front-matter extendido).
- `_tabs/` — Pestañas del menú principal (`writeups`, `roadmap`, `herramientas`, `certificaciones`, `titulos`, `maquinas`, `about`, `tags`).
- `_data/*.yml` — Datos de configuración de tablas y secciones (`cpts.yml`, `certificaciones.yml`, `titulos.yml`, `herramientas.yml`, `contact.yml`, `htb.yml`...).
- `_includes/` y `_layouts/` — Componentes personalizados con prefijo `hx-` (terminal hero, filtro dinámico, gráficas, rating en estrellas).
- `assets/` — Hojas de estilo personalizadas (`css/hacker.css`), scripts dinámicos (`js/hacker.js`), iconos e imágenes.
- `dev/` — Herramientas locales de desarrollo y edición visual:
  - `dev/submit-writeup/` — Generador y editor visual asistido para nuevos write-ups.
  - `dev/tools/` — Scripts de pruebas locales (`run.sh`, `test.sh`, `ascii.py`).
- `.github/workflows/pages.yml` — Despliegue automático y continuo a GitHub Pages mediante GitHub Actions.

---

## Despliegue en GitHub Pages

Cada vez que haces un `git push` a la rama `main`, la GitHub Action compila el sitio con Jekyll y lo publica automáticamente en GitHub Pages.
