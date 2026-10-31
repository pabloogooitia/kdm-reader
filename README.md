# Lector de KDMs — Cines Babel

Herramienta de un solo archivo (`index.html`) para revisar KDMs sin necesitar el resumen de la distribuidora.

## Qué hace
- Lee los `.zip` (incluidos ZIP dentro de ZIP) o `.xml` de KDM. Se pueden cargar varios archivos a la vez arrastrándolos o seleccionándolos.
- Agrupa las KDMs por versión de la película (título CPL) y muestra para cada servidor:
  - desde cuándo y hasta cuándo es válida, en hora local;
  - el estado: válida, caduca pronto (< 48 h), aún no válida o caducada.
- **Comprobar periodo**: indicas el primer y el último día de proyección y te dice qué KDMs no lo cubren.
- Si el ZIP trae la CPL, comprueba que la KDM corresponde a esa CPL y que incluye todas sus claves.
- **Nombres de sala**: asocias cada número de serie de servidor a su sala una sola vez y queda guardado en ese navegador (localStorage).
- Botones para copiar un resumen en texto y para exportar CSV (separado por `;`, se abre en Excel).
- Modo claro/oscuro.

Todo se procesa en el navegador; no se sube ningún archivo. No tiene dependencias externas: funciona sin conexión y desde GitHub Pages.


## Changelog
- **v1.0** (31/10/2026): primera versión.
