# Recipe: Native Android (Kotlin + Jetpack Compose) with Device Hub & Compose Preview

## When to Use
Use this recipe when building a native Android app with Kotlin and Jetpack Compose, taking full advantage of the **Android CLI**, **Android Device Hub**, and **Compose Preview** sidecar skills.

## 1. Recommended Workflow
1. Read the `android-cli`, `android-device-hub`, and `compose-preview` skills if available in your agent environment.
2. Annotate UI components with `@Preview(showBackground = true)` and render them via `android preview render` so the user can inspect UI changes immediately.

## 2. Verification Commands
- **Assemble Debug APK**: `.\gradlew assembleDebug`
- **Run Unit Tests**: `.\gradlew testDebugUnitTest`
- **Lint Check**: `.\gradlew lintDebug`
