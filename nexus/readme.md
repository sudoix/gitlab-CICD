Copy `nexus` and `docker` file to `/etc/nginx/site-avalible`

Run command on server

```
chown -R 200:200 /data/registry/
chown -R 200:200 /data/registry/nexus-data

sudo apt-get install python3-certbot-ngin nginx
certbot --nginx -d YOUR_DOMAIN

## For wildcard run:
sudo certbot certonly --manual --preferred-challenges=dns --server https://acme-v02.api.letsencrypt.org/directory --manual-public-ip-logging-ok -d "*.YOUR_DOMAIN"

ln -s /etc/nginx/sites-available/nexus /etc/nginx/sites-enabled/
ln -s /etc/nginx/sites-available/docker /etc/nginx/sites-enabled/
unlink /etc/nignx/sire-available/default
```
