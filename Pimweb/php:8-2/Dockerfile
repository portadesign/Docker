FROM webdevops/php-nginx:8.2

RUN apt-get update && apt-get install -y ffmpeg graphviz imagemagick jpegoptim libreoffice libimage-exiftool-perl optipng pngquant poppler-utils
WORKDIR /app

ENV COMPOSER_ALLOW_SUPERUSER=1

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer
