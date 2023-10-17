# Sử dụng PHP 8.2 FPM (FastCGI Process Manager)
FROM php:8.2-fpm

# Timezone
ENV TZ='Asia/Ho_Chi_Minh'
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Cài đặt các gói cần thiết và các extension PHP
RUN apt-get update && apt-get install -y \
    nginx \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    unzip \
    libpq-dev \
    libonig-dev \
    libcurl4-openssl-dev && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install -j$(nproc) gd pdo_mysql zip mbstring exif pcntl curl

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install MongoDB extension
RUN pecl install mongodb && \
    docker-php-ext-enable mongodb

# Install Redis extension
RUN pecl install redis && \
    docker-php-ext-enable redis

# Workdir
WORKDIR /var/www/html

# Copy code into image
COPY ./laravel /var/www/html

# Install dependencies by Composer
RUN composer install --no-dev --no-interaction --no-scripts

# Clear cache
RUN apt-get clean && rm -fr /var/lib/apt/lists

# Change directories permission
RUN chown -R www-data:www-data /var/www/html && chmod -R 775 /var/www/html/storage

# Copy nginx configuration file
COPY nginx/default.conf /etc/nginx/sites-available/default

# Expose Nginx port
EXPOSE 80

# Run Nginx && PHP-FPM
CMD [ "sh", "-c", "/usr/local/sbin/php-fpm -D && nginx -g 'daemon off;'" ]
