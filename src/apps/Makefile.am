# $Id: Makefile.am,v 1.30 2010/01/27 03:21:08 jklowden Exp $

AM_CPPFLAGS	= -I$(top_srcdir)/include 

SUBDIRS		= fisql

DIST_SUBDIRS	= $(SUBDIRS)

# build bsqlodbc only if the ODBC library was to be built
if ODBC
bin_PROGRAMS	= tsql freebcp bsqldb defncopy datacopy bsqlodbc
else
bin_PROGRAMS	= tsql freebcp bsqldb defncopy datacopy
endif


dist_bin_SCRIPTS = osql

freebcp_LDADD	= ../dblib/libsybdb.la ../replacements/libreplacements.la $(LIBICONV) $(NETWORK_LIBS)
freebcp_SOURCES = freebcp.c freebcp.h

tsql_LDADD	= ../tds/libtds.la \
		  ../replacements/libreplacements.la \
		  $(NETWORK_LIBS) $(LIBICONV) $(FREETDS_LIBGCC) $(READLINE_LIBS)

bsqldb_LDADD	= ../dblib/libsybdb.la \
		  ../replacements/libreplacements.la \
		  $(NETWORK_LIBS) $(LIBICONV)

if ODBC
bsqlodbc_CPPFLAGS	= $(ODBC_INC) $(AM_CPPFLAGS)
bsqlodbc_LDADD	= $(ODBCLIB) $(ODBCNODMLIBAPP) \
		  ../replacements/libreplacements.la $(NETWORK_LIBS) $(LIBICONV)
endif

defncopy_LDADD	= ../dblib/libsybdb.la \
		  ../replacements/libreplacements.la \
		  $(NETWORK_LIBS) $(LIBICONV)

datacopy_SOURCES= datacopy.c
datacopy_LDADD	= ../dblib/libsybdb.la \
		  ../replacements/libreplacements.la \
		$(NETWORK_LIBS) $(LIBICONV)
