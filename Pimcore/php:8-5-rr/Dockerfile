# Equivalent of pimcore-playground's Dockerfile `base` stage, extracted so app builds
# don't recompile PHP extensions on every commit. Build for new Pimcore + Pimcore Studio UI
# (RoadRunner-served, not the webdevops/php-nginx + php-fpm stack used by the other
# Pimcore/php:8-x images in this repo).
FROM php:8.5-cli-trixie

RUN set -eux; \
    echo 'Acquire::Retries "3";' > /etc/apt/apt.conf.d/80-retries; \
    echo "deb http://deb.debian.org/debian trixie-backports main" > /etc/apt/sources.list.d/backports.list; \
    apt-get update; \
    apt-get upgrade -y; \
    apt-get install -y --no-install-recommends \
        default-mysql-client \
        exiftool \
        ffmpeg \
        ghostscript \
        graphviz \
        iproute2 \
        jpegoptim \
        libreoffice-writer \
        libreoffice-calc \
        libreoffice-impress \
        locales \
        openssl \
        optipng \
        pngquant \
        poppler-utils \
        unzip \
        webp \
    ; \
    apt-get install -y --no-install-recommends -t trixie-backports \
        imagemagick \
    ; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/*

RUN --mount=type=bind,from=mlocati/php-extension-installer:2.11.1,source=/usr/bin/install-php-extensions,target=/usr/local/bin/install-php-extensions \
    install-php-extensions \
        apcu \
        bcmath \
        exif \
        gd \
        imagick \
        intl \
        pcntl \
        pdo_mysql \
        redis \
        soap \
        sockets \
        xdebug \
        zip

WORKDIR /var/www/html
