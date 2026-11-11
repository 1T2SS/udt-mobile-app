# Universal Mobile App Template (`udt-mobile-app`)

> **AI-First Vibe Coding Preset** for smooth 60/120fps iOS & Android mobile apps using **React Native + Expo**, **Flutter**, or **Kotlin Multiplatform / Jetpack Compose**.
> Includes built-in **Android CLI & Device Hub** sidecar integration and proactive mobile SDK environment setup.

---

## Quick Start (30 Seconds)

### Option A: From GitHub
1. Click **"Use this template" → "Create a new repository"** on GitHub.
2. Clone your new repo and open it in any AI coding agent.
3. Describe the iOS/Android app you want to build!

### Option B: From Local UDT Hub
```powershell
.\scripts\new-project.ps1 -Preset mobile-app -Target "E:\Projects\MyMobileApp" -InitGit
```

---

## Key Features
- **Proactive Mobile SDK & Emulator Doctor**: Checks your local Android SDK, `adb`, `android` CLI, **Android Device Hub** sidecar, **Compose Preview**, Flutter SDK, and Expo toolchain via [`.ai/MCP_AND_TOOLS.md`](./.ai/MCP_AND_TOOLS.md) — and offers to set up any missing tools automatically!
- **60/120fps Mobile Engineering Rules**: Enforces off-main-thread animations, fast local persistence (`MMKV` / `SQLite`), and virtualized lists (`FlashList`).
