FROM alpine:3.22.1@sha256:4bcff63911fcb4448bd4fdacec207030997caf25e9bea4045fa6c8c44de311d1

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

# hadolint ignore=DL3019
RUN apk upgrade --no-cache \
    && apk add --no-cache \
    7zip=24.09-r0 \
    bzip2=1.0.8-r6 \
    coreutils=9.7-r1 \
    curl=8.14.1-r1 \
    git=2.49.1-r0 \
    gzip=1.14-r1 \
    liblzf=3.6-r1 \
    lrzip=0.651-r1 \
    lz4=1.10.0-r0 \
    py3-pip=25.1.1-r0 \
    python3=3.12.11-r0 \
    tar=1.35-r3 \
    xz=5.8.1-r0 \
    zip=3.0-r13 \
    zstd=1.5.7-r0 \
    zutils=1.13-r0 \
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
