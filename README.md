# Lector de KDMs — Cines Babel

Herramienta de un solo archivo (`index.html`) para revisar KDMs sin necesitar el resumen de la distribuidora.

## Qué hace
- Lee los `.zip` (incluidos ZIP dentro de ZIP) o `.xml` de KDM. Se pueden cargar a la vez varios archivos de películas distintas, o una carpeta entera con subcarpetas, arrastrándolos o seleccionándolos.
- Muestra arriba un listado con una línea por película: número de KDMs y de versiones, salas, primera y última fecha, y avisos (caducadas, no cubren el periodo, no coinciden con la CPL…). Al pulsar una película se ve solo esa.
- Agrupa las KDMs por versión de la película (título CPL) y muestra para cada servidor:
  - desde cuándo y hasta cuándo es válida, en hora local;
  - el estado: válida, caduca pronto (< 48 h), aún no válida o caducada.
- **Comprobar periodo**: indicas el primer y el último día de proyección y te dice qué KDMs no lo cubren.
- Si el ZIP trae la CPL, comprueba que la KDM corresponde a esa CPL y que incluye todas sus claves.
- **Salas de los servidores** (opcional): asocias el número de serie de un servidor a su sala (Sala 1–5) una sola vez y queda guardado en ese navegador (localStorage).
- **Envío a la Lista de Ingestas de la Mostra**: se conecta al mismo Supabase que la Mostra (tabla `mostra_peliculas`) y rellena la KDM de cada película (salas S1–S5, válida desde y hasta) y la marca como *KDMs*. Solo modifica los campos `kdm` y `enc`; el resto de la película no se toca. Las películas se emparejan por el nombre de archivo (si la CPL está entre los archivos de la película) o por el título; si no las encuentra, se eligen a mano y la elección se recuerda. Si la película tiene un archivo marcado «a proyectar», solo cuentan las KDMs de esa versión. Las salas que ya estaban marcadas se mantienen. Se envía aunque no se sepa la sala de ningún servidor: siempre van las fechas; se marcan las salas conocidas; si hay KDMs para los 5 servidores se marcan todas; y los servidores sin sala se apuntan en la nota de la película para marcarlos a mano en la Mostra. Hay una opción para enviar automáticamente al cargar las KDMs.
- Botones para copiar un resumen en texto y para exportar CSV (separado por `;`, se abre en Excel).
- Modo claro/oscuro.

Los archivos se procesan en el navegador y no se suben a ningún sitio; a Supabase solo se envían las fechas y las salas. No tiene dependencias externas.

Credenciales de Supabase: si el lector está en el mismo dominio que la Lista de Ingestas (`pabloogooitia.github.io`), usa las que ya estén guardadas en ese navegador para la Mostra o para la lista normal. Si no hay ninguna, se introducen con el botón **Conectar**.

## Changelog
- **v1.3** (31/10/2026): se puede enviar a la Mostra aunque falte la sala de algún servidor.
- **v1.2** (31/10/2026): envío de las KDMs a la Lista de Ingestas de la Mostra (Supabase). La sala de cada servidor se elige en un desplegable (Sala 1–5).
- **v1.1** (31/10/2026): listado resumen por película (pulsar para filtrar), carga de carpetas enteras, plegar/desplegar cada versión.
- **v1.0** (31/10/2026): primera versión.
