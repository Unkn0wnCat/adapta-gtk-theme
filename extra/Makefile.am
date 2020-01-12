themedir     = $(datadir)/themes
kdaptadir    = $(DESTDIR)$(themedir)/Kdapta
noktodir     = $(DESTDIR)$(themedir)/Kdapta-Nokto
kdaptaetadir = $(DESTDIR)$(themedir)/Kdapta-Eta
noktoetadir  = $(DESTDIR)$(themedir)/Kdapta-Nokto-Eta

chromedir         = $(srcdir)/chrome
chrome_file       = $(chromedir)/kdapta-theme.crx
chrome_nokto_file = $(chromedir)/kdapta-nokto-theme.crx

plankdir   = $(srcdir)/plank
plank_file = $(plankdir)/dock.theme

telegramdir         = $(srcdir)/telegram
telegram_file       = $(telegramdir)/kdapta.tdesktop-theme
telegram_nokto_file = $(telegramdir)/kdapta-nokto.tdesktop-theme

geditdir   = $(srcdir)/gedit
gedit_file = \
	$(geditdir)/kdapta.xml \
	$(geditdir)/README.md

tweetdeckdir         = $(srcdir)/tweetdeck
tweetdeck_file       = $(tweetdeckdir)/light/ColorDeck-kdapta.cdk
tweetdeck_nokto_file = $(tweetdeckdir)/dark/ColorDeck-kdapta-nokto.cdk

# ******************
# * Generate files *
# ******************

all:
if ENABLE_TWEETDECK
	cd $(tweetdeckdir) && ./recolor-cdk.sh
endif

# *****************
# * Install files *
# *****************

install-data-local:
if ENABLE_CHROME_LEGACY
	$(MKDIR_P) $(kdaptadir)/chrome
	$(MKDIR_P) $(noktodir)/chrome
	cp -Rv $(chrome_file) $(kdaptadir)/chrome
	cp -Rv $(chrome_nokto_file) $(noktodir)/chrome

	cd $(kdaptadir)
	ln -sf ../Kdapta/chrome $(kdaptaetadir)/chrome
	ln -sf ../Kdapta-Nokto/chrome $(noktoetadir)/chrome
endif

if ENABLE_PLANK
	$(MKDIR_P) $(kdaptadir)/plank
	cp -Rv $(plank_file) $(kdaptadir)/plank
	cd $(kdaptadir)
	ln -sf ../Kdapta/plank $(noktodir)/plank
	ln -sf ../Kdapta/plank $(kdaptaetadir)/plank
	ln -sf ../Kdapta/plank $(noktoetadir)/plank
endif

if ENABLE_TELEGRAM
	$(MKDIR_P) $(kdaptadir)/telegram
	$(MKDIR_P) $(noktodir)/telegram
	cp -Rv $(telegram_file) $(kdaptadir)/telegram
	cp -Rv $(telegram_nokto_file) $(noktodir)/telegram

	cd $(kdaptadir)
	ln -sf ../Kdapta/telegram $(kdaptaetadir)/telegram
	ln -sf ../Kdapta-Nokto/telegram $(noktoetadir)/telegram
endif

if ENABLE_TWEETDECK
	$(MKDIR_P) $(kdaptadir)/tweetdeck
	$(MKDIR_P) $(noktodir)/tweetdeck
	cp -Rv $(tweetdeck_file) $(kdaptadir)/tweetdeck
	cp -Rv $(tweetdeck_nokto_file) $(noktodir)/tweetdeck
	cd $(kdaptadir)
	ln -sf ../Kdapta/tweetdeck $(kdaptaetadir)/tweetdeck
	ln -sf ../Kdapta-Nokto/tweetdeck $(noktoetadir)/tweetdeck
endif

	$(MKDIR_P) $(kdaptadir)/gedit
	cp -Rv $(gedit_file) $(kdaptadir)/gedit
	cd $(kdaptadir)
	ln -sf ../Kdapta/gedit $(noktodir)/gedit

# *******************
# * Uninstall files *
# *******************

uninstall-local:
if ENABLE_CHROME_LEGACY
	test -e $(noktodir)/chrome && rm -rfv $(noktodir)/chrome
	test -e $(kdaptadir)/chrome && rm -rfv $(kdaptadir)/chrome
	test -e $(noktoetadir)/chrome && rm -rfv $(noktoetadir)/chrome
	test -e $(kdaptaetadir)/chrome && rm -rfv $(kdaptaetadir)/chrome
endif

if ENABLE_PLANK
	test -e $(noktodir)/plank && rm -rfv $(noktodir)/plank
	test -e $(kdaptadir)/plank && rm -rfv $(kdaptadir)/plank
	test -e $(noktoetadir)/plank && rm -rfv $(noktoetadir)/plank
	test -e $(kdaptaetadir)/plank && rm -rfv $(kdaptaetadir)/plank
endif

if ENABLE_TELEGRAM
	test -e $(noktodir)/telegram && rm -rfv $(noktodir)/telegram
	test -e $(kdaptadir)/telegram && rm -rfv $(kdaptadir)/telegram
	test -e $(noktoetadir)/telegram && rm -rfv $(noktoetadir)/telegram
	test -e $(kdaptaetadir)/telegram && rm -rfv $(kdaptaetadir)/telegram
endif

if ENABLE_TWEETDECK
	test -e $(noktodir)/tweetdeck && rm -rfv $(noktodir)/tweetdeck
	test -e $(kdaptadir)/tweetdeck && rm -rfv $(kdaptadir)/tweetdeck
	test -e $(noktoetadir)/tweetdeck && rm -rfv $(noktoetadir)/tweetdeck
	test -e $(kdaptaetadir)/tweetdeck && rm -rfv $(kdaptaetadir)/tweetdeck
endif

	test -e $(noktodir)/gedit && rm -rfv $(noktodir)/gedit
	test -e $(kdaptadir)/gedit && rm -rfv $(kdaptadir)/gedit

# ****************************
# * Clean up generated files *
# ****************************

CLEANFILES =

if ENABLE_TWEETDECK
CLEANFILES += \
	$(tweetdeckdir)/light/ColorDeck-kdapta.cdk \
	$(tweetdeckdir)/dark/ColorDeck-kdapta-nokto.cdk
endif

DISTCLEANFILES = \
	$(CLEANFILES)
