# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is **Adele Bergh Creativity** - a single-page Vue 3 portfolio website showcasing artwork and photography. Built with TypeScript, Vite, and Tailwind CSS. The project uses modern Vue tooling including Pinia for state management and Vue Router for navigation.

**Working Directory**: The main application code is located in `adeleberghcreativity/` subdirectory, not the repository root.

**Site Type**: Single-page application with smooth scroll navigation between sections.

## Development Commands

All commands should be run from the `adeleberghcreativity/` directory:

```bash
cd adeleberghcreativity
```

### Essential Commands

- **Development server**: `npm run dev` (starts Vite dev server on http://localhost:5173)
- **Build for production**: `npm run build` (runs type-check + vite build)
- **Build only** (skip type-check): `npm run build-only`
- **Type checking**: `npm run type-check`
- **Preview production build**: `npm run preview`

### Testing

- **Unit tests** (Vitest): `npm run test:unit`
- **E2E tests** (Playwright): `npm run test:e2e`
  - First time setup: `npx playwright install`
  - Run specific browser: `npm run test:e2e -- --project=chromium`
  - Debug mode: `npm run test:e2e -- --debug`

### Linting & Formatting

- **Lint (all)**: `npm run lint` (runs both oxlint and eslint in sequence)
- **Oxlint**: `npm run lint:oxlint` (fast linter with auto-fix)
- **ESLint**: `npm run lint:eslint` (comprehensive linting with auto-fix)
- **Format**: `npm run format` (Prettier)

## Architecture

### Tech Stack

- **Framework**: Vue 3.5+ (Composition API with `<script setup>`)
- **Language**: TypeScript 5.9
- **Build Tool**: Vite 7
- **Router**: Vue Router 4 with HTML5 history mode
- **State Management**: Pinia 3
- **Styling**: Tailwind CSS 4
- **Testing**: Vitest (unit) + Playwright (e2e)

### Project Structure

```
adeleberghcreativity/
├── src/
│   ├── main.ts              # App entry point (creates Vue app, mounts router & Pinia)
│   ├── App.vue              # Root component (renders RouterView)
│   ├── router/index.ts      # Route definitions (/ → HomeView)
│   ├── views/
│   │   └── HomeView.vue     # Main single-page view (integrates all sections)
│   ├── components/          # Page section components
│   │   ├── NavBar.vue       # Sticky navigation with smooth scroll
│   │   ├── HeroBanner.vue   # Hero section with logo and title
│   │   ├── AboutSection.vue # About section with bio
│   │   ├── PaintingGallery.vue  # Paintings gallery (Instagram ready)
│   │   ├── PhotosGallery.vue    # Photography gallery (Instagram ready)
│   │   └── FooterSection.vue    # Footer with links and copyright
│   ├── stores/              # Pinia stores
│   └── assets/              # Static assets (CSS, images, logos)
├── e2e/                     # Playwright end-to-end tests
├── public/                  # Public static files (logo.svg, icon.svg, favicon.ico)
└── dist/                    # Production build output (gitignored)
```

### Key Configuration Files

- **vite.config.ts**: Defines `@` alias pointing to `src/` directory, Vue DevTools plugin
- **tsconfig.json**: Project references for app, node, and vitest configs
- **eslint.config.ts**: Flat config with Vue, TypeScript, Vitest, Playwright, and Oxlint plugins
- **playwright.config.ts**: E2E testing against chromium, firefox, webkit; auto-starts dev server

### Single-Page Architecture

**Overview**: The site is a single-page application where all content sections are on one page with smooth scroll navigation.

**Page Sections** (in order from top to bottom):
1. **NavBar** - Fixed navigation that scrolls to sections
2. **HeroBanner** - Full-screen hero with logo, title, subtitle
3. **AboutSection** - Artist biography and profile image placeholder
4. **PaintingGallery** - Gallery skeleton ready for Instagram integration
5. **PhotosGallery** - Photography gallery skeleton ready for Instagram integration
6. **FooterSection** - Footer with social links and copyright

**Navigation Pattern**:
- Each section has an `id` attribute (`#hero`, `#about`, `#paintings`, `#photos`)
- NavBar uses `scrollToSection()` function for smooth scroll behavior
- Global `scroll-behavior: smooth` enabled in `main.css`
- NavBar becomes opaque with background when user scrolls (tracked via scroll event listener)

### Router Setup

- Uses `createWebHistory` for clean URLs (no hash)
- Home route (`/`) loads `HomeView` which contains all page sections
- Currently single-page; router ready for future multi-page expansion
- Base URL configured via `import.meta.env.BASE_URL`

### State Management

- Pinia stores are located in `src/stores/`
- Example counter store exists at `src/stores/counter.ts`
- Pinia instance is created and installed in `src/main.ts`

### Styling Approach

- Tailwind CSS 4 is configured with PostCSS
- Global styles in `src/assets/main.css` (full-width layout, smooth scrolling)
- Component styles use scoped `<style>` blocks with custom CSS
- Gradient backgrounds used for visual hierarchy:
  - Hero: Purple gradient (`#667eea` to `#764ba2`)
  - Footer: Matching purple gradient
  - About: Light gray gradient
  - Galleries: White and light gray backgrounds
- Fully responsive design with mobile-first approach
- Hover effects and transitions for interactive elements

### Instagram Integration (Future)

Both gallery components (`PaintingGallery.vue`, `PhotosGallery.vue`) are prepared for Instagram API integration:
- Empty state displays placeholder messaging
- `ref` arrays ready for data (`paintings`, `photos`)
- TODO comments marking integration points
- Grid layout prepared for image display
- Responsive gallery grid (3 columns desktop, 1 column mobile)

## Node Version Requirements

Node.js `^20.19.0` or `>=22.12.0` is required (specified in package.json engines).

## Testing Strategy

### Unit Tests (Vitest)
- Run in jsdom environment
- Test files: `src/components/__tests__/*.spec.ts`
- Excludes e2e directory

### E2E Tests (Playwright)
- Tests located in `e2e/` directory
- Automatically starts dev server before running tests
- Uses different ports/URLs for CI vs local (CI: 4173, local: 5173)
- Configured for parallel execution locally, sequential on CI
- Runs headless on CI only

## Import Aliases

- `@/` → `src/` directory (configured in vite.config.ts)
- Example: `import Component from '@/components/Component.vue'`

## Linting Architecture

This project uses a **two-stage linting** approach:

1. **Oxlint** (fast, correctness-focused): Catches critical errors quickly
2. **ESLint** (comprehensive): Full Vue/TypeScript linting with auto-fix

The `npm run lint` command runs both in sequence using `npm-run-all2`.

## Key Development Patterns

### Component Structure
- All page section components follow Vue 3 Composition API with `<script setup lang="ts">`
- Components are self-contained with scoped styles
- Each section component handles its own empty/loading states

### Navigation
- Use `scrollToSection(sectionId)` pattern for internal navigation
- Section IDs follow lowercase naming: `hero`, `about`, `paintings`, `photos`
- Scroll events cleaned up properly with `onUnmounted` lifecycle hook

### Assets
- Logo files in `public/` directory: `logo.svg` (full), `icon.svg` (compact), `favicon.ico`
- Reference public assets with absolute paths: `/logo.svg`, `/icon.svg`
- Main CSS imports base styles and Tailwind

### Responsive Design
- Mobile breakpoint: `768px`
- Desktop breakpoint: `1024px`
- Use `@media (max-width: 768px)` for mobile-specific styles
