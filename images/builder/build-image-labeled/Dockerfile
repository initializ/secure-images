# Define the base image
FROM public.ecr.aws/initializ/builder/build-base:latest

# Switch to the root user to install packages
USER root

# Update package database and install dependencies
RUN apk update && \
    apk del libcrypt1  && \
    apk add \
        build-base \
        ca-certificates-bundle \
        curl \
        git \
        jq \
        libexpat1 \
        py3-pip \
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

# Create symbolic link for libpcre.so.3
RUN ln -s /usr/lib/libpcre.so.1 /usr/lib/libpcre.so.3
# Create symbolic link for all the libicu
RUN ln -s /usr/lib/libicuio.so.74 /usr/lib/libicuio.so.70
RUN ln -s /usr/lib/libicui18n.so.74 /usr/lib/libicui18n.so.70
RUN ln -s /usr/lib/libicudata.so.74 /usr/lib/libicudata.so.70
RUN ln -s /usr/lib/libicutest.so.74 /usr/lib/libicutest.so.70
RUN ln -s /usr/lib/libicutu.so.74 /usr/lib/libicutu.so.70
RUN ln -s /usr/lib/libicuuc.so.74 /usr/lib/libicuuc.so.70
# Switch back to the non-root user
USER cnb

# Set required CNB target information
LABEL io.buildpacks.base.distro.name="wolfi"
LABEL io.buildpacks.base.distro.version="20230201"

LABEL io.buildpacks.stack.id="Initializ Distroless Stack"

ENV CNB_STACK_ID="Initializ Distroless Stack"
