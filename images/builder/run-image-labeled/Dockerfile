# Define the base image
FROM public.ecr.aws/initializ/builder/run-base:latest

# Switch to the root user to install packages
USER root

# Update package database and install dependencies
RUN apk update && \
    apk add \
        build-base \
        ca-certificates-bundle \
        curl \
        git \
        jq \
        libexpat1 \
        gmp \
        libssl3 \
        yaml \
        openssl \
        pkgconf \
        tzdata \
        zlib \
        xz \
        xdg-utils \
        libstdc++ \
        bash \
        libffi-dev \
        python3-dev \
        libfontconfig1 \
        fontconfig \
        libcrypto3 \
        wolfi-base

# Switch back to the non-root user
USER cnb

# Set required CNB target information
LABEL io.buildpacks.base.distro.name="wolfi"
LABEL io.buildpacks.base.distro.version="20230201"

LABEL io.buildpacks.stack.id="Initializ Distroless Stack"

ENV CNB_STACK_ID="Initializ Distroless Stack"