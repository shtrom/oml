# This file was automatically generated by oml2-scaffold V2.10.0
PROGRAM = generator
SRCS = ${PROGRAM}.c

RUNARGS = --oml-id $(PROGRAM)-test --oml-domain $(hostname -d) \
	  --amplitude 42 --frequency 1337 --samples 1024 --sample-interval .25

BINDIR = $(DESTDIR)/usr/local/bin/

CFLAGS = -Wall -Werror -g -I. # -I/usr/local/include
LDFLAGS = # -L/usr/local/lib
LIBS = -loml2 -locomm -lpopt -lm

CCLD=$(CC)
SCAFFOLD = /usr/bin/oml2-scaffold

OBJS = $(SRCS:%.c=%.o)

all: build
build: $(PROGRAM)

install: $(PROGRAM)
	install -m 755 $(PROGRAM) $(BINDIR)

clean:
	rm -rf $(PROGRAM)
	rm -rf $(OBJS)

realclean: clean
	rm -rf $(PROGRAM)_popt.h $(PROGRAM)_oml.h

run: $(PROGRAM)
	./$(PROGRAM) $(RUNARGS) --oml-collect file:-

%.o: %.c
	$(CC) -c $(CFLAGS) $< -o $@


$(PROGRAM): $(OBJS)
	$(CCLD) -o $@ $^ $(LDFLAGS) $(LIBS)

$(PROGRAM).o: config.h $(PROGRAM)_popt.h $(PROGRAM)_oml.h
$(PROGRAM)_popt.h: $(PROGRAM).rb
	$(SCAFFOLD) --opts $<
$(PROGRAM)_oml.h: $(PROGRAM).rb
	$(SCAFFOLD) --oml $<

.PHONY: all build install clean realclean
