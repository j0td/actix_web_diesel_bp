FROM rust:1.41

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y default-mysql-client

ENV CARGO_TARGET_DIR=/tmp/target

RUN cargo install diesel_cli --no-default-features --features mysql
RUN cargo install cargo-watch

RUN USER=root cargo new --bin app
WORKDIR /app

COPY ./Cargo.toml Cargo.toml
COPY ./Cargo.lock Cargo.lock

RUN cargo build --release --color never && rm src/*.rs
