FROM alpine:3.24.0@sha256:8ddefa941e689fc29abcdeb8dae3b3c6d139cc08ce9a52633931160701770685

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    7zip=26.00-r0 \
    bzip2=1.0.8-r6 \
    coreutils=9.11-r0 \
    curl=8.20.0-r1 \
    git=2.54.0-r0 \
    gzip=1.14-r2 \
    liblzf=3.6-r1 \
    lrzip=0.660-r0 \
    lz4=1.10.0-r1 \
    py3-pip=26.1.2-r0 \
    python3=3.14.5-r0 \
    tar=1.35-r5 \
    xz=5.8.3-r0 \
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
