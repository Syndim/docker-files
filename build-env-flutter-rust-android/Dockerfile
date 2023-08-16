FROM ghcr.io/cirruslabs/android-sdk:33

LABEL org.opencontainers.image.source=https://github.com/cirruslabs/docker-images-flutter
USER root

ENV FLUTTER_HOME=${HOME}/sdks/flutter \
    FLUTTER_VERSION=3.10.6
ENV FLUTTER_ROOT=$FLUTTER_HOME

ENV PATH ${PATH}:${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin

RUN git clone --depth 1 --branch ${FLUTTER_VERSION} https://github.com/flutter/flutter.git ${FLUTTER_HOME}

RUN yes | flutter doctor --android-licenses \
    && flutter doctor \
    && chown -R root:root ${FLUTTER_HOME}

RUN yes | sdkmanager "ndk;25.2.9519653"
RUN yes | sdkmanager "build-tools;30.0.3"
RUN yes | sdkmanager "platforms;android-31"
RUN yes | sdkmanager "platforms;android-28"
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none
ENV PATH ${PATH}:/root/.cargo/bin
RUN rustup install 1.71.1
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y ruby libssl-dev build-essential pkg-config libclang-dev python3-dev python3-pip python3
RUN ln -s /usr/bin/python3 /usr/bin/python
RUN gem install bundler
RUN cargo install just nu
RUN rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android
