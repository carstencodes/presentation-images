# Build Images

These images contain all elements to build asciidoctor-revealjs based images.

## Base Image

The base image is used to build asciidoctor-reveal.js and reveal.js based presentations using yarn, bundler and rake.

## PDF Image

The pdf image can be used to create PDF files from the HTML presentation using chromium:

``` shell
$ chromium --headless --no-sandbox --disable-dev-shm-usage --disable-gpu --print-to-pdf=/out/file.pdf file://path/to/source.html?print-pdf
```
