FROM php:8.0-fpm-alpine

# Copy composer.lock and composer.json
COPY src/composer.lock* src/composer.json* /var/www/html/

# Set working directory
WORKDIR /var/www/html

# Install extensions
RUN docker-php-ext-install tokenizer mysqli pdo_mysql opcache

# Copy ini file
COPY ./internal/php/php.ini /usr/local/etc/php/conf.d/custom.ini

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy existing application directory contents
COPY ./src /var/www/html

# Expose port 9090 and start php-fpm server
EXPOSE 9090

CMD ["php-fpm"]
