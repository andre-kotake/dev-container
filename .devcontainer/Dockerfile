FROM buildpack-deps:jammy-curl

################################################################################
#
#   Add non root user
#   https://code.visualstudio.com/remote/advancedcontainers/add-nonroot-user#_creating-a-nonroot-user
#
################################################################################

ARG USERNAME="kotake"
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME
RUN useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

################################################################################
#
#   Install default packages
#
################################################################################
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get install -y --no-install-recommends \
    neovim \
    shellcheck \
    shfmt \
    neofetch \
    git \
    gh \
    python3-pip \
    pre-commit

RUN rm -rf /var/lib/apt/lists/*

RUN pip install --user -U \
    gitlint \
    Commitizen

# Set the default user. Omit if you want to keep the default as root.
USER $USERNAME
