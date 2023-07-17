ARG NODE_VERSION

FROM --platform=$TARGETOS/$TARGETARCH node:${NODE_VERSION}-bullseye-slim

LABEL author="Cleberson Saller" maintainer="hello@csaller.com"

RUN apt update \
  && apt -y install git jq iproute2 > /dev/null \
  && useradd -m -d /home/container container

RUN npm install npm@latest -g

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
