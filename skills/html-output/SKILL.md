---
name: html-output
description: >-
  HTML output generator for output that would benefit from being presented in
  a visually rich document. Use when communicating architectural plans, design
  options, code review summaries, workflows, comparisons, novel concepts, color
  choices, or any information that benefits from visual illustration — inline
  SVG diagrams, color swatches, structured comparison grids, interactive
  controls. Not needed for simple lists, linear text, or straightforward data
  using well-understood terminology.
compatibility: Any agent harness supporting HTML output
---

# HTML Output

Generate self-contained HTML documents instead of Markdown when the
information benefits from visual illustration. Read the supporting files
below as needed for the specific task.

## Output Location

Resolve the output directory using this fallback chain:

1. **Environment variable** `PI_HTML_OUTPUT_DIR` — if set, use this path
2. **Pi global settings** — check `htmlOutputDir` key in `~/.pi/agent/settings.json`
3. **Fallback** — use `~/.pi/agent/html-output/` (creates it if needed)

Name files descriptively, e.g. `oauth-flows-explainer.html`.

## Decision Heuristic

> *"Would the human reader get more understanding from **seeing** this than from **reading** it?"*

**Use HTML when** the information has *depth* — novel concepts, relationships,
tradeoffs, workflows, color choices — anything requiring mental visualization.

**Use Markdown when** the information is *wide* — linear lists using standard
terminology that carries the meaning. HTML adds no cognitive value there.

**Cost awareness:** HTML takes 2-4× longer to generate. Only use when the
cognitive benefit justifies the cost.

## Supporting Files

| File | When to read it |
|---|---|
| [DESIGN_SYSTEM.md](references/DESIGN_SYSTEM.md) | When building the HTML — contains color palette, typography, layout tokens, CSS patterns, and HTML boilerplate. **Swap this file to use a custom design system.** |
| [SVG_GUIDELINES.md](references/SVG_GUIDELINES.md) | When a diagram or illustration would help — contains SVG conventions, diagram types (flowchart, timeline, fan-out), and download button code. |
| [TEMPLATES.md](references/TEMPLATES.md) | When choosing a document structure — contains 7 use case templates with prompt patterns for exploration, code review, design, reports, explainers, slide decks, and custom editors. |

## References

- Blog post: https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html
- Examples: https://thariqs.github.io/html-effectiveness/
- GitHub: https://github.com/thariqs/html-effectiveness
