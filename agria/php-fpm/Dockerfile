FROM alpine:3.14

RUN apk --update add ca-certificates \
    && echo "@cast https://dl.bintray.com/php-alpine/v3.9/php-7.3" >> /etc/apk/repositories \
    && apk add -U \
    php7-fpm \
    php7-redis \
    php7-apcu \
    php7-ctype \
    php7-curl \
    php7-soap \
    php7-dom \
    php7-gd \
    php7-iconv \
    php7-imagick \
    php7-json \
    php7-intl \
    php7-mcrypt \
    php7-fileinfo\
    php7-mbstring \
    php7-opcache \
    php7-openssl \
    php7-pdo \
    php7-pdo_mysql \
    php7-mysqli \
    php7-xml \
    php7-zlib \
    php7-phar \
    php7-tokenizer \
    php7-session \
    php7-simplexml \
    php7-xdebug \
    php7-zip \
    php7-cli \
    make \
    curl \
    yarn \
    git \
    openssh-server \
    openssh-client

## ssh key
RUN mkdir /root/.ssh/
ADD .ssh/id_rsa /root/.ssh/id_rsa
RUN chmod 600 /root/.ssh/id_rsa

# composer
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/* && \
    curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer && chmod +x /usr/bin/composer

ADD symfony.ini /etc/php7/conf.d/
ADD symfony.ini /etc/php7/cli/conf.d/
ADD xdebug.ini  /etc/php7/conf.d/

ADD symfony.pool.conf /etc/php7/php-fpm.d/


CMD ["php-fpm7", "-F"]

WORKDIR /var/www/agria
EXPOSE 9002