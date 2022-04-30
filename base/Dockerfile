FROM debian:bullseye-slim

ARG WITH_CHROMIUM=0
ENV WITH_CHROMIUM=${WITH_CHROMIUM}

LABEL MAINTAINER "Carsten Igel <carsten@ahabitual.dev>"

ADD https://deb.nodesource.com/setup_18.x /opt/node.js/installer/setup_18.sh

RUN   chmod a+x /opt/node.js/installer/setup_18.sh \
   && /opt/node.js/installer/setup_18.sh \
   && apt-get update \
   && apt-get install -y --no-install-recommends ruby-full git nodejs libffi-dev build-essential \
   && ( test "${WITH_CHROMIUM}" = "0" || apt-get install -y --no-install-recommends chromium ) \
   && gem install bundler \
   && corepack enable \
   && apt-get clean \
   && useradd --uid 1000 --user-group --shell /bin/sh presenter \
   && mkdir -p /data /home/presenter \
   && chown presenter:presenter /data \
   && chown presenter:presenter /home/presenter

USER presenter

WORKDIR /data

ONBUILD COPY --chown=presenter:presenter . /data

ONBUILD RUN bundle install && yarn set version 1.22.18 && yarn install --production && bundle exec rake build

ENTRYPOINT [ "/usr/local/bin/bundle", "exec", "rake", "present:serve" ]
