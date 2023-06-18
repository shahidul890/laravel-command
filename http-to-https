# 301 REDIRECT HTTP TO HTTPS

``
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
``

# Redirect HTTPS to HTTP
``
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTPS} on
RewriteRule (.*) http://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
</IfModule>
``
