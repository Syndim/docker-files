FROM debian:bookworm

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y wget build-essential curl


RUN wget -qO - https://rtx.pub/gpg-key.pub | gpg --dearmor | tee /usr/share/keyrings/rtx-archive-keyring.gpg 1> /dev/null
RUN echo "deb [signed-by=/usr/share/keyrings/rtx-archive-keyring.gpg arch=amd64] https://rtx.pub/deb stable main" | tee /etc/apt/sources.list.d/rtx.list
RUN sudo apt update
RUN sudo apt install -y rtx

ENV PATH=$PATH:/root/.local/share/rtx/shims

RUN rtx install python 3.11.4 3.10.6 3.9.2
RUN rtx use python@3.11.4
RUN rtx plugin-add rust https://github.com/asdf-community/asdf-rust.git
RUN rtx install rust 1.70.0
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
