# ⚗️ Grilling Domain 4: React Native Mobile Application (PENDING USER REVIEW)
### Feynman Adaptive Engine (AI Tayyari Hub) — Stage 0 Baseline

> [!IMPORTANT]
> This domain replaces the generic web frontend grilling. It evaluates the architectural, native platform, and engineering decisions required to build a high-performance **React Native mobile application** (iOS & Android).

---

### 1. Toolchain: Expo Managed Workflow vs. Bare React Native CLI
- **Option A (Expo Managed Workflow with Prebuild / EAS):** Industry standard in 2026. Zero Xcode/Android Studio manual configuration; native modules supported via config plugins; seamless live testing on physical devices via Expo Go / EAS Update.
- **Option B (Bare React Native CLI):** Direct `npx react-native init` managing `ios/` and `android/` directories manually.
*Which toolchain do you want to use? (Recommendation: Expo)*

### 2. Navigation Architecture: Expo Router vs. React Navigation
- **Option A (Expo Router v3/v4):** File-based routing (`app/(tabs)/`, `app/course/[id].tsx`), similar to Next.js but fully native for mobile.
- **Option B (React Navigation):** Traditional imperative navigation stacks (`createNativeStackNavigator`, `createDrawerNavigator`).
*Which navigation system fits your preferences?*

### 3. Server-Sent Events (SSE) Streaming in React Native
React Native's standard `fetch` historically buffers responses rather than streaming tokens word-by-word on mobile devices:
- **Solution A:** Use `expo/fetch` (built-in streaming response body reader in modern Expo).
- **Solution B:** Use `react-native-sse` (dedicated native EventSource client).
- **Solution C:** Use `react-native-fetch-api` polyfill with stream reading.
*Which native streaming approach should we standardize on?*

### 4. Mathematical Equation Rendering (KaTeX in React Native)
React Native does not have a browser HTML DOM, so standard web KaTeX `<span>` tags cannot render directly:
- **Option A (`react-native-math-view`):** Native Android/iOS MathJax view for fast formula display.
- **Option B (SVG KaTeX Pipeline):** Pre-render LaTeX formulas into lightweight vector SVG on the backend or in a micro-headless worker.
- **Option C (Lightweight Headless Micro-WebView):** A zero-margin, transparent headless web component dedicated solely to rendering KaTeX text bubbles.
*Which math rendering approach do you prefer?*

### 5. Mobile Virtual Keyboard Collision Management
In your handwritten notes (`Image/3rd.jpeg`), you wrote: *“responsive page based on keyboard - make sure it does hide near and LLM response completely.”*
- **Option A (`react-native-keyboard-controller`):** The modern 60fps standard that provides synchronized native keyboard height animations, keeping the active question card locked above the keyboard.
- **Option B (Standard `KeyboardAvoidingView`):** Built-in React Native component with `behavior="padding"`.
*Which keyboard animation engine should we use?*

### 6. Side Drawer Navigation (`Image/3rd.jpeg`)
In your mobile wireframe, you drew a left slide-out hamburger drawer for topic/session history:
- Should this use **React Navigation Drawer** (with native 60fps touch gestures), or a custom animated overlay modal?

### 7. The Progress Bottom-Sheet Modal (`Image/WhatsApp Image...`)
In your blueprint, tapping the top progress header opens a bottom modal showing syllabus hierarchy:
- Should we use **`@gorhom/bottom-sheet`** (the gold standard for high-performance, native gesture-driven bottom sheets in React Native) to render the syllabus accordion?

### 8. High-Performance Local Cache & Storage
- Instead of slow `AsyncStorage`, should we use **`react-native-mmkv`** (Tencent MMKV—written in C++, 30x faster than AsyncStorage, synchronous read/write) for caching quiz state, user tokens, and active session drafts?

### 9. Voice Input (Speech-to-Text)
In `3rd.jpeg`, the bottom bar includes a voice button:
- **Option A:** On-device native speech recognition via **`@react-native-voice/voice`** (transcribes student speech directly to text on the phone).
- **Option B:** Record short `.m4a` audio clips with **`expo-av`** and send them to the backend Whisper endpoint for transcription.
*Which voice input method do you want?*

### 10. Styling Engine: NativeWind (Tailwind) vs. StyleSheet
- **Option A (NativeWind v4):** Write standard Tailwind CSS classes (`className="bg-card p-4 rounded-xl"`) in React Native, directly mapped to `tokens.json`.
- **Option B (Pure `StyleSheet.create`):** Write standard React Native style objects referencing a central theme token object.
*Which styling workflow do you prefer?*

### 11. Chat Stream Performance on Budget Phones (RAM & List Virtualization)
Students often use budget Android phones with 2GB–4GB RAM:
- Should the chat stream use **`@shopify/flash-list`** (5x faster recycling than standard `FlatList`, zero lag when scrolling 100+ message bubbles)?

### 12. Safe Area & Notch Insets
- Should the app use **`react-native-safe-area-context`** to guarantee that the top status bar, camera dynamic islands, and bottom Android navigation bars never clip the chat feed or bottom action bar?

### 13. Camera & Gallery Ingestion (`(+)` Button in `3rd.jpeg`)
For essay and handwritten response submissions:
- Should we integrate **`expo-image-picker`** allowing students to take a photo directly with the camera or pick an existing image from their photo library?

### 14. Tactile Touch Feedback (Haptics)
- Should the app use **`expo-haptics`** to trigger subtle physical vibrations on option selection (light impact) and topic mastery unlocks (success notification haptic)?

### 15. Offline Network State Detection
- Should the app use **`@react-native-community/netinfo`** to display a non-intrusive top banner when Wi-Fi/cellular connection drops, queuing quiz answers locally until reconnected?

### 16. Target Operating System Priority
- Is the primary target:
  - **Android first** (primary market for college/LAT test-takers in Pakistan)?
  - **iOS first**?
  - **Equal cross-platform parity** from Day 1?

### 17. Testing & Development Workflow
- During active local development, do you want to preview the app on your physical smartphone using the **Expo Go app** (scanning a QR code on your terminal), or via desktop Android/iOS emulators?

### 18. Standalone APK Generation
- For distributing the app to early beta testers:
  - Should the build pipeline support generating standalone **Android APKs** directly via **EAS Build** (`eas build -p android --profile preview`)?

### 19. Micro-Animations for Quiz Feedback
When a student taps an MCQ option:
- Should the green checkmark ripple and red horizontal shake be powered by **React Native Reanimated v3** to run smoothly on the UI thread at 60fps without JS thread stutter?

### 20. Code Splitting & Fast App Startup Time
- To guarantee the app boots in $< 1.5\text{ seconds}$ on low-end mobile devices:
  - Should heavy libraries (math view, image picker) be dynamically imported / lazy-loaded on demand?
