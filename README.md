# gemp-swccg-webui
GEMP-SWCCG WebUI - client for playing Star Wars CCG using a web browser. The program takes care of the rules so you don't have to.

This is the code running from the official webserver.

## Bootstrapping

The scripts assume the code is deployed to a vagrant box running a webserver.

The images are distributed separately and are to be downloaded first by running:

```
./get-card-images.sh
```

The webserver's root should point to gemp-swccg-webui/web

If the webserver and gemp-swccg java server are not running on the same system,
you'll have to set a proxy-forwarding rule in your localhost webserver to redirect all requests to

http://localhost/gemp-swccg-server/ to http://gemp.starwarsccg.org/gemp-swccg-server/

for example, in nginx:
```
    location /gemp-swccg-server/ {
            proxy_pass http://gemp.starwarsccg.org/gemp-swccg-server/;
    }
```


## Releasing

A release is created by running
```
./make_package.sh
```
within the bootstrapped development environment,
which will package the web pages, scripts and images to be unzipped on the production server.