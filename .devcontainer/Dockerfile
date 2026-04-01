FROM mcr.microsoft.com/devcontainers/python:3.13

ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    git \
    libffi-dev \
    gnupg2 \
    telnet \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install pipx and poetry
RUN pip install --user pipx && \
    pipx ensurepath && \
    pipx install poetry tox && \
    pipx inject poetry poetry-plugin-shell

# Install pyenv
ENV PYENV_ROOT=/home/vscode/.pyenv
ENV PATH="$PYENV_ROOT/bin:$PATH"

RUN curl -L https://pyenv.run | bash

# shell pyenv initialization
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc && \
    echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc && \
    echo 'eval "$(pyenv init --path)"' >> ~/.bashrc && \
    echo 'eval "$(pyenv init -)"' >> ~/.bashrc && \
    echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc


