# https://developers.home-assistant.io/docs/apps/configuration#app-dockerfile
ARG BUILD_FROM=ghcr.io/home-assistant/aarch64-base-python:3.13-alpine3.21
FROM ${BUILD_FROM}

ARG ISPONSORBLOCKTV_VERSION
RUN pip3 install --no-cache-dir \
    iSponsorBlockTV==${ISPONSORBLOCKTV_VERSION}

ENV iSPBTV_docker="True"

COPY rootfs /

RUN chmod a+x \
    /etc/services.d/isponsorblocktv/run \
    /etc/services.d/isponsorblocktv/finish \
    /usr/bin/generate_config

LABEL \
    org.opencontainers.image.title="Home Assistant App: iSponsorBlockTV" \
    org.opencontainers.image.description="Skip SponsorBlock segments and ads on YouTube TV" \
    org.opencontainers.image.source="https://github.com/fmurodov/hassio-apps" \
    org.opencontainers.image.licenses="GPL-3.0-only"
