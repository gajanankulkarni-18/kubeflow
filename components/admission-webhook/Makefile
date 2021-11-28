# Image URL to use all building/pushing image targets
IMG ?= quay.io/ibm/kubeflow-admission-webhook-ppc64le
TAG ?= $(eval TAG := $(shell date +v%Y%m%d)-$(shell git describe --tags --always --dirty)-$(shell git diff | shasum -a256 | cut -c -6))$(TAG)
GOLANG_VERSION ?= 1.12

build:
	go build -gcflags 'all=-N -l' -o bin/webhook .

build-gcr:
	docker build -t $(IMG):$(TAG) .
	@echo Built $(IMG):$(TAG)
