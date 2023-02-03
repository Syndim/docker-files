FROM cirrusci/flutter:3.7.0

USER root

RUN yes | sdkmanager "ndk;21.4.7075529"
RUN yes | sdkmanager "build-tools;30.0.3"
RUN yes | sdkmanager "platforms;android-31"
RUN yes | sdkmanager "platforms;android-28"
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none
ENV PATH ${PATH}:/root/.cargo/bin
RUN rustup install 1.67.0
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y ruby libssl-dev build-essential pkg-config libclang-dev
RUN gem install bundler
RUN cargo install just nu
RUN rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android
