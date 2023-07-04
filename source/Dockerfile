FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update -yq && apt install -yq ruby ruby-dev libsqlite3-dev libssl-dev pkg-config cmake \
  libssh2-1-dev libicu-dev zlib1g-dev g++ libyaml-dev ruby-bundler make

RUN mkdir /data
WORKDIR /data
ENV HOME /data

COPY Gemfile /data
RUN bundle install

COPY entrypoint /entrypoint

ENTRYPOINT [ "/entrypoint" ]
