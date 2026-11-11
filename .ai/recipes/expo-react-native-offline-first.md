# Recipe: React Native + Expo (Expo Router & Offline-First Architecture)

## When to Use
Use this recipe when building a cross-platform iOS, Android, and Web app with TypeScript and React Native.

## 1. Official Scaffold Commands
```powershell
bunx create-expo-app@latest .
# Install compatible packages via expo install:
npx expo install expo-router react-native-safe-area-context react-native-screens expo-linking expo-constants expo-status-bar
npx expo install @shopify/flash-list
```

## 2. Recommended Directory Layout
```text
├── app/                  # Expo Router file-based screens (_layout.tsx, index.tsx, (tabs)/)
├── components/           # Reusable mobile UI components
├── hooks/                # Custom hooks & state selectors
├── services/             # API clients & local SQLite/MMKV storage
└── app.json              # Expo config & native permissions
```

## 3. Verification Commands
- **Check Dependency Compatibility**: `npx expo install --check`
- **Typecheck**: `bun x tsc --noEmit`
- **Run Doctor**: `npx expo-doctor`
