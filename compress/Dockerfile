FROM alpine:3.23.2@sha256:865b95f46d98cf867a156fe4a135ad3fe50d2056aa3f25ed31662dff6da4eb62

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    7zip=25.01-r0 \
    bzip2=1.0.8-r6 \
    coreutils=9.8-r1 \
    curl=8.17.0-r1 \
    git=2.52.0-r0 \
    gzip=1.14-r2 \
    liblzf=3.6-r1 \
    lrzip=0.651-r1 \
    lz4=1.10.0-r0 \
    py3-pip=25.1.1-r1 \
    python3=3.12.12-r0 \
    tar=1.35-r4 \
    xz=5.8.2-r0 \
    zip=3.0-r13 \
    zstd=1.5.7-r2 \
    zutils=1.15-r0 \
    && apk cache --no-cache clean \
    && rm -rf /var/cache/apk/*

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

USER "${USER_NAME}"

ENV HOME="${USER_HOME}"

WORKDIR "${HOME}"
