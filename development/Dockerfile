FROM phusion/baseimage:0.9.18

#bring in some required dev tools
RUN apt-get update && apt-get install -y \
  wget \
  curl \
  git \
  npm\
  php5-fpm \
  php5-mysql \
  php5-cli \
  php5-curl \
  mysql-client

RUN bash -c "curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -"
RUN bash -c "sudo apt-get install -y nodejs"

#install some things
RUN bash -c "npm install -g bower"
RUN bash -c "npm install -g gulp"
RUN bash -c "npm install -g flightplan"

#install php composer
RUN bash -c "curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer"

#install wp cli
RUN bash -c "curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar"
RUN bash -c "chmod +x wp-cli.phar"
RUN bash -c "mv wp-cli.phar /usr/local/bin/wp"

WORKDIR /app

CMD ["bash"]