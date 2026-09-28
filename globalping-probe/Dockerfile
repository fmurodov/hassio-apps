# https://developers.home-assistant.io/docs/apps/configuration#app-dockerfile
# The upstream image is used as the base because the probe self-updates
# in place and relies on its layout (/app, /entrypoint.sh, bundled node).
ARG BUILD_VERSION
FROM globalping/globalping-probe:${BUILD_VERSION}

# renovate: datasource=github-releases depName=hassio-addons/bashio
ARG BASHIO_VERSION=v0.19.0
RUN mkdir -p /usr/lib/bashio \
    && curl -fsSL "https://github.com/hassio-addons/bashio/archive/${BASHIO_VERSION}.tar.gz" \
        | tar -xzf - --strip-components=2 -C /usr/lib/bashio "bashio-${BASHIO_VERSION#v}/lib" \
    && ln -s /usr/lib/bashio/bashio /usr/bin/bashio

COPY rootfs /

RUN chmod a+x /usr/bin/run-probe

# -g forwards signals to the whole process group so the probe shuts down cleanly
ENTRYPOINT ["/usr/bin/tini", "-g", "--"]
CMD ["/usr/bin/run-probe"]

LABEL \
    org.opencontainers.image.title="Home Assistant App: Globalping Probe" \
    org.opencontainers.image.description="Run a Globalping network probe and contribute to the global measurement network" \
    org.opencontainers.image.source="https://github.com/fmurodov/hassio-apps" \
    org.opencontainers.image.licenses="ISC"
