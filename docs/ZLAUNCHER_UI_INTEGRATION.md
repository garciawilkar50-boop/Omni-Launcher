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
1. Inspeccionar las actividades, layouts, temas, navegación y flujo de lanzamiento existentes.
2. Identificar la pantalla inicial real y las APIs internas disponibles para versiones, perfiles, mods, archivos y ejecución.
3. Crear primero una capa visual nativa con componentes Android existentes; evitar migraciones grandes de framework al comienzo.
4. Conectar cada acción a la función real correspondiente. Si una función no está implementada, mostrar claramente su estado en desarrollo en lugar de simular éxito.
5. Adaptar los layouts a móvil/tableta y probar navegación, accesibilidad, orientación y tamaños de pantalla.
6. Ejecutar el workflow Android existente y verificar los resultados antes de afirmar que compila.

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
