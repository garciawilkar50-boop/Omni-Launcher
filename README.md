# Omni Launcher

Omni Launcher es una versión personalizada para Android basada en el proyecto Amethyst/PojavLauncher. Este repositorio contiene el código de la aplicación Android; no contiene una versión de escritorio Windows (.exe).

> Estado: en desarrollo. No publiques un APK como versión estable hasta que la compilación de GitHub Actions termine correctamente y el archivo se haya verificado.

## Compilar Android

El workflow de GitHub Actions está en [`.github/workflows/android.yml`](.github/workflows/android.yml). Cuando termine correctamente, debe generar y subir los artefactos:

- `app-debug (recommended)`
- `app-release`

Puedes revisar las ejecuciones y descargar los artefactos en [GitHub Actions](https://github.com/garciawilkar50-boop/Omni-Launcher/actions).

Para compilar localmente, usa JDK 21 y sigue las instrucciones de dependencias/JRE del proyecto base. Comandos principales:

```bash
./gradlew :app_pojavlauncher:assembleDebug
./gradlew :app_pojavlauncher:assembleRelease
```

## Base del proyecto y licencias

Omni Launcher se basa en Amethyst/PojavLauncher y sus componentes. Consulta el historial del repositorio y los archivos de licencia incluidos para conocer las licencias y atribuciones aplicables. Conserva los avisos de copyright y las licencias de cada dependencia al distribuir modificaciones.

- Proyecto base: [AngelAuraMC/Amethyst-Android](https://github.com/AngelAuraMC/Amethyst-Android)
- PojavLauncher: [PojavLauncherTeam/PojavLauncher](https://github.com/PojavLauncherTeam/PojavLauncher)
- Licencia de Amethyst: [LGPLv3](https://github.com/AngelAuraMC/Amethyst-Android/blob/v3_openjdk/LICENSE)

## Plataforma de escritorio

El repositorio actual es Android. La descarga Windows EXE necesita un cliente de escritorio compatible y una compilación independiente; no se puede convertir el APK renombrando el archivo.
