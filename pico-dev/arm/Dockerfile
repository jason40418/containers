##
#  @file
#  Dockerfile for building Raspberry Pico firmware on Ubuntu Linux.
#
#  This file containing the below combination of software:
#    - Ubuntu 24.04
#    - GCC ARM
#    - Python 3.12
#
#  @copyright
#  Copyright (c) 2025, Jason Lin. All rights reserved.<BR>
#
#  SPDX-License-Identifier: BSD-3-Clause
#
#  @par reference
#
##

FROM ubuntu:24.04

#
# Arguments for building the container image.
#
ARG PYTHON_VERSION=3.12

#
# Add the required apt repositories.
#
RUN apt update && \
    apt install -y \
      software-properties-common

RUN add-apt-repository -y ppa:deadsnakes/ppa && \
    apt update

RUN apt install -y \
      build-essential \
      cmake \
      gcc-arm-none-eabi \
      g++ \
      libnewlib-arm-none-eabi \
      libstdc++-arm-none-eabi-newlib \
      libusb-1.0-0-dev \
      pkg-config \
      python${PYTHON_VERSION} \
      python${PYTHON_VERSION}-dev \
      python3-pip \
      python3-setuptools \
      python3-wheel

#
# Set the link files for changing the default application versions.
#
RUN ln -sf /usr/bin/python3 /usr/bin/python && \
    ln -sf /usr/bin/python${PYTHON_VERSION} /usr/bin/python3

#
# Install the required git packages.
#
RUN apt install -y \
      git \
      git-lfs

#
# Git system configuration.
#
RUN git config --system --add safe.directory "*"

ENTRYPOINT [ "/bin/bash" ]
