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
# Copyright (c) 2011, 2012, Oracle and/or its affiliates. All rights reserved.
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		motif
COMPONENT_VERSION=	2.3.4
COMPONENT_SRC_NAME=	motif
COMPONENT_SRC=		$(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC)-src.tgz
COMPONENT_ARCHIVE_HASH=	\
    sha256:637efa09608e0b8f93465dbeb7c92e58ebb14c4bc1b488040eb79a65af3efbe0
COMPONENT_ARCHIVE_URL=	http://prdownloads.sourceforge.net/motif/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=  http://motif.ics.com/motif
COMPONENT_BUGDB=	library/motif

include ../../make-rules/prep.mk
include ../../make-rules/configure.mk
include ../../make-rules/ips.mk

PKG_PROTO_DIRS += $(COMPONENT_DIR)/man

LDFLAGS += $(CC_BITS)

COMPONENT_PREP_ACTION =	( cd $(@D) && ./autogen.sh )
COMPONENT_PRE_CONFIGURE_ACTION = ( cp -a $(SOURCE_DIR)/* $(@D))

CONFIGURE_SCRIPT = $(@D)/configure

CONFIGURE_OPTIONS += --enable-xft
CONFIGURE_OPTIONS += --enable-jpeg
CONFIGURE_OPTIONS += --enable-png

include ../../make-rules/shared-targets.mk

# common targets
build: $(BUILD_32_and_64)

install:	$(INSTALL_32_and_64) \
		$(BUILD_DIR_32)/contrib/.installed \
		$(BUILD_DIR_64)/contrib/.installed

test: 		$(NO_TESTS)

BUILD_PKG_DEPENDENCIES =        $(BUILD_TOOLS)

include ../../make-rules/depend.mk
