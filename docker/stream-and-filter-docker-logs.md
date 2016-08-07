---
headline: 'Stream and filter docker logs'
date: 2016-08-07
category: docker
tags:
  - grep
  - logs
---

Watch [docker logs] of a container for keyword `INFO` or `WARNING`

```sh
# replace CONTAINER with the docker container id or name
$ docker logs -f CONTAINER | grep --color 'INFO\|WARNING'
```

- follow `-f` the docker log for CONTAINER
- pipe `|` the log stream into `grep` to output the entries matching pattern `INFO` or `WARNING`

[docker logs]: https://docs.docker.com/engine/reference/commandline/logs/