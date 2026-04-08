# Codebase Concerns

**Analysis Date:** 2026-04-08

## Critical

### No .gitignore File

- Issue: No `.gitignore` file exists. Generated files (`main.pdf`, `main.aux`, `main.log`, `main.out`, `book.aux`, `misc.aux`, `main.backup.pdf`) are not tracked in git (currently only `main.tex` and `photo.png` are tracked), but untracked generated files will show up as noise in `git status`. There is no protection against accidentally committing a large PDF binary or log files.
- Files: Entire project root
- Impact: Risk of committing generated binaries (250KB+ PDFs, 44KB log files) to version control, bloating repository history.
- Fix approach: Create a `.gitignore` with entries for `*.pdf`, `*.aux`, `*.log`, `*.out`, `*.synctex.gz`, `missfont.log`, and backup files (`backup_*.txt`, `current_text.txt`, `*.pdf.original`).

### Missing Build Script / Makefile

- Issue: No Makefile, build script, or any automation exists. The build command is `xelatex main.tex` run manually. No documentation of the required build command exists in the repository.
- Files: Project root (missing file)
- Impact: Anyone cloning this repo must figure out the build process by reading the `.log` file or guessing. Builds are not reproducible across machines.
- Fix approach: Add a `Makefile` with at least `build`, `clean`, and `open` targets. Example: `build: xelatex main.tex && xelatex main.tex` (double pass for references).

### Font Dependency Issue

- Issue: `missfont.log` at line 1 contains `mktexpk --mfmode / --bdpi 600 --mag 1+57/600 --dpi 657 unisong8b`, indicating a missing font (`unisong8b`) that XeTeX tried to generate at build time.
- Files: `missfont.log`
- Impact: Build may fail or produce incorrect output on machines that do not have the required Chinese fonts installed. The `ctex` package in `main.tex` (line 5) depends on system-specific Chinese font availability.
- Fix approach: Document required fonts in a README. Consider using `fontspec` with explicit font paths, or bundle font requirements. Test build on a clean machine.

## High

### Monolithic Single-File Content

- Issue: All resume content -- 142 lines of dense LaTeX -- lives in a single file `main.tex`. The file mixes document class configuration (lines 1-27), education (lines 32-34), work experience (lines 37-94), internships (lines 108-120), awards (lines 122-124), projects (lines 129-136), and research (lines 140-141) in one unstructured block.
- Files: `main.tex` (12,185 bytes, 142 lines)
- Impact: Editing a specific section requires navigating the entire file. Risk of accidentally modifying unrelated sections. Difficult to reuse sections for different resume versions (e.g., full resume vs. one-page summary).
- Fix approach: Split content into separate `.tex` files per section (`sections/education.tex`, `sections/work.tex`, etc.) and `\input{}` them from `main.tex`.

### Backup File Proliferation

- Issue: Three near-identical backup text files exist with no clear versioning strategy:
  - `backup_full_content.txt` (118 lines)
  - `backup_text.txt` (119 lines)
  - `current_text.txt` (116 lines)
  - `main.backup.pdf` (250KB)
  - `main.pdf.original` (250KB, identical size to `main.backup.pdf`)
- Files: All five files in project root
- Impact: Confusion about which backup is current. These files are untracked by git (shown as `??` in git status), meaning they serve no version control purpose since git itself tracks history.
- Fix approach: Remove all backup files. Git history already preserves previous versions. If plain-text extraction is needed, add a build target that extracts text via `pdftotext`.

### No Separation of Content from Presentation

- Issue: Resume content (job descriptions, achievements, metrics) is embedded directly in LaTeX formatting commands. For example, line 42 mixes content with `\newline`, `\textbf{}`, and `\textcolor[RGB]{64,127,191}{}`.
- Files: `main.tex` lines 40-63
- Impact: Content updates require understanding LaTeX syntax. Cannot reuse content for other formats (e.g., plain text for online forms, HTML for web version).
- Fix approach: Store resume data in a structured format (YAML/JSON) and generate LaTeX from a template. Alternatively, use `\input{}` for content-only sections.

## Medium

### No CI/CD or Automation

- Issue: No GitHub Actions workflow, no CI pipeline, no automated build verification. Git commits use informal messages like `[fix]更新简历` without conventional commit format.
- Files: `.github/workflows/` (missing)
- Impact: No guarantee that the PDF builds correctly after each commit. No automated deployment of the compiled PDF.
- Fix approach: Add a GitHub Actions workflow that runs `xelatex` on push and uploads the compiled PDF as an artifact.

### Binary Asset in Version Control

- Issue: `photo.png` (58KB binary) is tracked in git. Binary files are not diff-able and inflate repository size over time with each change.
- Files: `photo.png`
- Impact: Each photo update adds 58KB to repository history permanently.
- Fix approach: Acceptable for a single small image. If photos change frequently, consider Git LFS or external storage.

### Commit Message Quality

- Issue: All commit messages are in Chinese with informal format (`[fix]更新简历`, `[feat]添加项目`). No conventional commit format, no English fallback, no detailed commit body.
- Impact: Makes automated changelog generation impossible. Reduces readability for non-Chinese-speaking collaborators.
- Fix approach: Adopt conventional commits format: `fix(resume): update work experience section`.

### Tight Margins Hiding Content Overflow Risk

- Issue: `main.tex` line 8 sets margins to `0.5cm` on all sides. Combined with dense content and a forced page break at line 127 (`\newpage`), content may overflow silently.
- Files: `main.tex` line 8, line 127
- Impact: Adding content to either page could cause overflow without warning.
- Fix approach: Add visual overflow warnings during development. Consider using `\enlargethispage` for fine control instead of hardcoded margins.

## Low

### Hardcoded Personal Information

- Issue: Phone number (line 14), email (line 15), and GitHub username (line 17) are hardcoded in `main.tex`. No environment variable or config file abstraction.
- Files: `main.tex` lines 14-17
- Impact: Low -- personal info changes infrequently. But makes it harder to share a resume template without exposing personal details.
- Fix approach: Not urgent. If needed, extract to a `personal.tex` file that can be `.gitignore`-d.

### No README

- Issue: No README.md exists explaining the project, build instructions, or prerequisites (XeTeX, ctex package, specific fonts).
- Files: Project root (missing)
- Impact: New contributors or future-you must reverse-engineer the build process from `main.log`.
- Fix approach: Add a README.md with build instructions, prerequisites, and output description.

### LaTeX Package Versions Not Pinned

- Issue: The document relies on `moderncv` v2.4.1, `ctex`, and other packages from TeX Live 2025 (visible in `main.log` line 1). Package versions are not pinned or documented.
- Files: `main.log` lines 9-10
- Impact: Building on a different TeX Live version may produce different output.
- Fix approach: Document the tested TeX Live version in README. Consider using a Docker-based build environment for reproducibility.

### Stale Generated Files in Working Directory

- Issue: `main.aux`, `main.log`, `main.out`, `book.aux`, `misc.aux`, and `missfont.log` are present in the working directory as untracked files. The `.aux` files contain stale data from the last build.
- Files: `main.aux`, `main.log`, `main.out`, `book.aux`, `misc.aux`, `missfont.log`
- Impact: Clutter in working directory. May cause confusion about build state.
- Fix approach: Add a `clean` target to the Makefile: `rm -f *.aux *.log *.out missfont.log`. Add these to `.gitignore`.

---

*Concerns audit: 2026-04-08*
