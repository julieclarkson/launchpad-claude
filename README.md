# Launchpad for Claude

Three Claude Desktop (Cowork) plugins that work together to build, document, demo, and launch your project.

## What's Included

| Plugin | What It Does |
|--------|-------------|
| **Case Study Maker** | Captures your build decisions and generates marketing pages, portfolio case studies, and pitch decks |
| **Demo Maker** | Creates narrated video demos of your product for every platform |
| **Git Launcher** | Generates launch-ready GitHub assets — README, screenshots, architecture docs, social previews, and multi-platform launch posts |

## Recommended Workflow

```
1. Build your project with Case Study Maker capturing reflections
   /case-study-maker:activate

2. Generate narrated demo videos
   /demo-maker:activate → "make a demo"

3. Generate case study pages (auto-embeds demo videos if available)
   /case-study-maker:generate

4. Create launch kit for every platform
   /git-launcher:git-launch
```

## Install

### Option A: Clone this bundle (all three plugins at once)

```bash
cd your-project/
git clone https://github.com/julieclarkson/launchpad-claude.git .launchpad
```

Then copy the plugin directories you want into your project root.

### Option B: Install individually

```bash
git clone https://github.com/julieclarkson/case-study-maker.git .case-study-maker
# Use: claude/ directory

git clone https://github.com/julieclarkson/demo-maker.git .demo-maker
# Use: claude/ directory

git clone https://github.com/julieclarkson/git-launcher.git .git-launcher
# Use: claude/ directory
```

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
