dockerized digdag
===

### Prerequisistes

- `docker`
- `docker-compose`

### Usage

- On local machine

```bash
$ alias fig
fig=docker-compose

# run postgresql
$ fig -f tools/docker/docker-compose.yml up postgres

# run digdag server mode
$ fig -f tools/docker/docker-compose.yml up digdag-server
```
