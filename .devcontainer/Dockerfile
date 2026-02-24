FROM mcr.microsoft.com/devcontainers/go:1.24-bookworm

# Install node environment and Python 3 (required for Spec Kit)
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    nodejs graphviz npm python3 python3-pip \
    && rm -rf /var/lib/apt/lists/*

USER vscode

# Install go swagger
RUN go install github.com/swaggo/swag/cmd/swag@latest

# Install uv and Spec Kit (specify-cli) for Spec-Driven Development
RUN curl -LsSf https://astral.sh/uv/install.sh | sh \
    && export PATH="$HOME/.local/bin:$PATH" \
    && uv tool install specify-cli --from git+https://github.com/github/spec-kit.git