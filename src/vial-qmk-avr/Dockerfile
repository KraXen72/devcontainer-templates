FROM ghcr.io/kraxen72/fedora-toolchain-base:latest

ARG PYTHON_VERSION=3.12

USER root

RUN dnf -y upgrade && \
    dnf -y install \
        bash-completion \
        ca-certificates \
        curl \
        git \
        jq \
        less \
        man-db \
        nodejs \
        procps-ng \
        python${PYTHON_VERSION} \
        python3-pip \
        ripgrep \
        shadow-utils \
        sqlite3 \
        tree \
        unzip \
        util-linux \
        uv \
        wget \
        which \
        xz \
        zip \
        make \
        avr-binutils \
        avr-gcc \
        avr-libc \
        avrdude \
        dfu-programmer \
        dfu-util \
        hidapi \
        libusb1-devel && \
    ln -sf /usr/bin/python${PYTHON_VERSION} /usr/bin/python3 && \
    ln -sf /usr/bin/python${PYTHON_VERSION} /usr/bin/python && \
    ln -sf /usr/bin/pip3 /usr/bin/pip && \
    dnf clean all

RUN python3 -m pip install --no-cache-dir --upgrade pip && \
    python3 -m pip install --no-cache-dir \
        qmk \
        milc \
        hjson

RUN uv tool install "git+https://github.com/Nisker/vial-to-keymap.git" && \
    uv tool install keymap-drawer

ENV PATH="/home/vscode/.local/bin:${PATH}"

USER vscode
WORKDIR /home/vscode/workspace
