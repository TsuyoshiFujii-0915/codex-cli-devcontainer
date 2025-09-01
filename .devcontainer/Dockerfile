FROM node:22

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

# Set up non-root user
USER node

# Install uv for Python package management
RUN curl -LsSf https://astral.sh/uv/install.sh | sh