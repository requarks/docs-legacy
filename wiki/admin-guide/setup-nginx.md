<!-- TITLE: Setup nginx reverse proxy -->
<!-- SUBTITLE: A quick summary of Setup Nginx -->

# Sample nginx configurations

## HTTPS reverse-proxy example

```makefile
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name  wiki.example.com;

    include /etc/nginx/ssl/ssl_params.conf;

    ssl_certificate /etc/nginx/ssl/wiki.example.com/fullchain.pem;
    ssl_certificate_key /etc/nginx/ssl/wiki.example.com/privkey.pem;
    ssl_trusted_certificate /etc/nginx/ssl/wiki.example.com/chain.pem;
    ssl_verify_client on;

    location / {
        proxy_set_header Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_pass http://127.0.0.1:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_next_upstream error timeout http_502 http_503 http_504;
    }

    include /etc/nginx/error-pages/50x.conf;
}
```
