# Repository Guidelines

## Project Structure & Module Organization
- Theme lives in `2077terminal.user.css`; metadata block at the top is consumed by Stylus/userstyle managers.
- Everything is scoped via `@-moz-document url-prefix("https://chatgpt.com/")` to avoid leaking styles to other sites.
- No build artifacts, compiled assets, or test directories are present; edits go directly into the CSS file.

## Design of the Theme
- The theme is a fake terminal theme for chatgpt.
  - The user's cursor should be a fat caret
  - Input bar blends in with the chat interface
  - ChatGPT's output is made to look like any output on a terminal
  - The user's chats look like fired off commands
  - There is limited to no usage of gradients
  - The chatgpt sidebar where previous chats, search bar, organization bubble is represented as if its a TUI.
- There are some futuristic/cyberpunk/sci-fi elements in-play, but ultimately its a realistic terminal. Think: How would a show like Mr. Robot represent a terminal to its viewers?

## Build, Test, and Development Commands
- There is no build pipeline; the CSS is the source of truth.

## Coding Style & Naming Conventions
- Indent with four spaces; keep property ordering logical (variables, layout, color, effects).
- Prefer CSS custom properties over literals; existing palette uses OKLCH values (`--bg`, `--text`, `--primary`, etc.)—extend these instead of adding new color tokens when possible.
- Scope selectors narrowly (e.g., `[data-message-author-role="assistant"]`) to reduce regressions; avoid global tags unless intentional. Choose selectors carefully so that we minimize the chance of the theme breaking.
- Use concise block comments to mark sections (messages, bubbles, code blocks) and keep related declarations together. Always make the comments human readable so the developer can recognize what blocks are for what UI elements

## Testing Guidelines
- No automated tests; rely on manual verification in the browser.
- Validate key scenarios: user and assistant bubbles, inline and fenced code blocks, hover/focus states, and responsiveness at ≥900px and mobile widths.

## Commit & Pull Request Guidelines
- Repository has no commit history; default to short, imperative messages (e.g., `tune-assistant-bubble`, `adjust-code-block-header`).
- Prefer small, focused commits and PRs with a brief summary of visual changes and before/after screenshots or screen recordings.
- Note any selector scope changes or new variables in the PR description so reviewers can spot potential breakage areas.
