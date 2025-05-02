# Use the official Ubuntu 24.04 as the base image
FROM ubuntu:25.04

# Set environment variables to prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package list and install essential packages
RUN apt update && \
    apt install -y --no-install-recommends \
        build-essential \
        ca-certificates \
        clang \
        clang-20 \
        clang-tidy \
        curl \
        git \
        g++-15 \
        ninja-build \
        pipx \
        vim \
        wget \
        && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-15 90 && \
    update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-15 90 && \
    update-alternatives --install /usr/bin/cc cc /usr/bin/gcc 100 && \
    update-alternatives --set cc /usr/bin/gcc && \
    update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++ 100 && \
    update-alternatives --set c++ /usr/bin/g++

RUN update-alternatives --set gcc "/usr/bin/gcc-15" && \
    update-alternatives --set g++ "/usr/bin/g++-15"

# Install CMake 4 and Conan
RUN pipx ensurepath && pipx install conan cmake
RUN ln -s ~/.local/bin/conan /usr/bin/conan && \
    ln -s ~/.local/bin/cmake /usr/local/bin/cmake

# Print installation info
RUN gcc --version && g++ --version && cmake --version && ninja --version

# Install packages
COPY conan-profiles conan-profiles
RUN cd ./conan-profiles && ./conan-packages-installer.sh

# Set the default command to run when the container starts
CMD ["bash"]
