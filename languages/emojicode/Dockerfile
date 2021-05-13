FROM debian:stable-slim as build

ENV CC clang-8
ENV CXX clang++-8
ENV DEBIAN_FRONTEND=nontinteractive
ENV PYTHONIOENCODING utf8

RUN \
  apt-get update && \
  apt-get install -y \
    gnupg \
    wget && \
  echo "deb http://apt.llvm.org/bionic/ llvm-toolchain-bionic-8 main" >> /etc/apt/sources.list && \
  echo "deb-src http://apt.llvm.org/bionic/ llvm-toolchain-bionic-8 main" >> /etc/apt/sources.list && \
  wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key|apt-key add - && \
  apt-get update && \
  apt-get install -y \
    clang-8 \
    cmake \
    libstdc++-8-dev \
    libclang1-8 \
    libclang-8-dev \
    libclang-common-8-dev \
    libfuzzer-8-dev \
    libllvm8 \
    libncurses-dev \
    libz-dev \
    llvm-8 \
    llvm-8-dev \
    llvm-runtime \
    ninja-build \
    python3 \
    rsync \
    git && \
  rm -rf /var/lib/apt/lists/* && \
  mkdir /tmp/emojicode/

WORKDIR /tmp/emojicode/
RUN git clone https://github.com/emojicode/emojicode.git .
RUN cmake . -GNinja && \
    ninja && \
    ninja magicinstall


FROM debian:stable-slim
LABEL author="SunRed"

ENV CXX=g++

RUN apt-get update && \
    apt-get install -y ${CXX} && \
    apt-get autoremove -y && \
    apt-get autoclean -y

COPY --from=build /usr/local/bin /usr/local/bin
COPY --from=build /usr/local/EmojicodePackages /usr/local/EmojicodePackages
COPY run.sh /var/run/
