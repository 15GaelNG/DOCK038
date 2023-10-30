FROM php:7.2-apache

#Install dependencies
RUN apt-get update && apt-get install -y \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    locales \
    zip \
    unzip \
    vim \
    git \
    curl

COPY . /var/www/html

#Install the php extension
RUN docker-php-ext-install pdo_mysql zip exif gd

#Enable the Apache rewrite module
RUN a2enmod rewrite

#Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-install pdo mbstring

RUN sed -i 's!/var/www/html!/var/www/html/datos_maestros_raloy/DEV038/public!g' /etc/apache2/sites-available/000-default.conf

#-------------------------
#*** START THE PROJECT ***
#-------------------------

ARG TOKEN
ENV TOKEN=${TOKEN}

WORKDIR /var/www/html

RUN git clone https://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@github.com/Raloy-Lubricantes-S-A-de-C-V/DEV038 /var/www/html/datos_maestros_raloy

RUN chmod -R 775 datos_maestros_raloy
RUN chown -R www-data:www-data datos_maestros_raloy

WORKDIR /var/www/html/datos_maestros_raloy

COPY server.php /var/www/html/datos_maestros_raloy/
COPY entrypoint.sh /var/www/html/datos_maestros_raloy
RUN chmod +x /var/www/html/datos_maestros_raloy/entrypoint.sh
ENTRYPOINT ["/var/www/html/datos_maestros_raloy/entrypoint.sh"]
