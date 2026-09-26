# Frontend architecture

Next.js App Router, React, strict TypeScript, Tailwind CSS 4 with shared CSS design tokens, Lucide icons, Recharts, and Zod runtime validation.

`Pulsepoint` owns navigation and the huddle collection. Component state keeps unsent question and response text; navigation is a small in-app state machine. It is intentionally not a multi-route dashboard. Completed/pending huddles reopen from the workspace. A page reload returns to the home screen and restores demo history from session storage.

`QuestionInput` and `ExpertResponse` use the shared voice hook. Browser recognition is feature-detected, cleaned up on unmount, and replaced by a visible typed-input fallback when unsupported. No audio recordings are persisted. `HuddleBrief` provides text download, copy, and synthetic playback. `QuestionGraph` uses a fixed synthetic dataset and a native accessible specialty filter and table.

`huddleApi` chooses the demo implementation unless live mode is explicitly configured. Zod validates external responses. API failures are shown to the user. Demo fallback is explicit and labeled. No credentials or external AI calls exist in this frontend.

Responsive breakpoints: full sidebar, compact rail, then mobile bottom navigation. Focus moves to the page heading after in-app navigation. Native dialog semantics, Escape dismissal, focus outlines, reduced-motion support, semantic form labels, and non-color status text are included.
