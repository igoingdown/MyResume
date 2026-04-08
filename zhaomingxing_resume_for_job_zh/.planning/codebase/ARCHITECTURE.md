# Architecture
> Auto-generated codebase map

## Pattern Overview

**Overall:** Single-file moderncv LaTeX resume document

**Key Characteristics:**
- All content in one file: `main.tex` (145 lines)
- Uses `moderncv` document class (v2.4.1) with `classic` theme and blue accent
- Compiled with XeTeX (TeX Live 2025) to produce a 3-page A4 PDF
- Chinese language support via `ctex` package with UTF-8 encoding

## Document Structure

The document follows a linear narrative flow through six sections:

### Preamble (lines 1-30)
- Document class: `moderncv`, 11pt, A4 paper
- Theme: `classic` with blue accent (`\moderncvtheme[blue]{classic}`)
- Margins: 0.5cm all sides (line 8)
- Packages: `inputenc`, `ctex`, `graphicx`, `multibib`
- Contact info defined via moderncv macros (lines 11-19)
- Page numbers disabled (`\nopagenumbers{}`)

### Contact Info Configuration (lines 11-19)
Each field uses a dedicated moderncv macro:
- `\firstname{赵明星}` -- Name
- `\title{Golang,Python,C++}` -- Skills/title
- `\mobile{(+86) 188 1086 0130}` -- Phone
- `\email{zhaomingxingDL@gmail.com}` -- Email
- `\homepage{igoingdown.github.io}` -- Website
- `\social[github]{igoingdown}` -- GitHub
- `\photo[50pt]{photo.png}` -- Profile photo (58KB PNG)

### Content Sections

| Section | Lines | Page | Entry Count | Content Pattern |
|---------|-------|------|-------------|-----------------|
| 教育经历 | 32-34 | 1 | 2 | `\cventry` per degree |
| 工作经历 | 37-94 | 1-2 | 4 | `\cventry` + `\begin{itemize}` |
| 实习经历 | 108-120 | 2 | 2 | `\cventry` + `\begin{itemize}` |
| 获奖经历 | 122-125 | 2 | 2 pairs | `\cvlistdoubleitem` (two-column) |
| 项目经历 | 129-136 | 3 | 1 | `\cventry` + `\begin{itemize}` |
| 科研经历 | 140-141 | 3 | 1 | `\cventry` with paper citation |

### Page Break (line 127)
`\newpage` at line 127 separates:
- **Page 1-2:** Education, Work experience, Internships, Awards
- **Page 3:** Project experience, Research experience

## moderncv Command Patterns

### `\cventry` -- Primary content block
```
\cventry{dates}{organization}{department}{role}{award}{description}
```
Used for all work, internship, project, and research entries. The 6th argument always wraps a `\begin{itemize}...\end{itemize}` block with bullet points. Empty fields use `{}` (e.g., lines 90, 100, 130, 141).

### `\cvlistdoubleitem` -- Two-column list
Used only in the Awards section (lines 123-124) for compact two-column display.

### Bullet point structure
Each item follows a consistent pattern:
```
\item \textcolor[RGB]{64,127,191}{Role/Area Label}
\newline \textbf{Category}：Detail with \textbf{metric} emphasis
```

## Styling Approach

| Pattern | Purpose | Usage |
|---------|---------|-------|
| `\textcolor[RGB]{64,127,191}{...}` | Blue emphasis on role/area headers | Throughout work/internship items |
| `\textbf{...}` | Bold for metrics, categories, key results | Every bullet point |
| `\small{dates}` | Compact date display | First arg of `\cventry` in work sections |
| `\newline` | Line break within item | Separates header from detail text |

The color `\textcolor[RGB]{64,127,191}` (medium blue) matches the `moderncvtheme[blue]` accent and is used consistently as a visual marker for role/area labels.

## Dependencies

- `moderncv` v2.4.1 -- Document class providing resume layout, `\cventry`, `\maketitle`, etc.
- `ctex` -- Chinese typesetting support (requires XeTeX engine)
- `graphicx` -- Photo embedding (`\photo` command)
- `multibib` -- Multiple bibliography support (declared but not used in body)
- `inputenc` -- UTF-8 input encoding
- `photo.png` -- External asset (58KB), embedded at compile time

## Error Handling

No explicit error handling. The document relies on moderncv's defaults. If `photo.png` is missing, compilation will fail with a LaTeX file-not-found error.

## Cross-Cutting Concerns

**Logging:** Not applicable (static document)
**Validation:** Not applicable (static document)
**Authentication:** Not applicable

---

*Architecture analysis: 2026-04-08*
