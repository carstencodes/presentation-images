# Presentation base layer

A basic presentation layer for all asciidoctor-reveal.js based [talks](../). It can be used as base image the following way:

``` Dockerfile
FROM carstencodes/presentation-base:latest
```

The remaining parts will be done using the `ONBUILD` parts.

So, to start the file, just run `docker run -p 8080:8080 --rm $(docker build -q .)` and open your web-browser to [http://localhost:8080](http://localhost:8080).
