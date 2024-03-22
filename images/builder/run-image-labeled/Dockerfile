# Define the base image
FROM public.ecr.aws/initializ/builder/run-base:latest

# Switch to the root user to install packages
USER root

# Update package database and install dependencies
RUN apk update && \
    apk del libcrypt1 && \
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
        libxcrypt \
        libxml2 \
        sqlite \
        pcre \
        libunwind \
        icu \
        wolfi-base

# Create symbolic link for libpcre
RUN ln -s /usr/lib/libpcre.so.1 /usr/lib/libpcre.so.3
# Create symbolic link for libicuio.so.70
RUN ln -s /usr/lib/libicuio.so.70 /usr/lib/libicuio.so.70
# Create symbolic link for libicui18n.so.70
RUN ln -s /usr/lib/libicui18n.so.70 /usr/lib/libicui18n.so.70
# Create symbolic link for libicuuc.so.70
RUN ln -s /usr/lib/libicuuc.so.70 /usr/lib/libicuuc.so.70



# Switch back to the non-root user
USER cnb

# Set required CNB target information
LABEL io.buildpacks.base.distro.name="wolfi"
LABEL io.buildpacks.base.distro.version="20230201"

LABEL io.buildpacks.stack.id="Initializ Distroless Stack"

ENV CNB_STACK_ID="Initializ Distroless Stack"
