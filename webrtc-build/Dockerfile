FROM ubuntu:20.04
RUN sed -i 's@//.*archive.ubuntu.com@//mirrors.ustc.edu.cn@g' /etc/apt/sources.list
RUN sed -i 's/security.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
RUN mkdir /tools
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y git-core gnupg python2 lsb-release sudo build-essential tzdata
RUN git clone --depth=1  https://webrtc.bj2.agoralab.co/webrtc-mirror/depot_tools.git /tools/depot_tools
ENV PATH /tools/depot_tools:${PATH}
RUN ln -s /usr/bin/python2 /usr/bin/python
COPY install-build-deps.sh /tools/install-build-deps.sh
COPY install-build-deps-android.sh /tools/install-build-deps-android.sh
RUN chmod +x /tools/install-build-deps.sh
RUN bash /tools/install-build-deps-android.sh
ENTRYPOINT /bin/bash -i
