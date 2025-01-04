# Use the official Ubuntu 24.04 as the base image
FROM ubuntu:24.04

# Set environment variables to prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package list and install essential packages
RUN apt update && \
    apt install -y --no-install-recommends \
        build-essential \
        ca-certificates \
        clang \
        clang-18 \
        clang-tidy \
        cmake \
        curl \
        git \
        g++-14 \
        ninja-build \
        vim \
        wget \
        && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-14 90 && \
    update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-14 90 && \
    update-alternatives --install /usr/bin/cc cc /usr/bin/gcc 100 && \
    update-alternatives --set cc /usr/bin/gcc && \
    update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++ 100 && \
    update-alternatives --set c++ /usr/bin/g++

RUN update-alternatives --set gcc "/usr/bin/gcc-14" && \
    update-alternatives --set g++ "/usr/bin/g++-14"

# Print installation info
RUN gcc --version && g++ --version && cmake --version && ninja --version

# Set the default command to run when the container starts
CMD ["bash"]
