### 1. Получение сертификата для одного домена

```bash
docker exec certbot-container certbot certonly --webroot \
  -w /var/www/certbot \
  -d <домен> \
  --email evgeniy_shabakov@mail.ru \
  --agree-tos \
  --no-eff-email
```

### 2. Добавить конфигурационный файл в `vhosts/<домен>.conf`

### 3. Перезапустите nginx

```bash
docker exec nginx-container nginx -s reload
```

### После пересоздания контейнеров на которые проксирует nginx,
### чтобы обновить IP адреса  контейнеров

```bash
docker exec nginx-container nginx -s reload
```
