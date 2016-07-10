# nginx for localtunnel

Simple nginx config w/ssl for localtunnel. Certificate and key must be provided (obviously).

Your certificate and key must be called `server.crt` and `server.key` and will be volume mounted into the container at runtime.

There is nothing really special here that you couldn't do with your own nginx or other load balancers. This repo is provided as a reference for those wanting to run their own localtunnel servers.

```
docker run -d \
    --name localtunnel-nginx \
    --restart always \
    --net host \
    -v $HOME/ssl:/etc/nginx/ssl/ \
    defunctzombie/localtunnel-nginx:latest
```

## Local Testing

```
docker build -t localtunnel-nginx .
```

```
docker run \
    --restart always \
    -p 443:443 -p 80:80 \
    -v ./ssl:/etc/nginx/ssl/ \
    localtunnel-nginx
```
