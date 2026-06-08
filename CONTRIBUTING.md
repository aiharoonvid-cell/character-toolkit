# Contributing to Character Toolkit

Thanks for your interest in improving Character Toolkit! This document explains how to set up the project and submit changes.

## Code of Conduct

By participating you agree to uphold our [Code of Conduct](./CODE_OF_CONDUCT.md).

## Getting Started

1. **Fork** the repository and clone your fork.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run the test suite to confirm a clean baseline:
   ```bash
   npm test
   ```

## Development Workflow

- Source lives in `src/`, grouped by category (`analysis`, `transformation`, `statistics`, `extraction`, `encoding`, `validation`).
- Every public function must:
  - Be written in **TypeScript** with **strict mode** passing.
  - Validate its inputs and throw descriptive errors.
  - Include a complete **JSDoc** block with at least one `@example`.
  - Be exported from its category `index.ts` and re-exported from `src/index.ts`.
  - Ship with **unit tests** in `tests/`.

Useful scripts:

| Command | Description |
| --- | --- |
| `npm test` | Run the Vitest suite once. |
| `npm run test:watch` | Run tests in watch mode. |
| `npm run test:coverage` | Generate a coverage report. |
| `npm run typecheck` | Type-check without emitting. |
| `npm run lint` | Lint the source and tests. |
| `npm run build` | Compile to `dist/`. |
| `npm run bench` | Run benchmarks. |

## Commit & PR Guidelines

- Keep PRs focused and small where possible.
- Write clear commit messages (Conventional Commits encouraged: `feat:`, `fix:`, `docs:`, `test:`, `chore:`).
- Add or update tests and docs alongside code changes.
- Ensure `npm test`, `npm run typecheck`, and `npm run lint` all pass before opening a PR.

## Adding a New Function

1. Implement it in the relevant `src/<category>/` file with JSDoc.
2. Export it from the category `index.ts`.
3. Add tests in the matching `tests/*.test.ts`.
4. Document it (update the README API table and add to `docs/` if it maps to a tool).

## Reporting Bugs

Open an issue with a minimal reproduction, expected vs. actual behavior, and your environment (Node version, OS).

Thank you for contributing! 🎉
