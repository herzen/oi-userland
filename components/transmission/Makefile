#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2015 Alexander Pyhalov
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		transmission
COMPONENT_VERSION=	2.84
COMPONENT_PROJECT_URL=	http://www.transmissionbt.com/
COMPONENT_SUMMARY=	GTK and console BitTorrent client
COMPONENT_FMRI=		desktop/torrent/transmission
COMPONENT_CLASSIFICATION=	Applications/Internet
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH=	\
    sha256:a9fc1936b4ee414acc732ada04e84339d6755cd0d097bcbd11ba2cfc540db9eb
COMPONENT_ARCHIVE_URL=	http://download.transmissionbt.com/files/$(COMPONENT_ARCHIVE)
COMPONENT_LICENSE_FILE=	COPYING
COMPONENT_LICENSE=	GPLv2,MIT


include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

PATH=/usr/gnu/bin:/usr/bin

CONFIGURE_OPTIONS+=	--program-prefix=""

# common targets
build:		$(BUILD_32)

install:	$(INSTALL_32)

test:		$(NO_TESTS)
