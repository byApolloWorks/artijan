<p align="center">
  <img src="assets/logo.svg" alt="ARTIJAN" width="500" />
  <br />
  <br />
  <strong>Artijan, the artifact janitor.</strong>
  <br />
  <strong>Find and remove JS/TS build artifacts wasting disk space.</strong>
  <br />
  <br />
  <a href="https://www.npmjs.com/package/artijan"><img src="https://img.shields.io/npm/v/artijan.svg" alt="npm version" /></a>
  <a href="https://www.npmjs.com/package/artijan"><img src="https://img.shields.io/npm/dm/artijan.svg" alt="npm downloads" /></a>
  <a href="https://github.com/byApolloWorks/artijan/blob/main/LICENSE"><img src="https://img.shields.io/npm/l/artijan.svg" alt="license" /></a>
  <img src="https://img.shields.io/node/v/artijan.svg" alt="node version" />
</p>

---

## 🧹 What It Does

Scan your filesystem for JavaScript/TypeScript build artifacts — directories like `node_modules`, `.next`, `dist`, `.cache`, `coverage`, `.turbo`, and files like `.tsbuildinfo`, `.eslintcache`, heap snapshots, debug logs, and [more](#detected-artifacts) — then interactively browse, sort, select, and safely delete them to reclaim disk space.

## 🚀 Installation

Requires Node.js >= 18.18.0.

- **Via [npm](https://www.npmjs.com/package/artijan)** — no install required

  ```bash
  npx artijan
  ```

- **Via npm, pnpm, yarn or bun** global install

  ```bash
  npm install -g artijan
  # or
  pnpm add -g artijan
  # or
  yarn global add artijan
  # or
  bun install -g artijan
  ```

### CLI Options

```
artijan [options]

  -d, --directory <path>    Set scan root directory (default: current directory)
  -E, --exclude <names>     Exclude directories by name, comma-separated
  -t, --target <names>      Override default targets, comma-separated
  -V, --verbose             Write debug log to artijan-debug.log
  -h, --help                Show this help message
  -v, --version             Show version number
```

Examples:

```bash
artijan -d ~/projects                        # scan a specific directory
artijan --exclude "dist,build"               # skip dist and build directories
artijan --target "node_modules,.next"         # only scan for specific artifacts
```

## ✨ Features

### Smart Sorting

Sort by size, path, or age with `s` to find the biggest space hogs.

### Search & Filter

Press `/` to search — instantly filter artifacts by path. Press `f` to open the type filter and show only specific artifact types (e.g. just `node_modules` or `.next`).

### File Artifact Scanning

Artijan detects individual build artifact files (`.tsbuildinfo`, `.eslintcache`, debug logs, heap snapshots, etc.) and groups them by type into collapsible rows. Expand with `Enter` to see individual files, or select the whole group with `Space`.

### Directory Grouping

Press `x` to group artifacts by parent directory. Collapse and expand groups with `Enter` or arrow keys. Select an entire group at once with `Space` on the group header. File groups nest inside their parent directory groups.

### Range Multi-Select

Hold `Shift` + arrow keys (or use `J`/`K`) to select a contiguous range of artifacts. `Shift+Space` extends selection from an anchor point.

### Safe Deletion

Select artifacts with `Space`, delete with `d`. Confirmation dialog and live progress tracking.

### 10 Built-in Themes

Cycle with `t`. Your choice is saved across sessions.

## ⌨️ Keybindings

Vim-style navigation is fully supported alongside arrow keys.

| Key | Action |
|-----|--------|
| `↑` `k` | Move cursor up |
| `↓` `j` | Move cursor down |
| `Shift+↑` `K` | Range select up |
| `Shift+↓` `J` | Range select down |
| `g` / `G` | Jump to top / bottom |
| `PgUp` `PgDn` | Page up / down |
| `Space` | Toggle selection |
| `Shift+Space` | Extend selection from anchor |
| `a` | Select all |
| `d` | Delete selected |
| `s` | Cycle sort mode |
| `/` | Search / filter |
| `f` | Type filter |
| `x` | Toggle directory grouping |
| `Tab` | Toggle detail panel |
| `+` / `-` | Scroll detail panel |
| `t` | Cycle theme |
| `Esc` | Clear selection |
| `q` | Quit |

## 🎨 Themes

Cycle through themes with `t` during a session. Your preference is saved to `~/.config/artijan/config.json` (or `$XDG_CONFIG_HOME/artijan/config.json`) and persisted across sessions.

Built-in themes: Tokyo Night, Nord Frost, Dracula, Gruvbox Dark, Ros&eacute; Pine, Kanagawa, Everforest, Solarized Dark, Cyberpunk Neon, Catppuccin Mocha.

## 🔍 Detected Artifacts

### Directories

| Category | Directories |
|----------|-------------|
| **Package managers** | `node_modules`, `.npm`, `.pnpm-store` |
| **Framework builds** | `.next`, `.nuxt`, `.angular`, `.svelte-kit`, `.vite`, `.turbo`, `.nx` |
| **Bundler caches** | `.parcel-cache`, `.rpt2_cache`, `.esbuild`, `.rollup.cache`, `.cache` |
| **Transpiler** | `.swc` |
| **Test/coverage** | `coverage`, `.nyc_output`, `.jest` |
| **Docs/storybook** | `storybook-static`, `gatsby_cache`, `.docusaurus` |
| **Serverless** | `.serverless` |
| **Runtime** | `deno_cache` |
| **Build outputs** | `dist`, `build`, `.output` |

### Files

Files are grouped by type into collapsible rows.

| Category | Files |
|----------|-------|
| **Build/compiler** | `.tsbuildinfo` |
| **Linter/formatter caches** | `.eslintcache`, `.stylelintcache` |
| **Yarn PnP** | `.pnp.cjs`, `.pnp.loader.mjs` |
| **Package manager logs** | `npm-debug.log*`, `yarn-error.log*`, `yarn-debug.log*`, `pnpm-debug.log*`, `.pnpm-debug.log*`, `lerna-debug.log*` |
| **Profiling/diagnostics** | `*.heapsnapshot`, `*.cpuprofile`, `*.heapprofile` |
| **Package archives** | `*.tgz` |

## 📄 License

[MIT](LICENSE)
