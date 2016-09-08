FROM php:7.0-fpm

RUN docker-php-ext-install mysqli

RUN apt-get update && apt-get install -y \
  less 

#install wp cli
RUN bash -c "curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar"
RUN bash -c "chmod +x wp-cli.phar"
RUN bash -c "mv wp-cli.phar /usr/local/bin/wp"

WORKDIR /app/dist

CMD ["bash"]