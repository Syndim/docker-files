FROM ubuntu:20.04
RUN mkdir /tools
RUN apt-get update
RUN apt-get install -y git-core gnupg python2 lsb-release sudo build-essential
RUN git clone --depth=1  https://webrtc.bj2.agoralab.co/webrtc-mirror/depot_tools.git /tools/depot_tools
ENV PATH /tools/depot_tools:${PATH}
RUN ln -s /usr/bin/python2 /usr/bin/python
COPY install-build-deps.sh /tools/install-build-deps.sh
COPY install-build-deps-android.sh /tools/install-build-deps-android.sh
RUN bash /tools/install-build-deps.sh --syms --lib32 --arm --chromeos-fonts --nacl
RUN bash /tools/install-build-deps-android.sh
ENTRYPOINT /bin/bash -i
