# CLAUDE.md

Blog Jekyll (tema Chirpy con capa hacker/HTB) de Pyrhos: writeups de ciberseguridad ofensiva, HackTheBox, proyectos de hardware/scripts y Roadmap CPTS. Publicación continua mediante GitHub Pages.

## Convenciones y Estructura

- **Writeups en `_posts/`:** Ficheros con nomenclatura estándar de Jekyll: `AAAA-MM-DD-<slug>.md`.
  - Deben incluir en el front-matter:
    - `categories: ["Writeups", ...]` para que aparezcan listados en `/writeups/` y en el dashboard de `/maquinas/`.
    - `machine: "<Nombre>"` y `platform: "HackTheBox"` para que se vinculen automáticamente con el **Roadmap CPTS** (`_data/cpts.yml`) y se marquen como "Resuelta".
    - `os: "Linux" | "Windows"` y `difficulty: "Easy" | "Medium" | "Hard" | "Insane"`.
    - `thumb` y `accent` para personalizar las tarjetas con el color de acento.
- **Roadmap CPTS:** Los datos de las máquinas y dominios se definen en `_data/cpts.yml`.
- **Herramientas:** Viven en `_data/herramientas.yml` y se renderizan interactivamente en `/herramientas/`.
- **Certificaciones y Títulos:** Se gestionan desde `_data/certificaciones.yml` y `_data/titulos.yml`.
- **Efectos y Estilos:** `assets/css/hacker.css` y `assets/js/hacker.js`.
- **Despliegue:** `.github/workflows/pages.yml` compila el sitio en GitHub Actions tras cada push a `main`.
