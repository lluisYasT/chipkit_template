MPIDE=/opt/mpide
TOOLCHAIN_PREFIX=$(MPIDE)/hardware/pic32/compiler/pic32-tools
CC=$(TOOLCHAIN_PREFIX)/bin/pic32-gcc
CXX=$(TOOLCHAIN_PREFIX)/bin/pic32-g++
AR=$(TOOLCHAIN_PREFIX)/bin/pic32-ar

CPUTYPE=32MX795F512L
VARIANT=Max32

CFLAGS=-O0 -c -mno-smart-io -w -fno-exceptions -ffunction-sections -fdata-sections \
			 -g -mdebugger -Wcast-align -fno-short-double -mprocessor=$(CPUTYPE) \
			 -DF_CPU=80000000L -DARDUINO=23 -D_BOARD_MEGA_ -DMPIDEVER=0x01000202 \
			 -DMPIDE=23 -I../core/variants/$(VARIANT) -I../core 

LIBS=$(shell ls -d */)
CFLAGS+=$(patsubst %,-I%,$(LIBS))

SRC_C=$(wildcard **/**/*.c) 
SRC_CPP=$(wildcard **/*.cpp)

OBJ_C=$(patsubst %.c,%.o,$(SRC_C))
OBJ_CPP=$(patsubst %.cpp,%.o,$(SRC_CPP))

all: libs.a

$(OBJ_S): $(SRC_S)
	$(CXX) $(CFLAGS) $< -o $@

$(OBJ_C): $(SRC_C)
	$(CC) $(CFLAGS) $< -o $@

$(OBJ_CPP): $(SRC_CPP)
	$(CXX) $(CFLAGS) $< -o $@

libs.a: $(OBJ_S) $(OBJ_C) $(OBJ_CPP)
	$(AR) rcs libs.a $(OBJ_C) $(OBJ_CPP)

.PHONY: clean
clean:
	-rm `find . -name "*.o"` 
	-rm libs.a
