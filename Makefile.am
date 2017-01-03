ACLOCAL_AMFLAGS  = -I m4
AUTOMAKE_OPTIONS = no-dist foreign

sbin_SCRIPTS = \
	acme-renew-single \
	acme-renew-all \
	acme-setup-cert \
	acme-setup-account

CLEANFILES = \
	libcommon.sh \
	acme-renew-single \
	acme-renew-all \
	acme-setup-cert \
	acme-setup-account \
	acme.conf

pkgdata_DATA = \
	libcommon.sh \
	acme-tiny/acme_tiny.py

sysconf_DATA = \
	acme.conf

do_subst = sed  -e 's,[@]pkgdatadir[@],$(pkgdatadir),g' \
		-e 's,[@]sysconfdir[@],$(sysconfdir),g' \
		-e 's,[@]challengedir[@],$(challengedir),g' \
		-e 's,[@]certdir[@],$(certdir),g' \
		-e 's,[@]SU[@],$(SU),g' \
		-e 's,[@]DIG[@],$(DIG),g' \
		-e 's,[@]WGET[@],$(WGET),g' \
		-e 's,[@]PWGEN[@],$(PWGEN),g' \
		-e 's,[@]PYTHON[@],$(PYTHON),g' \
		-e 's,[@]SETFACL[@],$(SETFACL),g' \
		-e 's,[@]OPENSSL[@],$(OPENSSL),g'

acme.conf: acme.conf.in Makefile
	$(do_subst) < $(srcdir)/acme.conf.in > acme.conf

acme-renew-single: acme-renew-single.in Makefile
	$(do_subst) < $(srcdir)/acme-renew-single.in > acme-renew-single
	chmod +x acme-renew-single

acme-renew-all: acme-renew-all.in Makefile
	$(do_subst) < $(srcdir)/acme-renew-all.in > acme-renew-all
	chmod +x acme-renew-all

acme-setup-cert: acme-setup-cert.in Makefile
	$(do_subst) < $(srcdir)/acme-setup-cert.in > acme-setup-cert
	chmod +x acme-setup-cert

acme-setup-account: acme-setup-account.in Makefile
	$(do_subst) < $(srcdir)/acme-setup-account.in > acme-setup-account
	chmod +x acme-setup-account

libcommon.sh: libcommon.sh.in Makefile
	$(do_subst) < $(srcdir)/libcommon.sh.in > libcommon.sh
