FROM node:22

ENV DEBIAN_FRONTEND=noninteractive \
    PLAYWRIGHT_BROWSERS_PATH=/ms-playwright \
    PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1

# Install basic development tools and iptables/ipset
RUN apt update && apt install -y less \
    git \
    procps \
    sudo \
    fzf \
    zsh \
    man-db \
    unzip \
    gnupg2 \
    gh \
    iptables \
    ipset \
    iproute2 \
    dnsutils \
    aggregate \
    jq

# Install Codex CLI
RUN npm install -g @openai/codex

# Create workspace and config directories and set permissions
RUN mkdir -p /workspace /home/node/.codex && \
    chown -R node:node /workspace /home/node/.codex
WORKDIR /workspace

# Install Playwright and browsers
RUN mkdir -p /ms-playwright && \
    npx -y playwright@latest install-deps chromium && \
    chown -R node:node /ms-playwright

# Set up non-root user
USER node

# Install uv for Python package management
RUN curl -LsSf https://astral.sh/uv/install.sh | sh