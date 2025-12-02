ARG BUILD_FROM=ghcr.io/hassio-addons/nut/amd64:0.17.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# TEMPORARY
# Apply upstream PRs 472 and 473.
COPY rootfs.fixes /
# Install additional NUT drivers (upstream PR 474).
RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends \
        nut-i2c=2.8.1-5 \
        nut-ipmi=2.8.1-5 \
        nut-powerman-pdu=2.8.1-5 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="https://github.com/PaulSD" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="N/A" \
    org.opencontainers.image.authors="https://github.com/${BUILD_REPOSITORY}/graphs/contributors" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
