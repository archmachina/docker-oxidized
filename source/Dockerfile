FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
ARG BUILD_VERSION

# hadolint ignore=DL3008
RUN apt-get update -yq && apt-get install --no-install-recommends -yq \
  ruby \
  ruby-dev \
  libsqlite3-dev \
  libssl-dev \
  pkg-config \
  cmake \
  libssh2-1-dev \
  libicu-dev \
  zlib1g-dev \
  g++ \
  libyaml-dev \
  ruby-bundler \
  make \
  curl \
  openssh-client \
  netcat && \
  apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir /work && chmod 777 /work
WORKDIR /work
ENV HOME /work
ENV PID_FILE /work/pid

COPY Gemfile /work
RUN bundle install

COPY entrypoint /entrypoint
COPY wrapper /wrapper

RUN echo "$BUILD_VERSION" > /version.txt

ENTRYPOINT [ "/entrypoint" ]
