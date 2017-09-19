# The joy of programming

My tiny blog. Based on Hugo.

## Development

```
hugo serve
```

## Deploy

Just push to gitlab and CI will do the rest


## HTTPS

We are using let's encrypt certificates

``` shell
certbot certonly --manual -d joy.pm --config-dir certbot --logs-dir certbot --work-dir certbot --agree-tos
```

In Gitlab you need to copy certbot/live/joy.pm/fullchain.pem into the Certificate(PEM) section and certbot/live/joy.pm/privkey.pem in Key (PEM) section
