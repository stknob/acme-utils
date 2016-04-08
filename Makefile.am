ACLOCAL_AMFLAGS  = -I m4
AUTOMAKE_OPTIONS = no-dist foreign

sbin_SCRIPTS = \
	acme-renew-single \
	acme-renew-all \
	acme-setup-cert

CLEANFILES = \
	acme-renew-single \
	acme-renew-all \
	acme-setup-cert \
	acme.conf

pkgdata_DATA = \
	acme-tiny/acme_tiny.py

sysconf_DATA = \
	acme.conf

do_subst = sed  -e 's,[@]pkgdatadir[@],$(pkgdatadir),g' \
		-e 's,[@]sysconfdir[@],$(sysconfdir),g' \
		-e 's,[@]challengedir[@],$(challengedir),g' \
		-e 's,[@]certdir[@],$(certdir),g' \
		-e 's,[@]DIG[@],$(DIG),g' \
		-e 's,[@]WGET[@],$(WGET),g' \
		-e 's,[@]PWGEN[@],$(PWGEN),g' \
		-e 's,[@]PYTHON[@],$(PYTHON),g' \
		-e 's,[@]OPENSSL[@],$(OPENSSL),g'

acme.conf: acme.conf.in
	$(do_subst) < $(srcdir)/acme.conf.in > acme.conf

acme-renew-single: acme-renew-single.in
	$(do_subst) < $(srcdir)/acme-renew-single.in > acme-renew-single
	chmod +x acme-renew-single

acme-renew-all: acme-renew-all.in
	$(do_subst) < $(srcdir)/acme-renew-all.in > acme-renew-all
	chmod +x acme-renew-all

acme-setup-cert: acme-setup-cert.in
	$(do_subst) < $(srcdir)/acme-setup-cert.in > acme-setup-cert
	chmod +x acme-setup-cert
