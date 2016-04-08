### Steps to Install

1. Download the [latest version](http://monstra.org/download)
2. Unzip the contents to a new folder on your local computer.
3. Upload that whole folder with an FTP client to your host.
4. You may also need to recursively CHMOD the folder `/storage/`, `/tmp/`, `/backups/` and `/public/`<br/> to 755 (or 777) if your host doesn't set it implicitly.
5. Also you may also need to recursively CHMOD the `/install.php`, `/.htaccess` and `/sitemap.xml`<br/> to 755 (or 777) if your host doesn't set it implicitly.
6. Navigate to http://example.org/install.php in the browser.

**You can install Monstra with [Softaculous](http://www.softaculous.com/apps/cms/Monstra):

1. Login to your host and look for Software/Services
2. In Softaculous there is a 'Portals/CMS' Category. Collapse the category and Monstra will be there. Click on it.
3. You will see an 'Install' TAB. Click it.
4. Fill in the various details and Submit.
5. That's it, you are done!

#### Apache .htaccess for Monstra

	#
	# Monstra CMS :: php & apache settings
	#

	# Set default charset utf-8
	AddDefaultCharset UTF-8

	# Don't show directory listings for URLs which map to a directory.
	Options -Indexes

	# PHP 5, Apache 1 and 2.
	&lt;IfModule mod_php5.c&gt;
		php_flag magic_quotes_gpc                 off
		php_flag magic_quotes_sybase              off
		php_flag register_globals                 off
	&lt;/IfModule&gt;

	# Setting rewrite rules.
	&lt;IfModule mod_rewrite.c&gt;
		RewriteEngine on
		# Update code bellow for SEO improvements
		# RewriteCond %{HTTP_HOST} ^www.example.org [NC]
	 	# RewriteRule ^(.*)$ http://example.org/$1 [R=301,L]
		RewriteBase /%siteurlhere%/
		RewriteCond %{REQUEST_FILENAME} !-f
		RewriteCond %{REQUEST_FILENAME} !-d
		RewriteRule ^(.*)$ index.php [QSA,L]
		# Update code bellow for SEO improvements
		# Redirect 301 /home http://example.org/
	&lt;/IfModule&gt;

#### Ngnix config for Monstra

	# Monstra config
	server {
	    listen         80;
	    server_name    www.monstra.net monstra.net;
	    access_log   /var/log/nginx/monstra.net_access.log;
	    error_log    /var/log/nginx/monstra.net_error.log;
	    root /var/www/monstra;
	    index index.php;
	    location ~* ^.+\.(jpg|jpeg|gif|png|ico|css|txt|js|map)$ {
	        expires 1d;
	    }

	    location / {
	        rewrite /home / permanent;
	        rewrite ^/(.+)$ /index.php;
	    }

	    location ~ \.php$ {
	            include        fastcgi_params;
	            fastcgi_pass   127.0.0.1:9000;
	            fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
	    }
	}
