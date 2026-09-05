<div align="center">

  <a href="https://typoscale.vercel.app/">
    <img src="https://raw.githubusercontent.com/bilalmlkdev/typoscale/main/src/assets/logo.svg" alt="typoscale Logo" width="100%" height="120">
  </a>

# Typoscale

  A modern, open-source type scale generator for designers and developers,
  generate <br> harmonious typography systems, pair Google Fonts, and export
  production-ready CSS & Tailwind tokens from one fast browser-based workspace.

[![Live Demo](https://img.shields.io/badge/Live_Demo-Visit_Site-black?style=for-the-badge)](https://typoscale.vercel.app)
[![GitHub Stars](https://img.shields.io/github/stars/bilalmlkdev/typoscale?style=for-the-badge&logo=github&color=yellow)](https://github.com/bilalmlkdev/typoscale.git)

</div>

<p align="center">
  <i>Created by <a href="https://bilalmlkdev.vercel.app" target="_blank">Bilal Malik</a></i><br>
  <i>Follow on Github <a href="https://github.com/bilalmlkdev" target="_blank">bilalmlkdev</a></i>
</p>

[![typoscale Dashboard](https://raw.githubusercontent.com/bilalmlkdev/typoscale/main/src/assets/preview.png)](https://typoscale.vercel.app/)


# What is TypoScale?

TypoScale is an open-source type scale generator built for designers and developers creating modern design systems.

Choose a base font size, select a modular ratio, pair Google Fonts, preview typography in real time, and export production-ready tokens for CSS, Tailwind CSS, or Style Dictionary.

Unlike traditional font-size calculators, TypoScale combines modular scaling, responsive typography, WCAG contrast checking, and live editorial previews into a single workflow - and it runs entirely in your browser, with no server-side processing or tracking.

# Features

| Category | Highlights |
|-----------|------------|
| **Type Scale Generation** | Modular ratios, custom scales, independent steps, and instant px/rem conversion |
| **Font Pairing** | Browse 1000+ Google Fonts with dedicated Display, Body, and Monospace selectors |
| **Live Preview** | Responsive editorial preview with WCAG AA/AAA accessibility indicators |
| **Token Export** | Export typography tokens as CSS Variables, Tailwind CSS v3/v4, or Style Dictionary JSON |
| **Shareable State** | Every configuration syncs to the URL, so any scale is bookmarkable and shareable |
| **Themes** | Dark and light presentation, switchable without losing your current scale |
| **Utilities** | Fluid `clamp()` generation, preset management, import/export, and session persistence |

# Architecture

TypoScale follows one principle: every typography calculation should be deterministic, predictable, and completely independent from the UI.

**Calculations are pure functions, the UI just renders them.** All scale math, font-pairing logic, and token generation live in `src/utils/` as functions with no React or DOM dependency - given the same base size, ratio, and steps, they always produce the same output. The React layer's only job is displaying that output and reacting to input.

**State lives in Zustand, synced to the URL.** The current scale, selected fonts, and export format are held in a Zustand store and mirrored to URL query parameters on every change. That's what makes every configuration shareable as a plain link, with no save button or backend involved.

## Adding a New Scale Ratio

Register it in `src/types/scale.ts`:

```ts
newRatio: {
  label: "New Ratio",
  value: 1.618,
}
```

## Adding a New Export Format

Implement a new generator function in `src/utils/tokenGenerators.ts`. Once it's added there, it appears in the export panel automatically - no other file needs to change.

# Project Structure

```
typoscale
├── public
├── src
│   ├── assets          preview images, icons, static resources
│   ├── components       controls, previews, font pickers, token output
│   ├── hooks             font loading, typography generation, clipboard
│   ├── store              Zustand state + URL sync + local persistence
│   ├── types               shared TypeScript interfaces and models
│   ├── utils                scale math, token generation, WCAG contrast
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── package.json
├── vite.config.ts
└── tsconfig.json
```

# Design Principles

| Principle | Description |
|-----------|-------------|
| Deterministic Calculations | Identical inputs always produce identical output |
| Pure Functions | Typography logic stays fully independent from the UI |
| Client-Side First | Everything runs locally, no backend processing |
| Shareable State | URL parameters preserve and share full configurations |
| Data-Driven UI | Scales and export formats are generated from shared config, not hardcoded |

# Performance

Memoized scale generation (`useMemo`), debounced URL sync, shared font/ratio registries loaded once, local preference persistence, and zero network requests during calculation.

# Tech Stack

TypoScale is built using a modern frontend stack focused on performance and developer experience.

<p align="left">
  <img src="https://skillicons.dev/icons?i=react,vite,tailwind,ts,zustand,vercel" />
</p>

Also uses **Lucide React** for icons and **PrismJS** for token code highlighting.

# Getting Started

## Prerequisites

- Node.js 18 or later

## Installation

Clone the repository and move into it.

```bash
git clone https://github.com/bilalmlkdev/typoscale.git
cd typoscale
```

Install dependencies and start the dev server.

```bash
npm install
npm run dev
```

Optionally, create a `.env.local` file and add `VITE_GOOGLE_FONTS_KEY` to unlock the complete Google Fonts library instead of the default curated subset.

# Token Output

TypoScale generates production-ready typography tokens in multiple formats: CSS Custom Properties, Tailwind CSS v3, Tailwind CSS v4, or Style Dictionary JSON.

```css
:root {
  --font-size-base: 1rem;
  --font-size-lg: 1.333rem;
  --font-size-xl: 1.777rem;
}
```

Copy or download the generated tokens and use them directly in your design system.

# Usage

1. Pick a base font size and a modular ratio - or define a fully custom scale.
2. Choose Display, Body, and Monospace fonts from the Google Fonts picker.
3. Check the live editorial preview and its WCAG AA/AAA contrast indicators.
4. Switch export format to CSS, Tailwind v3/v4, or Style Dictionary JSON.
5. Copy or download the tokens, or copy the URL to share the exact configuration.

If the font picker only shows a small curated list, you're missing `VITE_GOOGLE_FONTS_KEY` - add it to `.env.local` to unlock the full Google Fonts catalog.

# Contributing

Contributions of every size are welcome.

```bash
git checkout -b feat/my-feature
npm run lint
npm run type-check
```

Please follow Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `style:`, `chore:`. After pushing your branch, open a pull request against `main`.


# License (MIT)

This project is licensed under the MIT License.

```
MIT License

Copyright (c) 2026 Bilal Malik

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software. The above copyright notice and this permission notice shall
be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

