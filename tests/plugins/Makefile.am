AM_CPPFLAGS += -I$(top_srcdir)/tests/utils -I$(top_srcdir)/plugins

LIBTAP=$(top_builddir)/tests/utils/tap/libtap.la
COMMON_TEST_LDADD = $(LIBTAP) \
	$(top_builddir)/lib/libbabeltrace.la \
	$(top_builddir)/common/libbabeltrace-common.la \
	$(top_builddir)/logging/libbabeltrace-logging.la \
	$(top_builddir)/compat/libcompat.la

check_SCRIPTS =
noinst_PROGRAMS =

if !ENABLE_BUILT_IN_PLUGINS
test_utils_muxer_SOURCES = test-utils-muxer.c
test_utils_muxer_LDADD = $(COMMON_TEST_LDADD)

noinst_PROGRAMS += test-utils-muxer
check_SCRIPTS += test-utils-muxer-complete
endif

if ENABLE_DEBUG_INFO
test_dwarf_LDADD = \
	$(top_builddir)/plugins/lttng-utils/libdebug-info.la \
	$(top_builddir)/logging/libbabeltrace-logging.la \
	$(top_builddir)/common/libbabeltrace-common.la \
	$(ELFUTILS_LIBS) \
	$(LIBTAP)
test_dwarf_SOURCES = test_dwarf.c

test_bin_info_LDADD = \
	$(top_builddir)/plugins/lttng-utils/libdebug-info.la \
	$(top_builddir)/logging/libbabeltrace-logging.la \
	$(top_builddir)/common/libbabeltrace-common.la \
	$(ELFUTILS_LIBS) \
	$(LIBTAP)
test_bin_info_SOURCES = test_bin_info.c

noinst_PROGRAMS += test_dwarf test_bin_info
check_SCRIPTS += test_dwarf_complete test_bin_info_complete
endif
