# vufind-nginx

*vufind-nginx* steht als alternativer Webserver zur Verfügung und kann statt [vufind-httpd] verwendet werden.
Das Basis-Image ist [nginx:alpine].

Ebenso wie beim [vufind-httpd]-Image werden VuFind-Dateien erwartet und der `BASE_PATH` zum Konfigurieren
des Pfad-Anteils gesetzt

## Unterstützte tags

* 1.13-*, 1.13, 1, latest ([1.13/Dockerfile])

## Nutzung des Images

Die Nutzung erfolgt analog zu der von [vufind-httpd]:
```
$# docker run --name nginx \
  --link php:php \
  --volume /path/to/vufind:/usr/local/vufind:ro \
  --volume /path/to/cache:/var/cache/vufind:ro \
  --environment BASE_PATH=/vufind
  ubleipzig/vufind-nginx
```

## Anmerkungen

* Das *vufind1*-Image existiert, um Entwicklern das Umschalten zu VuFind1-Instanzen so einfach wie möglich zu machen. Hier wird keine weitere Arbeit investiert, z.B. funktioniert die Pfad-Konfiguration über die `BASE_PATH`-Variable nicht.
* es müssen Tests geschrieben werden, sobald ich weiß, wie man das für Docker-Images am besten macht

[vufind-httpd]: https://hub.docker.com/r/ubleipzig/vufind-httpd/
[nginx:alpine]: https://hub.docker.com/_/nginx/
[1.13/Dockerfile]: https://git.sc.uni-leipzig.de/ubl/bdd_dev/docker/vufind-nginx/blob/master/1.13/Dockerfile

