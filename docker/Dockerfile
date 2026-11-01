FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
      sudo locales ca-certificates \
      build-essential gcc-multilib \
      git wget curl file rsync cpio unzip zip \
      gawk python python3 perl \
      tofrodos iproute2 net-tools \
      libncurses5-dev zlib1g-dev libssl-dev \
      flex bison libselinux1 gnupg diffstat chrpath socat \
      xterm autoconf automake libtool texinfo \
      libsdl1.2-dev libglib2.0-dev zlib1g:i386 \
      lib32z1 lib32ncurses5 lib32ncursesw5 lib32gomp1 \
      screen pax gzip bc u-boot-tools device-tree-compiler && \
    locale-gen en_US.UTF-8 && \
    ln -sf /bin/bash /bin/sh && \
    rm -rf /var/lib/apt/lists/*

ARG USER_UID=1000
ARG USER_GID=1000

RUN groupadd --gid ${USER_GID} builder && \
    useradd --uid ${USER_UID} --gid ${USER_GID} \
      --create-home --shell /bin/bash builder

ENV LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8

USER builder
WORKDIR /work
CMD ["/bin/bash"]
