# The PHP image
FROM php:8.1-fpm

RUN apt-get update && \
    apt-get install -y wget cron zlib1g-dev libzip-dev libpng-dev libicu-dev
    # The zlib1g-dev, libzip-dev, libpng-dev are necessary to enable both `gd` and `zip` extension
    # The libicu-dev is necessary to enable `intl` extension

# Installation PHP extensions
RUN docker-php-ext-install mysqli pdo pdo_mysql gd zip intl

# Installation composer
RUN wget https://getcomposer.org/composer-stable.phar -O /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer

ENTRYPOINT ["php-fpm", "-f"]
