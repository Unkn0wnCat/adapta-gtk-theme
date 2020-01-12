ACLOCAL_AMFLAGS = -I m4

themedir  = $(datadir)/themes
kdaptadir = $(DESTDIR)$(themedir)/Kdapta
noktodir  = $(DESTDIR)$(themedir)/Kdapta-Nokto
kdaptaetadir = $(DESTDIR)$(themedir)/Kdapta-Eta
noktoetadir  = $(DESTDIR)$(themedir)/Kdapta-Nokto-Eta

SUBDIRS = \
	gtk \
	shell \
	wm \
	extra

EXTRA_DIST = \
	COPYING \
	LICENSE_CC_BY_SA4 \
	README.md

install-data-hook:
	cp -Rv $(EXTRA_DIST) $(kdaptadir)

uninstall-hook:
	test -e $(noktodir) && rm -rfv $(noktodir)
	test -e $(kdaptadir) && rm -rfv $(kdaptadir)
	test -e $(noktetaodir) && rm -rfv $(noktoetadir)
	test -e $(kdaptaetadir) && rm -rfv $(kdaptaetadir)
