# Makefile.am

NULL = 

ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}

SUBDIRS = src \
          tests \
          web-assets \
          doc \
          $(NULL)


.PHONY: test
test:
	cd tests && $(MAKE) $(AM_MAKEFLAGS) check

