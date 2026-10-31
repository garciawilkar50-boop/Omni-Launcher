# ZLauncher — Plan de integración de interfaz Android

## Objetivo
Adaptar la dirección visual del prototipo ZLauncher creado en Bolt.new al launcher Android basado en Amethyst/Pojav, sin sustituir el runtime de Minecraft ni introducir el prototipo React/Vite dentro del módulo Android.

## Reglas de seguridad del trabajo
- Todo cambio de integración se realiza en la rama `zlauncher/ui-integration`.
- La rama de origen `v3_openjdk` debe permanecer intacta.
- No presentar el prototipo web como si fuera una aplicación Android nativa.
- No anunciar APK funcional hasta que GitHub Actions o una compilación real termine correctamente y se compruebe el artefacto.
- No añadir secretos, contraseñas, tokens ni claves de firma a nuevos commits.

## Dirección visual acordada
- Idioma principal: español.
- Paleta: negro, grises y violeta como acento.
- Estética: moderna, oscura, limpia y con contraste legible.
- Fondo ilustrado de Minecraft con una capa oscura para preservar la legibilidad.
- Diseño adaptable a teléfonos y tabletas; priorizar fluidez en dispositivos de recursos limitados.
- Navegación prevista: Inicio, Versiones, Mods, Biblioteca, Descargas, Perfiles y Ajustes.

## Estrategia de integración
1. Inspeccionar las actividades, layouts, temas, navegación y flujo de lanzamiento existentes. **Hecho:** la entrada pasa por `TestStorageActivity` y después abre `LauncherActivity`; `MainMenuFragment` es la pantalla principal y ya contiene el flujo real de lanzamiento.
2. Identificar las APIs internas disponibles para versiones, perfiles, mods, archivos y ejecución. **Hecho:** el selector de versión, edición de perfil, instalación de `.jar`, apertura de carpeta, controles y acción JUGAR ya tienen callbacks existentes.
3. Crear una capa visual nativa con componentes Android existentes. **Primer paso hecho:** cabecera de marca ZLauncher, paleta grafito/violeta y botones de acción con tarjetas redondeadas en `fragment_launcher.xml`.
4. Mantener las acciones existentes conectadas al comportamiento real. **Hecho en el diseño actual:** no se reemplazó `MainMenuFragment` ni su lógica de lanzamiento.
5. Adaptar a móvil/tableta y comprobar accesibilidad, orientación y tamaños de pantalla. **Pendiente de pruebas en dispositivo/emulador.**
6. Ejecutar el workflow Android existente y verificar los resultados antes de afirmar que compila. **Pendiente:** el endpoint de Actions no devolvió ejecuciones; no se ha confirmado una compilación de esta rama.

## Cambios ya guardados en esta rama
- Se añadió la cabecera visual nativa `ZLauncher` y el subtítulo en español.
- Se aplicó una paleta sin degradados: fondo casi negro, superficies grafito y acento violeta.
- Las acciones de la pantalla principal ahora usan superficies redondeadas oscuras con feedback táctil.
- Se cambiaron los nombres visibles de las variantes Android a `ZLauncher` / `ZLauncher (Debug)`.
- Se tradujeron a español algunas etiquetas de la pantalla principal, incluido el botón `JUGAR`.
- Se conservó el `applicationId` original para evitar una migración accidental de identidad de paquete y datos de instalación.

## Mapeo inicial de pantallas
- **Inicio:** perfil seleccionado, versión instalada/seleccionada y botón de jugar conectado al flujo real del launcher.
- **Versiones:** reutilizar el selector/instalador de versiones existente.
- **Mods:** enlazar al gestor compatible existente; distinguir mods instalados de archivos disponibles.
- **Biblioteca:** mostrar instalaciones/perfiles locales existentes, sin inventar datos.
- **Descargas:** aprovechar el estado real de descargas y tareas cuando esté disponible.
- **Perfiles:** reutilizar el almacenamiento y selección de perfiles existente.
- **Ajustes:** preservar preferencias actuales y añadir solo ajustes compatibles.

## Verificaciones pendientes
- Localizar la actividad que controla la pantalla inicial y los componentes de instalación/lanzamiento.
- Comprobar compatibilidad de recursos y dependencias antes de modificar layouts.
- Revisar el workflow de GitHub Actions y comprobar si la rama puede compilar.
- Revisar las claves de firma versionadas en el repositorio. El archivo `app_pojavlauncher/aamc_upload.jks` aparece en el repositorio; no debe asumirse que pertenece al usuario, pero si es una clave privada de publicación válida y ha estado expuesta, debe considerarse comprometida y rotarse por su propietario.

## Criterio de aceptación
La primera entrega solo se considera lista cuando la pantalla inicial nativa se ve coherente con ZLauncher, las acciones conectadas llevan a flujos reales del launcher, la rama original permanece sin cambios y existe evidencia verificable del resultado de compilación.


## Pantallas adicionales — fase de rediseño

- **Inicio:** conserva el selector real de versión, edición del perfil, controles, instalación de JAR, registros y carpeta del juego.
- **Biblioteca de modpacks:** nuevo acceso desde Inicio en orientación vertical y horizontal; abre el fragmento nativo `ModpackCreateFragment`. Desde ahí, Explorar modpacks abre la búsqueda conectada a CurseForge y la importación ZIP/.mrpack usa el selector del sistema y el flujo de instalación existente.
- **Versiones:** se mantiene el selector nativo y la lista real de versiones/modloaders; se actualizó la presentación de las filas y de la pantalla de selección.
- **Perfiles:** el editor existente conserva guardado, borrado, selección de versión, runtime, renderer, carpeta del juego y controles; se pulieron colores de texto y campos.
- **Archivos:** el selector existente mantiene navegación de carpetas, creación y selección; se mejoró la presentación de la ruta actual.
- **Ajustes:** el botón de ajustes de la actividad sigue abriendo `LauncherPreferenceFragment`; la pantalla usa el tema oscuro común del launcher.
- **Búsqueda de modpacks:** se mantiene búsqueda, filtros por versión, estados de carga/error y adaptador real; se ajustaron la tarjeta superior y el espacio de la lista.

## Validación pendiente

Los cambios se han guardado en la rama de trabajo y están incluidos en el PR abierto. Aún no se ha verificado una compilación Android ni una prueba en dispositivo/emulador. La conexión visual/código no equivale a confirmar que todas las pantallas compilen o funcionen en ejecución.


## Revisión de pantallas — correcciones aplicadas

- **Inicio vertical/horizontal:** los siete accesos usan tarjetas redondeadas y feedback táctil coherentes. Se comprobó que ambos layouts contienen todos los IDs que consume `MainMenuFragment`, incluido `library_button`.
- **Tema global:** texto y texto de ayuda pasan a colores claros sobre el fondo oscuro; el acento usa el violeta de ZLauncher.
- **Búsqueda:** se corrigió el contraste del campo de búsqueda y se eliminó el texto de ejemplo que podía aparecer como estado inicial.
- **Selector de archivos:** la lista ahora usa constraints laterales explícitos; la ruta larga se limita a una línea y muestra puntos suspensivos en vez de desbordarse.
- **Biblioteca de modpacks:** el contenedor y los dos botones usan anchos compatibles con ConstraintLayout y límites laterales explícitos.
- **Recursos:** se verificaron las cadenas de biblioteca en inglés/español, la presencia del icono y fondo usados, y el balance de etiquetas XML en las pantallas revisadas.

**Estado de validación:** las comprobaciones estáticas de recursos/IDs y estructura XML no reportaron errores en los archivos revisados. GitHub no muestra ejecuciones de Actions para la rama y no hay una compilación Android confirmada; por tanto, aún falta ejecutar `./gradlew :app_pojavlauncher:assembleDebug` y probar el APK en dispositivo/emulador.
