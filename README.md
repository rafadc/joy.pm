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
