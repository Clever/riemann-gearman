# riemann-gearman

Periodically outputs gearman admin data as [Riemann](http://riemann.io) events for monitoring and alerting.

## Installation

The following downloads and builds riemann-gearman.
You must have Go installed (developed/tested against version 1.2):

```bash
mkdir /tmp/gopath
export GOPATH=/tmp/gopath
go get github.com/Clever/riemann-gearman
mv $GOPATH/bin/riemann-gearman /usr/local/bin/riemann-gearman
rm -r $GOPATH
```

## Usage

```bash
$ riemann-gearman -h
Usage of riemann-gearman:
  -gearman="tcp://localhost:4730": Use the specified host:port to connect to gearman.
  -interval=60000: Interval in ms to output data.
  -riemann="tcp://localhost:5555": Write events to Riemann running at this port. Can also specify 'stdout' to debug.
  -tags="": Tags to add to the Riemann event.
```

Alternatively you can run via Docker (as an example):

```bash
docker run -d rgarcia/riemann-gearman riemann-gearman -gearman="tcp://<gearman host>:4730" -interval=60000 -riemann="<riemann host>" -tags="production,docker"
```

The image referenced above was built with the Dockerfile in this repo's root.
