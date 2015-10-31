# build the hyperkube image.

VERSION=$(shell git rev-parse --short master)
ARCH=amd64
BASEIMAGE=debian:jessie

## Comment in for arm builds, must be run on an arm machine
# ARCH=arm
# need to escape '/' for the regexp below
# BASEIMAGE=armbuild\\/debian:jessie

all:
	cp ../../saltbase/salt/helpers/safe_format_and_mount .
	cp ../../saltbase/salt/generate-cert/make-ca-cert.sh  .
	cp ../../../_output/local/bin/linux/amd64/hyperkube .
	sed -i "s/VERSION/${VERSION}/g" master-multi.json master.json
	sed -i "s/ARCH/${ARCH}/g" master-multi.json master.json
	sed -i "s/BASEIMAGE/${BASEIMAGE}/g" Dockerfile
	docker build -t 2opremio/hyperkube:${VERSION} .

.PHONY: all
