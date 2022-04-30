ARG ALPINE_VERSION
FROM ruby:2.7-alpine${ALPINE_VERSION} as base

RUN apk add --no-cache yarn gcc g++ make musl-dev \
    && mkdir -p /data /home/presentation \
    && addgroup -S presentation \
    && adduser -h /home/presentation -s /bin/sh -G presentation -S presentation \
    && chown -R presentation:presentation /data \
    && chown -R presentation:presentation /home/presentation

USER presentation:presentation

WORKDIR /data

VOLUME [ "/data" ]

FROM base as pdf

USER root:root

RUN apk add --no-cache chromium chromium-swiftshader \
    && ln -s /usr/bin/chromium-browser /usr/bin/chromium 

USER presentation:presentation
