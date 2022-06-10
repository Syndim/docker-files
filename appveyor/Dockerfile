FROM ubuntu:20.04

USER root

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y wget libcap2-bin lsof
RUN wget https://www.appveyor.com/downloads/appveyor/appveyor-server.deb
RUN dpkg -i appveyor-server.deb
RUN rm appveyor-server.deb

VOLUME [ "/var/opt/appveyor/server" ]
EXPOSE 80
ENV DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1

ENTRYPOINT [ "/opt/appveyor/server/appveyor-server" ]
