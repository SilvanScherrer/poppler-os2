SUBDIRS = . tests

VENDOR ?=community
BUILD_INFO=\#\#1\#\# $(shell date +'%d %b %Y %H:%M:%S')     $(shell uname -n)
BUILDLEVEL_INFO=@\#$(VENDOR):$(POPPLER_VERSION)\#@$(BUILD_INFO)::::$(POPPLER_MICRO_VERSION)::

lib_LTLIBRARIES = libpoppler-cpp.la

libpoppler_cpp_includedir = $(includedir)/poppler/cpp
libpoppler_cpp_include_HEADERS =		\
	poppler-document.h			\
	poppler-embedded-file.h			\
	poppler-font.h				\
	poppler-global.h			\
	poppler-image.h				\
	poppler-page.h				\
	poppler-page-renderer.h			\
	poppler-page-transition.h		\
	poppler-rectangle.h			\
	poppler-toc.h				\
	$(builddir)/poppler-version.h

libpoppler_cpp_la_SOURCES =			\
	poppler-document.cpp			\
	poppler-document-private.h		\
	poppler-embedded-file.cpp		\
	poppler-embedded-file-private.h		\
	poppler-font.cpp			\
	poppler-global.cpp			\
	poppler-image.cpp			\
	poppler-image-private.h			\
	poppler-page.cpp			\
	poppler-page-private.h			\
	poppler-page-renderer.cpp		\
	poppler-page-transition.cpp		\
	poppler-private.cpp			\
	poppler-private.h			\
	poppler-rectangle.cpp			\
	poppler-toc.cpp				\
	poppler-toc-private.h			\
	poppler-version.cpp

if BUILD_LIBJPEG
libjpeg_includes = $(LIBJPEG_CFLAGS)
endif

if BUILD_LIBTIFF
libtiff_includes = $(LIBTIFF_CFLAGS)
endif

if BUILD_LIBOPENJPEG
libjpeg2000_includes = $(LIBOPENJPEG_CFLAGS)
endif

if BUILD_LIBPNG
libpng_includes = $(LIBPNG_CFLAGS)
endif

libpoppler_cpp_la_CPPFLAGS =			\
	-I$(top_srcdir)				\
	-I$(top_srcdir)/goo			\
	-I$(top_srcdir)/poppler			\
	$(libjpeg_includes)			\
	$(libtiff_includes)			\
	$(libjpeg2000_includes)			\
	$(libpng_includes)

libpoppler_cpp_la_CXXFLAGS =			\
	-Dpoppler_cpp_EXPORTS

libpoppler_cpp_la_LIBADD =			\
	$(top_builddir)/poppler/libpoppler.la	\
	$(LIBICONV)

libpoppler_cpp_la_LDFLAGS =			\
	-version-info 3:0:3			\
	@create_shared_lib@			\
	@auto_import_flags@			\
	-shortname popplc			\
	-buildlevel '$(BUILDLEVEL_INFO)'
