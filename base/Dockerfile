FROM ubuntu:latest

USER root

RUN apt update && \
    apt upgrade -y && \
    apt install -y nala && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN ln -s /run/host/home/linuxbrew /home/linuxbrew
