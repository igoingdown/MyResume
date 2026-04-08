# Build and Verification Patterns

> Auto-generated codebase map

## Build System

**Engine:** XeTeX (TeX Live 2025)
- Confirmed from `main.log` line 1: `XeTeX, Version 3.141592653-2.6-0.999997 (TeX Live 2025)`
- XeTeX is required because the project uses `ctex` for Chinese text rendering (standard pdfLaTeX cannot handle `ctex` properly).

**Build command:**
```bash
xelatex main.tex
```

**Run from:** Project root directory `/Users/bytedance/github/MyResume/zhaomingxing_resume_for_job_zh/`

**Multiple passes:** Typically requires 2 runs of `xelatex` to resolve cross-references and hyperlinks (first pass generates `.aux`, second resolves references). The `main.aux` file contains `\@writefile` entries that need a second pass for final output.

## Build Artifacts

All artifacts are generated in the project root:

| File | Purpose |
|------|---------|
| `main.pdf` | Final compiled resume output (258KB) |
| `main.aux` | Auxiliary file with cross-reference data |
| `main.log` | Full compilation log (44KB) -- check this for warnings/errors |
| `main.out` | Hyperref outline entries |
| `book.aux` | Multibib auxiliary for "Books" bibliography (empty) |
| `misc.aux` | Multibib auxiliary for "Others" bibliography (empty) |

**Backup files:**
- `main.backup.pdf` -- older compiled output (250KB)
- `main.pdf.original` -- another backup copy (250KB)

**Other text files (not build artifacts):**
- `backup_full_content.txt`, `backup_text.txt`, `current_text.txt` -- content backups in plain text

## How to Verify Output

1. **Check compilation exit code:** `xelatex main.tex` should exit with code 0.
2. **Inspect `main.log`:** Search for `!` (LaTeX error marker) or `Warning` lines. The log file is 44KB so use `grep`:
   ```bash
   grep "^!" main.log          # Fatal errors
   grep "Warning" main.log     # Warnings
   grep "Overfull\|Underfull" main.log  # Box overflow warnings (cosmetic)
   ```
3. **Open `main.pdf`:** Verify 3 pages, all sections rendered, Chinese text displays correctly.
4. **Check page count:** The `.aux` file shows `\gdef \@abspage@last{3}` -- the output should be exactly 3 pages.

## Font Issues

**`missfont.log`** contains:
```
mktexpk --mfmode / --bdpi 600 --mag 1+57/600 --dpi 657 unisong8b
```

This indicates a missing or fallback font generation attempt for `unisong8b` (a Chinese Song/Ming font). This is likely a non-critical warning from a previous run where the font was temporarily unavailable. The current build completed successfully (no errors in `main.log`), so this font issue has been resolved on the system. However, this file is a red flag on a fresh machine -- if `unisong8b` is missing on another system, Chinese characters may fail to render.

## No Automated Build/CI

- No `Makefile`, no `latexmk` config, no CI pipeline detected.
- No `.github/workflows/` directory.
- No `Dockerfile` or container-based build.
- Build is entirely manual: run `xelatex main.tex` twice, then check `main.pdf`.

## Recommended Build Workflow

```bash
# 1. Compile (run twice for references)
xelatex main.tex
xelatex main.tex

# 2. Check for errors
grep "^!" main.log

# 3. Verify page count
grep "abspage@last" main.aux

# 4. Open output
open main.pdf          # macOS
# or: xdg-open main.pdf  # Linux
```

## Clean Build

To start fresh, remove all generated artifacts:
```bash
rm -f main.aux main.log main.out main.pdf book.aux misc.aux
```

Then rebuild with two `xelatex` passes.

## Dependencies

Required packages (resolved automatically by TeX Live):
- `moderncv` v2.4.1 (document class)
- `ctex` (Chinese support)
- `geometry` (margins)
- `graphicx` (photo inclusion)
- `multibib` (multiple bibliographies)
- `inputenc` (UTF-8 encoding, noted as Windows in comment)

**Platform requirement:** TeX Live 2025 with XeTeX engine and Chinese font support installed. On macOS, the `unisong8b` font must be available (part of CJK font packages).

---

*Build analysis: 2026-04-08*
