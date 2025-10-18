CC = gcc
CFLAGS = -Wall -Wextra -std=c17 -O2
LDFLAGS = -pthread
DOCKER_TAG = nyuenc-autograder-env

.PHONY: clean gradeit gradeit-docker

all: nyuenc

nyuenc: nyuenc.c
	$(CC) $(CFLAGS) -o nyuenc nyuenc.c $(LDFLAGS)

nyuenc.zip: nyuenc.c Makefile Dockerfile
	zip nyuenc.zip nyuenc.c Makefile Dockerfile

nyuenc-autograder: nyuenc-autograder.tar.xz
	tar -xf nyuenc-autograder.tar.xz

nyuenc-autograder/nyuenc.zip: nyuenc-autograder nyuenc.zip
	rm -f ./nyuenc-autograder/nyuenc.zip
	cp nyuenc.zip ./nyuenc-autograder/

docker-build: Dockerfile
	docker build --platform linux/amd64,linux/arm64 -t $(DOCKER_TAG) .
	touch docker-build

gradeit: clean nyuenc-autograder nyuenc-autograder/nyuenc.zip
	cp nyuenc.zip ./nyuenc-autograder/
	cd nyuenc-autograder && ./gradeit.sh

gradeit-docker: docker-build nyuenc-autograder/gradeit.sh nyuenc-autograder/nyuenc.zip
	docker run --platform=linux/amd64 --rm -it -v "$(PWD)/nyuenc-autograder:/nyuenc-autograder" $(DOCKER_TAG) bash -c "cd /nyuenc-autograder && ./gradeit.sh"

clean:
	rm -f nyuenc nyuenc.zip docker-build
	rm -rf nyuenc-autograder
