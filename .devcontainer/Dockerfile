FROM danteev/texlive

RUN apt-get update && \
    apt-get install -y make latexmk git && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

RUN tlmgr update --self && \
    tlmgr install fontawesome5 datetime2 datetime2-english datetime2-turkish