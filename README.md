# nginx for localtunnel

Simple nginx config w/ssl for localtunnel. Certificate and key must be provided (obviously).

Your certificate and key must be called `server.crt` and `server.key` and will be volume mounted into the container at runtime.

There is nothing really special here that you couldn't do with your own nginx or other load balancers. This repo is provided as a reference for those wanting to run their own localtunnel servers.

```
docker build -t nginx-localtunnel .
```

```
docker run \
    --restart always \
    -p 443:443 -p 80:80 \
    -v /path/to/folder/with/cert_and_key:/etc/nginx/ssl/
    nginx-localtunnel
```
