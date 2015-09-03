include env_make
#NS = your docker namespace
NS = thaihau
VERSION ?= latest

#REPO = your docker repo name
REPO = java8
#NAME = name of the image
NAME = java8
INSTANCE = default

.PHONY: build push shell run start stop rm release

build:
	docker build -t $(NS)/$(REPO):$(VERSION) .

push:
	docker push $(NS)/$(REPO):$(VERSION)

shell:
	docker run --rm --name $(NAME)-$(INSTANCE) -i -t $(PORTS) $(VOLUMES) $(ENV) $(NS)/$(REPO):$(VERSION) /bin/bash

run:
	docker run  --name $(NAME)-$(INSTANCE) $(LINK) $(PORTS) $(VOLUMES) $(ENV) -d $(NS)/$(REPO):$(VERSION)

start:
	docker start --name $(NAME)-$(INSTANCE) $(PORTS) $(VOLUMES) $(ENV) $(NS)/$(REPO):$(VERSION)

stop:
	docker stop $(NAME)-$(INSTANCE)

rm:
	docker rm $(NAME)-$(INSTANCE)

release: build
	make push -e VERSION=$(VERSION)

default: build