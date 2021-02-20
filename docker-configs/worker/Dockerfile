FROM php:7.4-fpm

USER root

RUN apt-get update \
    && apt-get install -y supervisor \
    && apt-get install -y unoconv \
    && systemctl enable supervisor

#RUN pecl install redis && docker-php-ext-enable redis
RUN docker-php-ext-install pcntl

ADD docker-configs/worker/laravel-worker.conf /etc/supervisor/conf.d/
ADD docker-configs/worker/supervisord.conf /etc/supervisor/

EXPOSE 9000

CMD /usr/bin/supervisord -c /etc/supervisor/supervisord.conf
