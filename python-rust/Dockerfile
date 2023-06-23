FROM python:3.11.4-bookworm

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y wget build-essential curl

RUN pip install maturin

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none
RUN rustup install 1.70.0

RUN curl -sSL https://install.python-poetry.org | python3 -

ENV PATH=$PATH:/root/.cargo/bin:/root/.local/bin

RUN echo "[source.crates-io]" >> $HOME/.cargo/config
RUN echo "replace-with = 'ustc'" >> $HOME/.cargo/config
RUN echo "[source.ustc]" >> $HOME/.cargo/config
RUN echo "registry = \"sparse+https://mirrors.ustc.edu.cn/crates.io-index/\"" >> $HOME/.cargo/config
RUN echo "[url \"https://ghproxy.com/https://github.com/\"]" >> $HOME/.gitconfig
RUN echo "        insteadOf = https://github.com/" >> $HOME/.gitconfig

RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
