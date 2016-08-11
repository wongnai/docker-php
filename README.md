#PHP
PHP with required libs.

  docker run --name php56-fpm -v /var/www/html:/var/www/html -p 9000:9000 -d --restart=always wongnai/php:5.6-fpm
  
  docker run --name php56-apache -v /var/www/html:/var/www/html -p 80:80 -d --restart=always wongnai/php:5.6-apache
  
