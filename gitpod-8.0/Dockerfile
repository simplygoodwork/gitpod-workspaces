# Start with the base workspace
FROM simplygoodwork/gitpod-base:latest

USER root

# Dazzle does not rebuild a layer until one of its lines are changed. Increase this counter to rebuild this layer.
ENV TRIGGER_REBUILD=3

# 1. Add in PHP 8.0
RUN add-apt-repository -y ppa:ondrej/php \
    && install-packages \
        php8.0 \
        php8.0-dev \
        php8.0-bcmath \
        php8.0-ctype \
        php8.0-curl \
        php8.0-gd \
        php8.0-intl \
        php8.0-mbstring \
        php8.0-mysql \
        php8.0-pgsql \
        php8.0-sqlite3 \
        php8.0-tokenizer \
        php8.0-xml \
        php8.0-zip \
    && curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php \
    && php /tmp/composer-setup.php  --version=2.2.5 --install-dir=/tmp \
    && sudo mv /tmp/composer.phar /usr/bin/composer \
    && rm /tmp/composer-setup.php

USER gitpod