public_icon_themes = \
	HighContrast \
	hicolor	\
	$(NULL)

public_icons = \
	HighContrast_apps_16x16_app.png \
	HighContrast_apps_22x22_app.png \
	HighContrast_apps_24x24_app.png \
	HighContrast_apps_32x32_app.png \
	HighContrast_apps_48x48_app.png \
	HighContrast_apps_256x256_app.png \
	hicolor_apps_16x16_app.png \
	hicolor_apps_22x22_app.png \
	hicolor_apps_24x24_app.png \
	hicolor_apps_32x32_app.png \
	hicolor_apps_48x48_app.png \
	hicolor_apps_256x256_app.png \
	$(NULL)

noinst_DATA = \
	$(NULL)

EXTRA_DIST = \
	$(public_icons) \
	$(noinst_DATA) \
	$(NULL)

gtk_update_icon_cache = gtk-update-icon-cache -f -t

update-icon-cache:
	@-if test -z "$(DESTDIR)"; then \
		echo "Updating Gtk icon cache."; \
		for theme in $(public_icon_themes); do \
			$(gtk_update_icon_cache) $(datadir)/icons/$$theme; \
		done; \
	else \
		echo "*** Icon cache not updated.  After (un)install, run this:"; \
		for theme in $(public_icon_themes); do \
			echo "***   $(gtk_update_icon_cache) $(datadir)/icons/$$theme"; \
		done; \
	fi

install-icons:
	for icon in $(public_icons); do \
		THEME=`echo $$icon | cut -d_ -f1`; \
		CONTEXT=`echo $$icon | cut -d_ -f2`; \
		SIZE=`echo $$icon | cut -d_ -f3`; \
		ICONFILE=`echo $$icon | cut -d_ -f4`; \
		mkdir -p $(DESTDIR)$(datadir)/icons/$$THEME/$$SIZE/$$CONTEXT; \
		$(INSTALL_DATA) $(srcdir)/$$icon $(DESTDIR)$(datadir)/icons/$$THEME/$$SIZE/$$CONTEXT/$$ICONFILE; \
	done

uninstall-icons:
	-for icon in $(public_icons); do \
		THEME=`echo $$icon | cut -d_ -f1`; \
		CONTEXT=`echo $$icon | cut -d_ -f2`; \
		SIZE=`echo $$icon | cut -d_ -f3`; \
		ICONFILE=`echo $$icon | cut -d_ -f4`; \
		rm -f $(DESTDIR)$(datadir)/icons/$$THEME/$$SIZE/$$CONTEXT/$$ICONFILE; \
	done

install-data-local: install-icons update-icon-cache

uninstall-local: uninstall-icons update-icon-cache

-include $(top_srcdir)/git.mk
