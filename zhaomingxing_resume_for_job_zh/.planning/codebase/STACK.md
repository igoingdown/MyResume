# Technology Stack
> Auto-generated codebase map

## Document Class

- **moderncv** v2.4.1 (2024-07-18) — LaTeX document class for curriculum vitae
- Options: `11pt, a4paper`
- Theme: `\moderncvtheme[blue]{classic}` — classic style with blue color scheme
- Source: `/usr/local/texlive/2025/texmf-dist/tex/latex/moderncv/moderncv.cls`

## LaTeX Packages

**Core resume:**
- `moderncv` v2.4.1 — Document class (includes moderncvcollection, moderncvcompatibility, moderncvcolorblue, moderncvstyleclassic)
- `moderncvstyleclassic` — Classic CV layout variant
- `moderncvheadi` — Header variant 1
- `moderncvbodyi` — Body variant 1
- `moderncvskillmatrix` — Skill matrix support

**Chinese language:**
- `ctex` v2.5.10 (2022/07/14) — Chinese adapter in LaTeX
- `xeCJK` v3.9.1 — Typesetting CJK scripts with XeLaTeX
- `zhnumber` v3.0 — Typesetting numbers with Chinese glyphs
- Font set: macOS (`ctex-fontset-mac.def`) — STSong (regular), STHeiti (bold), STKaiti (italic)

**Page layout and formatting:**
- `geometry` v5.9 — Page margins: top=0.5cm, bottom=0.5cm, left=0.5cm, right=0.5cm (from `main.tex` line 8)
- `fancyhdr` v5.2 — Page headers and footers
- `microtype` v3.2a — Micro-typographical refinements (character protrusion enabled)
- `multibib` v1.4 — Multiple bibliographies (declared `\newcites{book,misc}{{Books},{Others}}`)

**Graphics and icons:**
- `graphicx` v1.2d — Image inclusion (used for `photo.png`)
- `fontawesome5` v5.15.4 — Font Awesome 5 icons (free + brands)
- `academicons` v1.9.1 — Academic icons
- `pgf`/`tikz` v3.1.10 — Vector graphics

**Hyperlinks:**
- `hyperref` v7.01l — PDF hyperlinks and bookmarks
  - Driver: hxetex (auto-detected)
  - Options: `breaklinks=true`, `bookmarksopen=true`

**Encoding:**
- `inputenc` with `utf8` option — **Ignored** by XeTeX (log shows "inputenc package ignored with utf8 based engines") since XeTeX is natively UTF-8
- `fontspec` v2.9e — Font selection for XeLaTeX (loaded via xeCJK)

**Color:**
- `xcolor` v3.02 — Color extensions (CMY, RGB, HTML, Hsb, HSB, Gray, wave models)
- `colortbl` v1.0i — Color table columns

**Other bundled:**
- `etoolbox` v2.5l — e-TeX tools
- `calc` v4.3 — Infix arithmetic
- `xparse` — L3 document command parser
- `array` v2.6g — Tabular extensions
- `multirow` v2.9 — Multi-row table spans
- `arydshln` v1.76 — Dashed lines in arrays

## Build Toolchain

**Engine:** XeTeX (XeLaTeX)
- Version: XeTeX, Version 3.141592653-2.6-0.999997
- Format: xelatex 2025.8.24
- TeX Distribution: TeX Live 2025

**Build command:**
```bash
xelatex main.tex
```

**Why XeLaTeX:** Required by `ctex` package for native UTF-8 Chinese support. The ctex package auto-selects `ctex-engine-xetex.def` when running under XeLaTeX. XeLaTeX can directly use system fonts (STSong, STHeiti, STKaiti on macOS).

**Compilation passes:** Typically 2 passes needed for:
1. Cross-references and bookmarks (`main.aux`, `main.out`)
2. Page layout finalization

**Output:** `main.pdf` — 3 pages, ~258KB

## Character Encoding

- Source file: UTF-8
- Engine: XeTeX (natively handles UTF-8)
- Chinese fonts: macOS system fonts via ctex — STSong (宋体) as main, STHeiti (黑体) for bold, STKaiti (楷体) for italic
- Font encoding: TU (Unicode-aware font encoding)
- CJK punctuation kerning configured via xeCJK

## Page Configuration

- Paper: A4 (597.5pt x 845.0pt)
- Text area: 569.1pt x 816.6pt
- Margins: 0.5cm all sides (custom via geometry)
- Page numbers: Disabled (`\nopagenumbers{}`)

## Version Summary

| Component | Version | Source |
|-----------|---------|--------|
| TeX Live | 2025 | /usr/local/texlive/2025/ |
| XeTeX | 3.141592653-2.6-0.999997 | engine |
| LaTeX2e | 2024-11-01 patch 2 | kernel |
| moderncv | 2.4.1 (2024-07-18) | document class |
| ctex | 2.5.10 (2022/07/14) | CJK support |
| xeCJK | 3.9.1 (2022/08/05) | CJK typesetting |
| hyperref | 7.01l (2024-11-05) | PDF links |
| geometry | 5.9 (2020/01/02) | page layout |

---

*Stack analysis: 2026-04-08*
