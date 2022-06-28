FROM ruby:3.1.2

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y wget build-essential curl
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH=$PATH:/root/.cargo/bin
