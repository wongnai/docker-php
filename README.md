#PHP
PHP with required libs.

    docker run --name php56-fpm -d -p 9000:9000 --restart=always \
		-v /var/www/html:/var/www/html \
		wongnai/php:5.6-fpm
    
	docker run --name php56-apache -d -p 9000:9000 --restart=always \
		-v /var/www/html:/var/www/html \
		wongnai/php:5.6-apache

  
#Sending mail from PHP.
The sSMTP is installed in this image to enable email sending. It sends email to external smtp server named "exim". 

1. You need to create a docker bridge network so that 2 containers can talk to each other using hostname.

		
	docker network create shared
	
	
2. Run an STMP container (name needs to be "exim"), a very quick way is using the following images:-
	 
	
	docker run --name=exim -d --restart=always --net=shared \
		-e PRIMARY_HOST=example.org \
		-e ALLOWED_HOSTS="*" \
		rickw/debian-exim-send
	

3. Run this php container on the "shared" net :-

	
	docker run --name php56-apache -d --restart=always --net=shared -p 9000:9000 \
    		-v /var/www/html:/var/www/html \
    		wongnai/php:5.6-apache
    		

