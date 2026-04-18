# Agentic Engineering

A comprehensive reference to autonomous coding agents, agentic organizations, and the emerging patterns of AI-native software engineering. Covers 14+ agent systems (Stripe Minions, Claude Managed Agents, OpenAI Symphony, OpenHands, AgentField, Devin, and more), 180+ infrastructure vendors, and the architectural patterns driving the category.

The repository hosts **two independent sites** that render the same underlying content:

1. **Reference front end** — Plain HTML/CSS/JS at the repo root. Deploys to Vercel.
2. **Documentation portal** — [Mintlify](https://mintlify.com) site in `/docs`. Deploys to Mintlify Cloud.

They can ship together or separately. Pick the one that fits your needs.

---

## Reference front end (root)

Plain HTML/CSS/JS. Markdown content lives in `content/*.md` and is inlined into `index.html` at build time.

### Structure

```
.
├── index.html          # Generated — don't edit directly
├── build.sh            # Inlines content/*.md into index.html
├── content/            # Edit markdown here
│   ├── index.md
│   ├── approaches.md
│   ├── patterns.md
│   ├── comparison.md
│   ├── organizations.md
│   ├── inference.md
│   ├── sandboxes.md
│   └── infrastructure.md
├── css/style.css
└── js/main.js
```

### Develop

```bash
npm run build       # Rebuild index.html after editing content/
python3 -m http.server 3000   # Or any static server
```

### Deploy

Connected to Vercel. Pushes to `main` trigger automatic deploys.

```bash
vercel deploy --prod
```

Live: https://minions-alpha.vercel.app

---

## Documentation portal (`docs/`)

Mintlify MDX-based docs. Runs at its own URL on Mintlify Cloud hosting.

### Structure

```
docs/
├── docs.json           # Mintlify config (navigation, theme, logo)
├── index.mdx           # Home
├── approaches.mdx
├── patterns.mdx
├── comparison.mdx
├── organizations.mdx
├── inference.mdx
├── sandboxes.mdx
├── infrastructure.mdx
├── favicon.svg
├── logo/{light,dark}.svg
└── package.json
```

### Develop

Mintlify CLI requires Node ≤22.

```bash
cd docs
npm install
npm run dev           # Local preview on localhost:3000
npm run broken-links  # Validate internal links
```

Or from the repo root:

```bash
npm run docs:dev
npm run docs:broken-links
```

### Deploy

1. Sign up at [mintlify.com/dashboard](https://mintlify.com/dashboard)
2. Connect this GitHub repository
3. Set the source directory to `docs/`
4. Mintlify auto-builds and hosts on every push to `main`

---

## Editing content

If you want both sites updated, edit the markdown in `content/` and mirror the change in the matching `docs/*.mdx` file (or vice versa). The content is intentionally duplicated to let each site evolve with its own formatting conventions — `content/*.md` uses plain markdown, `docs/*.mdx` uses Mintlify components (Card, CardGroup, Note, Steps) for richer presentation.

Future work: a shared content source with per-target transformations.

## License

MIT
