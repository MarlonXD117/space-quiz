# Copilot instructions

## Project shape

Órbita is a standalone Spanish-language space-exploration quiz. The app lives in `index.html`: semantic page markup, all CSS in a `<style>` block, quiz data and state/rendering logic in a `<script>` block. It runs directly as a local file and has no server, framework, package manifest, or external runtime dependency.

The script keeps the question bank in `questions` and the current position, score, and answered state in module-level variables. `renderQuestion()` builds the answer buttons from the current data; `chooseAnswer()` locks answers, updates score and progress, and shows feedback; `showResult()` selects the final reaction; `restart()` resets the quiz. Keep these transitions consistent when changing the quiz flow.

## Build, test, and lint

There are no configured build, test, or lint commands. Open `index.html` directly in a browser to run the app. For a manual smoke test, answer questions correctly and incorrectly, advance through all ten, confirm the score and result screen, then restart.

## Project conventions

- Keep the app self-contained in `index.html`; do not add a server or dependency for features that can remain native to the page.
- Keep visible copy in Spanish. JavaScript identifiers and CSS selectors are in English.
- Each question has a `question`, four `options`, a zero-based `answer` index, and an `explanation`. Update those together when adding or editing quiz content.
- Theme colors are CSS custom properties in `:root`, with dark-mode overrides in `@media (prefers-color-scheme: dark)`. Use these tokens for new UI so both themes remain consistent.
- Preserve native button interactions and visible focus; progress uses a labeled `progressbar`, feedback uses a live status region, and the result/restart flow manages focus. Respect `prefers-reduced-motion` when adding animation.
- Keep answer states distinct: selection is tracked with `aria-pressed`, and correct/incorrect feedback is shown through the matching state classes and theme tokens.
