GZIP_COMPRESSION ?= no
USE_HEATSHRINK ?= yes

-include ../../../esphttpdconfig.mk

CFLAGS=-I../../lib/heatshrink -I../../include -I.. -std=gnu99 
ifeq ("$(GZIP_COMPRESSION)","yes")
CFLAGS		+= -DESPFS_GZIP $(ZLIB_CFLAGS)
endif

ifeq ("$(USE_HEATSHRINK)","yes")
CFLAGS		+= -DESPFS_HEATSHRINK
endif

OBJS=main.o heatshrink_encoder.o
TARGET=mkespfsimage

$(TARGET): $(OBJS)
ifeq ("$(GZIP_COMPRESSION)","yes")
	$(CC) -o $@ $^ $(ZLIB_LFLAGS)
else
	$(CC) -o $@ $^
endif

clean:
	rm -f $(TARGET) $(OBJS)