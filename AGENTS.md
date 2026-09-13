# Project context

This repository contains Filipe Fuentes Giroleti's Brazilian Portuguese LaTeX
memorial for the Software Engineering bachelor's degree at PUCRS. It documents
his experience across four AGES courses (Agência Experimental de Engenharia de
Software). According to the author, this practical sequence replaces the
traditional undergraduate final dissertation: the university receives and
selects stakeholder proposals, then assigns student teams to develop open-source
MVPs/POCs for them. The report combines project artifacts, individual
contributions, and reflection on technical and interpersonal learning.

## Responsibilities across the four courses

These are the author's description of the course roles, not proof of what he
personally delivered in any particular project:

| Course | Main responsibility |
| --- | --- |
| AGES I | Intern-like role: learn and implement code. |
| AGES II | Data modeling: conceptual and logical database schemas, relational or NoSQL according to project needs. |
| AGES III | Technical leadership and architecture: technology selection, infrastructure provisioning (including AWS), deployment diagrams, CI/CD, and MR/PR review and approval. |
| AGES IV | Project management: stakeholder communication, team/squad organization, agile practices (usually a Scrum/Kanban mix), and technical and interpersonal support. |

## Repository map

- `main.tex`: document entry point and chapter ordering; `abntex2`, A4, 12pt,
  Brazilian Portuguese, numeric `biblatex` citations.
- `util/style.tex`: shared typography, spacing, captions, links, and layout.
- `util/util.tex`: LaTeX usage examples, not included by `main.tex`; it is not a
  production macro library.
- `conteudo/0 - pre/`: cover metadata, dedication, acknowledgments, epigraph,
  abstract, lists, acronyms, and table of contents.
- `conteudo/1 - apresentacao/apresentacao.tex`: the author's academic and
  professional trajectory.
- `conteudo/2 - ages I/`: Vítimas de Crime.
- `conteudo/3 - ages II/`: Soul Amada.
- `conteudo/4 - ages III/`: WeConecta.
- `conteudo/5 - ages IV/`: fourth-course chapter, currently a template.
- `conteudo/6 - consideracoes/consideracoes.tex`: overall closing reflection.
- `conteudo/7 - pos/referencias.tex`: bibliography printing.
- `conteudo/8 - apendices/apendices.tex`: appendices.
- `bibliografia/bibliografia.bib`: bibliography entries.
- `main.pdf`: tracked compiled artifact; do not assume it matches current sources.

Each AGES chapter has an `index.tex` including introduction, development,
activities, and conclusion files under `conteudo/`. Activities include individual
`sprints/sprint 0.tex` through `sprint 4.tex`. Images live in the chapter's
`conteudo/figures/`. Paths contain spaces and sometimes accented characters;
quote shell paths and preserve filenames.

## Writing and evidence

- Write document content in Brazilian Portuguese. Follow the user's language
  for conversation.
- Preserve the author's first-person voice in activities and reflections,
  including candid criticism and self-criticism. Improve clarity without
  inventing feelings, sanitizing criticism into generic praise, or exaggerating
  achievements. Keep descriptions of team artifacts distinct from personal work.
- Use the relevant chapter and sprint files plus user-provided facts as evidence
  for personal history. Never invent dates, stakeholders, deliveries, metrics,
  citations, or experiences to fill a gap. Ask for missing facts when needed.
- Distinguish planned architecture from what was actually delivered. For example,
  WeConecta's final sprint records working backend deployment automation but
  unfinished frontend automation; broad technology summaries must respect that.
- Treat template instructions and sample references as placeholders, not facts.
  Do not infer the AGES IV project from neighboring repositories.
- Preserve the existing chapter structure and institutional formatting unless
  the task calls for changes. Read nearby template comments for section guidance.
- For new or revised figure mentions, prefer `Figura~\ref{...}` over hardcoded
  numbers. Use unique labels after captions, preserve source credits (`Fonte:`),
  and follow nearby figure conventions (`[H]`, centered, usually full width).
- Reuse acronym keys from `conteudo/0 - pre/0.8 - siglas.tex` via `\ac{...}`;
  define new keys there when needed. Use `\url{...}` for links and escape LaTeX
  special characters in prose. Add real bibliography entries for sourced claims.

## Current state and known gaps

Snapshot from the initial review, 2026-09-13; recheck before acting. This is a
navigation aid, not a request to fix everything automatically.

- AGES I–III contain substantial prose, figures, sprint reports, and conclusions.
  AGES IV, the abstract, and overall final considerations still contain template
  instructions. The appendix contains a sample entry.
- Cover metadata includes `\fim{YYYY}`, AGES II, and 2024; `\author{Gustavo}`
  differs from the displayed author Filipe Fuentes Giroleti. Confirm intended
  submission metadata before updating it.
- AGES II's introduction gives dates in August–November 2023, overlapping AGES I.
  Confirm the actual dates rather than guessing a replacement year.
- Bibliography entries are template examples. References and factual claims
  still need a dedicated sourcing pass.
- Hardcoded figure numbers and some captions need consistency review; the final
  WeConecta infrastructure figure is still captioned as initial infrastructure.

## Build and verification

No Dockerfile, Compose file, build script, or CI configuration was found in the
initial review. The author has a Docker-based setup on another laptop; do not
assume its image or commands. At initial inspection, `latexmk`, `pdflatex`,
`xelatex`, `lualatex`, `biber`, and `docker` were unavailable on PATH here.
Check availability again in later environments.

With a suitable TeX distribution including `abntex2`, Portuguese language
support, the packages declared in `main.tex`/`util/style.tex`, and Biber, a
candidate build command from the repository root is:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

This command has not been verified in this environment. Without latexmk, the
expected sequence is pdfLaTeX, Biber (`biber main`), then pdfLaTeX twice.
Docker is optional. If compilation is unavailable, perform relevant source
checks and explicitly report that the PDF was not rebuilt or visually checked.
Do not treat an existing PDF as proof that edits compile.

For document changes, check affected include/image paths, references, citation
and acronym keys, and LaTeX syntax. When compilation is available, inspect build
warnings and relevant PDF pages for layout issues. Avoid incidental changes to
the tracked `main.pdf`; regenerate it when the task calls for a refreshed PDF.

## Continuing work across sessions

Start with `git status --short`, this file, `main.tex`, and the files relevant to
the requested chapter or topic. Preserve unrelated user changes. Keep this file
up to date when the user confirms durable project facts, resolves the gaps above,
or establishes a working build workflow. Keep transient logs out of this file.
