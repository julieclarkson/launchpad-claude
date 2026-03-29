# Launchpad for Claude

**Three Claude Desktop (Cowork) plugins that work together to document, demo, and launch your project.**

Build your app normally. Case Study Maker captures your decisions. Demo Maker generates narrated videos. Git Launcher creates everything you need to ship on GitHub. Each plugin feeds into the next — install all three and they integrate automatically.

## What's Included

| Plugin | What it does | Activate |
|--------|-------------|----------|
| **[Case Study Maker](https://github.com/julieclarkson/case-study-maker)** | Captures build decisions in real time and generates portfolio case studies, marketing pages, and embeddable cards | `/case-study-maker:activate` |
| **[Demo Maker](https://github.com/julieclarkson/demo-maker)** | Generates 7 platform-ready narrated video demos (Full, GitHub, Twitter, Product Hunt, Instagram, TikTok, GIF) | `/demo` |
| **[Git Launcher](https://github.com/julieclarkson/git-launcher)** | Generates README, screenshots, architecture diagrams, social preview, and launch posts for Reddit, HN, Twitter, Product Hunt, Dev.to | `/git-launch` |

## Install

> **Important:** Clone this bundle _inside_ the project you want to launch.

### Quick Start (all three plugins)

```bash
cd ~/my-awesome-app
git clone https://github.com/julieclarkson/launchpad-claude.git .launchpad

# 1. Case Study Maker
cp -r .launchpad/case-study-maker/skills .claude/skills
cp -r .launchpad/case-study-maker/commands .claude/commands

# 2. Demo Maker
cp -r .launchpad/demo-maker/skills .claude/skills
cp -r .launchpad/demo-maker/commands .claude/commands

# 3. Git Launcher
cp -r .launchpad/git-launcher/skills .claude/skills
cp -r .launchpad/git-launcher/commands .claude/commands
```

### Or install individually

```bash
git clone https://github.com/julieclarkson/case-study-maker.git .case-study-maker
cp -r .case-study-maker/claude/skills .claude/skills
cp -r .case-study-maker/claude/commands .claude/commands

git clone https://github.com/julieclarkson/demo-maker.git .demo-maker-plugin
cp -r .demo-maker-plugin/claude/skills .claude/skills
cp -r .demo-maker-plugin/claude/commands .claude/commands

git clone https://github.com/julieclarkson/git-launcher.git .git-launcher
cp -r .git-launcher/claude/skills .claude/skills
cp -r .git-launcher/claude/commands .claude/commands
```

## Recommended Workflow

| Step | Command | What happens |
|------|---------|-------------|
| **1. Build** | `/case-study-maker:activate` | AI partner watches your coding sessions, prompts reflection questions at decision moments |
| **2. Capture** | `/case-study-maker:capture` or `/case-study-maker:auto-capture` | Save reflections about constraints, tradeoffs, risks, security, and iteration |
| **3. Demo** | `/demo` | 9-step pipeline: analyze → script → storyboard → capture → narrate → render → cutdowns |
| **4. Generate** | `/case-study-maker:generate` | Choose template, theme, tone → get portfolio and marketing pages with embedded demo videos |
| **5. Launch** | `/git-launch` | README, screenshots, architecture, social preview, launch posts for 5 platforms |
| **6. Deploy** | `/case-study-maker:send-to-pages` | Push case study pages to GitHub Pages |

## All Commands

### Case Study Maker

| Command | What it does |
|---------|-------------|
| `/case-study-maker:csm` | Show all commands and current status |
| `/case-study-maker:activate` | Initialize case study tracking |
| `/case-study-maker:capture` | Capture a reflection |
| `/case-study-maker:auto-capture` | Draft reflections from conversation and commits |
| `/case-study-maker:review` | Review coverage and identify gaps |
| `/case-study-maker:generate` | Generate a case study page |
| `/case-study-maker:generate-portfolio-card` | Generate an embeddable portfolio card |
| `/case-study-maker:generate-custom` | Generate for any installed category |
| `/case-study-maker:customize` | Change template, theme, tone, colors, fonts |
| `/case-study-maker:install-template` | Install premium or custom template packs |
| `/case-study-maker:send-to-pages` | Copy outputs to GitHub Pages |

### Demo Maker

| Command | What it does |
|---------|-------------|
| `/demo` | Start the full 9-step demo pipeline |
| `/dm` | Alias for `/demo` |

### Git Launcher

| Command | What it does |
|---------|-------------|
| `/git-launch` | Start the full pipeline |
| `/gl` | Alias for `/git-launch` |

## Requirements

| Requirement | Used by | Required? |
|------------|---------|-----------|
| **Node.js 18+** | All three plugins | Yes |
| **FFmpeg** | Demo Maker | Yes (for video) |
| **Playwright Chromium** | Demo Maker, Git Launcher | Yes (`npx playwright install chromium`) |
| **ElevenLabs API key** | Demo Maker | Optional (skip for caption-only mode) |
| **GitHub CLI (`gh`)** | Demo Maker | Optional (for GitHub Release publish) |

## Security

All three plugins run locally. No data leaves your machine unless you explicitly publish.

**Safeguards across all plugins:**

- **Scope boundary** — all reads and writes are confined to the project root
- **Zero dependencies** (Case Study Maker) — no npm packages, no supply chain risk
- **Secret scanning** (Git Launcher) — blocks `.env`, credentials, and API keys from generated output
- **SSRF prevention** (Demo Maker, Git Launcher) — capture URLs restricted to localhost only
- **CSP headers** — all generated HTML includes Content-Security-Policy meta tags
- **Shell safety** — hook scripts use `execFileSync` with argv arrays to prevent injection

**Your responsibility:**

- **Manage IDE scope and permissions.** Claude will request expanded permissions for Playwright downloads, narration API calls, headless browser rendering, and GitHub publishing. Review each prompt and approve only what you understand.
- **Store API keys securely.** Use `.demo-maker/.env` (gitignored) or a secrets manager like 1Password CLI (`op read`). Never paste keys into chat.
- **Install system dependencies in your terminal.** Run `npm install`, `npx playwright install chromium`, and `brew install ffmpeg` directly — not through the AI agent — to avoid unnecessary sandbox escalation.
- **Review generated content before publishing.** Launch kit posts and README are AI-generated. Case study reflections are your own words, but generated pages should be checked.

## Structure

```
case-study-maker/   — Claude plugin for case studies and portfolios
demo-maker/         — Claude plugin for narrated video demos
git-launcher/       — Claude plugin for GitHub launch assets
```

## Links

- [Case Study Maker](https://github.com/julieclarkson/case-study-maker)
- [Demo Maker](https://github.com/julieclarkson/demo-maker)
- [Git Launcher](https://github.com/julieclarkson/git-launcher)
- [Cursor version of this bundle](https://github.com/julieclarkson/launchpad-cursor)
