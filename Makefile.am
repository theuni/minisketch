ACLOCAL_AMFLAGS = -I build-aux/m4
AM_CXXFLAGS = $(WARN_CXXFLAGS) $(NOWARN_CXXFLAGS)

include sources.mk

include_HEADERS = $(MINISKETCH_DIST_HEADERS_INT)
noinst_HEADERS = $(MINISKETCH_LIB_HEADERS_INT) $(MINISKETCH_FIELD_GENERIC_HEADERS_INT) $(MINISKETCH_FIELD_CLMUL_HEADERS_INT)

LIBMINISKETCH = libminisketch.la
LIBMINISKETCH_FIELD_GENERIC = libminisketch_field_generic.la
if ENABLE_CLMUL
LIBMINISKETCH_FIELD_CLMUL = libminisketch_field_clmul.la
endif
if USE_TESTS
LIBMINISKETCH_DEBUG=libminisketch_debug.la
LIBMINISKETCH_FIELD_GENERIC_DEBUG=libminisketch_field_generic_debug.la
if ENABLE_CLMUL
LIBMINISKETCH_FIELD_CLMUL_DEBUG=libminisketch_field_clmul_debug.la
endif
endif

lib_LTLIBRARIES =
lib_LTLIBRARIES +=  $(LIBMINISKETCH)

noinst_LTLIBRARIES =
noinst_LTLIBRARIES += $(LIBMINISKETCH_FIELD_GENERIC)
noinst_LTLIBRARIES += $(LIBMINISKETCH_FIELD_GENERIC_DEBUG)
noinst_LTLIBRARIES += $(LIBMINISKETCH_FIELD_CLMUL)
noinst_LTLIBRARIES += $(LIBMINISKETCH_FIELD_CLMUL_DEBUG)
noinst_LTLIBRARIES += $(LIBMINISKETCH_DEBUG)

# Release libs
libminisketch_field_generic_la_SOURCES = $(MINISKETCH_FIELD_GENERIC_SOURCES_INT)
libminisketch_field_generic_la_CPPFLAGS = $(AM_CPPFLAGS) $(RELEASE_DEFINES)

libminisketch_field_clmul_la_SOURCES = $(MINISKETCH_FIELD_CLMUL_SOURCES_INT)
libminisketch_field_clmul_la_CPPFLAGS = $(AM_CPPFLAGS) $(RELEASE_DEFINES)
libminisketch_field_clmul_la_CXXFLAGS = $(AM_CXXFLAGS) $(CLMUL_CXXFLAGS)

libminisketch_la_SOURCES = $(MINISKETCH_LIB_SOURCES_INT)
libminisketch_la_CPPFLAGS = $(AM_CPPFLAGS) $(RELEASE_DEFINES)
libminisketch_la_LIBADD = $(LIBMINISKETCH_FIELD_CLMUL) $(LIBMINISKETCH_FIELD_GENERIC)

# Debug libs
libminisketch_field_generic_debug_la_SOURCES = $(MINISKETCH_FIELD_GENERIC_SOURCES_INT)
libminisketch_field_generic_debug_la_CPPFLAGS = $(AM_CPPFLAGS) $(DEBUG_DEFINES)

libminisketch_field_clmul_debug_la_SOURCES = $(MINISKETCH_FIELD_CLMUL_SOURCES_INT)
libminisketch_field_clmul_debug_la_CPPFLAGS = $(AM_CPPFLAGS) $(DEBUG_DEFINES)
libminisketch_field_clmul_debug_la_CXXFLAGS = $(AM_CXXFLAGS) $(CLMUL_CXXFLAGS)

libminisketch_debug_la_SOURCES = $(MINISKETCH_LIB_SOURCES_INT)
libminisketch_debug_la_CPPFLAGS = $(AM_CPPFLAGS) $(DEBUG_DEFINES)
libminisketch_debug_la_LIBADD = $(LIBMINISKETCH_FIELD_CLMUL_DEBUG) $(LIBMINISKETCH_FIELD_GENERIC_DEBUG)

noinst_PROGRAMS =
if USE_BENCHMARK
noinst_PROGRAMS += bench
endif
if USE_TESTS
noinst_PROGRAMS += test-exhaust
TESTS = test-exhaust
endif

bench_SOURCES = $(MINISKETCH_BENCH_SOURCES_INT)
bench_LDADD = $(LIBMINISKETCH)
bench_LDFLAGS = $(AM_LDFLAGS) -static

test_exhaust_SOURCES = $(MINISKETCH_TEST_SOURCES_INT)
test_exhaust_CPPFLAGS = $(AM_CPPFLAGS) -DMINISKETCH_VERIFY
test_exhaust_CXXFLAGS = $(AM_CXXFLAGS) $(PTHREAD_CFLAGS)
test_exhaust_LDADD = $(LIBMINISKETCH_DEBUG)
test_exhaust_LDFLAGS = $(AM_LDFLAGS) $(PTHREAD_CFLAGS) -static

EXTRA_DIST=
EXTRA_DIST += LICENSE
EXTRA_DIST += README.md
EXTRA_DIST += doc/example.c
EXTRA_DIST += doc/gen_params.sage
EXTRA_DIST += doc/math.md
EXTRA_DIST += doc/moduli.md
EXTRA_DIST += doc/plot_bits.png
EXTRA_DIST += doc/plot_capacity.png
EXTRA_DIST += doc/plot_diff.png
EXTRA_DIST += doc/plot_size.png
EXTRA_DIST += doc/protocoltips.md
