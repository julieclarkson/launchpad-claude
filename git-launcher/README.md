# Git Launcher — Claude Desktop Cowork Plugin

Your project is built. Now ship it properly.

Git Launcher is an AI agent plugin that reads your finished codebase and generates everything you need to launch on GitHub — a polished README, metadata files, screenshots, architecture diagrams, a social preview image, and platform-specific launch posts for Reddit, Hacker News, Twitter/X, Product Hunt, and Dev.to.

**No API keys. No cloud. No cost.** Runs entirely within Claude Desktop Cowork.

## Use It Right Now

You don't need to wait for marketplace approval. Clone this repo and start using it immediately:

1. **Clone this repo:**

```bash
git clone https://github.com/julieclarkson/git-launcher-claude.git
```

2. **Open Claude Desktop Cowork** and select your project folder as the working directory
3. **Copy the plugin into your project:**

```bash
cp -r git-launcher-claude/ your-project/.claude/plugins/git-launcher/
```

4. **Run it:**

```
/git-launcher:git-launch
```

Or just tell Claude: "run git launcher"

That's it. The AI will analyze your codebase and generate everything into a `git-launch/` folder.

### Can I just type `gl-init`?

No. `gl-init` is a Cursor-specific bash initializer. In Cowork, the plugin system handles setup. Just install the plugin and run `/git-launcher:git-launch` — dependencies are installed automatically on first run.

---

## Installation Options

### Option 1: Clone from GitHub (fastest — use this to start now)

```bash
git clone https://github.com/julieclarkson/git-launcher-claude.git
cp -r git-launcher-claude/ your-project/.claude/plugins/git-launcher/
```

Then open your project in Cowork and run `/git-launcher:git-launch`.

### Option 2: From GitHub Marketplace

In Claude Desktop Cowork, run:

```
/plugin marketplace add julieclarkson/git-launcher-claude
/plugin install git-launcher@git-launcher-marketplace
```

### Option 3: From the Anthropic Marketplace

If the plugin has been submitted and approved:

```
/plugin install git-launcher@claude-plugins-official
```

---

## Commands

| Command | What it does |
|---|---|
| `/git-launcher:git-launch` | Run the full Git Launcher workflow |
| `/git-launcher:gl` | Shortcut for git-launch |

Or say "run git launcher" or "git launch" in conversation — the skill triggers automatically.

---

## What Gets Generated

```
git-launch/
├── README.md                # Complete, optimized README
├── CONTRIBUTING.md          # Contributor guide
├── CODE_OF_CONDUCT.md       # Code of conduct
├── LICENSE                  # License file
├── ARCHITECTURE.md          # Mermaid diagrams + explanation
├── LAUNCH_CHECKLIST.md      # Step-by-step deploy instructions
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
├── images/
│   ├── desktop.png          # 1440x900 screenshot
│   ├── tablet.png           # 768x1024 screenshot
│   ├── mobile.png           # 375x812 screenshot
│   └── social-preview.png   # 1200x630 OG image
└── LAUNCH_KIT/
    ├── reddit-post.md
    ├── hackernews-post.md
    ├── twitter-thread.md
    ├── producthunt-listing.md
    ├── devto-post.md
    └── github-description.md
```

## How It Works

1. **Analyze** — Scans your codebase to understand what it does, its tech stack, dependencies, and structure
2. **Generate README** — Writes a complete README with badges, features, install instructions, and architecture overview
3. **Capture Screenshots** — Uses Playwright to take screenshots at 3 viewport sizes (or generates a preview for CLI projects)
4. **Map Architecture** — Parses imports to build component diagrams as Mermaid
5. **Create Social Image** — Renders a branded 1200x630 OG image for GitHub
6. **Write Launch Kit** — Generates platform-specific posts for Reddit, HN, Twitter/X, Product Hunt, and Dev.to
7. **Case Study Integration** — If [Case Study Maker](https://github.com/julieclarkson/case-study-maker-claude) data exists, enriches everything with your build narrative

After generation, run `apply-launch.sh` to copy all assets to your project root, ready to commit and push.

---

## Features

- **Codebase Analysis** — Detects your language, framework, dependencies, and project structure automatically
- **README Generation** — Writes a complete README with badges, features, install instructions, and architecture overview
- **Screenshot Capture** — Uses Playwright to photograph your running app at desktop, tablet, and mobile viewports (or generates a preview page for CLI projects)
- **Architecture Diagrams** — Parses your imports to generate Mermaid component diagrams
- **Social Preview Image** — Renders a branded 1200x630 OG image for GitHub and link sharing
- **Multi-Platform Launch Kit** — Generates tailored posts for Reddit, HN, Twitter/X, Product Hunt, and Dev.to
- **Security Hardened** — Input validation, SSRF prevention, secret scanning, path traversal protection, and optional container isolation

---

## Prerequisites

- **Node.js >= 18** — for screenshot capture, image generation, and codebase analysis (installed automatically on first run)
- **Claude Desktop Cowork** — the plugin runs inside Cowork

---

## Differences from the Cursor Version

This Cowork plugin is a port of the [Cursor IDE version](https://github.com/julieclarkson/git-launcher). Key differences:

| Feature | Cursor | Cowork |
|---|---|---|
| Trigger rule | `.mdc` rule with `alwaysApply: false` | Skill triggered by conversation or command |
| Commands | `/git-launch`, `/gl` | `/git-launcher:git-launch`, `/git-launcher:gl` |
| Init script | `gl-init` bash script | Plugin install + `/git-launcher:git-launch` |
| Post-commit check | Git pre-commit hook | `PostToolUse` on Bash tool |
| Distribution | Cursor Marketplace | Claude plugin marketplace or GitHub |

---

## Distribution

### Self-Hosted Marketplace

This plugin includes a `marketplace.json` for self-distribution. Push to GitHub and users add it with:

```
/plugin marketplace add julieclarkson/git-launcher-claude
```

### Official Marketplace

Submit at [claude.ai/settings/plugins/submit](https://claude.ai/settings/plugins/submit) for inclusion in the official Anthropic marketplace.

### Team Distribution

Add to your project's `.claude/settings.json` for automatic team installation:

```json
{
  "extraKnownMarketplaces": {
    "git-launcher-marketplace": {
      "source": {
        "source": "github",
        "repo": "julieclarkson/git-launcher-claude"
      }
    }
  }
}
```

---

## Submit to Marketplace

To submit this plugin to the official Claude plugin marketplace:

1. Push this folder to a GitHub repo
2. Go to [claude.ai/settings/plugins/submit](https://claude.ai/settings/plugins/submit) or [platform.claude.com/plugins/submit](https://platform.claude.com/plugins/submit)
3. Provide the repo URL and follow the submission flow

---

## License

MIT — see [LICENSE](LICENSE) for details.

Built by [Julie Clarkson](https://superflyweb.com) | [casestudymaker.dev](https://casestudymaker.dev)
