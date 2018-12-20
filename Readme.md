# docker-mhsendmail
Docker wrapper for [mhsendmail](https://github.com/mailhog/mhsendmail)

#### Usage

As a standalone tool

```bash
docker run aheadworks/mhsendmail --from="admin@mailhog.local" test@mailhog.local ...
```

As a source of compiled mhsendmail in your image, e.g. PHP devboxes with Mailhog linked

```dockerfile
FROM aheadworks/mhsendmail as mhsendmail
FROM your/phpbox
# ...
COPY --from=mhsendmail /usr/bin/mhsendmail /usr/bin/mhsendmail
RUN echo "sendmail_path=/usr/bin/mhsendmail --smtp-addr \$MAIL_HOST:25 " > /usr/local/etc/php/conf.d/sendmail.ini

```