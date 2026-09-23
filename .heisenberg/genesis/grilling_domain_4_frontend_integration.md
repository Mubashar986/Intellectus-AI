# ⚗️ Grilling Domain 4: Frontend Integration Perspective (PENDING USER REVIEW)
### Feynman Adaptive Engine (AI Tayyari Hub) — Stage 0 Baseline

> [!IMPORTANT]
> This domain is OPEN and PENDING USER REVIEW. No assumptions are locked until the user explicitly decides on each question.

---

### 1. Framework & Bundler Selection
To deliver a responsive, mobile-first web app with fast navigation and clean drawers:
- **Option A (Next.js 14 / App Router + TypeScript):** Server components, built-in API routes, optimal SSR/SEO if needed.
- **Option B (Vite + React 19 + TypeScript):** Pure client SPA, ultra-fast HMR, zero server complexity, easily bundled for PWA or desktop Electron/Tauri.
- **Option C (Other):** Nuxt / SvelteKit / Remix?
*Which frontend framework do you choose?*

### 2. Client State Management Architecture
The client must coordinate the active topic, question batch index, quiz selections, drawer states, and user credits:
- What state management library do you prefer? (Zustand, Jotai, Redux Toolkit, or simple React Context)?

### 3. Component Architecture for Interactive Widgets
In `3rd.jpeg` and `WhatsApp Image`, the chat stream contains text, equations, quiz cards, flashcards, and result modals:
- How should the chat feed render these?
  - Should the stream parser detect widget tags in the response payload and mount dedicated React components (`<QuizCard />`, `<FlashCard />`, `<ResultModal />`, `<EquationBlock />`)?

### 4. Mathematical Equation Rendering (KaTeX vs. MathJax)
For STEM topics and LAT elementary math:
- Should we use **KaTeX** (instant client-side math rendering, sub-10ms, tiny bundle footprint) over MathJax?

### 5. Mobile Virtual Keyboard Collision Handling
In `3rd.jpeg`, you explicitly noted: *“responsive page based on keyboard - make sure it does hide near and LLM response completely.”*
- Should the frontend use the modern `window.visualViewport` API and CSS dynamic viewport units (`height: 100dvh`) to guarantee the chat feed automatically scrolls the active question above the virtual keyboard when typing?

### 6. Progressive Web App (PWA) & Offline Shell
- Should the frontend include `manifest.json` and a Service Worker so students on Android and iOS can tap "Install App" and run the application full-screen with zero browser URL bar distractions?

### 7. Voice / Text-to-Speech (TTS) Integration (`3rd.jpeg`)
In your wireframe bottom bar, you drew a `voice button -> TTS system`:
- Should TTS voice output be deferred for Phase 1 (focusing on voice input), or do you want the browser's Web Speech API to read aloud explanations?

### 8. Speech-to-Text (Voice Input)
- Does the voice button allow the student to **speak their answer** via the browser's `webkitSpeechRecognition` API instead of typing on a mobile keyboard?

### 9. Mobile Slide-Out Drawer Component
In `3rd.jpeg`, you drew a responsive hamburger drawer showing chat/iteration history:
- Should the drawer support native touch swipe-to-close gestures (using libraries like **Vaul** or Framer Motion)?

### 10. The Progress Modal Component
In `WhatsApp Image`, tapping the progress bar opens a detailed modal:
- On mobile, should this render as a smooth **Bottom-Sheet Drawer** (sliding up from the bottom of the screen) rather than a centered popup dialog?

### 11. Clipboard & Message Actions
You drew `edit and clipboard` and `feedback hands` on message bubbles:
- Tapping copy writes clean text (or quiz question + explanation) to the device clipboard with a transient toast (*"Copied to clipboard"*). What should the "edit" icon do (edit the user's prior message and re-run)?

### 12. Feedback Telemetry Hook
- When a user taps thumbs-up or thumbs-down on a coach explanation, does the frontend emit an event to `POST /api/v1/telemetry/feedback` to log question ratings for future review?

### 13. Dynamic Stream Chunk Parsing
When an LLM response streams word-by-word via SSE:
- How does the frontend render incomplete markdown or KaTeX formulas without flickering or breaking syntax while the token stream is still arriving?

### 14. Network Offline Detection & Reconnection
If a student's mobile internet cuts out during a quiz:
- Should the UI display an offline banner and automatically queue answers in IndexedDB/localStorage, syncing when the connection is restored?

### 15. The `(+)` Action Modal Trigger (`3rd.jpeg`)
In the bottom bar, you drew a `(+)` button labeled: *“automatically file picker start new iteration modal.”*
- What exact menu options appear when a user taps this `(+)` button?
  - Start New Topic Iteration?
  - Upload Reference PDF / Image?
  - Change Difficulty Level?
  - Switch Subject?

### 16. Flashcard Component Interaction
When a flashcard appears in Stage E (Rapid Recall):
- Does the user tap to flip the card (revealing the memory hook / rule on the back), with "Got It" vs "Study Again" buttons?

### 17. Client-Side Bundle Sizing & Performance Targets
- To ensure fast loading on 3G/4G mobile connections across colleges, what is the initial JavaScript bundle budget? (Target: $< 150\text{KB}$ gzipped).

### 18. Theme Token Architecture (The Muses Integration)
Under Heisenberg OS **Rule 02 (Law 10)**:
- All UI colors, border radii, and spacing must map to CSS custom properties from `tokens.json` (zero raw hex codes). Are you comfortable with this token architecture?

### 19. Audio Playback Controls
If audio explanation is active:
- Should the UI display a floating audio player bar (Play/Pause, 1.25x speed, 10s skip) at the bottom of the screen?

### 20. Code Splitting for Heavy Modules
- Should KaTeX math, audio synthesizers, and essay text editors be dynamically imported (`React.lazy()`) so students only download code for the features they are actively using?
