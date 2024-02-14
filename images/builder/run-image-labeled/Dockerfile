# Define the base image
FROM public.ecr.aws/initializ/builder/run-base:latest

# Switch to the root user to install packages
USER root

# Update package database and install dependencies
RUN apk update && \
    apk add \
        ca-certificates-bundle \
        wolfi-base \
        libexpat1 \
        libssl3 \
        yaml \
        openssl \
        tzdata \
        zlib \
        libstdc++ \
        bash 

# Switch back to the non-root user
USER cnb

# Set required CNB target information
LABEL io.buildpacks.base.distro.name="wolfi"
LABEL io.buildpacks.base.distro.version="20230201"

LABEL io.buildpacks.stack.id="Initializ Distroless Stack"

ENV CNB_STACK_ID="Initializ Distroless Stack"