ARG ALPINE_VERSION
ARG RUBY_VERSION=2.7
FROM ruby:${RUBY_VERSION}-alpine${ALPINE_VERSION} AS base

RUN apk add --no-cache yarn gcc g++ make musl-dev \
    && mkdir -p /data /home/presentation \
    && addgroup -S presentation \
    && adduser -h /home/presentation -s /bin/sh -G presentation -S presentation \
    && chown -R presentation:presentation /data \
    && chown -R presentation:presentation /home/presentation

USER presentation:presentation

WORKDIR /data

VOLUME [ "/data" ]

FROM base AS pdf

USER root:root

RUN apk add --no-cache chromium chromium-swiftshader \
    && ln -s /usr/bin/chromium-browser /usr/bin/chromium 

USER presentation:presentation
