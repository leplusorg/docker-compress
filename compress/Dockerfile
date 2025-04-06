FROM alpine:3.21.3@sha256:a8560b36e8b8210634f77d9f7f9efd7ffa463e380b75e2e74aff4511df3ef88c

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

# hadolint ignore=DL3019
RUN apk -U upgrade \
    && apk add \
    7zip=24.08-r0 \
    bzip2=1.0.8-r6 \
    gzip=1.13-r0 \
    liblzf=3.6-r1 \
    lrzip=0.651-r1 \
    lz4=1.10.0-r0 \
    py3-pip=24.3.1-r0 \
    python3=3.12.9-r0 \
    xz=5.6.3-r1 \
    zip=3.0-r13 \
    zstd=1.5.6-r2 \
    zutils=1.13-r0 \
    && if apk -u list | grep -q -e . ; then \
      apk -u list ; \
      exit 1 ; \
    fi \
    && apk cache clean \
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
