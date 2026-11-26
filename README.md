<div align="center">

# Spektra

**A colour-first CSS framework.** 45 hues, 495 shades, fluid type, container queries, and one class that recolours everything.

<br/>

[![npm](https://img.shields.io/npm/v/spektra-css?style=for-the-badge&color=1f5fd6&logo=npm&logoColor=white)](https://www.npmjs.com/package/spektra-css)
[![License](https://img.shields.io/github/license/MeViksry/spektra?style=for-the-badge&color=2563eb)](LICENSE)
[![Stars](https://img.shields.io/github/stars/MeViksry/spektra?style=for-the-badge&logo=github&color=f59e0b)](https://github.com/MeViksry/spektra/stargazers)
[![Issues](https://img.shields.io/github/issues/MeViksry/spektra?style=for-the-badge&color=ef4444)](https://github.com/MeViksry/spektra/issues)

![Hues](https://img.shields.io/badge/hues-45-d946ef?style=for-the-badge)
![Shades](https://img.shields.io/badge/shades-495-8b5cf6?style=for-the-badge)
![Gzip](https://img.shields.io/badge/gzip-42%20KB-10b981?style=for-the-badge)
![JS](https://img.shields.io/badge/JS-optional%203%20KB-eab308?style=for-the-badge&logo=javascript&logoColor=black)
![Sass](https://img.shields.io/badge/Sass-1.79%2B-cc6699?style=for-the-badge&logo=sass&logoColor=white)

<br/>

[![Features](https://img.shields.io/badge/-Features-1f2937?style=flat-square)](#features)
[![Install](https://img.shields.io/badge/-Install-1f2937?style=flat-square)](#install)
[![Colour](https://img.shields.io/badge/-Colour%20system-1f2937?style=flat-square)](#colour-system)
[![Responsive](https://img.shields.io/badge/-Responsive-1f2937?style=flat-square)](#responsive)
[![Components](https://img.shields.io/badge/-Components-1f2937?style=flat-square)](#components)
[![Customise](https://img.shields.io/badge/-Customise-1f2937?style=flat-square)](#customise)
[![JS](https://img.shields.io/badge/-JavaScript-1f2937?style=flat-square)](#javascript)

</div>

<br/>

## Features

- **One class recolours a subtree.** `<section class="c-teal">` makes every button, badge, switch, tab and focus ring inside it teal. No per-component colour classes.
- **The whole spectrum built in.** 45 hues, each with 11 shades (50 to 950), as CSS variables and utilities. Add your own hue and it gets the same treatment.
- **Accessible by default.** The text colour on solid fills is picked at build time, so buttons and badges at rest reach a 4.5:1 contrast ratio.
- **Dark mode without a second stylesheet.** Tokens use `light-dark()`, so the page follows the OS, a `data-theme` attribute, or both, and any single element can be themed on its own.
- **Responsive in the CSS, not just the breakpoints.** Fluid type scale, intrinsic containers, auto-fit grids, container queries, tables that become cards on phones, modals that become bottom sheets.
- **Built for notched screens.** `env(safe-area-inset-*)` is built into the navbar and toasts, with `pt-safe`, `pb-safe` and `h-dvh` utilities.
- **Native first.** Modals and drawers are `<dialog>`, dropdowns and accordions are `<details>`, tooltips are CSS. The optional JS file is about 3 KB.
- **Easy to override.** Everything sits in cascade layers, so your own unlayered CSS always wins, and utilities beat components without `!important`.

<br/>

## Install

**npm**

```bash
npm install spektra-css
```

```html
<link rel="stylesheet" href="node_modules/spektra-css/dist/spektra.min.css">
<script src="node_modules/spektra-css/dist/spektra.min.js" defer></script>
```

**CDN** (after the package is published)

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/spektra-css@1/dist/spektra.min.css">
<script src="https://cdn.jsdelivr.net/npm/spektra-css@1/dist/spektra.min.js" defer></script>
```

**SCSS**

```scss
@use "spektra-css/scss/spektra";
// compile with: sass --load-path=node_modules app.scss app.css
```

**Hello, Spektra**

```html
<body class="c-teal">
  <nav class="navbar navbar-glass navbar-sticky navbar-expand-md">
    <a class="navbar-brand" href="/">Acme</a>
    <button class="navbar-toggle" aria-label="Menu" data-spk-toggle="collapse" data-spk-target="#menu"></button>
    <div class="navbar-menu" id="menu">
      <a class="nav-link active" href="#">Home</a>
      <a class="nav-link" href="#">Pricing</a>
    </div>
  </nav>

  <main class="container section stack">
    <h1>Hello</h1>
    <div class="grid-auto">
      <article class="card"><div class="card-body">
        <span class="badge badge-dot">Live</span>
        <button class="btn btn-solid">Teal button</button>
      </div></article>
    </div>
  </main>
</body>
```

<br/>

## Colour system

### Hues and shades

Every hue exists as `--spk-{hue}-{50..950}` and as three utilities per shade.

```html
<p class="text-coral-600">Coral text</p>
<div class="bg-teal-100 border border-teal-300">Teal panel</div>
<div style="color: var(--spk-plum-700)">Plum via CSS variable</div>
```

| Family | Hues |
| :--- | :--- |
| Neutrals | slate, gray, zinc, stone, steel |
| Reds and pinks | red, vermilion, crimson, ruby, rose, maroon, pink, magenta, fuchsia |
| Oranges and yellows | coral, peach, orange, rust, amber, gold, yellow, sand |
| Greens | lime, chartreuse, olive, green, emerald, jade, mint |
| Teals and cyans | teal, turquoise, cyan |
| Blues | sky, azure, blue, cobalt, sapphire, navy |
| Purples | periwinkle, indigo, violet, purple, lavender, plum |
| Earth | brown |

### Colour context

`.c-{hue}` and `.c-{role}` set the accent for everything inside.

```html
<div class="c-violet">
  <button class="btn btn-solid">Solid</button>
  <button class="btn btn-soft">Soft</button>
  <button class="btn btn-outline">Outline</button>
  <label class="switch"><input type="checkbox" checked> Follows violet</label>
</div>
```

Components read these variables, which you can also use in your own CSS: `--accent`, `--accent-hover`, `--accent-active`, `--accent-on`, `--accent-soft`, `--accent-text`, `--accent-border`, `--accent-ring`.

### Roles

Roles are names for intent. Each one points at a hue and can be remapped at runtime.

| Role | Default hue | Shorthand examples |
| :--- | :--- | :--- |
| `primary` | cobalt | `btn-primary`, `badge-primary`, `text-primary` |
| `secondary` | slate | `btn-secondary` |
| `success` | emerald | `alert-success` |
| `warning` | amber | `badge-warning` |
| `danger` | red | `btn-outline-danger` |
| `info` | sky | `alert-info` |
| `accent` | fuchsia | `bg-accent-soft` |

```css
/* retheme the whole site from CSS */
:root {
  --spk-primary-500: #ff3d71;
  --spk-primary-600: #e0295c;
  --spk-primary-700: #b81f49;
}
```

### Gradients

```html
<div class="bg-grad from-coral to-violet grad-br">Custom</div>
<div class="bg-grad grad-aurora">Preset</div>
<h1 class="text-grad grad-sunset">Gradient text</h1>
```

Presets: `sunset`, `ember`, `ocean`, `lagoon`, `aurora`, `orchid`, `meadow`, `dusk`.

### Dark mode

```html
<html>                      <!-- follows the OS -->
<html data-theme="dark">    <!-- forced -->
<section data-theme="dark"> <!-- one dark section on a light page -->
```

```js
Spektra.theme.set("dark");   // "light" | "dark" | "auto"
Spektra.theme.toggle();
```

<br/>

## Responsive

### Breakpoints

Mobile first, `min-width`. Prefix a utility with the breakpoint and a colon: `md:flex`, `lg:cols-3`, `xl:p-8`.

| Prefix | Starts at | Typical screens |
| :--- | :---: | :--- |
| base | 0 | small phones (320 to 479 px) |
| `sm:` | 480 px | large phones |
| `md:` | 768 px | tablets in portrait |
| `lg:` | 1024 px | tablets in landscape, small laptops |
| `xl:` | 1280 px | laptops and desktops |
| `xxl:` | 1536 px | large monitors |

### Layout

```html
<!-- 12 column grid: stacked on phones, 7/5 split from lg -->
<div class="row">
  <div class="lg:col-7">...</div>
  <div class="lg:col-5">...</div>
</div>

<!-- cards flow into as many columns as fit, no breakpoints needed -->
<div class="grid-auto" style="--min: 16rem">...</div>

<!-- layout primitives -->
<div class="stack">...</div>          <!-- vertical rhythm -->
<div class="cluster">...</div>        <!-- wrapping row of buttons or tags -->
<div class="with-sidebar">...</div>   <!-- sidebar drops below when narrow -->
<div class="switcher">...</div>       <!-- row to column by container width -->
```

Containers are intrinsic (`min(100% - gutter, max)`), never fixed steps: `container`, `container-sm`, `container-md`, `container-lg`, `container-xl`, `container-xxl`, `container-prose`, `container-fluid`.

### Container queries

Put `.cq` on a wrapper and the component inside responds to the wrapper, not the screen.

```html
<div class="cq">
  <article class="card card-adaptive">
    <img class="card-img" src="..." alt="">
    <div class="card-body">...</div>
  </article>
</div>
```

### Phones with notches

```html
<header class="pt-safe">...</header>
<footer class="pb-safe">...</footer>
<div class="min-h-dvh">fills the real visible height on mobile browsers</div>
```

### Tables on phones

```html
<table class="table table-stack">
  <thead>...</thead>
  <tbody>
    <tr><td data-label="Order">#4821</td><td data-label="Total">$248</td></tr>
  </tbody>
</table>
```

Below 768 px every row becomes a labelled card.

<br/>

## Components

| Group | Classes |
| :--- | :--- |
| Buttons | `btn` with `btn-solid`, `btn-outline`, `btn-soft`, `btn-ghost`, `btn-link`, `btn-plain`; sizes `btn-xs` `btn-sm` `btn-lg` `btn-xl`; `btn-pill`, `btn-block`, `btn-icon`, `is-loading`, `btn-group` |
| Forms | `field`, `label`, `hint`, `input`, `select`, `textarea`, `check` (checkbox and radio), `switch`, `range`, `input-group`, `input-addon`, `is-valid`, `is-invalid` |
| Cards | `card`, `card-body`, `card-header`, `card-footer`, `card-title`, `card-img`, `card-hover`, `card-accent`, `card-soft`, `card-adaptive`, `glass` |
| Feedback | `badge` (`badge-solid`, `badge-outline`, `badge-dot`), `alert`, `progress`, `spinner`, `skeleton`, `avatar`, `avatar-group` |
| Navigation | `navbar`, `nav-link`, `tabs`, `tabs-pill`, `breadcrumb`, `pagination`, `dropdown`, `accordion` |
| Overlays | `modal`, `modal-sheet`, `drawer`, `[data-tip]` tooltips, `toast` |
| Data | `table` (`table-striped`, `table-hover`, `table-compact`, `table-stack`, `table-responsive`), `list-group`, `divider` |

Open the [demo page](docs/index.html) for every component, a palette browser and a responsive lab.

<br/>

## Customise

Every setting is a `!default` Sass variable.

```scss
@use "spektra-css/scss/spektra" with (
  // your brand becomes a full hue: shades, utilities and .c-brand
  $custom-hues: ("brand": #ff3d71),
  $roles: ("primary": "brand", "secondary": "slate", "success": "emerald",
           "warning": "amber", "danger": "red", "info": "sky", "accent": "fuchsia"),

  // ship less CSS
  $enable-hue-utilities: false,
  $enable-responsive-spacing: false,

  // other knobs
  $prefix: "ui",
  $breakpoints: ("sm": 30rem, "md": 48rem, "lg": 64rem, "xl": 80rem, "xxl": 96rem),
  $enable-layers: true
);
```

Sass helpers are exported too:

```scss
@use "spektra-css/scss/spektra" as sp;

.hero { background: sp.hue("coral", 100); color: sp.hue("coral", 900); }
```

### Size

| Build | Minified | Gzip |
| :--- | ---: | ---: |
| Everything | 275 KB | 42 KB |
| No hue utilities | 197 KB | 32 KB |
| Lite (no hue utilities, no responsive spacing) | 155 KB | 26 KB |

The palette variables, `.c-*` classes, components and layout are always included.

### Cascade layers

```text
spektra.tokens  <  spektra.base  <  spektra.layout  <  spektra.components  <  spektra.utilities  <  your CSS
```

Utilities beat components without `!important`, and any CSS you write outside a layer beats all of Spektra. Set `$enable-layers: false` if you need to support very old browsers.

<br/>

## JavaScript

Optional and dependency-free. Everything is driven by data attributes, and the CSS works without it.

| Attribute | What it does |
| :--- | :--- |
| `data-spk-theme-toggle` | Switches between light and dark and remembers the choice |
| `data-spk-theme="dark"` | Sets a specific theme (`light`, `dark`, `auto`) |
| `data-spk-toggle="collapse"` with `data-spk-target="#id"` | Shows and hides a navbar menu or panel |
| `data-spk-open="#id"` and `data-spk-close` | Opens and closes a `<dialog>`. Clicking the backdrop closes it too |
| `role="tab"` with `aria-controls` | Tabs with arrow key support |
| `data-spk-copy="text"` | Copies text and shows a toast |

```js
Spektra.toast("Saved", { title: "Done", color: "success", duration: 3000 });
Spektra.copy("var(--spk-teal-500)");
Spektra.theme.toggle();
```

To avoid a flash of the wrong theme, add this to `<head>` before the stylesheet:

```html
<script>
  try { var t = localStorage.getItem("spektra-theme"); if (t) document.documentElement.setAttribute("data-theme", t); } catch (e) {}
</script>
```

<br/>

## Browser support

Spektra targets evergreen browsers from 2024 onward: Chrome and Edge 123+, Safari 17.5+, Firefox 120+. It relies on `light-dark()`, `color-mix()`, cascade layers, container queries and `:user-invalid`.

<br/>

## Build from source

```bash
git clone https://github.com/MeViksry/spektra.git
cd spektra
npm install
npm run build     # scss -> dist/spektra.css, spektra.min.css, spektra.js, spektra.min.js
npm run watch     # rebuild on change
```

```text
scss/
  spektra.scss        entry point
  _config.scss        every !default variable
  _palette.scss       shade generation and contrast logic
  _tokens.scss        CSS custom properties and themes
  _color-context.scss .c-{hue} and .c-{role}
  _reboot.scss        base styles and typography
  _layout.scss        containers, grid and primitives
  _buttons.scss  _forms.scss  _surfaces.scss  _navigation.scss  _overlays.scss
  _utilities.scss     responsive and colour utilities
js/spektra.js         optional helpers
docs/index.html       demo, palette browser, responsive lab
```

### Publish

```bash
npm login
npm publish          # runs the build first through prepublishOnly
```

To host the demo, enable GitHub Pages for the `main` branch root and open `/docs/`.

<br/>

## Contributing

Issues and pull requests are welcome. Please run `npm run build` and open `docs/index.html` at 360 px and 1280 px, in light and dark mode, before sending a change.

## License

[MIT](LICENSE) © 2026 [MeViksry](https://github.com/MeViksry)
