# https://developers.home-assistant.io/docs/apps/configuration#app-dockerfile
ARG BUILD_ARCH=aarch64
FROM ghcr.io/home-assistant/${BUILD_ARCH}-base-python:3.14-alpine3.21

ARG BUILD_VERSION
RUN \
    apk add --no-cache ttyd \
    && pip3 install --no-cache-dir iSponsorBlockTV==${BUILD_VERSION}

ENV \
    iSPBTV_docker="True" \
    iSPBTV_data_dir="/data" \
    TERM="xterm-256color" \
    COLORTERM="truecolor"

COPY rootfs /

RUN chmod a+x \
    /etc/services.d/isponsorblocktv-setup/run \
    /etc/services.d/isponsorblocktv-setup/finish \
    /usr/bin/run_setup \
    /usr/bin/show_devices

LABEL \
    org.opencontainers.image.title="Home Assistant App: iSponsorBlockTV Setup" \
    org.opencontainers.image.description="One-time wizard to discover YouTube TV devices and retrieve their Screen IDs" \
    org.opencontainers.image.source="https://github.com/fmurodov/hassio-apps" \
    org.opencontainers.image.licenses="GPL-3.0-only"
