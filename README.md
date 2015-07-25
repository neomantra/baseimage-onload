# baseimage-onload

`baseimage-onload` provides a Dockerfile which installs Solarflare's [OpenOnload](http://www.openonload.org/ "OpenOnload") into Phusion's [baseimage-docker](http://phusion.github.io/baseimage-docker/ "baseimage-docker"), which is based on Ubuntu 14.04.

This Dockerfile is rather simple and could probably be built `FROM` most Debian-oriented images, for example:
```
FROM ubuntu:14.04
```

### Launching Onload-enabled container

To expose the host and onload to this container, run like this:
```
   docker run --net=host --device=/dev/onload --device=/dev/onload_epoll -it ONLOAD_ENABLED_IMAGE_ID [COMMAND] [ARG...]
```

**NOTE:** The host's `onload` version must be the same as the container's.

### Customizing

The Dockerfile downloads specific versions from [openonload.org](http://openonload.org "openonload.org") using the following `ENV` settings:

 * ONLOAD_VERSION, e.g. "201502-u2"
 * ONLOAD_MD5SUM, e.g. "64e93e56d88c54367cf427bba5404492"

If you change the `ONLOAD_VERSION`, you must also change `ONLOAD_MD5SUM` to match.  Note that Docker is only supported by OpenOnload since version 201502.

### License

Copyright (c) 2015 neomantra BV

Released under the MIT License, see LICENSE.txt
