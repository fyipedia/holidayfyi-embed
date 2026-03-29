# holidayfyi-embed

[![npm](https://img.shields.io/npm/v/holidayfyi-embed)](https://www.npmjs.com/package/holidayfyi-embed)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/holidayfyi-embed)

Embed **HolidayFYI** widgets — holidays, glossary terms, interactive tools, and inline elements — on any website. **10 widget types**, zero dependencies, Shadow DOM style isolation, 4 built-in themes (light, dark, sepia, auto), 2 styles (modern, clean), and live data from the [HolidayFYI](https://holidayfyi.com) database.

Every widget includes a "Powered by HolidayFYI" backlink directing readers to the full reference.

> **Try the interactive widget builder at [widget.holidayfyi.com](https://widget.holidayfyi.com)**

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-holidayfyi="entity" data-slug="holidays" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

That's it. The widget fetches data from the HolidayFYI API and renders with full style isolation.

## Widget Types

| Type | Usage | Description |
|------|-------|-------------|
| `entity` | `<div data-holidayfyi="entity" data-slug="..."></div>` | Entity detail card — unit, city, holiday, or name |
| `glossary` | `<div data-holidayfyi="glossary" data-slug="..."></div>` | Glossary term definition with cross-references |
| `guide` | `<div data-holidayfyi="guide" data-slug="..."></div>` | Guide summary card with key takeaways |
| `search` | `<div data-holidayfyi="search" data-slug="..."></div>` | Search box linking to the full database |
| `compare` | `<div data-holidayfyi="compare" data-slug="..."></div>` | Side-by-side entity comparison |
| `faq` | `<div data-holidayfyi="faq" data-slug="..."></div>` | FAQ accordion with expand/collapse |
| `today` | `<div data-holidayfyi="today" data-slug="..."></div>` | Today's holidays from around the world |
| `upcoming` | `<div data-holidayfyi="upcoming" data-slug="..."></div>` | List of next N upcoming holidays |
| `countdown` | `<div data-holidayfyi="countdown" data-slug="..."></div>` | Live countdown to a specific date (pure client-side) |
| `badge` | `<div data-holidayfyi="badge" data-slug="..."></div>` | Inline holiday badge with date and emoji |

## Widget Options

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-holidayfyi` | entity, compare, glossary, guide, search, faq, [tools] | required | Widget type |
| `data-slug` | e.g. "holidays" | — | Entity slug from the HolidayFYI database |
| `data-theme` | light, dark, sepia, auto | light | Visual theme (`auto` follows OS preference) |
| `data-style` | modern, clean | modern | Widget design style |
| `data-size` | default, compact, large | default | Widget size |
| `data-placeholder` | any string | "Search Holidays..." | Search box placeholder |

## Themes

```html
<!-- Light (default) -->
<div data-holidayfyi="entity" data-slug="holidays" data-theme="light"></div>

<!-- Dark -->
<div data-holidayfyi="entity" data-slug="holidays" data-theme="dark"></div>

<!-- Sepia -->
<div data-holidayfyi="entity" data-slug="holidays" data-theme="sepia"></div>

<!-- Auto — follows OS dark/light preference -->
<div data-holidayfyi="entity" data-slug="holidays" data-theme="auto"></div>
```

## Styles

```html
<!-- Modern (default) — clean lines, rounded corners, accent gradients -->
<div data-holidayfyi="entity" data-slug="holidays" data-style="modern"></div>

<!-- Clean — minimal borders, utility-focused, data-first aesthetic -->
<div data-holidayfyi="entity" data-slug="holidays" data-style="clean"></div>
```

## Web Components (Custom Elements)

As an alternative to `data-*` attributes, you can use native HTML custom elements:

```html
<!-- Custom element form -->
<holidayfyi-entity slug="holidays" theme="light"></holidayfyi-entity>
<holidayfyi-compare slugs="holidays,other-slug"></holidayfyi-compare>
<holidayfyi-search placeholder="Search Holidays..."></holidayfyi-search>

<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

Use `style-variant` (not `style`) to avoid conflicts with the HTML reserved `style` attribute.

## Examples

### Entity Card

```html
<div data-holidayfyi="entity" data-slug="holidays" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

### Side-by-Side Comparison

```html
<div data-holidayfyi="compare" data-slugs="holidays,other-slug"></div>
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

### Search Box

```html
<div data-holidayfyi="search" data-placeholder="Search Holidays..."></div>
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

### Glossary Term

```html
<div data-holidayfyi="glossary" data-slug="example-term" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
```

### Specific version (production stability)

```html
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1.0.0/dist/embed.min.js"></script>
```

### npm (for bundlers)

```bash
npm install holidayfyi-embed
```

```javascript
import 'holidayfyi-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site
- **Zero dependencies**: No jQuery, React, or any external library
- **2 styles**: Modern (accent gradients) and Clean (minimal, data-first)
- **4 themes**: Light, Dark, Sepia, Auto (OS preference detection)
- **CORS**: HolidayFYI API has CORS enabled for all origins
- **MutationObserver**: Works with dynamically added elements (SPAs)
- **IntersectionObserver**: Lazy loading — widgets only fetch when entering viewport (200px margin)
- **Rich Snippets**: DefinedTerm JSON-LD injected for glossary widgets
- **Bundle size**: Tree-shaken per site — only includes tools available on HolidayFYI

## Learn More About Holidays

Visit [holidayfyi.com](https://holidayfyi.com) — HolidayFYI is a comprehensive holidays reference with interactive tools, guides, and developer resources.

- **API docs**: [holidayfyi.com/developers/](https://holidayfyi.com/developers/)
- **Widget builder**: [widget.holidayfyi.com](https://widget.holidayfyi.com)
- **npm package**: [npmjs.com/package/holidayfyi-embed](https://www.npmjs.com/package/holidayfyi-embed)
- **GitHub**: [github.com/fyipedia/holidayfyi-embed](https://github.com/fyipedia/holidayfyi-embed)

## Utility FYI Family

Part of [FYIPedia](https://fyipedia.com) — open-source developer tools ecosystem. Utility FYI covers unit conversion, timezones, holidays, and names. Hub: [toolfyi.com](https://toolfyi.com).

| Site | Domain | Focus | Package |
|------|--------|-------|---------|
| UnitFYI | [unitfyi.com](https://unitfyi.com) | 220 units, 20 categories, offline converter | [npm](https://www.npmjs.com/package/unitfyi-embed) |
| TimeFYI | [timefyi.com](https://timefyi.com) | 6,040 cities, live world clock, sunrise data | [npm](https://www.npmjs.com/package/timefyi-embed) |
| **HolidayFYI** | [holidayfyi.com](https://holidayfyi.com) | 626 holidays, 197 countries, live today feed | **[npm](https://www.npmjs.com/package/holidayfyi-embed)** |
| NameFYI | [namefyi.com](https://namefyi.com) | 35,585 names, Hanja characters, Five Elements | [npm](https://www.npmjs.com/package/namefyi-embed) |

## FYIPedia Developer Tools

| Package | PyPI | npm | Description |
|---------|------|-----|-------------|
| colorfyi | [PyPI](https://pypi.org/project/colorfyi/) | [npm](https://www.npmjs.com/package/@fyipedia/colorfyi) | Color conversion, WCAG contrast, harmonies — [colorfyi.com](https://colorfyi.com) |
| emojifyi | [PyPI](https://pypi.org/project/emojifyi/) | [npm](https://www.npmjs.com/package/emojifyi) | Emoji encoding & metadata for 3,953 emojis — [emojifyi.com](https://emojifyi.com) |
| unitfyi | [PyPI](https://pypi.org/project/unitfyi/) | [npm](https://www.npmjs.com/package/unitfyi) | Unit conversion, 220 units — [unitfyi.com](https://unitfyi.com) |
| timefyi | [PyPI](https://pypi.org/project/timefyi/) | [npm](https://www.npmjs.com/package/timefyi) | Timezone ops & business hours — [timefyi.com](https://timefyi.com) |
| holidayfyi | [PyPI](https://pypi.org/project/holidayfyi/) | [npm](https://www.npmjs.com/package/holidayfyi) | Holiday dates & Easter calculation — [holidayfyi.com](https://holidayfyi.com) |
| namefyi | [PyPI](https://pypi.org/project/namefyi/) | [npm](https://www.npmjs.com/package/namefyi) | Korean romanization & Five Elements — [namefyi.com](https://namefyi.com) |
| fyipedia | [PyPI](https://pypi.org/project/fyipedia/) | — | Unified CLI for all FYI tools — [fyipedia.com](https://fyipedia.com) |

## Embed Widget

Embed [HolidayFYI](https://holidayfyi.com) widgets on any website with [holidayfyi-embed](https://widget.holidayfyi.com):

```html
<script src="https://cdn.jsdelivr.net/npm/holidayfyi-embed@1/dist/embed.min.js"></script>
<div data-holidayfyi="entity" data-slug="example"></div>
```

Zero dependencies · Shadow DOM · 4 themes (light/dark/sepia/auto) · [Widget docs](https://widget.holidayfyi.com)

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [FYIPedia](https://fyipedia.com).
