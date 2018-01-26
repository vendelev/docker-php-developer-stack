FROM alpine

ENV TIMEZONE Europe/Moscow

RUN apk update

# Install timezone and pinba
RUN apk add tzdata \
            git \
            g++ \
            gcc \
            make \
            re2c \
    && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    && echo "${TIMEZONE}" > /etc/timezone \
# Install php 7
    && apk add \
            php7 \
            php7-fpm \
            php7-mbstring \
            php7-iconv \
            php7-mysqli \
            php7-pdo_mysql \
            php7-gd \
            php7-json \
            php7-memcached \
            php7-mcrypt \
            php7-amqp \
            php7-xdebug \
            php7-zip \
            php7-xml \
            php7-bcmath \
            php7-curl \
            php7-phar \
            php7-zlib \
            php7-pear \
            php7-soap \
            php7-pcntl \
            php7-ctype \
            php7-posix \
            php7-fileinfo \
            php7-session \
            php7-imagick \
            php7-opcache \
            php7-zip \
            php7-dev \
            php7-openssl \
            php7-redis \
            php7-pgsql\
            php7-intl \
            php7-gmp \
            php7-dom \
            php7-tokenizer \
            php7-xmlwriter \
    && ln -s /etc/php7 /etc/php \
    && ln -s /usr/sbin/php-fpm7 /usr/bin/php-fpm \
    && ln -s /usr/lib/php7 /usr/lib/php \
    && sed -i 's/127.0.0.1:9000/9000/g' /etc/php/php-fpm.d/www.conf \
# Install pinba
    && git clone https://github.com/tony2001/pinba_extension /tmp/pinba_extension \
    && cd /tmp/pinba_extension \
    && phpize \
    && ./configure --enable-pinba \
    && make install \
# Clean
    && apk del \
        g++ \
        gcc \
        make \
        re2c \
        autoconf \
    && rm -fr /var/cache/apk/* \
    && rm -fr /tmp/pinba_extension

WORKDIR /tmp

# Install composer global bin
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \\
    && php composer-setup.php --install-dir=/bin --filename=composer

EXPOSE 9000

WORKDIR /var/www/web

CMD ["/usr/sbin/php-fpm7", "--nodaemonize"]
