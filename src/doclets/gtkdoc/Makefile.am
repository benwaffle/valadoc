NULL =

AM_CFLAGS = \
	-DPACKAGE_ICONDIR=\"$(datadir)/valadoc/web-assets/\" \
	-I $(top_builddir)/src/libvaladoc/ \
	$(GLIB_CFLAGS) \
	$(LIBGEE_CFLAGS) \
	$(LIBGVC_CFLAGS) \
	-g \
	-w \
	$(NULL)

AM_VALAFLAGS = \
	$(VALAFLAGS) \
	--vapidir $(top_srcdir)/src/vapi \
	--vapidir $(top_builddir)/src/libvaladoc \
	--basedir $(srcdir) \
	--directory $(builddir) \
	-C \
	-g \
	$(NULL)

BUILT_SOURCES = libdoclet.vala.stamp

doclet_LTLIBRARIES = libdoclet.la

docletdir = $(libdir)/valadoc/doclets/gtkdoc

libdoclet_la_LDFLAGS = -module -avoid-version -no-undefined

libdoclet_la_VALASOURCES = \
	commentconverter.vala \
	dbus.vala \
	doclet.vala \
	gcomment.vala \
	generator.vala \
	utils.vala \
	$(NULL)

nodist_libdoclet_la_SOURCES = \
	$(libdoclet_la_VALASOURCES:.vala=.c) \
	$(NULL)

libdoclet.vala.stamp: $(libdoclet_la_VALASOURCES) Makefile
	$(VALAC) \
		$(AM_VALAFLAGS) \
		--pkg gee-0.8 \
		--pkg valadoc-1.0 \
		$(filter %.vala %.c,$^)
	touch $@

libdoclet_la_LIBADD = \
	$(top_builddir)/src/libvaladoc/libvaladoc.la \
	$(GLIB_LIBS) \
	$(LIBGEE_LIBS) \
	$(NULL)

EXTRA_DIST = \
	$(libdoclet_la_VALASOURCES) \
	$(NULL)

CLEANFILES = \
	$(BUILT_SOURCES) \
	$(nodist_libdoclet_la_SOURCES) \
	$(NULL)

