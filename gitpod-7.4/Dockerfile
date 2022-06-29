# Start with the base workspace
FROM simplygoodwork/gitpod-base:latest

USER root

# 1. Add in PHP 7.4
RUN  install-packages \
        php \
        php-all-dev \
        php-bcmath \
        php-ctype \
        php-curl \
        php-date \
        php-gd \
        php-intl \
        php-json \
        php-mbstring \
        php-mysql \
        php-net-ftp \
        php-pgsql \
        php-sqlite3 \
        php-tokenizer \
        php-xml \
        php-zip \
        rsync \
    && curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php \
    && php /tmp/composer-setup.php  --version=2.2.5 --install-dir=/tmp \
    && sudo mv /tmp/composer.phar /usr/bin/composer \
    && rm /tmp/composer-setup.php

USER gitpod