# Repository guidance

## Scope and files

- This repository is a reusable LaTeX dev-container, not an application with a package/test runner. The toolchain is defined by `.devcontainer/Dockerfile` and `.devcontainer/devcontainer.json`.
- Root-level `.tex` files are document entrypoints, but `.gitignore` deliberately ignores all `*.tex`. Treat any such files as local user content; do not delete or force-add them unless the task explicitly requires versioning them.
- Builds and auxiliary files belong in ignored `out/`; do not commit generated PDFs or LaTeX artifacts.

## Container workflow

- Open the repository with **Dev Containers: Reopen in Container** before building. The workspace is bind-mounted at `/workspace`, and the container name is `latex-<repository-folder-name>` (currently `latex-latex-builder`).
- The host-side `./scripts/latex` wrapper requires that container to already be running. Its default input is `main.tex`, which is not supplied, so pass the actual root document explicitly.
- Focused commands: `./scripts/latex lint <file.tex>`, `./scripts/latex build <file.tex>`, `./scripts/latex format <file.tex>`, and `./scripts/latex clean <file.tex>`. `format` uses `latexindent -w` and rewrites the source.
- For a document change, run lint and then build that document. There is no separate automated test suite or CI workflow.
- LaTeX Workshop formats, lints, and builds on save; it uses `latexmk -pdf`, SyncTeX, and `out/`. Auto-clean is disabled to preserve incremental build state.
