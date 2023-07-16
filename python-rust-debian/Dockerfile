FROM debian:bookworm

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y wget build-essential curl git libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

RUN curl https://rtx.pub/rtx-latest-linux-x64 > /bin/rtx
RUN chmod +x /bin/rtx

ENV PATH=/root/.local/share/rtx/shims:/root/.local/bin:/root/.cargo/bin:$PATH

ENV RTX_DEBUG=1
RUN rtx install -v python@3.11 python@3.10 python@3.9
RUN rtx use python@3.11
RUN curl -sSL https://install.python-poetry.org | python3.11 -
RUN pip3.11 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none
RUN rustup install 1.71.0
RUN rustup default 1.71.0

RUN echo "[source.crates-io]" >> $HOME/.cargo/config
RUN echo "replace-with = 'ustc'" >> $HOME/.cargo/config
RUN echo "[source.ustc]" >> $HOME/.cargo/config
RUN echo "registry = \"sparse+https://mirrors.ustc.edu.cn/crates.io-index/\"" >> $HOME/.cargo/config
RUN echo "[url \"https://ghproxy.com/https://github.com/\"]" >> $HOME/.gitconfig
RUN echo "        insteadOf = https://github.com/" >> $HOME/.gitconfig

RUN cargo install maturin
