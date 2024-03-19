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
        py3-pip \
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
        libxml2 \
        sqlite \
        pcre2 \
        libunwind \
        wolfi-base

# Create symbolic link for libpcre
RUN ln -s /usr/lib/libpcre2-8.so.0.12.0 /usr/lib/libpcre.so.3

# Switch back to the non-root user
USER cnb

# Set required CNB target information
LABEL io.buildpacks.base.distro.name="wolfi"
LABEL io.buildpacks.base.distro.version="20230201"

LABEL io.buildpacks.stack.id="Initializ Distroless Stack"

ENV CNB_STACK_ID="Initializ Distroless Stack"
