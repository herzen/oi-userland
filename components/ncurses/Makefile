#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2012, Oracle and/or its affiliates. All rights reserved.
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		ncurses
COMPONENT_VERSION=	5.7
COMPONENT_PROJECT_URL=	http://www.gnu.org/software/ncurses/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH= \
    sha256:0a9bdea5c7de8ded5c9327ed642915f2cc380753f12d4ad120ef7da3ea3498f4
COMPONENT_ARCHIVE_URL=	http://ftp.gnu.org/pub/gnu/$(COMPONENT_NAME)/$(COMPONENT_ARCHIVE)
COMPONENT_BUGDB=	library/libxml

include ../../make-rules/prep.mk
include ../../make-rules/configure.mk
include ../../make-rules/ips.mk

# Needed to make "gmake test" work.
COMPONENT_PRE_CONFIGURE_ACTION = \
	($(CLONEY) $(SOURCE_DIR) $(@D))

CONFIGURE_PREFIX =	/usr/gnu

# Needed to correctly build that 64-bit library.
LDFLAGS += $(CC_BITS)

CONFIGURE_OPTIONS +=	--with-shared
CONFIGURE_OPTIONS +=	--with-normal
CONFIGURE_OPTIONS +=	--enable-rpath
CONFIGURE_OPTIONS +=	--enable-widec
CONFIGURE_OPTIONS +=	--includedir=$(USRINCDIR)/ncurses

# Needed to pass -m32 or -m64 to the C/C++ compiler and linker.
CONFIGURE_OPTIONS +=	CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS +=	CXXFLAGS="$(CXXFLAGS)"
CONFIGURE_OPTIONS +=	LDFLAGS="$(LDFLAGS)"

# XXX: Ugly hack copied directly from the desktop SUNWncurses.spec file:
# The sun-color terminfo included in ncurses does not work;
# copying the one shipped with Sun's curses fixes it:
COMPONENT_POST_INSTALL_ACTION += \
	$(CP) /usr/share/lib/terminfo/s/sun-color \
	$(PROTO_DIR)$(GNULIB)/terminfo/s/

# common targets
build:          $(BUILD_32_and_64)

install:        $(INSTALL_32_and_64)

test:           $(BUILD_32_and_64)
		(cd $(BUILD_DIR)/$(MACH32)/test; $(GMAKE))
		(cd $(BUILD_DIR)/$(MACH64)/test; $(GMAKE))

BUILD_PKG_DEPENDENCIES =        $(BUILD_TOOLS)

include ../../make-rules/depend.mk