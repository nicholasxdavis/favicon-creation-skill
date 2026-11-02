# Favicon Creation (`favicon-creation`)

Evaluate brands, generate centered hyper-simplified square favicon concepts, and post-process them into transparent favicon.ico and multi-size PNG assets.

`favicon-creation` is an engineering agent skill designed for Claude Code, Cursor, Codex, OpenClaw, and LLM coding environments. It enforces strict visual clarity at tiny scale (16x16 and 32x32), automated chroma-keying, padding balancing, and export generation.

## Key Highlights

* **16x16 Scale Budget:** Enforces bold, rounded contours and high-contrast color blocks that remain legible at microscopic tab sizes.
* **Automated Post-Processing:** Uses Python and Pillow to remove solid backgrounds, apply edge feathering, and center padding.
* **Complete Asset Export:** Generates multi-resolution `favicon.ico` (16/32/48), PNG variants, and standard `apple-touch-icon.png` assets.
* **Plug-and-Play Integration:** Provides ready-to-use HTML `<head>` markup snippets alongside generated files.

## Quick Start

### Prerequisites

Ensure Python 3 and Pillow are installed in your execution environment:

```bash
pip install pillow
```

### Installation

#### Option A: Project-level Rule (Cursor / Claude / Gemini)

Copy the contents of `SKILL.md` directly into your project agent rules directory:

* **Cursor:** `.cursorrules` or `.cursor/rules/favicon-creation.md`
* **Claude Code:** `.claude/skills/favicon-creation/SKILL.md` or `CLAUDE.md`
* **OpenClaw / Codex:** `$HOME/.codex/skills/favicon-creation/SKILL.md`

#### Option B: Global Skill Registry

```bash
git clone https://github.com/your-username/favicon-creation.git ~/.copilot/skills/favicon-creation
```

## Usage Examples

Prompt your agent with:

* "Create a favicon for this project based on our branding."
* "Generate a browser icon from logo.png with a transparent background."
* "Build a site mark and apple touch icon for our web app."

## How It Works (Workflow Breakdown)

1. **Brand & Concept Selection:** Parses README or landing copy to pick a single recognizable focal emblem or monogram.
2. **Image Generation:** Produces a 1:1 full-bleed square subject centered on a solid high-contrast background.
3. **Python Keying & Centering:** Runs `make_favicon.py` to strip solid backgrounds, trim excess padding, and scale outputs.
4. **HTML Handoff:** Outputs the complete HTML head snippet and files ready for deployment.

## Production Script Usage

```bash
python scripts/make_favicon.py <source.png> -d favicon-out --fill 0.82
```

Flags:
* `--bg RRGGBB` force key color when auto-detect fails
* `--tolerance` / `--feather` tighten or soften background removal
* `--master-size 512` output transparent master resolution

## HTML Head Snippet

```html
<link rel="icon" href="/favicon.ico" sizes="any" />
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
```

## License

MIT License. Free to use across personal and commercial agent workflows.
