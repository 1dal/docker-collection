# Developer: Maik Ellerbrock <opensource@frapsoft.com>
#
# GitHub:  https://github.com/ellerbrock
# Twitter: https://twitter.com/frapsoft
# Docker:  https://hub.docker.com/u/ellerbrock
# Quay:    https://quay.io/user/ellerbrock

FROM alpine:3.6

LABEL maintainer "Maik Ellerbrock <opensource@frapsoft.com>"

# Optional Configuration Parameter
ARG SERVICE_USER
ARG SERVICE_HOME

# Default Settings
ENV SERVICE_USER ${SERVICE_USER:-office}
ENV SERVICE_HOME ${SERVICE_HOME:-/home/${SERVICE_USER}}

ENV VERSION 0.0.1

RUN \
  adduser -h ${SERVICE_HOME} -s /sbin/nologin -u 1000 -D ${SERVICE_USER} && \
  apk add --no-cache \
    dumb-init \
    openjdk8 \
    libreoffice \
    libreoffice-base \
    libreoffice-lang-de \
    mesa-gl \
    ttf-freefont

USER    ${SERVICE_USER}
WORKDIR ${SERVICE_HOME}
VOLUME  ${SERVICE_HOME}

ENTRYPOINT [ "/usr/bin/dumb-init", "/usr/bin/libreoffice" ]
