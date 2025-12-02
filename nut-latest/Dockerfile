ARG BUILD_FROM=ghcr.io/hassio-addons/nut/amd64:0.17.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# To avoid mixing Debian Stable upgrades with Debian Unstable upgrades (for clarity and to simplify
# troubleshooting), upgrade Debian Stable before upgrading to anything in Debian Unstable.
RUN \
    apt-get update \
    && apt-get -o 'Dpkg::Options::=--force-confold' dist-upgrade -y \
    && apt-get autoremove --purge -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Upgrade NUT using Debian Unstable/Sid.
# hadolint ignore=DL3003
COPY rootfs /
RUN \
    apt-get update \
    && apt-get -o 'Dpkg::Options::=--force-confold' dist-upgrade -y \
    && apt-get autoremove --purge -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Verify the expected version of NUT was installed.
RUN \
    NUT_VER='2.8.4+really-2' \
    && test "$(dpkg-query --show -f='${Version}' nut)" '=' "$NUT_VER"

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
