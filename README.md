# Compress

Docker container to compress/decompress data (ZIP, gzip, 7zip, bzip2...).

[![Dockerfile](https://img.shields.io/badge/GitHub-Dockerfile-blue)](https://github.com/leplusorg/docker-compress/blob/main/compress/Dockerfile)
[![Docker Build](https://github.com/leplusorg/docker-compress/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-compress/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/compress)](https://hub.docker.com/r/leplusorg/compress)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/compress)](https://hub.docker.com/r/leplusorg/compress)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/compress?sort=semver)](https://hub.docker.com/r/leplusorg/compress)

## Example without using the filesystem

Let's say that you have a file `foo.txt` in your current working directory that you want to compress:

**Mac/Linux**

```bash
cat foo.txt | docker run --rm -i --net=none leplusorg/compress gzip -c - > foo.txt.gz
```

**Windows**

```batch
type foo.txt | docker run --rm -i --net=none leplusorg/compress gzip -c - > foo.txt.gz
```

## Example using the filesystem

Same thing, assuming that you have a MP3 `foo.txt` in your current working directory that you want to compress:

**Mac/Linux**

```bash
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" leplusorg/compress gzip /tmp/foo.txt
```

**Windows**

In `cmd`:

```batch
docker run --rm -t --net=none -v "%cd%:/tmp" leplusorg/compress gzip /tmp/foo.txt
```

In PowerShell:

```pwsh
docker run --rm -t --net=none -v "${PWD}:/tmp" leplusorg/compress gzip /tmp/foo.txt
```

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-compress/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
