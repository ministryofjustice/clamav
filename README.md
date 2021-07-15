
# clamav

[![CircleCI](https://circleci.com/gh/ministryofjustice/clamav/tree/master.svg?style=svg)](https://circleci.com/gh/ministryofjustice/clamav/tree/master)

ClamAV daemon as a Docker image. It *builds* with a current virus database and
*runs* `freshclam` in the background constantly updating the virus signature database. `clamd` itself
is listening on exposed port `3310`.

On your main container, you still need to install `clamav-daemon` :

`apt-get install clamav-daemon -y`

Then you can scan a file with: `clamdscan -c clamd.container.conf --stream file`

clamd.container.conf being:
```
TCPSocket 3310
TCPAddr localhost # or wherever you setup this container
```

---

copied from https://github.com/mko-x/docker-clamav
