FROM webdevops/php-nginx:8.2

ENV SERVICE_NGINX_CLIENT_MAX_BODY_SIZE=128M \
    PHP_POST_MAX_SIZE=128M \
    PHP_UPLOAD_MAX_FILESIZE=128M \
    COMPOSER_ALLOW_SUPERUSER=true

COPY .docker/nginx/nginx-prod.conf /opt/docker/etc/nginx/vhost.conf
COPY .docker/imagemagick/policy.xml /etc/ImageMagick-6/policy.xml

RUN apt-get update && apt-get install -y \
    ffmpeg \
    graphviz \
    htop \
    imagemagick \
    jpegoptim \
    libreoffice \
    libimage-exiftool-perl \
    optipng \
    pngquant \
    poppler-utils \
    vim \
 && rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer \
 | php -- --install-dir=/usr/bin/ --filename=composer
