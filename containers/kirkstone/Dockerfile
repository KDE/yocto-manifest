FROM ubuntu:20.04

RUN apt-get update

ENV DEBIAN_FRONTEND="noninteractive"
ENV TZ=Europe/Berlin

RUN apt-get update && apt-get -y install gawk \
    bash-completion \
    build-essential \
    bzip2 \
    chrpath \
    cpio \
    curl \
    debianutils \
    diffstat \
    gcc-multilib \
    git-core \
    git-lfs \
    gzip \
    iputils-ping \
    libsdl1.2-dev \
    locales \
    python \
    python3 \
    python3-pexpect \
    python3-subunit \
    python3-jinja2 \
    python3-git \
    python3-pip \
    socat \
    sudo \
    tar \
    texinfo \
    tmux \
    unzip \
    vim \
    wget \
    xterm \
    xz-utils \
    libegl1-mesa \
    mesa-common-dev \
    zstd \
    liblz4-tool \
    && apt clean

RUN pip3 install sphinx sphinx_rtd_theme pyyaml

RUN curl https://storage.googleapis.com/git-repo-downloads/repo > /usr/bin/repo && \
    chmod a+x /usr/bin/repo

RUN locale-gen en_US.UTF-8 && update-locale LC_ALL=en_US.UTF-8 \
    LANG=en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

ARG host_uid=1000
ARG host_gid=1000
ARG USER_NAME=yoctouser

# Ensure sudo group users are not
# asked for a password when using
# sudo command by ammending sudoers file
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN groupadd -g $host_gid $USER_NAME
RUN useradd -g $host_gid -G sudo -m -s /bin/bash -u $host_uid $USER_NAME

USER yoctouser
ENV LANG=en_US.UTF-8
WORKDIR /opt/yocto
CMD /bin/bash
