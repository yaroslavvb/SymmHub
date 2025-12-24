# SymmHub Agent Rules (`gemini.md`)

## 1. Coding Standards & Constraints

- **Prohibited APIs:** Do not use `innerHTML` for creating or updating user interface elements, as it reduces readability and maintainability within this architecture.

## 2. Architectural Context

- **Rendering pipeline:** The core loop is driven by `requestAnimationFrame` and a `needToRepaint` flag. Render frames only when this flag is truthy to conserve resources.
- **Asynchronous data loading:** The `setDocumentData` function and texture loading processes are asynchronous. Ensure these processes complete, or wait for a confirmed “finished loading” state, before performing tests or screen captures.
- **Uniforms:** Time-based animations rely on the `uTime` uniform passed to GPU programs.

## 3. Testing & Verification Protocols

- **Regression testing:** For visual verification, create a specialized standalone HTML test page (e.g., `verify_presets.html`).
- **Ground truth comparison:** Compare WebGL canvas outputs against the existing ground-truth PNGs located in the `presets/` folders.
- **Deterministic rendering:** When testing, refactor calls to accept explicit time and canvas parameters to ensure deterministic, bit-for-bit consistency across different hardware.

## 4. Operational Instructions for the Agent

- **Linting policy:** Disable auto-linting during logic implementation. Do not perform any linting or stylisting changes to any existing lines of code unless a change in functionality is required from those lines of code
- **Task management:** Actively scan the codebase for `// TODO AI:` comments and prioritize them as the primary task list.
- **Specificity:** Do not accept generic prompts such as “fix the button.” Request or use specific component names, for example, “update the toggle component in `sim_renderer.js`.”
