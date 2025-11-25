<!-- Copilot / AI agent instructions for the Css_DailyLearning repo -->
# Copilot instructions — Css_DailyLearning

This repository is a small HTML/CSS learning playground (daily practice files). The guidance below helps an AI coding agent be productive quickly and avoid incorrect assumptions.

Core repo shape
- `day1.html`, `day2.html` — single-file examples with inline `<style>` blocks.
- `Day-3/`, `Day-4/` — directories containing similar single-page examples (`day3.html`, `task.html`).
- `image/` — static assets (e.g., `image/ice.jpg`).

What the project is for
- Purpose: learning and experimenting with basic CSS rules. There is no build system, framework, or tests. Changes are expected to be small edits to HTML/CSS.

Key patterns and project-specific notes
- Styles live in page-local `<style>` blocks (not external CSS). When editing, update the `<style>` block inside the same `.html` file unless the user explicitly requests extracting a stylesheet.
- Class names often reflect the day or example (e.g., `.day1`, `.three`, `.task`, `.img`). Keep naming consistent with the existing pattern when adding similar examples.
- Image paths: some files use `background-image: url('/image/ice.jpg');` (leading slash). When previewing by opening the file directly in a browser, a leading slash resolves to filesystem root and may break. Prefer either:
  - repository-root relative paths without a leading slash: `image/ice.jpg`, or
  - running a simple local HTTP server so leading-slash paths resolve to repo root.

How to run / preview locally (developer workflows)
- Quick preview (no server): open the `.html` file directly in the browser (double-click the file). Adjust image paths if they rely on a web server.
- Recommended (server preview): run a local HTTP server at the repository root so URLs like `/image/ice.jpg` work as intended.
  - With Python (PowerShell):
    - `python -m http.server 8000` (then open `http://localhost:8000/Day-4/day3.html`)
  - VS Code: use the Live Server extension and point it at the repository root.

Common edits you may be asked to perform
- Fix broken asset paths: change `url('/image/ice.jpg')` -> `url('image/ice.jpg')` or advise running a local server.
- Convert inline styles to an external stylesheet only when the user requests extraction; otherwise prefer minimal, focused edits inside the file.
- Make CSS changes that preserve the page-local structure (i.e., avoid introducing global toolchains).

Examples (explicit references)
- To preview `Day-4/day3.html` with image working, either:
  - Replace `background-image: url('/image/ice.jpg');` with `background-image: url('image/ice.jpg');` and open the file, or
  - From repo root run `python -m http.server 8000` and open `http://localhost:8000/Day-4/day3.html`.
- Class naming example: if adding a new sample for day 5, prefer `Day-5/day5.html` and a class like `.day5` to match existing convention.

Repository constraints and things not to assume
- No package manager files (no `package.json`, no `requirements.txt`) — do not add dependency-based tooling unless the user asks.
- No automated tests or CI configured. Keep changes minimal and human-reviewable.

When to open a discussion with the user
- If a change requires adding a build step, external dependency, or restructuring into multiple files, ask before making the change.
- If an image path uses an absolute web-root path (leading `/`), confirm whether the user will preview with a local server.

Where to look for examples
- `Day-4/day3.html` — background image usage and `background-size: contain` pattern.
- `Day-3/task.html` — letter-spacing / line-height examples and use of `display:flex` for simple text blocks.

If the user asks for commits
- Keep each change small and focused; include the modified file path in the commit message (e.g., `Update Day-4/day3.html — fix image path`).

If anything in this document is unclear or you want additional examples (e.g., extracting a stylesheet or previewing with Live Server), ask the user before applying larger refactors.
