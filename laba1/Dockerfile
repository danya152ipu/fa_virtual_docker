FROM ubuntu:latest

RUN apt update && apt upgrade -y && apt install -y nginx && apt-get clean && \
     rm -rf /var/www/* && mkdir /var/www/laba1 && mkdir /var/www/laba1/img

WORKDIR /var/www/laba1
COPY ./index.html ./	
COPY ./img.png ./img/

RUN chmod -R 755 ./ && useradd laba_user && groupadd laba_group && usermod laba_user -G laba_group && \
    chown -R laba_user:laba_group ./ && sed -i 's/\/var\/www\/html/\/var\/www\/laba1/g' /etc/nginx/sites-enabled/default && \
     sed -i 's/user www-data/user laba_user/g' /etc/nginx/nginx.conf

EXPOSE 83

CMD ["nginx","-g","daemon off;"]

