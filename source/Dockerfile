FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update -yq && apt install -yq ruby ruby-dev libsqlite3-dev libssl-dev pkg-config cmake \
  libssh2-1-dev libicu-dev zlib1g-dev g++ libyaml-dev ruby-bundler make curl openssh-client netcat

RUN mkdir /work && chmod 777 /work
WORKDIR /work
ENV HOME /work

COPY Gemfile /work
RUN bundle install

COPY entrypoint /entrypoint

ENTRYPOINT [ "/entrypoint" ]
