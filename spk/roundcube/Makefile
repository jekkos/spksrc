SPK_NAME = roundcube
SPK_VERS = 1.0.1
SPK_REV = 2
SPK_ICON = src/roundcube.png
DSM_UI_DIR = app

DEPENDS  = cross/$(SPK_NAME)

MAINTAINER = moneytoo
DESCRIPTION = Roundcube is a free and open source webmail solution with a desktop-like user interface which is easy to install/configure and that runs on a standard LAMPP server. It is the same software Synology offers as Mail Station except this does not depend on Mail Server package.
ADMIN_URL = /roundcube/
RELOAD_UI = yes
DISPLAY_NAME = Roundcube Webmail
CHANGELOG = "1. DSM 5.0 compatibility"

HOMEPAGE   = http://www.roundcube.net/
LICENSE    = GPLv3

WIZARDS_DIR = src/wizard/
CONF_DIR = src/conf/

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh

INSTALL_DEP_SERVICES = apache-web mysql
START_DEP_SERVICES = apache-web mysql

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

POST_STRIP_TARGET = roundcube_extra_install

# Pure PHP package, make sure ARCH is not defined
override ARCH=

include ../../mk/spksrc.spk.mk

.PHONY: roundcube_extra_install
roundcube_extra_install:
	install -m 755 -d $(STAGING_DIR)/app
	install -m 644 src/app/config $(STAGING_DIR)/app/config
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48 72; do \
		convert $(SPK_ICON) -thumbnail $${size}x$${size} \
		        $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done
