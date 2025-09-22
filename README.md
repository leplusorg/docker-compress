# Compress

Multi-platform Docker container with utilities to compress/decompress data (`zip`, `gzip`, `7zip`, `bzip2`, `lz4`, `xz`...).

[![Dockerfile](https://img.shields.io/badge/GitHub-Dockerfile-blue)](compress/Dockerfile)
[![Docker Build](https://github.com/leplusorg/docker-compress/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-compress/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/compress)](https://hub.docker.com/r/leplusorg/compress)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/compress)](https://hub.docker.com/r/leplusorg/compress)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/compress?sort=semver)](https://hub.docker.com/r/leplusorg/compress)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/10082/badge)](https://bestpractices.coreinfrastructure.org/projects/10082)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/leplusorg/docker-compress/badge)](https://securityscorecards.dev/viewer/?uri=github.com/leplusorg/docker-compress)

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

Same thing, assuming that you have a file `foo.txt` in your current working directory that you want to compress:

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

## Software Bill of Materials (SBOM)

To get the SBOM for the latest image (in SPDX JSON format), use the
following command:

```bash
docker buildx imagetools inspect leplusorg/compress --format '{{ json (index .SBOM "linux/amd64").SPDX }}'
```

Replace `linux/amd64` by the desired platform (`linux/amd64`, `linux/arm64` etc.).

### Sigstore

[Sigstore](https://docs.sigstore.dev) is trying to improve supply
chain security by allowing you to verify the origin of an
artifcat. You can verify that the image that you use was actually
produced by this repository. This means that if you verify the
signature of the Docker image, you can trust the integrity of the
whole supply chain from code source, to CI/CD build, to distribution
on Maven Central or whever you got the image from.

You can use the following command to verify the latest image using its
sigstore signature attestation:

```bash
cosign verify leplusorg/compress --certificate-identity-regexp 'https://github\.com/leplusorg/docker-compress/\.github/workflows/.+' --certificate-oidc-issuer 'https://token.actions.githubusercontent.com'
```

The output should look something like this:

```text
Verification for index.docker.io/leplusorg/xml:main --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - The code-signing certificate was verified using trusted certificate authority certificates

[{"critical":...
```

For instructions on how to install `cosign`, please read this [documentation](https://docs.sigstore.dev/cosign/system_config/installation/).

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-compress/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
