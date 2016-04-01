<h3>Steps to Install</h3>

<ol><li><a href="http://monstra.org/download">Download the latest version.</a></li>

<li>Unzip the contents to a new folder on your local computer.</li>

<li>Upload that whole folder with an FTP client to your host.</li>

<li>You may also need to recursively CHMOD the folder <code>/storage/</code>, <code>/tmp/</code>, <code>/backups/</code> and <code>/public/</code><br/> to 755(or 777) if your host doesn't set it implicitly.</li>

<li>Also you may also need to recursively CHMOD the <code>/install.php</code>, <code>/.htaccess</code> and <code>/sitemap.xml</code><br/> to 755(or 777) if your host doesn't set it implicitly.</li>

<li>Type <a href="#">http://example.org/install.php</a> in the browser.</li>

</ol>



<br>



<strong>You can install Monstra with <a href="http://www.softaculous.com/apps/cms/Monstra">Softaculous</a>:</strong><br>

1. Login to your host and look for Software/Services<br>

2. In Softaculous there is a 'Portals/CMS' Category. Collapse the category and Monstra will be there. Click on it.<br>

3. You will see an 'Install' TAB. Click it.<br>

4. Fill in the various details and Submit.<br>

5. That's it, you are done!<br>

<br>





<br>

<h4>Apache .htaccess for Monstra</h4>

<pre class="prettyprint">

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
</pre>

<br>

<h4>Ngnix config for Monstra</h4>

<pre class="prettyprint">
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
</pre>
