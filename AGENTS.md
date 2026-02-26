# AGENTS.md

This document provides operational guidance for autonomous coding agents working in this repository.

Project overview:
- Tooling: Parcel v2
- Language: Vanilla JavaScript (no framework)
- Styling: Bootstrap 5 + custom CSS
- Entry point: `src/index.html`
- Output: `dist/`

There is currently no test framework or linter configured.

---------------------------------------------------------------------
Build, Dev, and Preview Commands
---------------------------------------------------------------------

Install dependencies:

```
npm install
```

Start development server (with HMR, no cache):

```
npm run start
```

This runs:

```
parcel --no-cache
```

Production build:

```
npm run build
```

This runs:

```
parcel build
```

Build artifacts are emitted into `dist/`.

---------------------------------------------------------------------
Testing
---------------------------------------------------------------------

There is currently:
- No unit test framework
- No integration test setup
- No end-to-end tests
- No test scripts in `package.json`

If tests are added in the future, prefer:
- Unit tests: Vitest or Jest
- DOM testing: Testing Library

Recommended future single-test pattern (Vitest example):

```
npx vitest run path/to/file.test.js
```

Or for a single test name:

```
npx vitest run -t "test name"
```

Do not assume a test runner exists unless explicitly added to `package.json`.

---------------------------------------------------------------------
Linting and Formatting
---------------------------------------------------------------------

There is currently:
- No ESLint configuration
- No Prettier configuration
- No formatting scripts

Agents should:
- Follow consistent formatting manually
- Avoid introducing stylistic inconsistencies
- Keep diffs minimal and intentional

If introducing ESLint or Prettier, update `package.json` and document commands here.

---------------------------------------------------------------------
Project Structure
---------------------------------------------------------------------

```
src/
  index.html      # Application entry
  index.js        # Main JavaScript
  style.css       # Custom styles

dist/             # Generated build output (do not edit)
```

Rules:
- Never edit files inside `dist/`
- Never commit `.parcel-cache/`
- Treat `node_modules/` as read-only

---------------------------------------------------------------------
JavaScript Conventions
---------------------------------------------------------------------

General:
- Use modern ES syntax (ES2015+)
- Prefer `const` over `let`
- Avoid `var`
- Use strict equality (`===`)
- Prefer early returns over nested conditionals

Modules:
- Use ES modules (`import` / `export`) if splitting files
- Keep imports at the top of the file
- Avoid circular dependencies

Naming:
- camelCase for variables and functions
- PascalCase for classes
- UPPER_SNAKE_CASE for constants
- Use descriptive names (avoid single-letter identifiers)

Functions:
- Keep functions small and focused
- Avoid side effects unless clearly intended
- Prefer pure functions where possible

Error Handling:
- Use `try/catch` for async logic where needed
- Fail fast with clear error messages
- Do not silently swallow errors

Async:
- Prefer `async/await` over `.then()` chains
- Always handle rejected promises

DOM Manipulation:
- Query DOM once and reuse references
- Avoid unnecessary reflows
- Prefer event delegation for repeated elements

---------------------------------------------------------------------
HTML Guidelines
---------------------------------------------------------------------

- Keep structure semantic (`header`, `main`, `section`, `footer`)
- Avoid inline styles
- Avoid inline JavaScript
- Keep Bootstrap usage consistent
- Ensure accessibility basics (alt text, labels, button types)

---------------------------------------------------------------------
CSS Guidelines
---------------------------------------------------------------------

- Prefer class selectors over IDs
- Avoid overly specific selectors
- Group related styles together
- Keep custom styles separate from Bootstrap overrides when possible
- Avoid `!important` unless absolutely necessary

---------------------------------------------------------------------
Bootstrap Usage
---------------------------------------------------------------------

- Use Bootstrap utility classes before writing custom CSS
- Do not modify Bootstrap source files
- Override via `style.css` only when necessary
- Keep layout responsive (mobile-first)

---------------------------------------------------------------------
Static Web Apps CLI
---------------------------------------------------------------------

Dev dependency:
- `@azure/static-web-apps-cli`

If running Azure SWA locally (example):

```
npx swa start dist
```

Only use this if Azure Static Web Apps integration is required.

---------------------------------------------------------------------
Git and Change Discipline
---------------------------------------------------------------------

- Do not modify unrelated files
- Do not reformat entire files unnecessarily
- Keep commits focused and atomic
- Do not commit generated assets unless explicitly required

---------------------------------------------------------------------
Agent Operating Principles
---------------------------------------------------------------------

- Read existing code before modifying it
- Match existing style and structure
- Prefer minimal, clear solutions
- Do not introduce heavy dependencies without justification
- If adding tooling (tests, lint, formatter), update this file

There are no Cursor rules or Copilot instructions present in this repository.
