AM_CFLAGS = \
	$(PTHREAD_CFLAGS)
AM_CPPFLAGS = \
	-I$(top_srcdir)/src/gtest/include \
	-I$(top_srcdir)/src \
	-I$(top_srcdir)/src/mapi \
	-I$(top_builddir)/src/mapi/glapi \
	-I$(top_srcdir)/src/mapi/glapi \
	-I$(top_builddir)/src/mesa \
	-I$(top_srcdir)/src/mesa \
	-I$(top_srcdir)/include \
	$(DEFINES) $(INCLUDE_DIRS)

TESTS = main-test
check_PROGRAMS = main-test

main_test_SOURCES =			\
	enum_strings.cpp

main_test_LDADD = \
	$(top_builddir)/src/mesa/libmesa.la \
	$(top_builddir)/src/gtest/libgtest.la \
	$(PTHREAD_LIBS) \
	$(DLOPEN_LIBS) \
	$(CLOCK_LIB)

if HAVE_SHARED_GLAPI
main_test_SOURCES +=			\
	dispatch_sanity.cpp		\
	mesa_formats.cpp			\
	mesa_extensions.cpp			\
	program_state_string.cpp

main_test_LDADD += \
	$(top_builddir)/src/mapi/shared-glapi/libglapi.la
else
main_test_SOURCES +=			\
	stubs.cpp
endif

EXTRA_DIST = meson.build
