# $Id: Makefile 5862 2009-07-15 10:06:05Z andreidragus $
#
# Memcached implementation for memcache API.
#
# 
# WARNING: do not run this directly, it should be run by the master Makefile

include ../../Makefile.defs
auto_gen=
NAME=json.so

ifeq ($(CROSS_COMPILE),)
JSON_BUILDER = $(shell \
	if pkg-config --exists json; then \
		echo 'pkg-config json'; \
	elif pkg-config --exists json-c; then\
		echo 'pkg-config json-c'; \
	fi)

endif

ifeq ($(JSON_BUILDER),)
	DEFS += -I$(LOCALBASE)/include -I$(SYSBASE)/include
	LIBS += -L$(LOCALBASE)/lib -ljson
else
	DEFS += $(shell $(JSON_BUILDER) --cflags)
	LIBS += $(shell $(JSON_BUILDER) --libs)
endif

include ../../Makefile.modules
