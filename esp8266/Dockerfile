FROM ubuntu:24.04

SHELL ["/bin/bash", "-c"]

# Install prerequisites
RUN DEBIAN_FRONTEND=noninteractive apt update -qy && \
    DEBIAN_FRONTEND=noninteractive apt upgrade -qy && \
    DEBIAN_FRONTEND=noninteractive apt install -qy \
        python3 \
        python3-pip \
        python3-venv \
        cmake \
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

# Get RTOS SDK
RUN cd esp && \
    git clone --depth 1 --recursive https://github.com/espressif/ESP8266_RTOS_SDK.git

ENV PATH="$PATH:/esp/xtensa-lx106-elf/bin:/esp/esp-venv/bin"
ENV IDF_PATH="/esp/ESP8266_RTOS_SDK"
# for CMakePresets.json - CMake needs to use Python venv
ENV ESP_VENV="/esp/esp-venv"

RUN python3 -m venv /esp/esp-venv && \
    source /esp/esp-venv/bin/activate && \
    pip install -r $IDF_PATH/requirements.txt


