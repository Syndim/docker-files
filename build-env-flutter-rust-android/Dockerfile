FROM cirrusci/flutter:3.0.5

USER root

RUN yes | sdkmanager "ndk;21.4.7075529"
RUN yes | sdkmanager "build-tools;30.0.3"
RUN yes | sdkmanager "platforms;android-31"
RUN yes | sdkmanager "platforms;android-28"
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y 1.63.0
ENV PATH ${PATH}:/root/.cargo/bin
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y python3 python3-pip python3-dev ruby libssl-dev build-essential pkg-config
RUN ln -s /usr/bin/python3 /usr/bin/python
RUN pip3 install invoke
RUN gem install bundler
RUN cargo install just nu
RUN rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android
