secret-octo-robot
=================
server {
        listen   80;

        root /var/www/html;
        index index.php index.html index.htm;

        # Make site accessible from http://localhost/
        server_name csub.com;
        location = /robots.txt  { access_log off; log_not_found off; }
        location ~ ~$           { access_log off; log_not_found off; deny all; }

        location ~* .(js|css|png|jpg|jpeg|gif|ico|xml|swf|flv|eot|ttf|woff|pdf|xls|htc)$ {
                add_header Pragma "public";
                add_header Cache-Control "public, must-revalidate, proxy-revalidate";
                access_log off;
                log_not_found off;
                expires   360d;
        }
