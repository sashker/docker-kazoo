FROM    telephoneorg/debian:stretch

MAINTAINER Joe Black <me@joeblack.nyc>

ENV     APP kazoo
ENV     USER $APP
ENV     HOME /opt/$APP

WORKDIR $HOME

ARG     KAZOO_VERSION
ENV     KAZOO_VERSION=${KAZOO_VERSION:-4.1.40}
LABEL   app.kazoo.core.version=$KAZOO_VERSION

COPY    build.sh /tmp/
RUN     /tmp/build.sh

ENV     KAZOO_SOUNDS_VERSION 4.1.0
ENV     MONSTER_APPS_TAG 4.1
LABEL   app.kazoo.sounds.version=$KAZOO_SOUNDS_VERSION
LABEL   app.monster.apps.tag=$MONSTER_APPS_TAG

COPY    sup /usr/local/bin/
COPY    kazoo-tool /usr/local/bin/
COPY    dl-assets /usr/local/bin/

VOLUME  ["/var/www/html/monster-ui", "/opt/kazoo/media/prompts"]

SHELL   ["/bin/bash", "-lc"]

HEALTHCHECK --interval=15s --timeout=5s CMD /bin/true
