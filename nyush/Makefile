# Makefile
CC = gcc
CFLAGS=-g -pedantic -std=gnu17 -Wall -Wextra
TARGET = nyush
.PHONY: gradeit clean

all: $(TARGET)

$(TARGET): nyush.c
	$(CC) $(CFLAGS) -o $(TARGET) nyush.c

nyush.zip: nyush.c Makefile
	zip nyush.zip nyush.c Makefile

nyush-autograder: nyush-autograder.tar.xz
	tar xvf nyush-autograder.tar.xz

nyush-autograder/nyush.zip: nyush.zip nyush-autograder
	cp nyush.zip nyush-autograder/nyush.zip

gradeit: clean nyush-autograder/nyush.zip
	cd nyush-autograder && ./gradeit.sh

clean:
	rm -f $(TARGET) nyush.zip
	rm -rf nyush-autograder
