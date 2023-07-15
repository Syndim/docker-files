FROM ruby:3.1.2

USER root

RUN gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
RUN bundle config mirror.https://rubygems.org https://gems.ruby-china.com
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y wget build-essential curl
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none
ENV PATH ${PATH}:/root/.cargo/bin
RUN rustup install 1.71.0

ENV PATH=$PATH:/root/.cargo/bin

RUN echo "[source.crates-io]" >> $HOME/.cargo/config
RUN echo "replace-with = 'ustc'" >> $HOME/.cargo/config
RUN echo "[source.ustc]" >> $HOME/.cargo/config
RUN echo "registry = \"sparse+https://mirrors.ustc.edu.cn/crates.io-index/\"" >> $HOME/.cargo/config
RUN echo "[url \"https://ghproxy.com/https://github.com/\"]" >> $HOME/.gitconfig
RUN echo "        insteadOf = https://github.com/" >> $HOME/.gitconfig
