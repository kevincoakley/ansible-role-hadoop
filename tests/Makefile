.PHONY: docker-start docker-systemd docker-stop all

DEBUG =
TAGS = all

INVENTORY 				:=
UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Linux)
    INVENTORY += inventory-docker
endif
ifeq ($(UNAME_S),Darwin)
    INVENTORY += inventory-docker-machine
endif

all: executable

docker-start: TAGS = docker-start
docker-start: executable

hadoop: TAGS = hadoop
hadoop: executable

docker-stop: TAGS = docker-stop
docker-stop: executable

debug: DEBUG = -vvvv
debug: executable

executable:
	ansible-playbook -i $(INVENTORY) -t $(TAGS) test.yml $(DEBUG)
