FROM ghcr.io/my-declarative-pc/distroboxes-ubuntu-base

RUN nala update && \
    nala install --no-install-recommends -y \
    python3 \
    curl \
    nodejs \
    npm \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/* /var/tmp/*

### install UV
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/
###

### install LSP's
RUN uv tool install ruff@latest && \
    mv /root/.local/share/uv/tools/ruff/bin/ruff /usr/bin && \
    npm -g i pyright && \
    npm cache clean --force
###
