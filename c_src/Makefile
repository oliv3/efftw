.PHONY: clean
.SUFFIXES: .o .c .cc

OS= ${shell uname}
CC=gcc
CFLAGS=-Wall -g -fpic -O2

# Erlang
ERL_INCLUDE = -I/usr/local/lib/erlang/usr/include 
ERL_LIBS    = -L/usr/local/lib/erlang/usr/lib \
              -lerts
EI_INCLUDE  = -I/usr/local/lib/erlang/lib/erl_interface-3.5.6/include
EI_LIBS     = -L/usr/local/lib/erlang/lib/erl_interface-3.5.6/lib \
              -lei \
              -lerl_interface

TARGET_LIB = efftw_drv.so

all: $(TARGET_LIB)

.c.o:
	$(CC) $(CFLAGS) -c $<

efftw_drv.so: efftw_drv.o
	$(CX) -o $@ $^ $(ERL_LIBS) $(EI_LIBS) $(EXTRA_OPTIONS)
	mv efftw_drv.so ../priv/lib 

clean:
	rm -f *.o *.so
