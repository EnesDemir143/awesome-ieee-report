# awesome-ieee-report

An AI agent skill that generates IEEE-format technical reports as LaTeX. Point it at your project, and it reads the codebase, maps requirements to sections, and produces a publication-ready `.tex` + `.bib` output with zero code artifacts in the report body.

---

## Features

- **Requirement-driven structure** — reads your requirement document and derives section headings from it; falls back to standard IEEE baseline when no document is provided
- **Zero code artifacts** — no file paths, class names, or function names in the report body; everything is described in academic prose
- **Pseudocode only** — core algorithms are expressed using the IEEE `algorithm` environment, never raw source code
- **Figure placeholders** — labeled `\fbox{}` placeholders with capture intent; you replace them with real screenshots manually
- **BibTeX output** — generates a `references.bib` alongside the `.tex` file
- **Quality gate** — built-in checklist that verifies every rule before the report is finalized
- **Language-agnostic** — English by default; Turkish (or any babel-supported language) on request

---

## Key Topics

- IEEE `IEEEtran` conference class
- Two-column academic layout
- `booktabs` tables for parameters, thresholds, and comparisons
- `algorithm` + `algorithmic` environments for pseudocode
- BibTeX / `\cite{}` reference management
- Figure placeholder workflow
- Requirement-to-section mapping

---

## How to Use

**1. Install the skill**

Clone this repository into your agent's skills directory:

```bash
git clone https://github.com/EnesDemir143/awesome-ieee-report ~/.agents/skills/awesome-ieee-report
```

**2. Invoke**

```
Write an IEEE technical report for this project.
```

With a requirement document:

```
Write an IEEE technical report based on requirements.pdf.
Report language: English
Author: Jane Doe, Computer Engineering, MIT
```

**3. Provide inputs when prompted**

| Input | Required | Default |
|---|---|---|
| Requirement document (PDF/MD) | No | Standard IEEE baseline |
| Target scope | Yes | — |
| Output directory | Yes | — |
| Report language | No | English |
| Author name & affiliation | Yes | — |

**4. Compile the output**

```bash
pdflatex report.tex
bibtex report
pdflatex report.tex
pdflatex report.tex
```

Or use `latexmk`:

```bash
latexmk -pdf report.tex
```

**5. Replace figure placeholders**

Find every `\fbox{...PLACEHOLDER...}` block and replace with:

```latex
\setlength{\fboxsep}{0pt}\fbox{\includegraphics[width=0.57\linewidth]{images/your-screenshot.png}}
```

---

## Repository Structure

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

---

## Community & Feedback

Found a bug, have a suggestion, or want to contribute a template?

- **Issues** — open a [GitHub Issue](https://github.com/EnesDemir143/awesome-ieee-report/issues) for bug reports or feature requests
- **Discussions** — use [GitHub Discussions](https://github.com/EnesDemir143/awesome-ieee-report/discussions) for questions, ideas, and sharing reports you've generated
- **Pull Requests** — contributions are welcome; please keep changes focused and include a short description of what was changed and why

---

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

Quick summary:
- Fork → branch → commit → PR
- Keep changes focused and minimal
- Good targets: new example reports, checklist improvements, template variants, bug fixes in skill rules
- Do not add project-specific content (university names, course codes, etc.)

---

## License

MIT
