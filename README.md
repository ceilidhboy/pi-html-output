# pi-html-output

HTML output for Pi — generate beautiful, self-contained HTML documents
instead of raw Markdown when the information benefits from visual illustration.

Inspired by [Thariq Shihipar's "The Unreasonable Effectiveness of HTML"](https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html)
and his [20 example files](https://thariqs.github.io/html-effectiveness/).

## Installation

```bash
pi install npm:pi-html-output
```

Or from a local copy:

```bash
pi install /path/to/pi-html-output
```

## What It Does

When you ask Pi a question whose answer would benefit from visual illustration —
architectural plans, design options, code reviews, workflows, comparisons,
novel concepts, color choices — this skill kicks in and generates a
self-contained HTML file instead of Markdown.

The HTML includes:

- **Visual hierarchy** — cards, grids, callouts, responsive layouts
- **Inline SVG diagrams** — flowcharts, architecture, timelines, fan-out/in
- **Color swatches** — for design discussions where hex codes aren't enough
- **Tradeoff tables** — with green/red dot indicators
- **Code panels** — dark background with syntax highlighting
- **Interactive controls** — sliders, toggles, copy buttons (optional)
- **Export buttons** — download SVG diagrams as standalone files

## Configuration

The output directory is resolved using this fallback chain:

1. **Environment variable** — set `PI_HTML_OUTPUT_DIR` to your preferred path
2. **Pi settings** — add `"htmlOutputDir": "/path/to/output"` to `~/.pi/agent/settings.json`
3. **Fallback** — `~/.pi/agent/html-output/`

### Quick setup

```bash
# Option A: settings.json (recommended)
# Add this line to ~/.pi/agent/settings.json:
# "htmlOutputDir": "/path/to/your/output"

# Option B: environment variable
echo 'export PI_HTML_OUTPUT_DIR="/path/to/your/output"' >> ~/.bashrc
```

Then restart Pi or run `/reload`.

## How It Works

### Skill structure

```
pi-html-output/
├── package.json
├── README.md
└── skills/
    └── html-output/
        ├── SKILL.md                    ← Entry point (55 lines)
        └── references/
            ├── DESIGN_SYSTEM.md        ← Color palette, typography, CSS
            ├── SVG_GUIDELINES.md       ← SVG conventions and diagram types
            └── TEMPLATES.md            ← Use case templates
```

The entry point (`SKILL.md`) is 55 lines and contains only the decision
heuristic, output path resolution, and pointers to the reference files. The
reference files are read on-demand when the agent needs that specific
information.

### Decision heuristic

The agent asks itself:

> *"Would the human reader get more understanding from **seeing** this than
> from **reading** it?"*

If yes → HTML. If no → Markdown.

**Use HTML when** the information has *depth* — relationships, tradeoffs,
workflows, color choices, novel concepts — anything requiring mental
visualization.

**Use Markdown when** the information is *wide* — linear lists using standard
terminology that carries the meaning.

### Customizing the design system

Replace `references/DESIGN_SYSTEM.md` with your own color palette, typography,
and CSS patterns. Keep the same token names (`--ivory`, `--slate`, `--clay`,
etc.) for consistency, or add your own.

## Requirements

- Pi (any version)
- Any compatible LLM model

## License

Apache-2.0
