# Monitor RSS v2 · Argentina y La Rioja

Incluye gestión de canales (alta, activar/desactivar y exportar `feeds_argentina_larioja.json`), taxonomías y etiquetas del día, visualización individual de notas, copia de contenido y diseño móvil minimalista.

Estructura del repositorio para GitHub*
.
├── .github/
│   └── workflows/
│       └── update-feeds.yml          # Cron 3x/día (0 11,16,22 * * *) + disparo manual
├── data/
│   ├── feeds_argentina_larioja.json  # Directorio maestro (versión RSSv2), taxonomías y reglas
│   └── noticias_consolidadas.json    # Notas consolidadas, etiquetas y versiones de corridas
├── scripts/
│   └── fetch_and_classify.py         # Recolección, deduplicación, clasificación y etiquetas
├── index.html                        # SPA minimalista móvil con gestión RSS, etiquetas y copia
├── requirements.txt                  # Dependencias Python
└── README.md

Flujo de uso en GitHub

Descomprime monitor-rss-argentina-larioja-RSSv2.zip y sube los archivos al repositorio manteniendo la estructura de carpetas (asegúrate de tener activados los permisos de escritura en Settings → Actions → General → Workflow permissions y GitHub Pages en Settings → Pages).   

En la pestaña Canales RSS (Alta / Estado) de la SPA, agrega nuevos canales o alterna Activar / Desactivar y pulsa Exportar feeds_argentina_larioja.json para reemplazar data/feeds_argentina_larioja.json en el repositorio cuando quieras persistir cambios en el cron automático.

Ejecuta el workflow desde Actions → Run workflow (o espera las corridas programadas) para actualizar data/noticias_consolidadas.json con nuevas notas, taxonomías y etiquetas

Tutorial Paso a Paso para Publicar en GitHub
Crea el repositorio y sube los archivos:

Crea un repositorio nuevo en GitHub (por ejemplo monitor-rss-arg-larioja).

Extrae el ZIP y sube todo su contenido a la rama principal (main), respetando las carpetas .github/workflows/, data/ y scripts/.

Habilita permisos de escritura para GitHub Actions:

Entra en Settings → Actions → General → Workflow permissions.

Selecciona Read and write permissions y guarda los cambios. Así el workflow podrá hacer commit y push automático de data/noticias_consolidadas.json.

Activa GitHub Pages:

Entra en Settings → Pages.

En Build and deployment → Source, elige Deploy from a branch, selecciona la rama main y la carpeta / (root), y guarda.

En unos minutos tu SPA quedará disponible en https://<tu-usuario>.github.io/<tu-repositorio>/.

Ejecuta la primera recolección en vivo:

Ve a la pestaña Actions en tu repositorio.

Selecciona el workflow Actualizar Canales RSS (3x al dia) y haz clic en Run workflow.

Al terminar, data/noticias_consolidadas.json contendrá los ítems recolectados y la corrida quedará registrada en el selector de versiones de la SPA.

Personaliza fuentes o temas:

Edita data/feeds_argentina_larioja.json para activar/desactivar canales ("activo": true/false), añadir nuevas URLs o ajustar las palabras clave de reglas_clasificacion.

