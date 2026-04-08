# LaTeX Coding Conventions

> Auto-generated codebase map

## Document Class & Theme

- **Class:** `moderncv` v2.4.1, `11pt` font, A4 paper (`main.tex` line 1)
- **Theme:** `classic` with blue color scheme (`main.tex` line 3)
- **Chinese support:** `ctex` package (`main.tex` line 5)
- **Margins:** Tight 0.5cm on all sides via `geometry` package (`main.tex` line 8)

## Section Structure

Sections are defined with `\section{}` and appear in this fixed order:

1. `\section{教育经历}` (Education)
2. `\section{工作经历}` (Work Experience)
3. `\section{实习经历}` (Internships)
4. `\section{获奖经历}` (Awards)
5. `\section{项目经历}` (Projects)
6. `\section{科研经历}` (Research)

All section titles are in Chinese. There is a `\newpage` before "项目经历" (line 127).

## Entry Format (`\cventry`)

Every resume entry follows the same `\cventry` pattern:

```latex
\cventry{time-period}{company/org}{department/field}{role}{award/extra}{
    \begin{itemize}
        \item <content>
    \end{itemize}
}
```

Parameters in order:
1. **Time period** -- Format: `YYYY.MM-YYYY.MM` or `YYYY-MM` ranges. Use `至今` for "present". Enclosed in `\small{}` for work entries.
2. **Company/organization** -- Wrapped in `\textcolor[RGB]{64,127,191}{...}` (the theme blue, RGB 64,127,191).
3. **Department or field** -- Plain text.
4. **Role/title** -- Plain text.
5. **Awards/bonus** -- Brief text, e.g. "获 spotbonus 3 次", or left empty `{}`.
6. **Body** -- Always an `\itemize` environment.

## Color Conventions

- **Company names and sub-roles:** Always highlighted with `\textcolor[RGB]{64,127,191}{...}` (blue, R=64 G=127 B=191).
  - Company: e.g. `\textcolor[RGB]{64,127,191}{字节跳动}` (lines 39, 70, 90, 100)
  - Sub-role headings within itemize: e.g. `\textcolor[RGB]{64,127,191}{商城营销活动方向负责人}` (line 41)
- **Metrics/achievements:** Wrapped in `\textbf{...}` to make them stand out.
  - Example: `渗透 7+\%`, `GMV\_ROI 长期显著 > 1`, `\textbf{100+\%}`, `\textbf{1000w+}QPS`
- No other custom colors are used beyond the theme blue.

## Metrics and Achievement Highlighting Pattern

Quantitative results always use one of two patterns:

1. **Bold only:** `\textbf{数字}` -- e.g. `\textbf{30\%}`, `\textbf{240+ms}`, `\textbf{1854}`
2. **Bold + context:** embedded in sentence -- e.g. `渗透 \textbf{7+\%}`, `pct99降低\textbf{90\%}`

Metric descriptions are always in Chinese, with units in English/standard notation (`\%`, `ms`, `QPS`, `UV`, `GMV`).

## Bullet Point Content Structure

Within each `\cventry`, body items follow this pattern:

```latex
\item \textcolor[RGB]{64,127,191}{sub-role or focus area label}
\newline \textbf{Category}：Description with \textbf{metrics}
\newline \textbf{Category}：Description with \textbf{metrics}
```

- Sub-role label is colored blue and on its own line.
- Achievement lines use `\newline` (not new `\item`) for multiple accomplishments under one sub-role.
- Each achievement line starts with a bold category label followed by a Chinese colon (`：`).
- Categories used: `业务建设`, `技术建设`, `稳定性建设`, `能效提升`, `商业化建设`, `玩法效率探索`, `全链路效能提升`, `问题预防`, `链路治理`, `监控建设`, `报警治理`, `压测提效`, `工具建设`, `专项重保`.

## List Items (`\cvlistdoubleitem`)

Used for the awards section only (lines 123-124). Two items per row, Chinese text with `\textbf{}` for rankings.

## Language

- **Section titles:** Chinese only
- **Work/internship descriptions:** Chinese, with English terms for technical concepts (GMV, QPS, ROI, SDK, SOP, etc.)
- **One internship entry is in English:** Shopee@Singapore entry (line 100-104)
- **Research/publiciation:** English (IEEE citation format, line 141)

## Spacing & Formatting

- Blank lines between `\cventry` entries (2-3 blank lines)
- No indentation inside `\itemize` blocks
- `\newline` used for line breaks within items (not blank lines)
- Multiple consecutive blank lines appear between sections (aesthetic, no functional impact)

## Escaped Characters

- Percent sign: `\%` (always escaped)
- Greater-than: `>` used directly in some places, `\_` for underscores (e.g. `GMV\_ROI`)
- Tilde: `~` used as non-breaking space in some places

## Photos & Personal Info

- Photo file: `photo.png` (line 19), 50pt height
- Personal fields use `\firstname`, `\familyname`, `\title`, `\mobile`, `\email`, `\homepage`, `\social`
- `\quote` used for job title display: `\textbf{研发工程师}` (line 23)
- Page numbers suppressed: `\nopagenumbers{}` (line 27)

---

*Convention analysis: 2026-04-08*
