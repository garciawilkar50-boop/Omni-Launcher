# Omni Launcher — Branding and UI direction

This document tracks the first rebranding pass on the Amethyst-Android codebase.

## Product direction
- Name shown to users: **Omni Launcher**
- Platform: Android, portrait-first launcher UI with landscape support retained for gameplay
- Visual style: minimal, premium, gaming-focused
- Palette: near-black and charcoal surfaces, white primary text, muted gray secondary text, soft pixel-green accent
- Avoid gradients, excessive glow, or cluttered gamer UI
- Keep gameplay controls and accessibility legible; do not sacrifice function for branding

## Current changes on `omni-branding`
- Gradle app label now displays `Omni Launcher` for release builds and `Omni Launcher (Debug)` for debug builds.
- The existing `minebutton_color` accent changed from purple to muted green (`#A3D977`).
- The original application ID and provider authorities are intentionally unchanged in this first pass to avoid breaking data paths, app links, saved profiles, or file providers before a migration plan exists.

## Next implementation steps
1. Inspect the main activity and home-screen layouts before changing navigation or layout structure.
2. Create original Omni Launcher launcher icons for all mipmap densities and the Play Store artwork. Do not reuse Amethyst branding in a release.
3. Rework the home screen around a clear primary **Play** action, selected Minecraft version, installed profile, and concise status.
4. Restyle version selection, installations/mods, memory/performance settings, and touch-control editor using the same color tokens.
5. Review all user-facing references to Amethyst/PojavLauncher. Keep legal notices, credits, license texts, and upstream attribution intact.
6. Run Android CI/build checks and test on an actual Android device before producing an APK.

## Important release notes
- This project is based on Amethyst-Android/PojavLauncher-derived code. Preserve all required license notices and third-party credits.
- Omni Launcher is an independent community project and is not an official Minecraft product or affiliated with Mojang/Microsoft.
- Do not distribute a release APK until signing configuration and any upstream signing artifacts have been reviewed. Never publish signing passwords or private keys.
