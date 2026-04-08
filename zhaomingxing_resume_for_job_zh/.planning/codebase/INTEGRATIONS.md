# External Integrations
> Auto-generated codebase map

## External Assets

**Photo:**
- File: `photo.png` (58,036 bytes)
- Referenced at `main.tex` line 19: `\photo[50pt]{photo.png}`
- Format: BMP (despite `.png` extension — log confirms "Graphic file (type bmp)")
- Used as profile photo in the resume header, sized at 50pt

## Build Dependencies

**Required system packages (TeX Live 2025):**
- `xelatex` — XeTeX engine (core)
- `moderncv` — Document class v2.4.1
- `ctex` — Chinese support v2.5.10 (pulls in xeCJK, zhnumber, fontspec)
- `geometry` — Page layout v5.9
- `graphicx` — Image inclusion v1.2d
- `multibib` — Multiple bibliographies v1.4
- `hyperref` — PDF bookmarks v7.01l
- `fontawesome5` — Icons v5.15.4
- `academicons` — Academic icons v1.9.1
- `microtype` — Micro-typography v3.2a
- `fancyhdr` — Headers v5.2
- `tikz`/`pgf` — Vector graphics v3.1.10

**System fonts (macOS):**
- STSong — CJK main font (宋体)
- STHeiti — CJK bold font (黑体)
- STKaiti — CJK italic font (楷体)
- Latin Modern Roman — Latin text font

**Font resolution issue:**
- `missfont.log` shows a failed attempt to generate `unisong8b` via `mktexpk` (line 1 in `missfont.log`). This indicates a bitmap font was attempted but not generated. The build still succeeds because XeLaTeX falls back to system fonts via fontspec.

## Auxiliary Files (Generated During Build)

| File | Size | Purpose |
|------|------|---------|
| `main.pdf` | 258,496 bytes | Compiled resume output |
| `main.aux` | 741 bytes | Cross-reference data (section labels, page numbers) |
| `main.out` | 450 bytes | PDF bookmark outline data (UTF-16 encoded section names) |
| `main.log` | 44,551 bytes | Full compilation log |
| `book.aux` | 0 bytes | Auxiliary file for multibib "Books" bibliography (unused) |
| `misc.aux` | 0 bytes | Auxiliary file for multibib "Others" bibliography (unused) |
| `missfont.log` | 65 bytes | Font generation failure log |

**Note:** `.aux`, `.out`, and `.log` files are generated artifacts and should not be committed to version control. The `.aux` files are empty because no `\citebook` or `\citemid` entries are used despite `multibib` being loaded.

## Backup Files

| File | Size | Purpose |
|------|------|---------|
| `main.backup.pdf` | 250,898 bytes | Earlier compiled version of the resume |
| `main.pdf.original` | 250,898 bytes | Another earlier compiled version (same size as `main.backup.pdf`, likely identical) |
| `backup_full_content.txt` | 9,614 bytes | Full text backup of resume content (plain text extraction) |
| `backup_text.txt` | 9,612 bytes | Text backup of resume content (near-identical to above) |
| `current_text.txt` | 9,573 bytes | Current resume text content (slightly shorter, may reflect a revision) |

**Purpose:** These backup files preserve previous versions of the resume for comparison or recovery. The `.txt` files contain plain-text extractions of the resume content and are useful for diffing changes without parsing LaTeX source.

## No External API or Service Integrations

This project has no external API calls, webhooks, CI/CD pipeline, or remote service dependencies. It is a standalone LaTeX document compiled locally.

---

*Integration audit: 2026-04-08*
