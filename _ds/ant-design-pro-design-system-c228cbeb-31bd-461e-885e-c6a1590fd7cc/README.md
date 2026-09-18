# Ant Design Pro — Design System

A design system folder reconstructed from **[Ant Design Pro](https://github.com/ant-design/ant-design-pro)**, the official out-of-the-box enterprise-class **admin / back-office** scaffold from the Ant Design team. It pairs three layers of technology:

- **antd v6** — the Ant Design React component library (the visual language: tokens, colors, type, components).
- **ProComponents v3** (`@ant-design/pro-components`) — heavyweight templated building blocks: `ProLayout`, `ProTable`, `ProForm`, `PageContainer`, `ProDescriptions`, `LoginForm`, `StatisticCard`.
- **Umi Max v4** — the React application framework (routing, data, mock, i18n).

This is a system for building **management consoles / dashboards** — the kind of internal tooling where a persistent **left-hand navigation menu** sits beside a fluid content area. The reference app uses ProLayout in **`mix`** mode: a slim top header carrying the logo, global actions and the user avatar, with the primary navigation living in a **fixed left sider**.

> **Per the project owner's note:** this is a Design System for building back-office / admin systems, with the **menu on the left-hand side.**

---

## Sources

Everything here was reconstructed from the public repository. Nothing assumes you have access — but if you do, explore these to go deeper:

- **GitHub:** https://github.com/ant-design/ant-design-pro (branch `master`)
- Related upstream projects worth exploring for richer fidelity:
  - Ant Design (component library + tokens): https://github.com/ant-design/ant-design
  - ProComponents: https://github.com/ant-design/pro-components
  - Live preview of the reference app: https://preview.pro.ant.design

Key files read to build this system: `config/defaultSettings.ts` (theme), `config/routes.ts` (menu structure), `src/app.tsx` (ProLayout runtime config), `src/global.less` (fonts + globals), `src/pages/user/login/index.tsx`, `src/pages/dashboard/analysis/*`, `src/pages/table-list/index.tsx`.

---

## The products / surfaces

Ant Design Pro is a single product (an admin console) made of many template **surfaces**. The routes (`config/routes.ts`) map the full menu:

| Menu group | Pages | What it demonstrates |
|---|---|---|
| **Dashboard** | Analysis · Monitor · Workplace | KPI cards, charts, activity feeds |
| **Form** | Basic · Step · Advanced | ProForm patterns, multi-step wizards |
| **List** | Table List · Basic List · Card List · Search (Articles/Projects/Applications) | ProTable, CRUD, filtering |
| **Profile** | Basic · Advanced | Read-only detail / descriptions pages |
| **Account** | Center · Settings | User profile, tabbed settings |
| **Result** | Success · Fail | Outcome / feedback screens |
| **Exception** | 403 · 404 · 500 | Error states |
| **User** (no chrome) | Login · Register · Register Result | Auth flows |
| **Chatbot** | — | AI chat surface |

The UI kit in this system recreates the highest-value, most representative surfaces: **Login**, the **app shell** (ProLayout sider + header), the **Analysis dashboard**, and the **Table List** CRUD page.

---

## CONTENT FUNDAMENTALS

How copy is written across Ant Design Pro. The reference app is bilingual (8 locales); the **English defaultMessages** define the canonical English voice.

- **Voice & person.** Neutral, instructional, system-oriented. Copy addresses the task, not the person — there is very little "you/your." Labels are nouns or noun phrases: *Rule name*, *Number of service calls*, *Last scheduled time*, *Operating*.
- **Casing.** **Sentence case** everywhere — page titles, form labels, table headers, menu items. Title Case is avoided. e.g. *"Batch deletion"*, *"Subscribe to alerts"*, *"Total number of service calls"*. Buttons use sentence case verbs: *Submit*, *Cancel*, *New*, *Configuration*.
- **Tone.** Calm, factual, enterprise. Confirmation/feedback is plain and direct: *"Deleted successfully and will refresh soon"*, *"Delete failed, please try again"*. No exclamatory marketing voice in-product (the Chinese strings do use `！`, e.g. *登录成功！* — energy lives in the localized strings, not English).
- **Status vocabulary.** A fixed lexicon maps to the semantic palette: **Running** (processing/blue), **Online** (success/green), **Shut down** (default/grey), **Abnormal** (error/red). Reuse these exact words for state.
- **Placeholders are helpful, not decorative.** Login fields literally tell you the demo creds: *"Username: admin or user"*, *"Password: ant.design"*. Search/filter placeholders describe the action.
- **Microcopy density.** Forms carry inline hints and required-field messages (*"Please enter the rule name"*). Empty/selection states summarize counts: *"Chosen **3** items"*.
- **Numbers & units.** Currency rendered as `￥126,560` (Yuan glyph + thousands separators). Large counts abbreviated with the 万 (ten-thousand) unit in zh. Percentages plain: *60%*, *78%*.
- **Emoji.** **None.** Emoji never appear in product chrome, labels, or copy. Meaning is carried by icons and the semantic color system instead.
- **Vibe.** "Quiet competence." The product gets out of the way; copy is terse, predictable and reassuring. When in doubt, write the shortest accurate noun-phrase and let the component styling carry the polish.

---

## VISUAL FOUNDATIONS

The look is **clean, bright, information-dense enterprise UI** — the canonical "Ant Design" aesthetic. White surfaces float on a soft grey canvas; a single confident blue carries all primary action; everything is gridded, calm and low-drama.

### Color
- **One primary, used sparingly.** Daybreak Blue **`#1677ff`** for primary buttons, active menu items, links and focus. Hover lightens to `#4096ff`, active darkens to `#0958d9`. Selected menu items get a `#e6f4ff` tinted background with blue text.
- **Neutrals are alpha-on-white**, not solid greys: text is `rgba(0,0,0,0.88)` → `0.65` → `0.45` → `0.25` across four levels; fills are `rgba(0,0,0,0.04/0.06/0.15)`. This makes the UI sit gracefully on any background.
- **Semantic set:** success `#52c41a`, warning `#faad14`, error `#ff4d4f`, info = primary. Each has a tinted `-bg` and `-border` for tags/alerts/badges.
- **Canvas vs container.** App background is `#f5f5f5`; content surfaces (cards, tables, the sider, the header) are pure `#ffffff`. This figure/ground contrast is the system's defining move.
- **Imagery vibe.** The brand illustration art (login background, layout decorations) is light, airy, **cool blues and corals on white** — soft gradient blobs, not photography. Cool, optimistic, weightless.

### Type
- **Family:** *Alibaba Sans* (the pro template's webfont), falling back to the system UI stack (`-apple-system, Segoe UI, Roboto…`). Mono is `SFMono-Regular, Consolas, Menlo`.
- **Base body is 14px / line-height 1.5714** — denser than consumer web, appropriate for data. Small text (captions, dense tables) is 12px.
- **Headings** use weight **500 (medium)**, not bold: H1 38 · H2 30 · H3 24 · H4 20 · H5 16. Emphasis is 600.
- Type does little work decoratively; hierarchy comes from size, weight-500 and the four text-alpha levels.

### Spacing, radius, elevation
- **8px-based spacing** scale: 4 · 8 · 12 · 16 · 24 · 32 · 48. Card padding and grid gutters are commonly **24**.
- **Radius:** base **6px** (buttons, inputs), **8px** for cards/modals, **4px** for tags/small controls, **2px** xs. Nothing is pill-shaped or sharp-cornered.
- **Elevation is whisper-soft and multi-layer.** Cards are mostly *borderless with no shadow* on the grey canvas, separated by whitespace. Floating surfaces (dropdowns, popovers, drawers) use antd's signature triple-shadow: `0 6px 16px 0 rgba(0,0,0,.08), 0 3px 6px -4px rgba(0,0,0,.12), 0 9px 28px 8px rgba(0,0,0,.05)`. No heavy drop shadows, ever.

### Borders, dividers, cards
- Hairline borders: inputs `#d9d9d9`; card/table internal dividers `#f0f0f0`; `Divider` is `rgba(5,5,5,0.06)`.
- **Cards:** white, `8px` radius, `1px #f0f0f0` border *or* borderless, `24px` padding. A card header has a title in text-88% / weight-500 with a bottom divider; extras (links, tooltips) sit top-right.
- Tables: header row is `#fafafa`-ish fill (`rgba(0,0,0,0.04)`), cells divided by `#f0f0f0`, hover row `rgba(0,0,0,0.04)`.

### Motion
- **Fast and functional.** Durations 0.1 / 0.2 / 0.3s. Standard easing `cubic-bezier(0.645,0.045,0.355,1)`; "out" `cubic-bezier(0.215,0.61,0.355,1)`.
- Interactions = **fades and slides**, no bounce on chrome. Dropdowns/menus slide+fade, modals zoom-fade in, drawers slide from edge. The one expressive easing (`ease-out-back`, slight overshoot) is reserved for things like wave/ripple on buttons.

### Interaction states
- **Hover:** primary buttons → lighter blue (`#4096ff`); default/ghost buttons → blue text + blue border; menu/list rows → `rgba(0,0,0,0.04)` fill; links → lighter blue.
- **Active/press:** colors *darken* (`#0958d9`). antd buttons emit a **wave/ripple** (an expanding shadow ring) on click.
- **Focus:** a 2px primary-tinted outline/box-shadow ring (`rgba(22,119,255,0.1)` glow) on inputs and focusable controls.
- **Selected (nav/menu):** tinted bg `#e6f4ff` + blue text + weight 500; mix-layout sider shows a left/inline indicator.
- **Disabled:** text drops to `rgba(0,0,0,0.25)`, bg to `rgba(0,0,0,0.04)`, no shadow.

### Layout rules
- **Fixed left sider** (default 208px, collapsible to 48px), **fixed = true** in defaults; light theme. **Top header is 56px**, white, with logo + title at left, global actions (docs, version, language) and avatar at right.
- Content area is **Fluid** width with `24px` outer padding; `PageContainer` adds a page header (breadcrumb + title) above the content.
- **Transparency / blur** is essentially unused in the light enterprise theme — surfaces are opaque. (Glass/blur appears only incidentally.) The system favors solid white panels over translucency.

---

## ICONOGRAPHY

- **System:** **[Ant Design Icons](https://ant.design/components/icon)** (`@ant-design/icons`) — a large, purpose-built SVG icon set, the native iconography of the whole ecosystem. Icons are React components rendered as inline SVG on a **1024×1024 grid**.
- **Three themes per glyph:** **Outlined** (default, hairline ~62-unit stroke — used for nearly all UI: menus, actions, inputs), **Filled** (solid — used for emphasis/status), and **TwoTone** (two-color, primary tint — used sparingly for illustration-like accents). The pro app is overwhelmingly **Outlined**.
- **Usage in the reference app:** menu icons are set by string name in routes (`icon: 'dashboard' | 'form' | 'table' | 'user' | 'crown' | 'robot'…`). Inline action icons: `UserOutlined`, `LockOutlined`, `MobileOutlined` (login fields), `InfoCircleOutlined` (tooltips), plus brand glyphs `AlipayCircleOutlined`, `TaobaoCircleOutlined`, `WeiboCircleOutlined` on the login screen.
- **Emoji / unicode as icons:** never. All iconography is the SVG set; the Yuan unit `￥` is the only glyph used semantically (currency), not as an icon.
- **In this design system:** the exact Ant Design icon set is available via **Iconify** (`ant-design` collection = the official icons). UI kits load the `<iconify-icon>` web component and reference glyphs as `ant-design:<name>-outlined` (e.g. `ant-design:dashboard-outlined`, `ant-design:user-outlined`). This reproduces the real icons faithfully without hand-rolled SVG. See `ui_kits/admin-console/` for usage.
- **Brand logo** lives in `assets/logo.svg` (the angular blue/red Ant Design mark) and `assets/pro_icon.svg` (the "Pro" badge). PWA icons in `assets/icon-*.png`.

---

## Index / Manifest

### Components

Exported on `window.AntDesignProDesignSystem_c228cb` — each lives in `components/<Name>/` with a `.jsx`, a `.d.ts` and a specimen card.

- **`AntIcon`** — renders any Ant Design Outlined icon from the inlined path map. Requires `assets/icons.js`.
- **`Button`** — primary / default / dashed / text / link, three sizes, danger + icon support.
- **`Tag`** — semantic tag presets (processing, success, warning, error, default).
- **`StatusBadge`** — dot + label for the admin status lexicon (Running / Online / Shut down / Abnormal).
- **`StatCard`** — dashboard KPI card: label, big total, visual slot, divided footer.
- **`SiderMenu`** — the fixed **left** navigation; 208px expanded / 48px collapsed, one level of children.
- **`DataTable`** — the ProTable surface: `#fafafa` header, hairline dividers, 4% row hover, optional row selection.
- **`PageHeader`** — breadcrumb trail + page title band with optional extra actions.

Root files:
- **`README.md`** — this file: product context, content + visual foundations, iconography.
- **`styles.css`** — the single entry stylesheet; `@import`s the tokens and the kit component classes. Link this one file.
- **`colors_and_type.css`** — all design tokens as CSS custom properties (color, type, spacing, radius, shadow, motion) + semantic type presets.
- **`thumbnail.html`** — the design system's homepage tile.
- **`components/`** — the exported components listed above.
- **`SKILL.md`** — Agent-Skill-compatible entry point.
- **`assets/`** — `logo.svg`, `pro_icon.svg`, `favicon.ico`, PWA `icon-192/512`.
- **`preview/`** — small HTML specimen cards that populate the Design System tab (colors, type, spacing, components).
- **`ui_kits/admin-console/`** — high-fidelity, interactive recreation of the admin console: app shell (left sider + top header), Login, Analysis dashboard, Table List. See its own `README.md`.

### Using the tokens
```html
<link rel="stylesheet" href="styles.css" />
<!-- then -->
<button style="background: var(--color-primary); color:#fff; border-radius: var(--radius); height: var(--control-height-lg);">
  Submit
</button>
```
