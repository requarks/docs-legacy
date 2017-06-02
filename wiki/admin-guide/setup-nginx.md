<!-- TITLE: Setup NGINX reverse proxy -->
<!-- SUBTITLE: Quick tutorial for using NGINX as a reverse proxy for Wiki.js -->

Below are example configurations that can be used as a reverse proxy setup for Wiki.js.
# Sample NGINX configurations
## HTTP reverse-proxy example

```makefile
server {
	listen 80;
	listen [::]:80;
	server_name  wiki.example.com;

	location / {
		proxy_set_header Host $http_host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_pass http://127.0.0.1:3001;
		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection "upgrade";
		proxy_next_upstream error timeout http_502 http_503 http_504;
	}
}
```

## HTTPS reverse-proxy example

```makefile
server {
	listen 443 ssl http2;
	listen [::]:443 ssl http2;
	server_name  wiki.example.com;

	ssl_session_timeout 1d;
	ssl_session_cache shared:SSL:50m;
	ssl_session_tickets off;

	ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
	ssl_ciphers "EECDH+ECDSA+AESGCM EECDH+aRSA+AESGCM EECDH+ECDSA+SHA384 EECDH+ECDSA+SHA256 EECDH+aRSA+SHA384 EECDH+aRSA+SHA256 EECDH EDH+aRSA !RC4 !aNULL !eNULL !LOW !3DES !MD5 !EXP !PSK !SRP !DSS";
	ssl_prefer_server_ciphers on;

	ssl_certificate /etc/nginx/ssl/wiki.example.com/fullchain.pem;
	ssl_certificate_key /etc/nginx/ssl/wiki.example.com/privkey.pem;
	ssl_trusted_certificate /etc/nginx/ssl/wiki.example.com/chain.pem;

	location / {
		proxy_set_header Host $http_host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_pass http://127.0.0.1:3001;
		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection "upgrade";
		proxy_next_upstream error timeout http_502 http_503 http_504;
	}
}
```
