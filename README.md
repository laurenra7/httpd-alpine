# docker-httpd-alpine

This is a temporary httpd:alpine Docker image to be used by uPortal for
development and testing. This replaces the current official Dockerhub
[httpd:alpine image](https://hub.docker.com/_/httpd/) because
it is broken. See
[Issue #115 "Apache 2.4.37 does not start with mod_ssl"](https://github.com/docker-library/httpd/issues/115)
for the status of the issue. If it's fixed, you can use the official
[Dockerhub](https://hub.docker.com/_/httpd/) image again.

This will build a Docker image based on Apache httpd 2.4.34 and Alpine
Linux 3.7 from the
[docker-library/httpd](https://github.com/docker-library/httpd) Github repo
[snapshot of July 30, 2018](https://github.com/docker-library/httpd/tree/656d8e2f26c0624e294d4132f5559801aac8ec38).

## Build Docker image

1\. Clone this project.

2\. Remove or rename the current **httpd:alpine** image.


Rename:
```
docker tag httpd-old:alpine httpd:alpine
```

Remove:
```
docker rmi httpd:alpine
```

3\. Build the new (temporary) httpd:alpine image.

```
docker build -t httpd:alpine .
```

Once it's built, you should be able to build the Docker containers for
uPortal the normal way with:

```
docker-compose -f byu/docker/docker-compose.yml up -d
```

