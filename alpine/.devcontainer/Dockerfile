ARG ALPINE_VERSION_NAME=latest

FROM alpine:${ALPINE_VERSION_NAME}

# Your Property
ARG USER=user
ARG USER_ID=1000
ARG GROUP_ID=1000

RUN apk update && apk add --no-cache python3 python3-dev py3-pip sudo \
    && addgroup -g ${GROUP_ID} ${USER} \
    && adduser -D -u ${USER_ID} -s /bin/sh -G ${USER} ${USER} \
    && adduser ${USER} wheel \
    && echo '%wheel ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers \
    && ln -s "`which python3`" "/usr/local/bin/python" \
    && pip3 install autopep8 && pip3 install flake8

USER ${USER}

# TMP Docker Volume
VOLUME ["/WORKDIR"]

WORKDIR /WORKDIR