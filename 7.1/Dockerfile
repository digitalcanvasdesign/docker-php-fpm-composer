FROM digitalcanvasdesign/php-fpm:7.1-fpm

LABEL maintainer="Jason Raimondi <jason@raimondi.us>"

WORKDIR /usr/local/src

ENV BUILD_DEPENDENCIES="\
		\
        autoconf \
		\
		ca-certificates \
        curl"

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends $BUILD_DEPENDENCIES \

    \
    && ( \
        curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer \
    ) \
    && apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $BUILD_DEPENDENCIES \
    && apt-get clean

EXPOSE 9001

CMD ["php-fpm"]
