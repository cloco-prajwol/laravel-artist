# Use PHP 8.2 with Alpine
FROM php:8.2-fpm-alpine

# Install dependencies
RUN apk update && apk add --no-cache \
    freetype-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    zlib-dev \
    libzip-dev \
    unzip \
    mysql-client \
    bash \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd zip pdo pdo_mysql

# Set the working directory
WORKDIR /var/www/app

# Copy the application files
COPY . /var/www/app/

# Set permissions
RUN mkdir -p storage bootstrap/cache \
    && chown -R www-data:www-data /var/www/app \
    && chmod -R 775 storage bootstrap/cache

# Install Composer dependencies
COPY --from=composer:2.6.5 /usr/bin/composer /usr/local/bin/composer
COPY composer.json composer.lock ./
RUN composer install --no-dev --optimize-autoloader

# Start PHP-FPM
CMD ["php-fpm"]
