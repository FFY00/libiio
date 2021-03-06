# libiio - Library for interfacing industrial I/O (IIO) devices
#
# Copyright (C) 2014 Analog Devices, Inc.
# Author: Paul Cercueil <paul.cercueil@analog.com>
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.


TARGETS := ad9361-iiostream ad9371-iiostream adrv9009-iiostream dummy-iiostream iio-monitor

CFLAGS = -Wall -DIIO_CHECK_RET

UNAME_S := $(shell uname -s)

ifeq ($(UNAME_S),Darwin)
	CFLAGS += -framework iio
else
	LDFLAGS += -liio
endif

.PHONY: all clean

all: $(TARGETS)

iio-monitor: iio-monitor.o
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS) -lpthread -lncurses -lcdk

ad9361-iiostream : ad9361-iiostream.o
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)

ad9371-iiostream : ad9371-iiostream.o
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)

adrv9009-iiostream : adrv9009-iiostream.o
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)

dummy-iiostream : dummy-iiostream.o
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)

clean:
	rm -f $(TARGETS) $(TARGETS:%=%.o)
