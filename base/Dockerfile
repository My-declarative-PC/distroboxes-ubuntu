FROM ubuntu:latest

USER root

RUN apt update && \
    apt upgrade -y && \
    apt install -y \
        build-essential \
        curl \
        file \
        git \
        nala \
        procps \
        xsel \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/* /var/tmp/*

RUN ln -s /run/host/home/linuxbrew /home/linuxbrew && \
    curl -fL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh -o /usr/bin/brew-install.sh && \
    chmod +x /usr/bin/brew-install.sh
