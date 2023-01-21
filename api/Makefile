SHELL := /bin/bash

GIT := github.com/wormhole-foundation/wormhole-explorer
VERSION := 1.0.0
BUILD := `git rev-parse --short HEAD`
BUILD_DATE := `date +%Y%m%d%H%M%S`
BRANCH := `git branch --show-current`


# Use linker flags to provide version/build settings to the target
LDFLAGS=-ldflags "-X=$(GIT)build.Version=$(VERSION)\
				  -X=$(GIT)build.Time=$(BUILD_DATE)\
				  -X=$(GIT)build.Build=$(BUILD)\
 				  -X=$(GIT)build.Branch=$(BRANCH)\

## help: print this help message
.PHONY: help
help:
	@echo 'Usage:'
	@sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' |  sed -e 's/^/ /'

build:
	go build -o api main.go
	
doc:
	swag init -pd


test:
	go test -v -cover ./...


.PHONY: build doc test
