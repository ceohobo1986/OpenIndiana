#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2013 Andrzej Szeszo.  All rights reserved.
# Copyright 2016-2019 Aurelien Larcher. All rights reserved.
#

BUILD_BITS=64
include ../../../make-rules/shared-macros.mk

COMPONENT_VERSION= 10.1.0
COMPONENT_SRC= gcc-releases-gcc-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_NAME)-$(COMPONENT_VERSION).tar.gz
COMPONENT_ARCHIVE_URL= https://github.com/gcc-mirror/gcc/archive/releases/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= \
  sha256:0fd6876c022daa1fc84db88396ecf114ab3598c4408d2ffd28ca3cd9be7d3b16

MPFR_VERSION=4.0.2
MPFR_ARCHIVE_HASH= \
  sha256:c05e3f02d09e0e9019384cdd58e0f19c64e6db1fd6f5ecf77b4b1c61ca253acc

MPC_VERSION=1.1.0
MPC_ARCHIVE_HASH= \
  sha256:6985c538143c1208dcb1ac42cedad6ff52e267b47e5f970183a3e75125b43c2e

GMP_VERSION=6.1.2
GMP_ARCHIVE_HASH= \
  sha256:5275bb04f4863a13516b2f39392ac5e272f5e1bb8057b18aec1c9b79d73d8fb2

include $(WS_MAKE_RULES)/gcc-component.mk

PYTHON_VERSION= 3.5

GCC_MAJOR="$(GCC_COMPONENT_VERSION_MAJOR)"
PKG_VARS += GCC_MAJOR

# Workaround platform definition inconsistency
ifeq ($(strip $(BUILD_BITS)),64)
PARCH = $(MACH:i386=x86_64-pc)
else
PARCH = $(MACH:i386=i386-pc)
endif
GNU_TRIPLET = $(PARCH:sparc=sparc-sun)-solaris$(SOLARIS_VERSION)
PKG_MACROS += GNU_TRIPLET="$(GNU_TRIPLET)"

CONFIGURE_BINDIR.64 = $(CONFIGURE_PREFIX)/bin
CONFIGURE_LIBDIR.64 = $(CONFIGURE_PREFIX)/lib

CONFIGURE_OPTIONS+= --with-diagnostics-urls=auto-if-env
CONFIGURE_OPTIONS+= --enable-plugins
CONFIGURE_OPTIONS+= --enable-objc-gc
CONFIGURE_OPTIONS.i386+= --enable-initfini-array
CONFIGURE_OPTIONS+= --enable-languages=c,c++,fortran,lto,objc
CONFIGURE_OPTIONS+= --disable-libitm
CONFIGURE_OPTIONS+= enable_frame_pointer=yes

# Auto-generated dependencies
REQUIRED_PACKAGES += library/gc

