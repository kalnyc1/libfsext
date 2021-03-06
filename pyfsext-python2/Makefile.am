# Note that we cannot use: AUTOMAKE_OPTIONS = subdir-objects
# subdir-objects will compile the source files to a single version of Python.
# Since subdir-objects is being deprecated we copy the source files instead.
am__installdirs = "$(DESTDIR)$(pyexecdir2)"
pyexecdir = $(pyexecdir2)

if HAVE_PYTHON2
AM_CFLAGS = \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/common \
	@LIBCERROR_CPPFLAGS@ \
	@LIBCDATA_CPPFLAGS@ \
	@LIBCLOCALE_CPPFLAGS@ \
	@LIBCSPLIT_CPPFLAGS@ \
	@LIBUNA_CPPFLAGS@ \
	@LIBCFILE_CPPFLAGS@ \
	@LIBCPATH_CPPFLAGS@ \
	@LIBBFIO_CPPFLAGS@ \
	@LIBFGUID_CPPFLAGS@

am_pyfsext_la_rpath = -rpath $(pyexecdir2)

BUILT_SOURCES = \
	pyfsext.c pyfsext.h \
	pyfsext_error.c pyfsext_error.h \
	pyfsext_file_object_io_handle.c pyfsext_file_object_io_handle.h \
	pyfsext_integer.c pyfsext_integer.h \
	pyfsext_libbfio.h \
	pyfsext_libcerror.h \
	pyfsext_libfsext.h \
	pyfsext_python.h \
	pyfsext_unused.h \
	pyfsext_volume.c pyfsext_volume.h

pyexec_LTLIBRARIES = pyfsext.la

nodist_pyfsext_la_SOURCES = $(BUILT_SOURCES)

pyfsext_la_LIBADD = \
	@LIBCERROR_LIBADD@ \
	../libfsext/libfsext.la \
	@LIBCDATA_LIBADD@ \
	@LIBCLOCALE_LIBADD@ \
	@LIBCSPLIT_LIBADD@ \
	@LIBUNA_LIBADD@ \
	@LIBCFILE_LIBADD@ \
	@LIBCPATH_LIBADD@ \
	@LIBBFIO_LIBADD@ \
	@LIBFGUID_LIBADD@

pyfsext_la_CPPFLAGS = $(PYTHON2_CPPFLAGS)
pyfsext_la_LDFLAGS  = -module -avoid-version $(PYTHON2_LDFLAGS)

$(BUILT_SOURCES):
	/bin/cp -f $(top_srcdir)/pyfsext/$@ $@

endif

MAINTAINERCLEANFILES = \
	Makefile.in

clean-local:
	/bin/rm -f pyfsext*.[ch]

distclean: clean
	/bin/rm -f Makefile

