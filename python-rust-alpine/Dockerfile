FROM alpine:latest

USER root

RUN apk add --no-cache bash wget curl alpine-sdk rtx git musl-dev linux-headers

ENV PATH=$PATH:/root/.local/share/rtx/shims

RUN rtx install python@3.11 python@3.10 python@3.9
RUN rtx use python@3.11
RUN rtx plugin-add rust https://github.com/asdf-community/asdf-rust.git
RUN rtx install rust@1.70.0
RUN rtx use rust@1.70.0

RUN echo "[source.crates-io]" >> $HOME/.cargo/config
RUN echo "replace-with = 'ustc'" >> $HOME/.cargo/config
RUN echo "[source.ustc]" >> $HOME/.cargo/config
RUN echo "registry = \"sparse+https://mirrors.ustc.edu.cn/crates.io-index/\"" >> $HOME/.cargo/config
RUN echo "[url \"https://ghproxy.com/https://github.com/\"]" >> $HOME/.gitconfig
RUN echo "        insteadOf = https://github.com/" >> $HOME/.gitconfig

RUN curl -sSL https://install.python-poetry.org | python3 -

RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip install maturin
