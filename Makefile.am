AUTOMAKE_OPTIONS = foreign

CFLAGS = -Wall -pedantic
include_HEADERS = skinc.h

lib_LTLIBRARIES = libskinc.la
libskinc_la_SOURCES  = skinclib.c
libskinc_la_LDFLAGS= -version-info 1:0:0

bin_PROGRAMS = skin_embedded_c_prog_example
skin_embedded_c_prog_example_SOURCES = skinc.c
skin_embedded_c_prog_example_LDADD = .libs/libskinc.la
skin_embedded_c_prog_example_DEPENDENCIES = libskinc.la
