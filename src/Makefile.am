dist_bin_SCRIPTS =
dist_bin_SCRIPTS += firmwarenator

sysconf_DATA =
sysconf_DATA += firmwarenator.conf

pkgdata_DATA =
pkgdata_DATA += firmwarenator.sh


install-exec-hook:
	sed -i 's|__LIBDIR__|$(pkgdatadir)|' $(DESTDIR)$(bindir)/firmwarenator
	sed -i 's|__CONFDIR__|$(sysconfdir)|' $(DESTDIR)$(bindir)/firmwarenator
