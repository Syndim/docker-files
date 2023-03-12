FROM cirrusci/flutter:3.7.6

USER root

RUN yes | sdkmanager "ndk;25.2.9519653"
RUN yes | sdkmanager "build-tools;30.0.3"
RUN yes | sdkmanager "platforms;android-31"
RUN yes | sdkmanager "platforms;android-28"
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none
ENV PATH ${PATH}:/root/.cargo/bin
RUN rustup install 1.68.0
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y ruby libssl-dev build-essential pkg-config libclang-dev python3-dev python3-pip python3
RUN ln -s /usr/bin/python3 /usr/bin/python
RUN gem install bundler
RUN cargo install just nu
RUN rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android
