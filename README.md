### 1. Получение сертификата для одного домена

```bash
docker exec certbot-container certbot certonly --webroot \
  -w /var/www/certbot \
  -d <домен> \
  --email evgeniy_shabakov@mail.ru \
  --agree-tos \
  --no-eff-email
```

### 2. Раскомментируйте SSL-директивы в `vhosts/<домен>.conf`

```nginx
ssl_certificate     /etc/letsencrypt/live/<домен>/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/<домен>/privkey.pem;
```

### 3. Перезапустите nginx

```bash
docker compose restart nginx-service
```
