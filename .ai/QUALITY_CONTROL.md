# QUALITY_CONTROL.md — Master Quality Control Sub-Agent Protocol (`mobile-app`)

> **Preset**: `mobile-app`
> **QC Persona**: **Principal Mobile Design Director + Lead iOS/Android Architect** (`master-qc-director`)
> **Mandatory Rule**: Use **ONE** Master Quality Control Sub-Agent at the end of each development round. Never spawn multiple separate review sub-agents.
> **Pass Threshold**: Overall Average **`>= 8.5 / 10.0`** AND **every individual category `>= 8.5 / 10.0`**.

---

## 1. How to Invoke the Single Master QC Check

When a mobile development round is complete:
- **Antigravity**: Define/invoke the single `master-qc-director` sub-agent (`EnableWriteTools: true`, `EnableMCPTools: true`) to audit mobile UI screens (via Compose Preview / Android Device Hub / Expo), animations, offline state, and build health, writing `.ai/QC_REPORT.md`.
- **Claude Code**: Invoke `.claude/agents/master-qc-director.md`.
- **Cursor / Windsurf / Copilot / Cline**: Execute a dedicated **Master QC Director Audit Pass** using the rubric below and write `.ai/QC_REPORT.md`.

---

## 2. The 5-Pillar Zero-Trust Deduction Rubric (Starts at `10.0` Per Category)

### Category 1: Mobile UI/UX, Safe Areas & Visual Polish (`>= 8.5 / 10`)
- **`-2.0 pts`**: UI clipped by top notches/Dynamic Island, bottom home indicator, or on-screen keyboard (missing `SafeAreaView` / `WindowInsets` / `KeyboardAvoidingView`).
- **`-1.5 pts`**: Touch targets smaller than `44x44pt` / `48x48dp` or inconsistent typography/theme tokens.

### Category 2: Touch Mechanics, Gestures & 60/120fps Feel (`>= 8.5 / 10`)
- **`-2.0 pts`**: Running animations on the JS thread in React Native instead of `react-native-reanimated` / native driver, or sluggish screen transitions.
- **`-1.5 pts`**: Missing pull-to-refresh, haptic/visual touch feedback, or skeleton/loading states.

### Category 3: Code Architecture & Offline-First Persistence (`>= 8.5 / 10`)
- **`-2.5 pts`**: Using slow `AsyncStorage` for high-frequency state reads instead of `MMKV` / `SQLite` / `Drift` / `Room`, or installing mismatched native packages without `npx expo install`.
- **`-1.5 pts`**: Screen files exceeding ~300 lines with business logic tightly coupled to UI views.

### Category 4: Features & Navigation Completeness (`>= 8.5 / 10`)
- **`-2.0 pts`**: Broken back-button / deep-link navigation or unhandled offline network errors that crash the screen.
- **`-1.5 pts`**: Placeholder screens or incomplete user flows promised in `.ai/SPEC.md`.

### Category 5: List Virtualization, Memory & Doctor/Build Health (`>= 8.5 / 10`)
- **`-3.0 pts` (Automatic)**: `tsc --noEmit`, `npx expo-doctor`, `flutter analyze`, or `./gradlew assembleDebug` fails.
- **`-2.0 pts`**: Rendering dynamic lists with `ScrollView + .map()` instead of `@shopify/flash-list`, `FlatList`, `ListView.builder`, or `LazyColumn`.

---

## 3. Auto-Refinement Protocol (Up to 3 Rounds)
If any category scores `< 8.5 / 10`, `master-qc-director` sets `qc_status: REFINEMENT_REQUIRED` in [`.ai/QC_REPORT.md`](./QC_REPORT.md). The main agent must fix all listed deductions and re-run `master-qc-director` (up to 3 rounds max) before completing the round.
