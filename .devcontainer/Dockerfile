FROM danteev/texlive:latest

# danteev/texlive already contains a full TeX Live installation,
# including latexmk and the common TeX packages. Keep apt only for
# general development tools that are useful inside the dev container.
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      git \
      make \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

# Fail the image build early if an expected LaTeX tool is missing.
RUN command -v latexmk >/dev/null && \
    command -v latexindent >/dev/null && \
    command -v chktex >/dev/null
