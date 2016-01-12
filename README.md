# Vanilla Forums in Docker
Built to serve my own needs. Built around the principle that plugins, themes
and config is part of your image. Uploads are data though, so that's a volume!

Naive run. You probably don't want to do this:
`docker run -p 80:80 --name vanillary --rm -v "uploads:/var/www/html/uploads" vanilla:v2.2.0`

Better:
```Dockerfile
FROM vanilla:v2.2.0

ADD https://15254b2dcaab7f5478ab-24461f391e20b7336331d5789078af53.ssl.cf1.rackcdn.com/www.vanillaforums.org/addons/ODBOLSKWR903.zip /var/www/html/plugins/ #jsConnect
COPY myconfig.php /var/www/html/conf/config.php
```

### Unsolved
*Help wanted*
- Keeping track of changes to config.php (made by vanilla)
- Creating initial config.php
- Other data/config wars that need fighting
