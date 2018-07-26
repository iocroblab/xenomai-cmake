###### CONFIGURATION ######

### List of applications to be build
APPLICATIONS = rtprint

### Default Xenomai installation path
XENO ?= /usr/xenomai

XENOCONFIG=$(shell PATH=$(XENO):$(XENO)/bin:$(PATH) which xeno-config 2>/dev/null)

CC=$(shell $(XENOCONFIG) --cc)

CFLAGS=$(shell $(XENOCONFIG) --skin=native --cflags)

LDFLAGS=$(shell $(XENOCONFIG) --skin=native --ldflags)

%.o: %.c 
	$(CC) -c -o $@ $< $(CFLAGS)

rtprint: rtprint.o
	$(CC) -o $@ rtprint.o $(LDFLAGS)

clean:
	$(RM) $(APPLICATIONS) *.o

all: $(APPLICATIONS)
