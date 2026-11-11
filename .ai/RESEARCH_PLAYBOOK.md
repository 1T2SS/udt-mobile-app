# RESEARCH_PLAYBOOK.md — Mobile App Pre-Coding Research Protocol

> **Preset**: `mobile-app`
> **Rule**: Verify SDK compatibility matrices (`npx expo install --check` / `flutter doctor`) and device/emulator availability before writing native integrations.

---

## 1. SDK Compatibility Verification
- **Expo / React Native**: Never install React Native native packages with raw `npm install <pkg>@latest` — always use **`npx expo install <pkg>`** so Expo resolves the exact version compatible with the active Expo SDK!
- **Android Gradle & Kotlin**: Check `gradle/libs.versions.toml` so Compose Compiler, Kotlin version, and Android Gradle Plugin (AGP) stay aligned.

## 2. Visual & On-Device Verification
- If **Android CLI** (`android`), **Android Device Hub**, or **Compose Preview** skills are available in your agent environment, load their skill instructions first so you can render `@Preview` composables or inspect live AVD screens (`android screen`, `android layout`, `adb`).
- Always test dark mode, safe area insets, loading states, and offline network fallback.
