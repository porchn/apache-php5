# apache-php5

This repo used in Dockerhub url 'https://hub.docker.com/r/porchn/php5.6.28-apache/'


extenion install in images
* gd
* iconv
* mcrypt
* intl
* mysql
* mysqli
* pdo_mysql
* zip
* mbstring
* mod_rewrite

External extention
* Memcached
* Composer

Volume
* /var/www
* /var/log/apache2
* /etc/apache2/sites-available

Port
* 80
* 443

How to use single 
```
docker run --name testphp -p 8080:80 -d -v /Users/pichaichin/Sites/test:/var/www/html porchn/php5-apache
```
On Docker-compose 
```
  apache:
    image: porchn/php5.6.28-apache
    container_name: apache
    ports:
      - "8080:80"
    volumes:
      - ./apache2/conf:/etc/apache2/sites-enabled
      - ./apache2/www:/var/www
      - ./file-media/farms:/var/www/farms
      - ./file-media/static:/var/www/static
      - ./apache2/logs:/var/log/apache2
    environment:
      - TZ=Asia/Bangkok
    restart: always
    links: 
      - postfix:postfix
    networks:
      - webnetwork
```