# Frontend Lab

> An advanced, hands-on frontend learning path: notes, exercises, and production-grade projects covering HTML, CSS, JavaScript, TypeScript, React, performance, testing, and architecture.

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-in%20progress-orange)
![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

<!-- Add the CI badge once .github/workflows/ci.yml exists:
![CI](https://github.com/yashvardhansingh442-dev/Frontend-Lab/actions/workflows/ci.yml/badge.svg)
-->

---

## Table of Contents

- [About](#about)
- [Who This Is For](#who-this-is-for)
- [How to Use This Repo](#how-to-use-this-repo)
- [Progress Dashboard](#progress-dashboard)
- [Featured Projects](#featured-projects)
- [Repository Structure](#repository-structure)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Related Repositories](#related-repositories)
- [Contributing](#contributing)
- [License](#license)

---

## About

This repository is my public record of learning frontend engineering in depth. It serves two purposes:

1. **Learning:** structured notes, runnable examples, and exercises for each topic, written in my own words.
2. **Showcase:** real projects built with the concepts, each with a live demo, architecture notes, and tests.

The goal is to go beyond "how to use a framework" and understand how the browser, the language, and the tools actually work.

## Who This Is For

- **Beginners to intermediate learners** who want an ordered path instead of scattered tutorials.
- **Developers moving into frontend** from other fields.
- **Recruiters and collaborators** who want to see how I learn, build, and document.

## How to Use This Repo

1. Start at `curriculum/` and work through the modules **in order**.
2. In each topic folder, read the `README.md` first, then run the `examples/`.
3. Try the `exercises/` **before** looking at `solutions/`.
4. Build the matching project in `apps/` to apply what you learned.
5. Read `pitfalls.md` in each topic to avoid common mistakes.

> Tip: star or watch the repo to follow along as new topics are added.

---

## Progress Dashboard

Legend: ✅ complete | 🚧 in progress | ⬜ not started

| # | Track | Status |
|---|-------|--------|
| 00 | Foundations (browser, HTTP, security, DevTools) | ✅ |
| 01 | HTML and Accessibility | ✅ |
| 02 | Advanced CSS | 🚧 |
| 03 | JavaScript Deep Dive | ⬜ |
| 04 | TypeScript | ⬜ |
| 05 | React Advanced | ⬜ |
| 06 | Meta-Frameworks (Next.js) | ⬜ |
| 07 | State and Data Management | ⬜ |
| 08 | Architecture and System Design | ⬜ |
| 09 | Performance | ⬜ |
| 10 | Testing | ⬜ |
| 11 | Tooling and DevOps | ⬜ |
| 12 | Security and Auth | ⬜ |
| 13 | Advanced Topics (WASM, WebGL, PWA, i18n) | ⬜ |

---

## Featured Projects

| Project | Description | Skills Demonstrated | Demo |
|---------|-------------|---------------------|------|
| Portfolio Site | Personal site with MDX blog | Next.js, SEO, Lighthouse 95+ | _coming soon_ |
| Design System Docs | Component library with Storybook | Accessibility, theming, testing | _coming soon_ |
| Kanban Board | Drag and drop task board | Optimistic UI, undo/redo | _coming soon_ |
| Realtime Chat | Multi-user chat | WebSockets, presence | _coming soon_ |
| Analytics Dashboard | Charts and large tables | Virtualization, URL state | _coming soon_ |
| E-commerce Storefront | Cart and checkout | SSR, payments (test mode) | _coming soon_ |
| Offline Notes PWA | Works without internet | Service workers, IndexedDB | _coming soon_ |
| Full-Stack Capstone | End-to-end app | Connects to my backend repo | _coming soon_ |

Each project has its own README with screenshots, setup steps, and an `ARCHITECTURE.md` explaining the decisions made.

---

## Repository Structure

```
Frontend-Lab/
├── curriculum/    # Written lessons, module by module
├── apps/          # Deployable showcase projects
├── packages/      # Shared code: ui, hooks, utils, api-client
├── labs/          # Experiments: mini-React, mini-router, state library
├── tooling/       # Shared ESLint, TypeScript, Prettier, Vitest configs
├── resources/     # Curated books, courses, and references
└── .github/       # CI workflows and templates
```

---

## Tech Stack

| Area | Tools |
|------|-------|
| Language | JavaScript (ES2023+), TypeScript |
| Framework | React, Next.js |
| Styling | CSS (modern), Tailwind CSS, CSS Modules |
| State and Data | Zustand, Redux Toolkit, TanStack Query |
| Forms and Validation | React Hook Form, Zod |
| Testing | Vitest, React Testing Library, Playwright, axe |
| Tooling | Vite, ESLint, Prettier, Husky, pnpm, Turborepo |
| CI/CD | GitHub Actions, Vercel |

_This list reflects the end goal. Items are added as I reach each track._

---

## Getting Started

### Prerequisites

- Node.js 20 or later
- pnpm 9 or later (`npm install -g pnpm`)
- Git

### Setup

```bash
# Clone the repository
git clone https://github.com/yashvardhansingh442-dev/Frontend-Lab.git
cd Frontend-Lab

# Install dependencies for all packages
pnpm install

# Run one project
pnpm --filter <app-name> dev

# Run tests
pnpm test

# Lint and typecheck
pnpm lint
pnpm typecheck
```

> The monorepo tooling (pnpm workspaces, Turborepo) is introduced once there are multiple projects. Until then, each project can be run on its own with `npm install` and `npm run dev`.

---

## Related Repositories

- **Backend Mastery** (coming soon): the matching backend learning path, used by the full-stack capstone.
- **LEETCODE_DSA**: data structures and algorithms practice.

---

## Contributing

Contributions are welcome, especially:

- Fixing errors or unclear explanations
- Suggesting topics or resources
- Reporting broken examples

Please read [CONTRIBUTING.md](./CONTRIBUTING.md) before opening a pull request.

---

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE) for details.

---

## Connect

- GitHub: [@yashvardhansingh442-dev](https://github.com/yashvardhansingh442-dev)

If this repo helps you learn, consider giving it a star.
