# Base image
FROM ubuntu:latest

ENV php_version=8.1

RUN ln -s /usr/share/zoneinfo/Asia/Taipei /etc/localtime

# Install software-properties-common to enable add-apt-repository
RUN apt-get clean 
RUN rm -rf /var/lib/apt/lists/*
RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y \
   software-properties-common \
   gnupg vim unzip --no-install-recommends 

# Install PHP from ondrej/php
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4f4ea0aae5267a6c
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update && apt-get install -y \
   apache2 \
   php${php_version} \
   libapache2-mod-php${php_version} \
   php${php_version}-mysql \
   php${php_version}-gd \
   php${php_version}-imagick \
   php${php_version}-common \
   php${php_version}-curl \
   php${php_version}-mbstring \
   php${php_version}-xml \
   php${php_version}-zip \
   php${php_version}-bcmath \ 
   php${php_version}-mcrypt \ 
   libssl-dev \
   zlib1g-dev \
   libwebp-dev \
   libpng-dev \
   libjpeg-dev \
   libfreetype6-dev

# Enable Apache mod_rewrite, headers
RUN a2enmod rewrite
RUN a2enmod headers

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set working directory
WORKDIR /var/www/html

# Copy application directory
COPY . /var/www/html/

# Set permissions
RUN chown -R www-data:www-data /var/www/html/

# Clear out the local repository of retrieved package files
RUN rm -rf /var/lib/apt/lists/*

CMD [ "/usr/sbin/apache2ctl", "-D", "FOREGROUND" ]
