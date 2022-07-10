# [Choice] Debian OS version: bullseye, buster
ARG VARIANT=bullseye
FROM --platform=linux/amd64 mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

ENV DENO_INSTALL=/deno
RUN mkdir -p /deno \
    && curl -fsSL https://deno.land/x/install/install.sh | sh \
    && chown -R vscode /deno

ENV PATH=${DENO_INSTALL}/bin:${PATH} \
    DENO_DIR=${DENO_INSTALL}/.cache/deno

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#    && apt-get -y install --no-install-recommends <your-package-list-here>

# build wabt
ARG WABT_VER=1.0.29

WORKDIR /workspaces
RUN curl -LO https://github.com/WebAssembly/wabt/releases/download/${WABT_VER}/wabt-${WABT_VER}-ubuntu.tar.gz \
    && tar zxvf wabt-${WABT_VER}-ubuntu.tar.gz

ENV WABT_HOME=/workspaces/wabt-${WABT_VER}
