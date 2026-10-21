# EnderCore Client

**EnderCore Client** es una versión personalizada para Android basada en el proyecto Amethyst/PojavLauncher, con identidad visual propia. El repositorio actual contiene el cliente Android; no contiene todavía una versión de escritorio Windows (.exe).

> **Estado:** en desarrollo. No publiques un APK como versión estable hasta que la compilación de GitHub Actions termine correctamente y el archivo se haya verificado.

## Plataformas

- **Android:** cliente basado en el proyecto existente.
- **Windows:** no disponible en este repositorio. Requiere un cliente de escritorio compatible y una compilación independiente; no se puede convertir el APK renombrando el archivo.

## Compilar Android

El workflow de GitHub Actions está en [`.github/workflows/android.yml`](.github/workflows/android.yml). Cuando termine correctamente, debe generar y subir los artefactos:

- `app-debug (recommended)`
- `app-release`

Revisa las ejecuciones y descarga los artefactos en [GitHub Actions](https://github.com/garciawilkar50-boop/Omni-Launcher/actions).

Para compilar localmente, usa JDK 21 y sigue las instrucciones de dependencias/JRE del proyecto base. Comandos principales:

```bash
./gradlew :app_pojavlauncher:assembleDebug
./gradlew :app_pojavlauncher:assembleRelease
```

## Identidad visual

- Nombre del producto: **EnderCore Client**
- Paleta: carbón, obsidiana, gris y verde esmeralda.
- Lema: **Tu mundo, sin límites.**

## Base del proyecto y licencias

EnderCore Client se basa en Amethyst/PojavLauncher y sus componentes. Conserva los avisos de copyright y las licencias aplicables al distribuir modificaciones.

- Proyecto base: [AngelAuraMC/Amethyst-Android](https://github.com/AngelAuraMC/Amethyst-Android)
- PojavLauncher: [PojavLauncherTeam/PojavLauncher](https://github.com/PojavLauncherTeam/PojavLauncher)
- Licencia de Amethyst: [LGPLv3](https://github.com/AngelAuraMC/Amethyst-Android/blob/v3_openjdk/LICENSE)
