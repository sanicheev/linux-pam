#
# Copyright (c) 2005, 2006, 2009 Thorsten Kukuk <kukuk@suse.de>
#

CLEANFILES = *~
MAINTAINERCLEANFILES = $(MANS) README

EXTRA_DIST = README $(MANS) $(XMLS) tst-pam_localuser

TESTS = tst-pam_localuser

man_MANS = pam_localuser.8
XMLS = README.xml pam_localuser.8.xml

securelibdir = $(SECUREDIR)
secureconfdir = $(SCONFIGDIR)

AM_CFLAGS = -I$(top_srcdir)/libpam/include -I$(top_srcdir)/libpamc/include \
	$(WARN_CFLAGS)
AM_LDFLAGS = -no-undefined -avoid-version -module
if HAVE_VERSIONING
  AM_LDFLAGS += -Wl,--version-script=$(srcdir)/../modules.map
endif

securelib_LTLIBRARIES = pam_localuser.la
pam_localuser_la_LIBADD = $(top_builddir)/libpam/libpam.la

if ENABLE_REGENERATE_MAN
noinst_DATA = README
README: pam_localuser.8.xml
-include $(top_srcdir)/Make.xml.rules
endif
