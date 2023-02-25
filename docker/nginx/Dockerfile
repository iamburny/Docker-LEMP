FROM debian:bullseye-slim

RUN apt install -y nginx gnupg libxml2-dev libpng-dev curl libcurl4-gnutls-dev libxslt-dev libzip-dev libtidy-dev && \
    wget -q https://packages.sury.org/php/apt.gpg -O- | sudo apt-key add - && \
    echo "deb https://packages.sury.org/php/ bullseye main" | sudo tee /etc/apt/sources.list.d/php.list && \
    sudo apt -y install -y ca-certificates apt-transport-https && \
    sudo apt -y update && sudo apt -y upgrade

RUN sudo apt install -y php7.4 php7.4-cli php7.4-common php7.4-opcache php7.4-curl php7.4-mbstring php7.4-mysql php7.4-zip php7.4-xml php7.4-fpm php7.4-bcmath

RUN sudo apt install -y php8.2 php8.2-cli php8.2-common php8.2-opcache php8.2-curl php8.2-mbstring php8.2-mysql php8.2-zip php8.2-xml php8.2-fpm php8.2-bcmath

RUN docker-php-ext-install -j$(nproc) xml opcache bcmath gd curl xsl intl zip tidy mysqli pdo pdo_mysql

RUN pecl install xdebug-3.2.0 \
    && docker-php-ext-enable xdebug

RUN sudo apt install -y certbot python-certbot-nginx

RUN curl -sS https://getcomposer.org/installer -o composer-setup.php
RUN sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

# dev.sandbox.com
RUN ln -s "/opt/projects/dev.sandbox.com" "/var/www/dev.sandbox.com"


#CMD ["apache2ctl", "-k", "graceful"]
#RUN kill -USR1 1