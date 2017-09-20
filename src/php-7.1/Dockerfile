FROM chesszebra/php:7.1

# Run as root
USER root:root

# Update PECL and install XDebug
RUN pecl update-channels \
 && pecl install xdebug \
 && docker-php-ext-enable xdebug

# Copy over the configuration file for PHP
COPY usr/local/etc/php/php.ini /usr/local/etc/php/php.ini

# Install phpcbf
RUN curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar \
 && chmod +x phpcbf.phar \
 && mv phpcbf.phar /usr/local/bin/phpcbf

# Run the container as the configured user
USER php:php

# Execute phpunit
ENTRYPOINT ["phpcbf"]
