# Gassa’s Blog

An opinionated personal blog focused on technology and life.

- Live site: `https://blog.gassayy.com/`

Built with [Astro](https://astro.build), using a customized version of [Astro Theme Cactus](https://github.com/chrismwilliams/astro-theme-cactus).

## Tech / features

- Astro v5
- Tailwind v4
- Markdown + MDX for posts & notes
- Code blocks via [Expressive Code](https://expressive-code.com/)
- Static search via [Pagefind](https://pagefind.app/) (runs after build)
- OG image generation (Satori)
- RSS feeds (`/rss.xml` and `/notes/rss.xml`)
- Sitemap, robots.txt, and web app manifest
- Optional webmentions (webmention.io + brid.gy)

## Commands

| Command            | Action |
| :----------------- | :----- |
| `pnpm install`     | Install dependencies |
| `pnpm dev`         | Start dev server (Astro default: `http://localhost:4321`) |
| `pnpm build`       | Build production site to `./dist/` |
| `pnpm postbuild`   | Build Pagefind index for search (`dist/`) |
| `pnpm preview`     | Preview the production build locally |
| `pnpm check`       | Typecheck (`astro check`) |
| `pnpm lint`        | Lint (`biome`) |
| `pnpm format`      | Format code + imports |
| `pnpm format:code` | Run Biome + Prettier |
| `pnpm format:imports` | Fix imports via Biome |

> Note: for search to work locally, run `pnpm build && pnpm postbuild && pnpm preview`.

## Writing content

Content lives in:

- Posts: `src/content/post/*.md` / `src/content/post/*.mdx`
- Notes: `src/content/note/*.md` / `src/content/note/*.mdx`
- Tag overrides (optional): `src/content/tag/*.md` / `src/content/tag/*.mdx`

This repo uses [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/) with schemas in `src/content.config.ts`.

### Post frontmatter (`src/content/post/*`)

| Field | Required | Notes |
| :---- | :------- | :---- |
| `title` | ✅ | Max length 60 |
| `description` | ✅ | SEO description |
| `publishDate` | ✅ | Parsed into a `Date` |
| `updatedDate` | ❌ | Parsed into a `Date` |
| `tags` | ❌ | Defaults to `[]`; deduped and lowercased |
| `coverImage` | ❌ | `{ src, alt }` (`src` is an Astro `image()` reference) |
| `ogImage` | ❌ | If set, skips auto-generated OG image |
| `draft` | ❌ | Defaults to `false` |
| `pinned` | ❌ | Defaults to `false` |

### Note frontmatter (`src/content/note/*`)

| Field | Required | Notes |
| :---- | :------- | :---- |
| `title` | ✅ | Max length 60 |
| `publishDate` | ✅ | ISO 8601 w/ offset (e.g. `2024-01-01T00:00:00Z`) |
| `description` | ❌ | Optional meta description |

### Tag frontmatter (`src/content/tag/*`)

| Field | Required | Notes |
| :---- | :------- | :---- |
| `title` | ❌ | Optional display title |
| `description` | ❌ | Optional description |

## Configuration

- Site identity + menu links: `src/site.config.ts`
- Astro + integrations: `astro.config.ts`
- Global styles: `src/styles/global.css`
- Social links: `src/components/SocialList.astro`
- Default social card: `public/social-card.png`
- App icons / manifest source: `public/icon.svg`

## Webmentions (optional)

This repo supports displaying likes/mentions/replies from webmention.io.

Create a local `.env` (don’t commit it) if you want webmentions enabled:

```bash
WEBMENTION_API_KEY="..."
WEBMENTION_URL="https://webmention.io/api/mentions.jf2?..."
WEBMENTION_PINGBACK="https://webmention.io/.../xmlrpc" # optional
```

## Deploy

Deploy anywhere Astro can run. Output is generated into `dist/` via `pnpm build` (and `pnpm postbuild` if you want search).

## License

MIT (see `LICENSE`).
