FROM ubuntu:24.04

# Install prerequisites
RUN DEBIAN_FRONTEND=noninteractive apt update -qy && \
    DEBIAN_FRONTEND=noninteractive apt upgrade -qy && \
    DEBIAN_FRONTEND=noninteractive apt install -qy \
        gcc \
        git \
        wget \
        make \
        libncurses-dev \
        flex \
        bison \
        gperf && \
    DEBIAN_FRONTEND=noninteractive apt purge -qy && \
    DEBIAN_FRONTEND=noninteractive apt autoremove -yq --purge && \
    DEBIAN_FRONTEND=noninteractive apt-get clean

# Toolchain setup
RUN wget https://dl.espressif.com/dl/xtensa-lx106-elf-gcc8_4_0-esp-2020r3-linux-amd64.tar.gz && \
    mkdir esp &&\
    tar -xzf xtensa-lx106-elf-gcc8_4_0-esp-2020r3-linux-amd64.tar.gz -C esp && \
    rm xtensa-lx106-elf-gcc8_4_0-esp-2020r3-linux-amd64.tar.gz    

ENV PATH "$PATH:/xtensa-lx106-elf/bin"
