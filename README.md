# awesome-ieee-report

A Kiro skill that generates IEEE-format technical reports as LaTeX. Point it at your project, and it reads the codebase, maps requirements to sections, and produces a publication-ready `.tex` + `.bib` output with zero code artifacts in the report body.

## What It Does

- Reads your requirement document (optional) and derives section structure from it
- Analyzes the codebase internally to extract architecture, algorithm, and behavior facts
- Writes purely academic prose — no file paths, class names, or code identifiers in the report
- Produces a `IEEEtran` two-column `.tex` file + `references.bib`
- Inserts labeled figure placeholders you replace with real screenshots
- Runs a quality gate checklist before finalizing

## Structure

```
latex-report-creator/
├── SKILL.md                          # Main skill definition
├── templates/
│   ├── report-template.tex           # LaTeX skeleton (IEEEtran)
│   ├── report-template.md            # Markdown skeleton
│   └── figure-placeholders.md        # Figure placeholder format
├── reference/
│   ├── style-baseline.md             # Academic writing style rules
│   ├── requirements-mapping.md       # Requirement → section mapping guide
│   ├── image-policy.md               # Figure handling rules
│   ├── repo-evidence-sources.md      # Evidence gathering guide
│   └── companion-skill-routing.md    # Companion skill routing table
├── checklists/
│   └── quality-gate.md               # Final quality checklist
└── examples/
    └── sample-filled-outline.md      # Example filled report outline
```

## Usage

Install the skill into your Kiro skills directory, then ask:

```
Write an IEEE technical report for this project.
```

Or with a requirement document:

```
Write an IEEE technical report based on requirements.pdf.
```

The skill collects: requirement document (optional), target scope, output directory, report language, and author info — then builds the full report.

## Output

Every run produces:

1. `.tex` file using `\documentclass[conference]{IEEEtran}`
2. `references.bib` with all cited sources
3. Build README explaining how to compile
4. At least 3 labeled figure placeholders

## Key Rules

- No source code in the report — pseudocode only (IEEE `algorithm` environment)
- All figures are placeholders; real images are added manually
- Report language follows user preference (default: English)
- Requirement document drives section structure when provided; standard IEEE baseline otherwise

## License

MIT
