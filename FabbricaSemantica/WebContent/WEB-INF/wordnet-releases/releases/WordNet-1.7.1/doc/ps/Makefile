SHELL=/bin/sh

# Makefile for WordNet 1.7.1 manual pages in PostScript format

WN_ROOT = /usr/local/WordNet-1.7.1
WN_INSTALLDIR = $(WN_ROOT)/doc/ps

all install install-man:
	if [ ! -d $(WN_INSTALLDIR) ] ; then \
		echo "Making directory $(WN_INSTALLDIR)" ; \
		mkdir -p $(WN_INSTALLDIR) ; \
		chmod 755 $(WN_INSTALLDIR) ; \
	fi ;
	@echo "Installing HTML pages in $(WN_INSTALLDIR)"
	@$(MAKE) -k WN_INSTALLDIR='$(WN_INSTALLDIR)' doinstall
	@echo "Done installing HTML pages in $(WN_INSTALLDIR)"

doinstall:
	@for file in *.ps ; \
	  do \
		filename=$(WN_INSTALLDIR)/$$file ; \
		if [ -f $$filename ] ; then \
			echo "Cannot install $$filename: file exists" ; \
		else \
			echo "Installing $$filename" ; \
			cp -p $$file $$filename ; \
		fi ; \
	 done ;

uninstall:
	@echo "Uninstalling WordNet documentation from $(WN_INSTALLDIR)"
	@$(MAKE) -k WN_INSTALLDIR='$(WN_INSTALLDIR)' douninstall
	@echo "Done uninstalling WordNet documentation from $(WN_INSTALLDIR)"

douninstall:
	@for file in *.ps ; \
	 do \
		filename=$(WN_INSTALLDIR)/$$file ; \
		if [ ! -f $$filename ] ; then \
			echo "Cannot uninstall $$filename: file not present" ; \
		else \
			echo "Uninstalling $$filename" ; \
			rm -f $$filename ; \
		fi ; \
	 done ;

clean:
	@rm -f *~ "#"*

