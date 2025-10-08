# Builder image used in Rust build pipelines
FROM ubuntu:25.04 AS base

FROM ubuntu:25.04 AS base

RUN apt update && apt install -y \
  binutils \
  iproute2 \
  clang \
  clang-19 \
  curl \
  make \
  ca-certificates \
  pkg-config \
  gnupg \
  software-properties-common \
  wget \
  git \
  python-is-python3 \
  cgroup-tools \
  libstdc++-15-dev \
  gcc-15 \
  g++-15 \
  libcrypto++-dev \
  libhugetlbfs0 \
  libhugetlbfs-bin \
  libhugetlbfs-dev \
  libboost1.83-dev \
  libboost-atomic1.83.0 \
  libboost-container1.83.0 \
  libboost-fiber1.83.0 \
  libboost-fiber1.83-dev \
  libboost-filesystem1.83.0 \
  libboost-graph1.83.0 \
  libboost-graph1.83-dev \
  libboost-json1.83.0 \
  libboost-json1.83-dev \
  libboost-regex1.83.0 \
  libboost-stacktrace1.83.0 \
  libboost-stacktrace1.83-dev \
  libcgroup-dev \
  libabsl-dev \
  libarchive-dev \
  libbenchmark-dev \
  libbrotli-dev \
  libcap-dev \
  libcli11-dev \
  libgmock-dev \
  libgmp-dev \
  libgtest-dev \
  libmimalloc-dev \
  libtbb-dev \
  liburing-dev \
  libzstd-dev \
  cmake \
  libssl-dev \
  gdb \
  valgrind \
  ninja-build \
  python3-pytest \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

## Add ubuntu user if not exists
RUN useradd -ms /bin/bash ubuntu || true
USER ubuntu

WORKDIR /usr/src/monad-bft

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | bash -s -- -y
ENV PATH="/home/ubuntu/.cargo/bin:${PATH}"
RUN /bin/bash -c "source /home/ubuntu/.cargo/env && rustup toolchain install 1.87.0-x86_64-unknown-linux-gnu"
ARG TRIEDB_TARGET=triedb_driver