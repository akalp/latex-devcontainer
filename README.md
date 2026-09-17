# LaTeX Dev Container

This repository provides a lightweight VS Code Dev Container template for working on LaTeX-based documents with a consistent toolchain. Build and preview your sources directly inside the container and share the same setup across machines without touching the host environment.

## Features

- **Full TeX Live environment:** Built from `danteev/texlive:latest`, which supplies TeX Live, common packages, `latexmk`, `latexindent`, and `chktex`. The image also installs `git` and `make`.
- **VS Code integration:** The Dev Container installs LaTeX Workshop and Prettier.
- **Build and lint on save:** LaTeX Workshop builds with `latexmk`, lints with `chktex`, and reports file-and-line errors.
- **Incremental output:** PDFs and auxiliary files are written to `out/`. Automatic cleanup is disabled so `latexmk` can reuse incremental build state.
- **Formatting and preview:** `latexindent` formats LaTeX on save, package-aware completions remain enabled, and PDFs open in an editor tab with SyncTeX navigation.

## Quick Start

1. Open the repo with VS Code and run **Dev Containers: Reopen in Container**.
2. Place your `.tex` documents at the project root and open the document you want to build.
3. Save the document to format, lint, and build it. The generated PDF and auxiliary files appear in `out/`.
4. Use the following commands in the container for manual builds and cleanup:

   ```bash
   latexmk -pdf -interaction=nonstopmode -file-line-error -synctex=1 -outdir=out <file.tex>
   latexmk -C -outdir=out <file.tex>
   ```

5. Open the PDF in a VS Code tab; double-click it to navigate back to the corresponding source through SyncTeX.

Once the Dev Container is running, the host-side helper provides the same focused workflow:

```bash
./scripts/latex lint <file.tex>
./scripts/latex build <file.tex>
./scripts/latex format <file.tex>
./scripts/latex clean <file.tex>
```

Always pass a filename unless your document is named `main.tex`, which is the helper's default.

## Dev Container Details

- VS Code displays the Dev Container as `latex-dev`; Docker names it `latex-<repository-folder-name>`.
- The repository is bind-mounted at the stable `/workspace` path inside the container.
- Global `editor.formatOnSave` is enabled, with James-Yu LaTeX Workshop configured as the default formatter for `.tex` files.
- JSON and JSONC documents are formatted through the Prettier extension.
- The image build verifies that `latexmk`, `latexindent`, and `chktex` are available and fails early if any are missing.

## Contributing & License

Extend `.devcontainer/Dockerfile` if a document requires tools or TeX packages not provided by the base image. This project is distributed under the terms listed in [`LICENSE`](LICENSE).
