FROM cirrusci/flutter:stable

USER root

RUN yes | sdkmanager "ndk;21.4.7075529"
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y python3 python3-pip python3-dev ruby
RUN ln -s /usr/bin/python3 /usr/bin/python
RUN pip3 install invoke
RUN gem install bundler
RUN cargo install just nu
ENV PATH ${PATH}:/root/.cargo/bin
RUN rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android
