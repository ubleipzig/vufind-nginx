# vufind-nginx

This repository holds the Dockerfiles and VuFind-configuration for the Nginx-webserver.

## Image-Tags

The images are created via a gitlab-pipeline, see [.gitlab-ci.yml]. There are several tags which can be used:

* `1.13-*`: points to a specific build. Each build is specified by a number. The higher, the latter.
* `1.13`: points to the latest build from the `1.13`-line. It is the same as the last `1.13-*`.
* `1`: points to the latest build from the `1`-line. If there will be a `1.14`-line it will point to that latest build.
* `latest`: always points to the latest build.

## create Images

Pushing the Code to the Repository does nothing. Images are created via GIT-Tags.

```
git tag -a 1.13-2 -m 'minor optimization'
git push origin 1.13-2
```
_this will create a new image with a tag named `1.13-2`. Also the Tags `1.13`, `1`, and `latest` will point to this image._

Only Repository-Masters will be able to create a new Tag.
## Contribution

In case you want to contribute please fork and make a pull-request at [Gitlab-hosting of Leipzig University]. This is due to internal policies and the higher flexibility when it comes to build images and push to [Docker-Hub]

## Todo

* Tests

[.gitlab-ci.yml]: https://git.sc.uni-leipzig.de/ubl/bdd_dev/docker/vufind-nginx/blob/master/.gitlab-ci.yml
[Gitlab-hosting of Leipzig University]: https://git.sc.uni-leipzig.de/ubl/bdd_dev/docker/vufind-nginx
[Docker-Hub]: https://hub.docker.com/r/ubleipzig/vufind-nginx/