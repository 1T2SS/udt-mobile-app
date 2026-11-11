# MCP_AND_TOOLS.md — Proactive Mobile Environment & Device Hub Setup (`mobile-app`)

> **AI Agent Instruction**: On Day-0 Bootstrap, check which mobile SDKs, emulators (`adb`, `android` CLI), and sidecar skills (**Android Device Hub**, **Compose Preview**) are available. **If a required SDK or CLI tool is missing, explain what it does and ask the user if you can install/set it up for them!** Save all verified paths and SDK versions in [`.ai/ENVIRONMENT.md`](./ENVIRONMENT.md).

---

## 1. Recommended Skills & Sidecars to Check

| Skill / Tool | Purpose in `mobile-app` | How to Check & Offer Setup |
| :--- | :--- | :--- |
| **`android-cli` & `android-device-hub` Skills** | Manages Android Virtual Devices (AVDs), mirrors physical/virtual devices in the Device Hub pane, inspects UI layout trees (`android layout`), and captures screenshots (`android screen`). | Check if `android-cli` and `android-device-hub` skills exist in your skill list; read their `SKILL.md` before running Android commands! |
| **`compose-preview` Skill** | Renders Jetpack Compose `@Preview` functions directly in the Compose Preview sidecar pane (`android preview render`). | When building Kotlin/Jetpack Compose UI, load `compose-preview` and re-render previews after UI edits. |

---

## 2. Mobile Toolchain Doctor Checklist

Run these non-destructive checks and record results in [`.ai/ENVIRONMENT.md`](./ENVIRONMENT.md):

```powershell
# 1. Check Android CLI, ADB & Java JDK
android --version 2>$null
adb version 2>$null
java -version 2>$null

# 2. Check Bun / Node (for Expo / React Native)
bun --version 2>$null
node --version 2>$null

# 3. Check Flutter (if building with Flutter)
flutter --version 2>$null
```

### Auto-Setup Commands (Offer to Run with User Permission if Missing)
- **Install Java 17/21 JDK (required for Android builds)**: `winget install EclipseAdoptium.Temurin.21.JDK`
- **Install Bun (for Expo)**: `winget install Oven-sh.Bun`
- **Install Flutter**: `winget install Google.Flutter`
- **Follow `android-cli` skill instructions** if `android` CLI needs installation or SDK component setup.

---

## 3. Save Verified Setup Info for Future Creations
Record `ANDROID_HOME`, Java JDK path, connected AVDs, and active mobile SDK versions in [`.ai/ENVIRONMENT.md`](./ENVIRONMENT.md) (`Environment Check Status: VERIFIED`), and log any helpful emulator/build tricks in Section 5 of [`.ai/MEMORY.md`](./MEMORY.md).
