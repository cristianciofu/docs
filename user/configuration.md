<a name="url-rewriting"></a>

## URL Rewriting

<a name="apache"></a>

### Apache

Flarum includes a `.htaccess` file – make sure it's been uploaded correctly. If you're using shared hosting, confirm with your hosting provider that `mod_rewrite` is enabled. You may need to add the following to your Apache configuration:

    <Directory "/path/to/your/forum">
        AllowOverride All
    </Directory>

<a name="nginx"></a>

### Nginx

Add the following lines to your server's configuration block:

```
    location / { try_files $uri $uri/ /index.php?$query_string; }
    location /api { try_files $uri $uri/ /api.php?$query_string; }
    location /admin { try_files $uri $uri/ /admin.php?$query_string; }

    location /flarum {
        deny all;
        return 404;
    }

    location ~* \.php$ {
        fastcgi_split_path_info ^(.+.php)(/.+)$;
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param HTTP_PROXY ""; # Fix for https://httpoxy.org/ vulnerability
        fastcgi_index index.php;
    }
    
    location ~* \.html$ {
        expires -1;
    }

    location ~* \.(css|js|gif|jpe?g|png)$ {
        expires 1M;
        add_header Pragma public;
        add_header Cache-Control "public, must-revalidate, proxy-revalidate";
    }

    gzip on;
    gzip_http_version 1.1;
    gzip_vary on;
    gzip_comp_level 6;
    gzip_proxied any;
    gzip_types application/atom+xml
               application/javascript
               application/json
               application/vnd.ms-fontobject
               application/x-font-ttf
               application/x-web-app-manifest+json
               application/xhtml+xml
               application/xml
               font/opentype
               image/svg+xml
               image/x-icon
               text/css
               text/plain
               text/xml;
    gzip_buffers 16 8k;
    gzip_disable "MSIE [1-6]\.(?!.*SV1)";
```

<a name="lighttpd"></a>

### Lighttpd

Add the following lines to your server's configuration block:

```
    url.rewrite-if-not-file = (
        "/admin.*" => "/admin.php",
        "/api.*"   => "/api.php",
        "/.*"      => "/index.php"
    )
```
