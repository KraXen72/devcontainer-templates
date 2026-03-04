FROM registry.fedoraproject.org/fedora:43

ARG PYTHON_VERSION=3.12

RUN dnf -y upgrade \
    && dnf -y install \
        ca-certificates \
        chromium-headless \
        curl \
        git \
        golang \
        python${PYTHON_VERSION} \
        python${PYTHON_VERSION}-pip \
        shadow-utils \
        sudo \
        unzip \
        xz \
    && ln -sf /usr/bin/python${PYTHON_VERSION} /usr/bin/python3 \
    && ln -sf /usr/bin/python${PYTHON_VERSION} /usr/bin/python \
    && ln -sf /usr/bin/pip${PYTHON_VERSION} /usr/bin/pip3 \
    && ln -sf /usr/bin/pip${PYTHON_VERSION} /usr/bin/pip \
    && ln -sf /usr/lib64/chromium-browser/headless_shell /usr/bin/headless_shell \
    && mkdir -p /go/bin \
    && dnf clean all

ENV GOPATH=/go
ENV PATH=/go/bin:${PATH}
ENV ROD_CHROME_BIN=/usr/bin/headless_shell
