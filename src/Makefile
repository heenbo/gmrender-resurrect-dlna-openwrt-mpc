CROSS_COMPILE = mips-openwrt-linux-
CC = gcc

MACRO_FLAGS = -DPACKAGE_NAME=\"aistoytestt\" -DPACKAGE_STRING=\"aistorydlna\" -DPKG_DATADIR=\"test\" -DHAVE_GST
CFLAGS = -lpthread ${MACRO_FLAGS} -std=gnu99 -g -O2 -Wall -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wwrite-strings
DLNA_CFLAG = -I/home/heenbo/work/openwrt-bb/staging_dir/target-mips_34kc_uClibc-0.9.33.2/usr/include
DLNA_CFLAGS = ${CFLAGS} ${DLNA_CFLAG} ${DLNA_CFLAG}/upnp ${DLNA_CFLAG}/glib-2.0 ${DLNA_CFLAG}/gstreamer-0.10 ${DLNA_CFLAG}/libxml2
DLNA_LDFLAGS =  -lpthread -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lxml2 -lglib-2.0 -lupnp -lthreadutil -lixml -lm -lffi -lz -luClibc -lmpdclient
CLIENT_CFLAGS = ${DLNA_CFLAGS}
CLIENT_LDFLAGS = -L/home/heenbo/work/openwrt-bb/staging_dir/target-mips_34kc_uClibc-0.9.33.2/usr/lib -L/home/heenbo/work/openwrt-bb/staging_dir/target-mips_34kc_uClibc-0.9.33.2/root-ar71xx/lib ${DLNA_LDFLAGS} 

SOURCES=main.c upnp.c upnp_control.c \
	upnp_connmgr.c upnp_transport.c \
	song-meta-data.c variable-container.c \
	upnp_device.c upnp_renderer.c \
	webserver.c output.c logging.c \
	xmldoc.c xmlescape.c output_mpc.c


PROJECTS=main.o upnp.o upnp_control.o \
	upnp_connmgr.o upnp_transport.o \
	song-meta-data.o variable-container.o \
	upnp_device.o upnp_renderer.o \
	webserver.o output.o logging.o \
	xmldoc.o xmlescape.o output_mpc.o

OBJECT = dlna_test

.PHONY: all clean

#all : $(OBJECT)

$(OBJECT):$(PROJECTS)
	${CROSS_COMPILE}${CC} ${CLIENT_LDFLAGS} $^ -o $@

#$(PROJECTS):$(SOURCES)
%o:%c
	${CROSS_COMPILE}${CC} -c ${CLIENT_CFLAGS} $< -o $@

clean:
	@rm *.o ${OBJECT}
