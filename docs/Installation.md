### Installation Requirements: 
1. PHP 7.1
2. Composer 

Installing Zest is very simple, first ensure you have the right PHP version and composer installed then in your command prompt run:

`$ composer create-project softhub99/zest blog`


The above command will create a new Zest project inside a new folder name blog, then:

`$ cd blog`

and then run

`$ composer update`

# Local Development With VirtualHost

Running Your Project With VirtualHost

	    <VirtualHost *:80>

	    DocumentRoot "/var/www/html/blog/public"

	    ServerName example.com

	    </VirtualHost>


Restart Apache
`$ service httpd restsart`

Navigate to http://example.com, you should be able to view the app.

Running Your Project Without `VirtualHost `if you choose to run your project without `VirtualHost`, So you have to access it with `http://localhost/blog/public` then