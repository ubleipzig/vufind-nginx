# vufind-nginx

*vufind-nginx* is an alternative webserver for [VuFind] and can be used analog to [vufind-httpd]. The base-image is [nginx:alpine].

As for [vufind-httpd] the images are extended by a default configuration with [VuFind]-specific configuration. The configuration expects the [VuFind]-Sources under `/usr/local/vufind`, and the cache-files which are built at [VuFind]-runtime under `/var/cache/vufind`.

Also i created a new *entrypoint* that modifies the configuration based on the value from the environment variable `BASE_PATH`. If you want to access [VuFind] unter http://localhost/vufind you need to provide the environment variable `BASE_PATH=/vufind` on container-create.

## supported tags

* 1.13-*, 1.13, 1, latest ([1.13/Dockerfile])

## Usage of the image

As for [vufind-httpd] the usage makes only sense in connection with with [vufind-php], which provides the application server of [VuFind]. The server needs to be available as host *php*. Also the [VuFind]-files need to be connected to the container, so that the webserver can serve static content. [VuFind] creates additional cache-files, which have to be served by the webserver. This folder needs to be connected to the container as well.
```
$# docker run --name nginx \
  --link php:php \
  --volume /path/to/vufind:/usr/local/vufind:ro \
  --volume /path/to/cache:/var/cache/vufind:ro \
  --environment BASE_PATH=/vufind
  ubleipzig/vufind-nginx
```

[VuFind]: https://github.com/vufind-org/vufind
[httpd:alpine]: https://hub.docker.com/_/httpd/
[1.13/Dockerfile]: https://git.sc.uni-leipzig.de/ubl/bdd_dev/docker/vufind-nginx/blob/master/1.13/Dockerfile
[vufind-httpd]: https://hub.docker.com/r/ubleipzig/vufind-httpd/
[vufind-php]: https://hub.docker.com/r/ubleipzig/vufind-php/
