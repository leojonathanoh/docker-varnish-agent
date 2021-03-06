# docker-varnish-agent

[![github-actions](https://github.com/leojonathanoh/docker-varnish-agent/workflows/build/badge.svg)](https://github.com/leojonathanoh/docker-varnish-agent/actions)
[![docker-image-size](https://img.shields.io/microbadger/image-size/leojonathanoh/docker-varnish-agent/latest)](https://hub.docker.com/r/leojonathanoh/docker-varnish-agent)
[![docker-image-layers](https://img.shields.io/microbadger/layers/leojonathanoh/docker-varnish-agent/latest)](https://hub.docker.com/r/leojonathanoh/docker-varnish-agent)

This is a docker image for the [Varnish Agent](https://github.com/varnish/vagent2), based on Ubuntu 16.04.
It also includes the [Enhanced Varnish Dashboard ](https://github.com/brandonwamboldt/varnish-dashboard) which you may use if you want to.

| Tags |
|:-------:| 
| `:4.1.4` |

## Environment variables

| Name | Default value | Description
|:-------:|:---------------:|:---------:|
| `VARNISH_HOST` | `varnish` | Hostname of the varnish server
| `VARNISH_HOST_MANAGEMENT_PORT` | `6082` | Management port opened by the varnish server
| `VARNISH_AGENT_USER` | `admin` | The Varnish Agent user for basic authentication.
| `VARNISH_AGENT_PASSWORD` | `admin` | The Varnish Agent password for basic authentication.
| `VARNISH_AGENT_PORT` | `6085` | The Varnish Agent port.
| `DASHBOARD_ENABLED` | `''` | Whether you want to use the realtime [`Varnish Dashboard`](https://github.com/brandonwamboldt/varnish-dashboard). If the value is empty, the dashboard is disabled.
| `DASHBOARD_VARNISH_SERVER_DISPLAY_NAME` | `Varnish` | The display name of the varnish instance as seen in the `Varnish Dashboard`.

## Behaviour
- At entrypoint, if it does not exist, a Varnish Agent secret file is created in `/usr/local/etc/varnish/agent_secret` in the format `$VARNISH_AGENT_USER:$VARNISH_AGENT_PASSWORD`. By default, that will be `admin:admin`
- Once the container has fully started up, the Varnish Agent / Varnish Dashboard frontend will be ready, and accessible via basic authentication.

## How to use
- An example `docker-compose.yml` is included demonstrating how to use this image with an separate Varnish image (e.g. [`varnish-alpine-docker`](https://github.com/thiagofigueiro/varnish-alpine-docker)).

## TODO
- Alpine image, which at the moment is not yet supported by the [Varnish Agent](https://github.com/varnish/vagent2)