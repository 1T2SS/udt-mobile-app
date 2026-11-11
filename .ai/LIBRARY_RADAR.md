# LIBRARY_RADAR.md — Mobile App Tech Stack & Library Guide

> **Preset**: `mobile-app`
> **Rule for AI Agents**: Always choose from the **Approved Mobile Radar** below. Never use bare `react-native init` (without Expo) or slow JS-thread animation/storage libraries on the **Banned** list.

---

## 1. Mobile Stack Decision Tree

| Mobile Goal | Recommended Primary Stack | Why It Excels | Matching Recipe |
| :--- | :--- | :--- | :--- |
| **Cross-Platform iOS + Android + Web with TypeScript/React** | **React Native + Expo SDK (Expo Router + Prebuild/CNG)** | File-based routing, zero native Xcode/Gradle headaches until needed, OTA updates | [`.ai/recipes/expo-react-native-offline-first.md`](./recipes/expo-react-native-offline-first.md) |
| **Pixel-Perfect 120fps Custom UI Across iOS + Android + Desktop** | **Flutter (Dart + Impeller + Riverpod)** | Consistent GPU rendering across every OS and screen size | [`.ai/recipes/flutter-crossplatform-app.md`](./recipes/flutter-crossplatform-app.md) |
| **Native Android or Shared Native Business Logic** | **Kotlin + Jetpack Compose** (or **Kotlin Multiplatform KMP**) | Direct access to Android Device Hub & Compose Preview sidecars | [`.ai/recipes/native-android-compose-kmp.md`](./recipes/native-android-compose-kmp.md) |

---

## 2. Approved Library Radar

- **Expo / React Native Ecosystem**:
  - **Navigation**: `expo-router` (typed file-based routing).
  - **Styling**: `nativewind` (Tailwind CSS for React Native) or `StyleSheet.create` with theme tokens.
  - **Fast Storage**: `react-native-mmkv` (30x faster synchronous key-value storage than AsyncStorage) or `expo-sqlite` + Drizzle ORM.
  - **Lists**: `@shopify/flash-list` (replaces slow `FlatList` for large lists).
  - **Animations & Gestures**: `react-native-reanimated` + `react-native-gesture-handler` (runs at 60/120fps on UI thread).
- **Flutter Ecosystem**:
  - **State**: `flutter_riverpod` (with `riverpod_annotation`) or `flutter_bloc`.
  - **Routing**: `go_router`.
  - **Local DB**: `drift` (type-safe SQLite) or `shared_preferences`.
- **Android / Kotlin Compose Ecosystem**:
  - **Architecture**: Jetpack ViewModel + Kotlin `StateFlow` + `Hilt` / `Koin` + `Room` (SQLite) + `Retrofit` / `Ktor`.

---

## 3. Banned / Deprecated by Default (DO NOT USE)

| Banned Pattern / Library | Why It Is Banned | Use This Instead |
| :--- | :--- | :--- |
| **Legacy `@react-native-community/cli init` without Expo** | Painful native upgrades and broken config plugins | **Expo (`bunx create-expo-app`)** with Continuous Native Generation (CNG) |
| **`AsyncStorage` for frequent state reads** | Slow serialized bridge bottleneck | **`react-native-mmkv`** or **`expo-sqlite`** |
| **Un-virtualized `ScrollView .map()` for >30 items** | Drops frames and crashes mobile memory | **`@shopify/flash-list`** or `FlatList` |
| **Hardcoding pixel dimensions without SafeArea / Keyboard handling** | Clips UI under notches, Dynamic Island, and on-screen keyboards | Always use `SafeAreaView` (`react-native-safe-area-context`) and `KeyboardAvoidingView` |
