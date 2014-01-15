SPK_NAME = jappix
SPK_VERS = 0.9.9
SPK_REV = 1
SPK_ICON = src/jappix.png
DSM_UI_DIR = app

DEPENDS  = cross/$(SPK_NAME)

MAINTAINER = SynoCommunity
DESCRIPTION = Jappix, a full-featured XMPP web-client \(Jappix Desktop, Jappix Mobile \& Jappix Mini\). Jappix is a fresh new open social platform which enables you to create your own cloud, wherever you want to. People must be able to get in touch with all their friends on a free decentralized network!
ADMIN_URL = /jappix/
RELOAD_UI = yes
STARTABLE = no
DISPLAY_NAME = Jappix
BETA = 1

HOMEPAGE   = http://jappix.org/
LICENSE    = AGPL

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh

INSTALL_DEP_SERVICES = apache-web
START_DEP_SERVICES = apache-web

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

POST_STRIP_TARGET = jappix_extra_install

# Pure PHP package, make sure ARCH is not defined
override ARCH=

include ../../mk/spksrc.spk.mk

.PHONY: jappix_extra_install
jappix_extra_install:
	install -m 755 -d $(STAGING_DIR)/app
	install -m 644 src/app/config $(STAGING_DIR)/app/config
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48; do \
		convert $(SPK_ICON) -thumbnail $${size}x$${size} \
		        $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done