# Omni Launcher — Branding and UI direction

This document tracks the visual rebrand on the Amethyst-Android codebase.

## Product direction
- Name shown to users: **Omni Launcher**
- Platform: Android; portrait-first launcher UI while preserving gameplay orientation support
- Visual style: minimal, premium, gaming-focused
- Palette: near-black and charcoal surfaces, off-white primary text, muted gray secondary text, soft pixel-green accent (#A3D977)
- Rounded surfaces with subtle outlines and touch feedback
- No gradients, excessive glow, or cluttered gamer UI
- Keep gameplay controls and accessibility legible; do not sacrifice function for branding

## Visual pass completed on omni-branding
- Updated release/debug display names and the app's short name to Omni Launcher / Omni.
- Replaced adaptive and legacy launcher icons with an original pixel-portal mark using the Omni green accent.
- Rebuilt the launcher home layout with a brand header, Java Edition subtitle, cleaner spacing, card-style shortcuts, version/profile surface, and the existing prominent Play action.
- Unified color tokens and card/menu surfaces in graphite, off-white, gray, and muted green.
- Applied the accent color to Android controls, selections, dialogs, and settings theme.
- Updated key user-facing crash, background-service, storage, and notification strings to use Omni branding.
- Updated shared card surfaces used by profile, login, and installation flows so secondary screens inherit the new palette.
- Kept the original application ID and provider authorities unchanged to avoid breaking data paths, app links, saved profiles, or file providers.

## Next phase: code and verification
1. Inspect and preserve the existing launcher state flow; make sure the redesigned version/profile selector and Play action still bind to the existing behavior.
2. Review navigation, profile/version selection, settings, installations/mod screens, and touch-control flows for regressions.
3. Audit remaining user-facing references to upstream names while preserving legal notices, credits, and license texts.
4. Run Android CI/build checks and resolve resource or compatibility errors.
5. Test on a real Android device before producing an APK.

## Important release notes
- This project is based on Amethyst-Android/PojavLauncher-derived code. Preserve all required license notices and third-party credits.
- Omni Launcher is an independent community project and is not an official Minecraft product or affiliated with Mojang/Microsoft.
- Do not distribute a release APK until signing configuration and any upstream signing artifacts have been reviewed. Never publish signing passwords or private keys.
