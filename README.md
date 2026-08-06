# Connor Savugot Resume

This repository keeps each major résumé design in a separate, self-contained revision folder.

The [`experience/`](experience/) folder stores detailed source material for future résumé revisions, including teaching, AEGIS, TEAM Industries, senior design, and ECE 306 experience.

## Revisions

| Revision | Description |
| --- | --- |
| [`Rev0/`](Rev0/) | Reconstructed November 2024 résumé using the original Source Sans layout, gray contact banner, icon links, ruled headings, and legacy content. `.build/legacy-reference.pdf` is the original uploaded PDF used to verify the reconstruction. |
| [`Rev1/`](Rev1/) | Compact one-page embedded-firmware résumé created before the visual redesign. |
| [`Rev2/`](Rev2/) | Current content presented in the Rev0 visual style, with the expanded AEGIS, BMS, senior-design, soldering-instructor, and teaching-assistant experience. |

Each revision root contains:

- `Resume.tex` — self-contained LaTeX source, including contact information
- `Resume.pdf` — compiled résumé
- `.build/` — hidden directory for LaTeX intermediates such as `.aux`, `.log`, `.fls`, and SyncTeX files

## Building

VS Code's LaTeX Workshop is configured by [`.vscode/settings.json`](.vscode/settings.json) to keep the final PDF beside the source and send every intermediate file to `.build/`.

For the same behavior from a terminal, run this from the desired revision directory:

```sh
cd Rev2
latexmk -pdf -synctex=0 -emulate-aux-dir -auxdir=.build -outdir=. Resume.tex
```

Use `latexmk -C -auxdir=.build -outdir=. Resume.tex` to clean generated outputs. SyncTeX is disabled so it does not place a `.synctex.gz` file beside the PDF. The `.build/` name is used because these files are compiler outputs, not dependencies.
