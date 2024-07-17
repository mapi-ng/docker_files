# Use the official Ubuntu 24.04 as the base image
FROM ubuntu:24.04

# Set environment variables to prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package list and install essential packages
RUN apt update && \
    apt install -y --no-install-recommends \
        build-essential \
        ca-certificates \
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

# Set the default command to run when the container starts
CMD ["bash"]