FROM gpupo/container-orchestration:php-dev

ENV PHPCENSOR_VERSION=0.23.0

WORKDIR /var/www/html


RUN apt-get install -y gettext-base;

RUN git clone -b $PHPCENSOR_VERSION --single-branch --depth 1 https://github.com/corpsee/php-censor.git .

RUN composer install

ADD entrypoint.sh /
ADD config.tmpl.yml /

ENV DB_HOST=localhost
ENV DB_TYPE=mysql
ENV DB_NAME=phpcensor
ENV DB_USER=phpcensor
ENV DB_PASS=changethepass
ENV BEANSTALK_HOST=beanstalk
ENV BEANSTALK_QUEUE_NAME=phpcensor

ENTRYPOINT ["/entrypoint.sh"]
