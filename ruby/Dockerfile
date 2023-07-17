ARG RUBY_VERSION

FROM --platform=$TARGETOS/$TARGETARCH ruby:${RUBY_VERSION}-slim-bullseye

LABEL author="Cleberson Saller" maintainer="hello@csaller.com"

RUN apt update \
  && apt -y install ffmpeg iproute2 git ca-certificates dnsutils tzdata zip tar curl build-essential libtool iputils-ping make \
  && useradd -m -d /home/container container

RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
  && apt install -y nodejs

RUN npm install npm@latest -g
RUN gem install rails

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
