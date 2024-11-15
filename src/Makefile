##############################################################################
##
##  Makefile for Detours.
##
##  Microsoft Research Detours Package, Version 4.0.1
##
##  Copyright (c) Microsoft Corporation.  All rights reserved.
##

ROOT = ..
include ../system.mak
CC=x86_64-w64-mingw32-g++

DETOURS_SOURCE_BROWSING = 0

#######################/#######################################################
##
CFLAGS=-O2

OBJS = \
    $(OBJD)/detours.obj     \
    $(OBJD)/modules.obj     \
    $(OBJD)/disasm.obj      \
    $(OBJD)/image.obj       \
    $(OBJD)/creatwth.obj    \
    $(OBJD)/disolx86.obj    \
    $(OBJD)/disolx64.obj    \
    $(OBJD)/disolia64.obj   \
    $(OBJD)/disolarm.obj    \
    $(OBJD)/disolarm64.obj  \

all: dirs \
	$(LIBD)/detours.lib \
	$(INCD)/detours.h   \
	$(INCD)/detver.h

dirs:
	@mkdir -p $(INCD) $(LIBD) $(BIND) $(OBJD)

$(OBJD)/%.obj: %.cpp $(INCD)/detours.h
	$(CC) $(CFLAGS) -o $@ -c $<

$(LIBD)/detours.lib : $(OBJS)
	$(CC) --shared -o $@ $(OBJS)

$(INCD)/detours.h : detours.h
	cp detours.h $@

$(INCD)/detver.h : detver.h
	cp detver.h $@

$(OBJD)/detours.obj : detours.cpp detours.h
$(OBJD)/modules.obj : modules.cpp detours.h
$(OBJD)/disasm.obj : disasm.cpp detours.h
$(OBJD)/image.obj : image.cpp detours.h
$(OBJD)/creatwth.obj : creatwth.cpp uimports.cpp detours.h
$(OBJD)/disolx86.obj: disasm.cpp detours.h
$(OBJD)/disolx64.obj: disasm.cpp detours.h
$(OBJD)/disolia64.obj: disasm.cpp detours.h
$(OBJD)/disolarm.obj: disasm.cpp detours.h
$(OBJD)/disolarm64.obj: disasm.cpp detours.h