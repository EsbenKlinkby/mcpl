##################################################################################
#                                                                                #
# A very simple makefile which compiles the autogenerated "fat" commandline      #
# tools in src_fat of the MCPL distribution.                                     #
#                                                                                #
# Note that this simply builds the final executables directly in src_fat, with   #
# no intermediate build output.                                                  #
#                                                                                #
# Refer to the INSTALL file from the MCPL distribution for more details.         #
#                                                                                #
# Written 2017 by T. Kittelmann.                                                 #
#                                                                                #
##################################################################################

SHELL         = /bin/sh
CFLAGS        = -std=c99 -lm
CFLAGS_EXTRA ?=
DEBUGFLAGS    = -g -O0
RELEASEFLAGS  = -O2 -DNDEBUG
SRCDIR        = $(dir $(lastword $(MAKEFILE_LIST)))
DESTDIR       = $(SRCDIR)
CC           ?= gcc

TARGETS       = $(DESTDIR)mcpl2ssw $(DESTDIR)ssw2mcpl $(DESTDIR)mcpltool
CFLAGS += $(CFLAGS_EXTRA)

all: release

release: CFLAGS += $(RELEASEFLAGS)
release: $(TARGETS)

debug: CFLAGS += $(DEBUGFLAGS)
debug: $(TARGETS)

.PHONY : all clean release debug

clean:
	rm -f $(TARGETS)

$(DESTDIR)mcpltool: $(SRCDIR)mcpltool_app_fat.c
	$(CC) $(CFLAGS) $< -o $@

$(DESTDIR)ssw2mcpl: $(SRCDIR)ssw2mcpl_app_fat.c
	$(CC) $(CFLAGS) $< -o $@

$(DESTDIR)mcpl2ssw: $(SRCDIR)mcpl2ssw_app_fat.c
	$(CC) $(CFLAGS) $< -o $@
