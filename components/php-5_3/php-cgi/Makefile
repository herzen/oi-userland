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
# Copyright (c) 2012, Oracle and/or its affiliates. All rights reserved.
#
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		php
COMPONENT_VERSION=	5.3.14
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH= \
    sha256:c8075b6e83c5db0d26cc8426a7456856421089a76c963813b1fcac3ced041cb3
COMPONENT_ARCHIVE_URL=	http://us.php.net/get/$(COMPONENT_ARCHIVE)/from/this/mirror

PATCH_DIR = ../php-sapi/patches

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

include ../common.mk
include ../php-sapi/php.mk

CONFIGURE_OPTIONS  += \
	--disable-all \
	$(COMMON_CONFIG_OPTIONS) \
	--with-config-file-path=$(NSAPI_CONF_DIR) \
	--with-config-file-scan-dir=$(MODULES_CONF_DIR) \
	--disable-discard-path \
	--enable-cgi \
	--enable-fastcgi \
	--enable-force-cgi-redirect

CONFIGURE_ENV += $(CONF_ENVLINE)

COMPONENT_INSTALL_TARGETS = install-sapi

# common targets
build:		$(BUILD_32)

install:	$(INSTALL_32)

test:		$(TEST_32)

# php-sapi does the publish
publish:	install

BUILD_PKG_DEPENDENCIES =	$(BUILD_TOOLS)

include $(WS_TOP)/make-rules/depend.mk
