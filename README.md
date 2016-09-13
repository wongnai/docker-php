#PHP
PHP with required libs.

    docker run --name php56-fpm -d -p 9000:9000 --restart=always \
		-v /var/www/html:/var/www/html \
		wongnai/php:5.6-fpm
    
	docker run --name php56-apache -d -p 9000:9000 --restart=always \
		-v /var/www/html:/var/www/html \
		wongnai/php:5.6-apache

