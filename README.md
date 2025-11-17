# LaTeX Dev Container

This repository provides a lightweight VS Code Dev Container template for working on LaTeX-based documents with a consistent toolchain. Build and preview your sources directly inside the container and share the same setup across machines without touching the host environment.

## Features

- **Docker-based environment:** Built on top of the `danteev/texlive` image and extended with everyday CLI tools such as `make`, `latexmk`, and `git`.
- **Up-to-date LaTeX packages:** `tlmgr` installs `fontawesome5` plus the `datetime2` family with both English and Turkish localizations.
- **VS Code integration:** Opening the Dev Container automatically installs LaTeX Workshop, other LaTeX helpers, Docker tooling, and the ChatGPT extension.
- **Opinionated workflow:** LaTeX Workshop runs the `latexmk` recipe on every save, keeps the build directory tidy, and presents the PDF preview inside an editor tab.
- **Formatting and IntelliSense:** `latexindent` powers format-on-save, package-aware completions stay enabled, and LaTeX Workshop only surfaces logs when errors appear.

## Quick Start

1. Open the repo with VS Code and run **Dev Containers: Reopen in Container**.
2. Place your `.tex` files at the project root so LaTeX Workshop and `latexmk` pick them up without extra configuration.
3. After the container starts, LaTeX Workshop runs `latexmk` whenever you save a document and produces the PDF automatically.
4. For manual builds, run `latexmk -pdf <document-name>` in the integrated terminal; use `latexmk -c` to clean auxiliary artifacts.
5. Default settings keep the PDF preview in an editor tab with double-click SyncTeX navigation.

## Dev Container Details

- The container is named `latex-dev`, and VS Code launches it with `--name=latex-devcontainer`.
- Global `editor.formatOnSave` is enabled, with James-Yu LaTeX Workshop configured as the default formatter for `.tex` files.
- JSON and JSONC documents are formatted through the Prettier extension.

## Contributing & License

Feel free to extend the container configuration—for instance, install extra TeX packages with `tlmgr install <package>`. This project is distributed under the terms listed in [`LICENSE`](LICENSE).
