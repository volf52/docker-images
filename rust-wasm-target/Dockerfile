FROM ubuntu:22.04

COPY sudoers /etc/sudoers.d/nopasswd

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive && \
  apt-get install -yq build-essential curl git sudo && \
  apt-get clean && rm -rf /var/lib/apt/lists/* && \
  useradd volfy --user-group --create-home --shell /bin/bash --groups sudo

ENV RUSTUP_HOME=/opt/rust/rustup \
  PATH=/home/volfy/.cargo/bin:/opt/rust/cargo/bin:/usr/local/musl/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

RUN curl https://sh.rustup.rs -sSf | \
  env CARGO_HOME=/opt/rust/cargo \
  sh -s -- -y --default-toolchain stable --profile minimal --no-modify-path && \
  env CARGO_HOME=/opt/rust/cargo \
  rustup target add wasm32-unknown-unknown

USER volfy
RUN mkdir -p /home/volfy/libs /home/volfy/src /home/volfy/.cargo && \
  ln -s /opt/rust/cargo/config /home/volfy/.cargo/config

WORKDIR /home/volfy/src

