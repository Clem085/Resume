# Historical Resume and Cover-Letter Archive

This directory preserves Connor's recovered resume, cover-letter, and application history. Originals and exact duplicates are retained so a future targeted revision can be traced back to the document that supported each claim. The concise, normalized account of the work belongs in [`../experience/`](../experience/); historical drafts are evidence, not automatically current facts.

No source files were deleted during organization. Empty import folders were removed after their contents were moved. Original filenames were retained except for three duplicate NC State transcripts, which were renamed with their application context to prevent filename collisions.

## Directory Guide

- [`resumes/`](resumes/) — authored resumes, separated into LaTeX, PDF, and Word sources, then by supported date/application context
- [`cover-letters/`](cover-letters/) — authored PDF and Word cover letters; many files named `CV` are actually cover letters
- [`application-materials/`](application-materials/) — combined packets and the NVIDIA application questionnaire
- `private/` — transcripts, signature images, signature-bearing LaTeX cover-letter packages, the transcript-bearing NAVSEA packet, and a sensitive M.C. Dean draft
- `job-postings/` — saved AMD, Cirrus Logic, Dell, and Red Hat pages with their required asset directories
- [`legacy/`](legacy/) — unrelated samples, placeholder templates, classroom writing, and non-resume material
- [`INVENTORY.md`](INVENTORY.md) — audit totals, duplicate groups, mislabeled sources, privacy notes, and evidence rules

The `private/` and `job-postings/` trees remain available locally but are excluded by the repository's `.gitignore`. Do not commit them to a public repository without reviewing and sanitizing them.

## Dating and Provenance

- `2023-drafts` is based on dates embedded in filenames.
- `2024-summer` is based on dates and role language inside the documents, even when a recovered parent folder was named `2025_Summer`.
- `2025-summer` preserves the clearly targeted 2025 application set.
- `legacy-audit` contains the 36 files previously stored under `experience/history/`.
- `retrieved-root` and `undated-drafts` preserve source provenance where a reliable date was not established.
- Extracted LaTeX sources live beside their original ZIP archive in a `source/` directory. The cover-letter packages are private because all twelve archives contain handwritten-signature images.

LaTeX cover letters use `\today`; recompiling one now will not reproduce its historical application date. Rely on explicit dates inside the text and this archive classification instead.

## Known Source Problems

- `ConnorSavugot_CV_MCDean_`: the body targets M.C. Dean, but `info.tex` identifies Northrop Grumman.
- `ConnorSavugot_CV_SchneiderElectric_Firmware_Engineer_`: the metadata targets Schneider Electric, but the body targets a Lenovo server-hardware role.
- `ConnorSavugot_CV__NorthropGrumman_`: the body is a CesiumAstro FPGA letter while the metadata targets Northrop Grumman.
- `ConnorSavugot_CV__CesiumAstro_`: its body and metadata name different CesiumAstro roles.
- `Red Minimalist Modern Cover Letter (1).pdf` is internally a Word document despite its `.pdf` filename. It remains unmodified under `cover-letters/word/legacy-lenovo/misnamed-extension/`.
- `resume_info__bad_format_.zip` is an obsolete/broken layout draft and is isolated under `resumes/latex/needs-review/`.

These files are preserved as historical evidence but must not be copied into a new application without review.

## How to Use the Archive

1. Start with the relevant file in [`../experience/`](../experience/).
2. Use this archive only to verify dates, titles, technologies, metrics, or original wording.
3. Prefer facts repeated across contemporaneous resumes or confirmed by an official record.
4. Treat one-off cover-letter claims as leads until Connor confirms them; cover letters also contain aspirational job-alignment language that is not prior experience.
5. Resolve every conflict listed in the experience source and [`INVENTORY.md`](INVENTORY.md) before publishing a targeted resume.
