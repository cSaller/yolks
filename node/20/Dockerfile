FROM --platform=$TARGETOS/$TARGETARCH node:20-bullseye-slim

LABEL author="Michael Parker" maintainer="parker@pterodactyl.io"

RUN apt update \
  && apt -y install git jq \
  && useradd -m -d /home/container container

RUN npm install npm@latest -g

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
