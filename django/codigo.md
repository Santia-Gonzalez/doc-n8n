Directory structure:
└── django-django/
    └── docs/
        ├── Makefile
        ├── README.rst
        ├── conf.py
        ├── contents.txt
        ├── glossary.txt
        ├── index.txt
        ├── make.bat
        ├── requirements.txt
        ├── spelling_wordlist
        ├── _ext/
        │   ├── djangodocs.py
        │   └── github_links.py
        ├── _theme/
        │   ├── djangodocs/
        │   │   ├── genindex.html
        │   │   ├── layout.html
        │   │   ├── modindex.html
        │   │   ├── search.html
        │   │   ├── theme.conf
        │   │   └── static/
        │   │       ├── console-tabs.css
        │   │       ├── default.css
        │   │       ├── djangodocs.css
        │   │       ├── homepage.css
        │   │       ├── reset-fonts-grids.css
        │   │       └── fontawesome/
        │   │           ├── README.md
        │   │           ├── LICENSE.txt
        │   │           └── webfonts/
        │   │               ├── fa-brands-400.eot
        │   │               ├── fa-brands-400.ttf
        │   │               ├── fa-brands-400.woff
        │   │               └── fa-brands-400.woff2
        │   └── djangodocs-epub/
        │       ├── epub-cover.html
        │       ├── theme.conf
        │       └── static/
        │           └── epub.css
        ├── faq/
        │   ├── admin.txt
        │   ├── contributing.txt
        │   ├── general.txt
        │   ├── help.txt
        │   ├── index.txt
        │   ├── install.txt
        │   ├── models.txt
        │   ├── troubleshooting.txt
        │   └── usage.txt
        ├── howto/
        │   ├── auth-remote-user.txt
        │   ├── csrf.txt
        │   ├── custom-file-storage.txt
        │   ├── custom-lookups.txt
        │   ├── custom-management-commands.txt
        │   ├── custom-model-fields.txt
        │   ├── custom-shell.txt
        │   ├── custom-template-backend.txt
        │   ├── custom-template-tags.txt
        │   ├── delete-app.txt
        │   ├── error-reporting.txt
        │   ├── index.txt
        │   ├── initial-data.txt
        │   ├── legacy-databases.txt
        │   ├── logging.txt
        │   ├── outputting-csv.txt
        │   ├── outputting-pdf.txt
        │   ├── overriding-templates.txt
        │   ├── upgrade-version.txt
        │   ├── windows.txt
        │   ├── writing-migrations.txt
        │   ├── deployment/
        │   │   ├── checklist.txt
        │   │   ├── index.txt
        │   │   ├── asgi/
        │   │   │   ├── daphne.txt
        │   │   │   ├── hypercorn.txt
        │   │   │   ├── index.txt
        │   │   │   └── uvicorn.txt
        │   │   └── wsgi/
        │   │       ├── apache-auth.txt
        │   │       ├── gunicorn.txt
        │   │       ├── index.txt
        │   │       ├── modwsgi.txt
        │   │       └── uwsgi.txt
        │   └── static-files/
        │       ├── deployment.txt
        │       └── index.txt
        ├── internals/
        │   ├── deprecation.txt
        │   ├── git.txt
        │   ├── howto-release-django.txt
        │   ├── index.txt
        │   ├── mailing-lists.txt
        │   ├── organization.txt
        │   ├── release-process.txt
        │   ├── security.txt
        │   ├── _images/
        │   │   └── triage_process.graffle
        │   └── contributing/
        │       ├── bugs-and-features.txt
        │       ├── committing-code.txt
        │       ├── index.txt
        │       ├── localizing.txt
        │       ├── new-contributors.txt
        │       ├── triaging-tickets.txt
        │       ├── writing-documentation.txt
        │       └── writing-code/
        │           ├── coding-style.txt
        │           ├── index.txt
        │           ├── javascript.txt
        │           ├── submitting-patches.txt
        │           ├── unit-tests.txt
        │           └── working-with-git.txt
        ├── intro/
        │   ├── contributing.txt
        │   ├── index.txt
        │   ├── install.txt
        │   ├── overview.txt
        │   ├── reusable-apps.txt
        │   ├── tutorial01.txt
        │   ├── tutorial02.txt
        │   ├── tutorial03.txt
        │   ├── tutorial04.txt
        │   ├── tutorial05.txt
        │   ├── tutorial06.txt
        │   ├── tutorial07.txt
        │   ├── tutorial08.txt
        │   └── whatsnext.txt
        ├── man/
        │   └── django-admin.1
        ├── misc/
        │   ├── api-stability.txt
        │   ├── design-philosophies.txt
        │   ├── distributions.txt
        │   └── index.txt
        ├── ref/
        │   ├── applications.txt
        │   ├── checks.txt
        │   ├── clickjacking.txt
        │   ├── csrf.txt
        │   ├── databases.txt
        │   ├── django-admin.txt
        │   ├── exceptions.txt
        │   ├── index.txt
        │   ├── logging.txt
        │   ├── middleware.txt
        │   ├── migration-operations.txt
        │   ├── paginator.txt
        │   ├── request-response.txt
        │   ├── schema-editor.txt
        │   ├── settings.txt
        │   ├── signals.txt
        │   ├── template-response.txt
        │   ├── unicode.txt
        │   ├── urlresolvers.txt
        │   ├── urls.txt
        │   ├── utils.txt
        │   ├── validators.txt
        │   ├── views.txt
        │   ├── class-based-views/
        │   │   ├── base.txt
        │   │   ├── flattened-index.txt
        │   │   ├── generic-date-based.txt
        │   │   ├── generic-display.txt
        │   │   ├── generic-editing.txt
        │   │   ├── index.txt
        │   │   ├── mixins-date-based.txt
        │   │   ├── mixins-editing.txt
        │   │   ├── mixins-multiple-object.txt
        │   │   ├── mixins-simple.txt
        │   │   ├── mixins-single-object.txt
        │   │   └── mixins.txt
        │   ├── contrib/
        │   │   ├── auth.txt
        │   │   ├── contenttypes.txt
        │   │   ├── flatpages.txt
        │   │   ├── humanize.txt
        │   │   ├── index.txt
        │   │   ├── messages.txt
        │   │   ├── redirects.txt
        │   │   ├── sitemaps.txt
        │   │   ├── sites.txt
        │   │   ├── staticfiles.txt
        │   │   ├── syndication.txt
        │   │   ├── admin/
        │   │   │   ├── actions.txt
        │   │   │   ├── admindocs.txt
        │   │   │   ├── filters.txt
        │   │   │   ├── index.txt
        │   │   │   └── javascript.txt
        │   │   ├── gis/
        │   │   │   ├── admin.txt
        │   │   │   ├── commands.txt
        │   │   │   ├── db-api.txt
        │   │   │   ├── deployment.txt
        │   │   │   ├── feeds.txt
        │   │   │   ├── forms-api.txt
        │   │   │   ├── functions.txt
        │   │   │   ├── gdal.txt
        │   │   │   ├── geoip2.txt
        │   │   │   ├── geoquerysets.txt
        │   │   │   ├── geos.txt
        │   │   │   ├── index.txt
        │   │   │   ├── layermapping.txt
        │   │   │   ├── measure.txt
        │   │   │   ├── model-api.txt
        │   │   │   ├── ogrinspect.txt
        │   │   │   ├── serializers.txt
        │   │   │   ├── sitemaps.txt
        │   │   │   ├── testing.txt
        │   │   │   ├── tutorial.txt
        │   │   │   ├── utils.txt
        │   │   │   └── install/
        │   │   │       ├── geolibs.txt
        │   │   │       ├── index.txt
        │   │   │       ├── postgis.txt
        │   │   │       └── spatialite.txt
        │   │   └── postgres/
        │   │       ├── aggregates.txt
        │   │       ├── constraints.txt
        │   │       ├── expressions.txt
        │   │       ├── fields.txt
        │   │       ├── forms.txt
        │   │       ├── functions.txt
        │   │       ├── index.txt
        │   │       ├── indexes.txt
        │   │       ├── lookups.txt
        │   │       ├── operations.txt
        │   │       ├── search.txt
        │   │       └── validators.txt
        │   ├── files/
        │   │   ├── file.txt
        │   │   ├── index.txt
        │   │   ├── storage.txt
        │   │   └── uploads.txt
        │   ├── forms/
        │   │   ├── api.txt
        │   │   ├── fields.txt
        │   │   ├── formsets.txt
        │   │   ├── index.txt
        │   │   ├── models.txt
        │   │   ├── renderers.txt
        │   │   ├── validation.txt
        │   │   └── widgets.txt
        │   ├── models/
        │   │   ├── class.txt
        │   │   ├── conditional-expressions.txt
        │   │   ├── constraints.txt
        │   │   ├── database-functions.txt
        │   │   ├── expressions.txt
        │   │   ├── fields.txt
        │   │   ├── index.txt
        │   │   ├── indexes.txt
        │   │   ├── instances.txt
        │   │   ├── lookups.txt
        │   │   ├── meta.txt
        │   │   ├── options.txt
        │   │   ├── querysets.txt
        │   │   └── relations.txt
        │   └── templates/
        │       ├── api.txt
        │       ├── builtins.txt
        │       ├── index.txt
        │       └── language.txt
        ├── releases/
        │   ├── 0.95.txt
        │   ├── 0.96.txt
        │   ├── 1.0-porting-guide.txt
        │   ├── 1.0.1.txt
        │   ├── 1.0.2.txt
        │   ├── 1.0.txt
        │   ├── 1.1.2.txt
        │   ├── 1.1.3.txt
        │   ├── 1.1.4.txt
        │   ├── 1.1.txt
        │   ├── 1.10.1.txt
        │   ├── 1.10.2.txt
        │   ├── 1.10.3.txt
        │   ├── 1.10.4.txt
        │   ├── 1.10.5.txt
        │   ├── 1.10.6.txt
        │   ├── 1.10.7.txt
        │   ├── 1.10.8.txt
        │   ├── 1.10.txt
        │   ├── 1.11.1.txt
        │   ├── 1.11.10.txt
        │   ├── 1.11.11.txt
        │   ├── 1.11.12.txt
        │   ├── 1.11.13.txt
        │   ├── 1.11.14.txt
        │   ├── 1.11.15.txt
        │   ├── 1.11.16.txt
        │   ├── 1.11.17.txt
        │   ├── 1.11.18.txt
        │   ├── 1.11.19.txt
        │   ├── 1.11.2.txt
        │   ├── 1.11.20.txt
        │   ├── 1.11.21.txt
        │   ├── 1.11.22.txt
        │   ├── 1.11.23.txt
        │   ├── 1.11.24.txt
        │   ├── 1.11.25.txt
        │   ├── 1.11.26.txt
        │   ├── 1.11.27.txt
        │   ├── 1.11.28.txt
        │   ├── 1.11.29.txt
        │   ├── 1.11.3.txt
        │   ├── 1.11.4.txt
        │   ├── 1.11.5.txt
        │   ├── 1.11.6.txt
        │   ├── 1.11.7.txt
        │   ├── 1.11.8.txt
        │   ├── 1.11.9.txt
        │   ├── 1.11.txt
        │   ├── 1.2.1.txt
        │   ├── 1.2.2.txt
        │   ├── 1.2.3.txt
        │   ├── 1.2.4.txt
        │   ├── 1.2.5.txt
        │   ├── 1.2.6.txt
        │   ├── 1.2.7.txt
        │   ├── 1.2.txt
        │   ├── 1.3.1.txt
        │   ├── 1.3.2.txt
        │   ├── 1.3.3.txt
        │   ├── 1.3.4.txt
        │   ├── 1.3.5.txt
        │   ├── 1.3.6.txt
        │   ├── 1.3.7.txt
        │   ├── 1.3.txt
        │   ├── 1.4.1.txt
        │   ├── 1.4.10.txt
        │   ├── 1.4.11.txt
        │   ├── 1.4.12.txt
        │   ├── 1.4.13.txt
        │   ├── 1.4.14.txt
        │   ├── 1.4.15.txt
        │   ├── 1.4.16.txt
        │   ├── 1.4.17.txt
        │   ├── 1.4.18.txt
        │   ├── 1.4.19.txt
        │   ├── 1.4.2.txt
        │   ├── 1.4.20.txt
        │   ├── 1.4.21.txt
        │   ├── 1.4.22.txt
        │   ├── 1.4.3.txt
        │   ├── 1.4.4.txt
        │   ├── 1.4.5.txt
        │   ├── 1.4.6.txt
        │   ├── 1.4.7.txt
        │   ├── 1.4.8.txt
        │   ├── 1.4.9.txt
        │   ├── 1.4.txt
        │   ├── 1.5.1.txt
        │   ├── 1.5.10.txt
        │   ├── 1.5.11.txt
        │   ├── 1.5.12.txt
        │   ├── 1.5.2.txt
        │   ├── 1.5.3.txt
        │   ├── 1.5.4.txt
        │   ├── 1.5.5.txt
        │   ├── 1.5.6.txt
        │   ├── 1.5.7.txt
        │   ├── 1.5.8.txt
        │   ├── 1.5.9.txt
        │   ├── 1.5.txt
        │   ├── 1.6.1.txt
        │   ├── 1.6.10.txt
        │   ├── 1.6.11.txt
        │   ├── 1.6.2.txt
        │   ├── 1.6.3.txt
        │   ├── 1.6.4.txt
        │   ├── 1.6.5.txt
        │   ├── 1.6.6.txt
        │   ├── 1.6.7.txt
        │   ├── 1.6.8.txt
        │   ├── 1.6.9.txt
        │   ├── 1.6.txt
        │   ├── 1.7.1.txt
        │   ├── 1.7.10.txt
        │   ├── 1.7.11.txt
        │   ├── 1.7.2.txt
        │   ├── 1.7.3.txt
        │   ├── 1.7.4.txt
        │   ├── 1.7.5.txt
        │   ├── 1.7.6.txt
        │   ├── 1.7.7.txt
        │   ├── 1.7.8.txt
        │   ├── 1.7.9.txt
        │   ├── 1.7.txt
        │   ├── 1.8.1.txt
        │   ├── 1.8.10.txt
        │   ├── 1.8.11.txt
        │   ├── 1.8.12.txt
        │   ├── 1.8.13.txt
        │   ├── 1.8.14.txt
        │   ├── 1.8.15.txt
        │   ├── 1.8.16.txt
        │   ├── 1.8.17.txt
        │   ├── 1.8.18.txt
        │   ├── 1.8.19.txt
        │   ├── 1.8.2.txt
        │   ├── 1.8.3.txt
        │   ├── 1.8.4.txt
        │   ├── 1.8.5.txt
        │   ├── 1.8.6.txt
        │   ├── 1.8.7.txt
        │   ├── 1.8.8.txt
        │   ├── 1.8.9.txt
        │   ├── 1.8.txt
        │   ├── 1.9.1.txt
        │   ├── 1.9.10.txt
        │   ├── 1.9.11.txt
        │   ├── 1.9.12.txt
        │   ├── 1.9.13.txt
        │   ├── 1.9.2.txt
        │   ├── 1.9.3.txt
        │   ├── 1.9.4.txt
        │   ├── 1.9.5.txt
        │   ├── 1.9.6.txt
        │   ├── 1.9.7.txt
        │   ├── 1.9.8.txt
        │   ├── 1.9.9.txt
        │   ├── 1.9.txt
        │   ├── 2.0.1.txt
        │   ├── 2.0.10.txt
        │   ├── 2.0.11.txt
        │   ├── 2.0.12.txt
        │   ├── 2.0.13.txt
        │   ├── 2.0.2.txt
        │   ├── 2.0.3.txt
        │   ├── 2.0.4.txt
        │   ├── 2.0.5.txt
        │   ├── 2.0.6.txt
        │   ├── 2.0.7.txt
        │   ├── 2.0.8.txt
        │   ├── 2.0.9.txt
        │   ├── 2.0.txt
        │   ├── 2.1.1.txt
        │   ├── 2.1.10.txt
        │   ├── 2.1.11.txt
        │   ├── 2.1.12.txt
        │   ├── 2.1.13.txt
        │   ├── 2.1.14.txt
        │   ├── 2.1.15.txt
        │   ├── 2.1.2.txt
        │   ├── 2.1.3.txt
        │   ├── 2.1.4.txt
        │   ├── 2.1.5.txt
        │   ├── 2.1.6.txt
        │   ├── 2.1.7.txt
        │   ├── 2.1.8.txt
        │   ├── 2.1.9.txt
        │   ├── 2.1.txt
        │   ├── 2.2.1.txt
        │   ├── 2.2.10.txt
        │   ├── 2.2.11.txt
        │   ├── 2.2.12.txt
        │   ├── 2.2.13.txt
        │   ├── 2.2.14.txt
        │   ├── 2.2.15.txt
        │   ├── 2.2.16.txt
        │   ├── 2.2.17.txt
        │   ├── 2.2.18.txt
        │   ├── 2.2.19.txt
        │   ├── 2.2.2.txt
        │   ├── 2.2.20.txt
        │   ├── 2.2.21.txt
        │   ├── 2.2.22.txt
        │   ├── 2.2.23.txt
        │   ├── 2.2.24.txt
        │   ├── 2.2.25.txt
        │   ├── 2.2.26.txt
        │   ├── 2.2.27.txt
        │   ├── 2.2.28.txt
        │   ├── 2.2.3.txt
        │   ├── 2.2.4.txt
        │   ├── 2.2.5.txt
        │   ├── 2.2.6.txt
        │   ├── 2.2.7.txt
        │   ├── 2.2.8.txt
        │   ├── 2.2.9.txt
        │   ├── 2.2.txt
        │   ├── 3.0.1.txt
        │   ├── 3.0.10.txt
        │   ├── 3.0.11.txt
        │   ├── 3.0.12.txt
        │   ├── 3.0.13.txt
        │   ├── 3.0.14.txt
        │   ├── 3.0.2.txt
        │   ├── 3.0.3.txt
        │   ├── 3.0.4.txt
        │   ├── 3.0.5.txt
        │   ├── 3.0.6.txt
        │   ├── 3.0.7.txt
        │   ├── 3.0.8.txt
        │   ├── 3.0.9.txt
        │   ├── 3.0.txt
        │   ├── 3.1.1.txt
        │   ├── 3.1.10.txt
        │   ├── 3.1.11.txt
        │   ├── 3.1.12.txt
        │   ├── 3.1.13.txt
        │   ├── 3.1.14.txt
        │   ├── 3.1.2.txt
        │   ├── 3.1.3.txt
        │   ├── 3.1.4.txt
        │   ├── 3.1.5.txt
        │   ├── 3.1.6.txt
        │   ├── 3.1.7.txt
        │   ├── 3.1.8.txt
        │   ├── 3.1.9.txt
        │   ├── 3.1.txt
        │   ├── 3.2.1.txt
        │   ├── 3.2.10.txt
        │   ├── 3.2.11.txt
        │   ├── 3.2.12.txt
        │   ├── 3.2.13.txt
        │   ├── 3.2.14.txt
        │   ├── 3.2.15.txt
        │   ├── 3.2.16.txt
        │   ├── 3.2.17.txt
        │   ├── 3.2.18.txt
        │   ├── 3.2.19.txt
        │   ├── 3.2.2.txt
        │   ├── 3.2.20.txt
        │   ├── 3.2.21.txt
        │   ├── 3.2.22.txt
        │   ├── 3.2.23.txt
        │   ├── 3.2.24.txt
        │   ├── 3.2.25.txt
        │   ├── 3.2.3.txt
        │   ├── 3.2.4.txt
        │   ├── 3.2.5.txt
        │   ├── 3.2.6.txt
        │   ├── 3.2.7.txt
        │   ├── 3.2.8.txt
        │   ├── 3.2.9.txt
        │   ├── 3.2.txt
        │   ├── 4.0.1.txt
        │   ├── 4.0.10.txt
        │   ├── 4.0.2.txt
        │   ├── 4.0.3.txt
        │   ├── 4.0.4.txt
        │   ├── 4.0.5.txt
        │   ├── 4.0.6.txt
        │   ├── 4.0.7.txt
        │   ├── 4.0.8.txt
        │   ├── 4.0.9.txt
        │   ├── 4.0.txt
        │   ├── 4.1.1.txt
        │   ├── 4.1.10.txt
        │   ├── 4.1.11.txt
        │   ├── 4.1.12.txt
        │   ├── 4.1.13.txt
        │   ├── 4.1.2.txt
        │   ├── 4.1.3.txt
        │   ├── 4.1.4.txt
        │   ├── 4.1.5.txt
        │   ├── 4.1.6.txt
        │   ├── 4.1.7.txt
        │   ├── 4.1.8.txt
        │   ├── 4.1.9.txt
        │   ├── 4.1.txt
        │   ├── 4.2.1.txt
        │   ├── 4.2.10.txt
        │   ├── 4.2.11.txt
        │   ├── 4.2.12.txt
        │   ├── 4.2.13.txt
        │   ├── 4.2.14.txt
        │   ├── 4.2.15.txt
        │   ├── 4.2.16.txt
        │   ├── 4.2.17.txt
        │   ├── 4.2.18.txt
        │   ├── 4.2.19.txt
        │   ├── 4.2.2.txt
        │   ├── 4.2.3.txt
        │   ├── 4.2.4.txt
        │   ├── 4.2.5.txt
        │   ├── 4.2.6.txt
        │   ├── 4.2.7.txt
        │   ├── 4.2.8.txt
        │   ├── 4.2.9.txt
        │   ├── 4.2.txt
        │   ├── 5.0.1.txt
        │   ├── 5.0.10.txt
        │   ├── 5.0.11.txt
        │   ├── 5.0.12.txt
        │   ├── 5.0.2.txt
        │   ├── 5.0.3.txt
        │   ├── 5.0.4.txt
        │   ├── 5.0.5.txt
        │   ├── 5.0.6.txt
        │   ├── 5.0.7.txt
        │   ├── 5.0.8.txt
        │   ├── 5.0.9.txt
        │   ├── 5.0.txt
        │   ├── 5.1.1.txt
        │   ├── 5.1.2.txt
        │   ├── 5.1.3.txt
        │   ├── 5.1.4.txt
        │   ├── 5.1.5.txt
        │   ├── 5.1.6.txt
        │   ├── 5.1.7.txt
        │   ├── 5.1.txt
        │   ├── 5.2.txt
        │   ├── 6.0.txt
        │   ├── index.txt
        │   └── security.txt
        └── topics/
            ├── async.txt
            ├── cache.txt
            ├── checks.txt
            ├── composite-primary-key.txt
            ├── conditional-view-processing.txt
            ├── email.txt
            ├── external-packages.txt
            ├── files.txt
            ├── index.txt
            ├── install.txt
            ├── logging.txt
            ├── migrations.txt
            ├── pagination.txt
            ├── performance.txt
            ├── security.txt
            ├── serialization.txt
            ├── settings.txt
            ├── signals.txt
            ├── signing.txt
            ├── templates.txt
            ├── auth/
            │   ├── customizing.txt
            │   ├── default.txt
            │   ├── index.txt
            │   └── passwords.txt
            ├── class-based-views/
            │   ├── generic-display.txt
            │   ├── generic-editing.txt
            │   ├── index.txt
            │   ├── intro.txt
            │   └── mixins.txt
            ├── db/
            │   ├── aggregation.txt
            │   ├── fixtures.txt
            │   ├── index.txt
            │   ├── instrumentation.txt
            │   ├── managers.txt
            │   ├── models.txt
            │   ├── multi-db.txt
            │   ├── optimization.txt
            │   ├── queries.txt
            │   ├── search.txt
            │   ├── sql.txt
            │   ├── tablespaces.txt
            │   ├── transactions.txt
            │   └── examples/
            │       ├── index.txt
            │       ├── many_to_many.txt
            │       ├── many_to_one.txt
            │       └── one_to_one.txt
            ├── forms/
            │   ├── formsets.txt
            │   ├── index.txt
            │   ├── media.txt
            │   └── modelforms.txt
            ├── http/
            │   ├── decorators.txt
            │   ├── file-uploads.txt
            │   ├── generic-views.txt
            │   ├── index.txt
            │   ├── middleware.txt
            │   ├── sessions.txt
            │   ├── shortcuts.txt
            │   ├── urls.txt
            │   └── views.txt
            ├── i18n/
            │   ├── formatting.txt
            │   ├── index.txt
            │   ├── timezones.txt
            │   └── translation.txt
            └── testing/
                ├── advanced.txt
                ├── index.txt
                ├── overview.txt
                ├── tools.txt
                └── _images/
                    └── django_unittest_classes_hierarchy.graffle


Files Content:

(Files content cropped to 300k characters, download full ingest to see more)
================================================
File: docs/Makefile
================================================
# Makefile for Sphinx documentation
#

# You can set these variables from the command line.
PYTHON        ?= python
SPHINXOPTS    ?=
SPHINXBUILD   ?= sphinx-build
PAPER         ?=
BUILDDIR      ?= _build
LANGUAGE      ?=
JOBS          ?= auto

# Set the default language.
ifndef LANGUAGE
override LANGUAGE = en
endif

# Convert something like "en_US" to "en", because Sphinx does not recognize
# underscores. Country codes should be passed using a dash, e.g. "pt-BR".
LANGUAGEOPT = $(firstword $(subst _, ,$(LANGUAGE)))

# Internal variables.
PAPEROPT_a4     = -D latex_paper_size=a4
PAPEROPT_letter = -D latex_paper_size=letter
ALLSPHINXOPTS   = -n -d $(BUILDDIR)/doctrees -D language=$(LANGUAGEOPT) --jobs $(JOBS) $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .
# the i18n builder cannot share the environment and doctrees with the others
I18NSPHINXOPTS  = $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .

.PHONY: help clean html htmlview dirhtml singlehtml pickle json htmlhelp qthelp devhelp epub latex latexpdf text man changes linkcheck doctest gettext

help:
	@echo "Please use \`make <target>' where <target> is one of"
	@echo "  html       to make standalone HTML files"
	@echo "  htmlview   to open the index page built by the html target in your browser"
	@echo "  dirhtml    to make HTML files named index.html in directories"
	@echo "  singlehtml to make a single large HTML file"
	@echo "  pickle     to make pickle files"
	@echo "  json       to make JSON files"
	@echo "  htmlhelp   to make HTML files and a HTML help project"
	@echo "  qthelp     to make HTML files and a qthelp project"
	@echo "  devhelp    to make HTML files and a Devhelp project"
	@echo "  epub       to make an epub"
	@echo "  latex      to make LaTeX files, you can set PAPER=a4 or PAPER=letter"
	@echo "  latexpdf   to make LaTeX files and run them through pdflatex"
	@echo "  text       to make text files"
	@echo "  man        to make manual pages"
	@echo "  texinfo    to make a Texinfo source file"
	@echo "  gettext    to make PO message catalogs"
	@echo "  changes    to make an overview of all changed/added/deprecated items"
	@echo "  linkcheck  to check all external links for integrity"
	@echo "  doctest    to run all doctests embedded in the documentation (if enabled)"
	@echo "  spelling   to check for typos in documentation"
	@echo "  black      to apply the black formatting to code blocks in documentation"


clean:
	-rm -rf $(BUILDDIR)/*

html:
	$(SPHINXBUILD) -b djangohtml $(ALLSPHINXOPTS) $(BUILDDIR)/html
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/html."

htmlview: html
	$(PYTHON) -m webbrowser "$(BUILDDIR)/html/index.html"

dirhtml:
	$(SPHINXBUILD) -b dirhtml $(ALLSPHINXOPTS) $(BUILDDIR)/dirhtml
	@echo
	@echo "Build finished. The HTML pages are in $(BUILDDIR)/dirhtml."

singlehtml:
	$(SPHINXBUILD) -b singlehtml $(ALLSPHINXOPTS) $(BUILDDIR)/singlehtml
	@echo
	@echo "Build finished. The HTML page is in $(BUILDDIR)/singlehtml."

pickle:
	$(SPHINXBUILD) -b pickle $(ALLSPHINXOPTS) $(BUILDDIR)/pickle
	@echo
	@echo "Build finished; now you can process the pickle files."

json:
	$(SPHINXBUILD) -b json $(ALLSPHINXOPTS) $(BUILDDIR)/json
	@echo
	@echo "Build finished; now you can process the JSON files."

htmlhelp:
	$(SPHINXBUILD) -b htmlhelp $(ALLSPHINXOPTS) $(BUILDDIR)/htmlhelp
	@echo
	@echo "Build finished; now you can run HTML Help Workshop with the" \
	      ".hhp project file in $(BUILDDIR)/htmlhelp."

qthelp:
	$(SPHINXBUILD) -b qthelp $(ALLSPHINXOPTS) $(BUILDDIR)/qthelp
	@echo
	@echo "Build finished; now you can run "qcollectiongenerator" with the" \
	      ".qhcp project file in $(BUILDDIR)/qthelp, like this:"
	@echo "# qcollectiongenerator $(BUILDDIR)/qthelp/django.qhcp"
	@echo "To view the help file:"
	@echo "# assistant -collectionFile $(BUILDDIR)/qthelp/django.qhc"

devhelp:
	$(SPHINXBUILD) -b devhelp $(ALLSPHINXOPTS) $(BUILDDIR)/devhelp
	@echo
	@echo "Build finished."
	@echo "To view the help file:"
	@echo "# mkdir -p $$HOME/.local/share/devhelp/django"
	@echo "# ln -s $(BUILDDIR)/devhelp $$HOME/.local/share/devhelp/django"
	@echo "# devhelp"

epub:
	$(SPHINXBUILD) -b epub $(ALLSPHINXOPTS) $(BUILDDIR)/epub
	@echo
	@echo "Build finished. The epub file is in $(BUILDDIR)/epub."

latex:
	$(SPHINXBUILD) -b latex $(ALLSPHINXOPTS) $(BUILDDIR)/latex
	@echo
	@echo "Build finished; the LaTeX files are in $(BUILDDIR)/latex."
	@echo "Run \`make' in that directory to run these through (pdf)latex" \
	      "(use \`make latexpdf' here to do that automatically)."

latexpdf:
	$(SPHINXBUILD) -b latex $(ALLSPHINXOPTS) $(BUILDDIR)/latex
	@echo "Running LaTeX files through pdflatex..."
	make -C $(BUILDDIR)/latex all-pdf
	@echo "pdflatex finished; the PDF files are in $(BUILDDIR)/latex."

text:
	$(SPHINXBUILD) -b text $(ALLSPHINXOPTS) $(BUILDDIR)/text
	@echo
	@echo "Build finished. The text files are in $(BUILDDIR)/text."

man:
	$(SPHINXBUILD) -b man $(ALLSPHINXOPTS) $(BUILDDIR)/man
	@echo
	@echo "Build finished. The manual pages are in $(BUILDDIR)/man."

texinfo:
	$(SPHINXBUILD) -b texinfo $(ALLSPHINXOPTS) $(BUILDDIR)/texinfo
	@echo
	@echo "Build finished; the Texinfo files are in $(BUILDDIR)/texinfo."

gettext:
	$(SPHINXBUILD) -b gettext $(I18NSPHINXOPTS) $(BUILDDIR)/locale
	@echo
	@echo "Build finished. The message catalogs are in $(BUILDDIR)/locale."

changes:
	$(SPHINXBUILD) -b changes $(ALLSPHINXOPTS) $(BUILDDIR)/changes
	@echo
	@echo "The overview file is in $(BUILDDIR)/changes."

linkcheck:
	$(SPHINXBUILD) -b linkcheck $(ALLSPHINXOPTS) $(BUILDDIR)/linkcheck
	@echo
	@echo "Link check complete; look for any errors in the above output " \
	      "or in $(BUILDDIR)/linkcheck/output.txt."

doctest:
	$(SPHINXBUILD) -b doctest $(ALLSPHINXOPTS) $(BUILDDIR)/doctest
	@echo "Testing of doctests in the sources finished, look at the " \
	      "results in $(BUILDDIR)/doctest/output.txt."

spelling:
	$(SPHINXBUILD) -b spelling $(ALLSPHINXOPTS) $(BUILDDIR)/spelling
	@echo
	@echo "Check finished. Wrong words can be found in " \
		"$(BUILDDIR)/spelling/output.txt."

black:
	@mkdir -p $(BUILDDIR)/black
	find . -name "*.txt" -not -path "./_build/*" -not -path "./_theme/*" \
		| xargs blacken-docs --rst-literal-block; echo $$? > "$(BUILDDIR)/black/output.txt"
	@echo
	@echo "Code blocks reformatted"


================================================
File: docs/README.rst
================================================
The documentation in this tree is in plain text files and can be viewed using
any text file viewer.

It uses `ReST`_ (reStructuredText), and the `Sphinx`_ documentation system.
This allows it to be built into other forms for easier viewing and browsing.

To create an HTML version of the docs:

* Install Sphinx (using ``python -m pip install Sphinx`` or some other method).

* In this docs/ directory, type ``make html`` (or ``make.bat html`` on
  Windows) at a shell prompt.

The documentation in ``_build/html/index.html`` can then be viewed in a web
browser.

.. _ReST: https://docutils.sourceforge.io/rst.html
.. _Sphinx: https://www.sphinx-doc.org/


================================================
File: docs/conf.py
================================================
# Django documentation build configuration file, created by
# sphinx-quickstart on Thu Mar 27 09:06:53 2008.
#
# This file is execfile()d with the current directory set to its containing dir.
#
# The contents of this file are pickled, so don't put values in the namespace
# that aren't picklable (module imports are okay, they're removed automatically).
#
# All configuration values have a default; values that are commented out
# serve to show the default.

import functools
import sys
from os.path import abspath, dirname, join

from sphinx import version_info as sphinx_version

# Workaround for sphinx-build recursion limit overflow:
# pickle.dump(doctree, f, pickle.HIGHEST_PROTOCOL)
#  RuntimeError: maximum recursion depth exceeded while pickling an object
#
# Python's default allowed recursion depth is 1000 but this isn't enough for
# building docs/ref/settings.txt sometimes.
# https://groups.google.com/g/sphinx-dev/c/MtRf64eGtv4/discussion
sys.setrecursionlimit(2000)

# Make sure we get the version of this copy of Django
sys.path.insert(1, dirname(dirname(abspath(__file__))))

# If extensions (or modules to document with autodoc) are in another directory,
# add these directories to sys.path here. If the directory is relative to the
# documentation root, use os.path.abspath to make it absolute, like shown here.
sys.path.append(abspath(join(dirname(__file__), "_ext")))

# Use the module to GitHub url resolver, but import it after the _ext directoy
# it lives in has been added to sys.path.
import github_links  # NOQA

# -- General configuration -----------------------------------------------------

# If your documentation needs a minimal Sphinx version, state it here.
needs_sphinx = "4.5.0"

# Add any Sphinx extension module names here, as strings. They can be extensions
# coming with Sphinx (named 'sphinx.ext.*') or your custom ones.
extensions = [
    "djangodocs",
    "sphinx.ext.extlinks",
    "sphinx.ext.intersphinx",
    "sphinx.ext.autosectionlabel",
    "sphinx.ext.linkcode",
]

# AutosectionLabel settings.
# Uses a <page>:<label> schema which doesn't work for duplicate sub-section
# labels, so set max depth.
autosectionlabel_prefix_document = True
autosectionlabel_maxdepth = 2

# Linkcheck settings.
linkcheck_ignore = [
    # Special-use addresses and domain names. (RFC 6761/6890)
    r"^https?://(?:127\.0\.0\.1|\[::1\])(?::\d+)?/",
    r"^https?://(?:[^/.]+\.)*example\.(?:com|net|org)(?::\d+)?/",
    r"^https?://(?:[^/.]+\.)*(?:example|invalid|localhost|test)(?::\d+)?/",
    # Pages that are inaccessible because they require authentication.
    r"^https://github\.com/[^/]+/[^/]+/fork",
    r"^https://code\.djangoproject\.com/github/login",
    r"^https://code\.djangoproject\.com/newticket",
    r"^https://(?:code|www)\.djangoproject\.com/admin/",
    r"^https://www\.djangoproject\.com/community/add/blogs/",
    r"^https://www\.google\.com/webmasters/tools/ping",
    r"^https://search\.google\.com/search-console/welcome",
    # Fragments used to dynamically switch content or populate fields.
    r"^https://web\.libera\.chat/#",
    r"^https://github\.com/[^#]+#L\d+-L\d+$",
    r"^https://help\.apple\.com/itc/podcasts_connect/#/itc",
    # Anchors on certain pages with missing a[name] attributes.
    r"^https://tools\.ietf\.org/html/rfc1123\.html#section-",
]

# Spelling check needs an additional module that is not installed by default.
# Add it only if spelling check is requested so docs can be generated without it.
if "spelling" in sys.argv:
    extensions.append("sphinxcontrib.spelling")

# Spelling language.
spelling_lang = "en_US"

# Location of word list.
spelling_word_list_filename = "spelling_wordlist"

spelling_warning = True

# Add any paths that contain templates here, relative to this directory.
# templates_path = []

# The suffix of source filenames.
source_suffix = {".txt": "restructuredtext"}

# The encoding of source files.
# source_encoding = 'utf-8-sig'

# The root toctree document.
root_doc = "contents"

# Disable auto-created table of contents entries for all domain objects (e.g.
# functions, classes, attributes, etc.) in Sphinx 5.2+.
toc_object_entries = False

# General substitutions.
project = "Django"
copyright = "Django Software Foundation and contributors"


# The version info for the project you're documenting, acts as replacement for
# |version| and |release|, also used in various other places throughout the
# built documents.
#
# The short X.Y version.
version = "6.0"
# The full version, including alpha/beta/rc tags.
try:
    from django import VERSION, get_version
except ImportError:
    release = version
else:

    def django_release():
        pep440ver = get_version()
        if VERSION[3:5] == ("alpha", 0) and "dev" not in pep440ver:
            return pep440ver + ".dev"
        return pep440ver

    release = django_release()

# The "development version" of Django
django_next_version = "6.0"

extlinks = {
    "bpo": ("https://bugs.python.org/issue?@action=redirect&bpo=%s", "bpo-%s"),
    "commit": ("https://github.com/django/django/commit/%s", "%s"),
    "pypi": ("https://pypi.org/project/%s/", "%s"),
    # A file or directory. GitHub redirects from blob to tree if needed.
    "source": ("https://github.com/django/django/blob/main/%s", "%s"),
    "ticket": ("https://code.djangoproject.com/ticket/%s", "#%s"),
}

if sphinx_version < (8, 1):
    extlinks["cve"] = ("https://www.cve.org/CVERecord?id=CVE-%s", "CVE-%s")

# The language for content autogenerated by Sphinx. Refer to documentation
# for a list of supported languages.
# language = None

# Location for .po/.mo translation files used when language is set
locale_dirs = ["locale/"]

# There are two options for replacing |today|: either, you set today to some
# non-false value, then it is used:
# today = ''
# Else, today_fmt is used as the format for a strftime call.
today_fmt = "%B %d, %Y"

# List of patterns, relative to source directory, that match files and
# directories to ignore when looking for source files.
exclude_patterns = ["_build", "_theme", "requirements.txt"]

# The reST default role (used for this markup: `text`) to use for all documents.
default_role = "default-role-error"

# If true, '()' will be appended to :func: etc. cross-reference text.
add_function_parentheses = True

# If true, the current module name will be prepended to all description
# unit titles (such as .. function::).
add_module_names = False

# If true, sectionauthor and moduleauthor directives will be shown in the
# output. They are ignored by default.
show_authors = False

# The name of the Pygments (syntax highlighting) style to use.
pygments_style = "trac"

# Links to Python's docs should reference the most recent version of the 3.x
# branch, which is located at this URL.
intersphinx_mapping = {
    "python": ("https://docs.python.org/3", None),
    "sphinx": ("https://www.sphinx-doc.org/en/master", None),
    "psycopg": ("https://www.psycopg.org/psycopg3/docs", None),
}

# Python's docs don't change every week.
intersphinx_cache_limit = 90  # days

# The 'versionadded' and 'versionchanged' directives are overridden.
suppress_warnings = ["app.add_directive"]

# -- Options for HTML output ---------------------------------------------------

# The theme to use for HTML and HTML Help pages.  See the documentation for
# a list of builtin themes.
html_theme = "djangodocs"

# Theme options are theme-specific and customize the look and feel of a theme
# further.  For a list of options available for each theme, see the
# documentation.
# html_theme_options = {}

# Add any paths that contain custom themes here, relative to this directory.
html_theme_path = ["_theme"]

# The name for this set of Sphinx documents.  If None, it defaults to
# "<project> v<release> documentation".
# html_title = None

# A shorter title for the navigation bar.  Default is the same as html_title.
# html_short_title = None

# The name of an image file (relative to this directory) to place at the top
# of the sidebar.
# html_logo = None

# The name of an image file (within the static path) to use as favicon of the
# docs.  This file should be a Windows icon file (.ico) being 16x16 or 32x32
# pixels large.
# html_favicon = None

# Add any paths that contain custom static files (such as style sheets) here,
# relative to this directory. They are copied after the builtin static files,
# so a file named "default.css" will overwrite the builtin "default.css".
# html_static_path = ["_static"]

# If not '', a 'Last updated on:' timestamp is inserted at every page bottom,
# using the given strftime format.
html_last_updated_fmt = "%b %d, %Y"

# Content template for the index page.
# html_index = ''

# Custom sidebar templates, maps document names to template names.
# html_sidebars = {}

# Additional templates that should be rendered to pages, maps page names to
# template names.
html_additional_pages = {}

# If false, no module index is generated.
# html_domain_indices = True

# If false, no index is generated.
# html_use_index = True

# If true, the index is split into individual pages for each letter.
# html_split_index = False

# If true, links to the reST sources are added to the pages.
# html_show_sourcelink = True

# If true, "Created using Sphinx" is shown in the HTML footer. Default is True.
# html_show_sphinx = True

# If true, "(C) Copyright ..." is shown in the HTML footer. Default is True.
# html_show_copyright = True

# If true, an OpenSearch description file will be output, and all pages will
# contain a <link> tag referring to it.  The value of this option must be the
# base URL from which the finished HTML is served.
# html_use_opensearch = ''

# This is the file name suffix for HTML files (e.g. ".xhtml").
# html_file_suffix = None

# Output file base name for HTML help builder.
htmlhelp_basename = "Djangodoc"

modindex_common_prefix = ["django."]

# Appended to every page
rst_epilog = """
.. |django-users| replace:: :ref:`django-users <django-users-mailing-list>`
.. |django-developers| replace:: :ref:`django-developers <django-developers-mailing-list>`
.. |django-announce| replace:: :ref:`django-announce <django-announce-mailing-list>`
.. |django-updates| replace:: :ref:`django-updates <django-updates-mailing-list>`
"""  # NOQA

# -- Options for LaTeX output --------------------------------------------------

# Use XeLaTeX for Unicode support.
latex_engine = "xelatex"
latex_use_xindy = False
# Set font for CJK and fallbacks for unicode characters.
latex_elements = {
    "fontpkg": r"""
        \setmainfont{Symbola}
    """,
    "preamble": r"""
        \usepackage[UTF8]{ctex}
        \xeCJKDeclareCharClass{HalfLeft}{"2018, "201C}
        \xeCJKDeclareCharClass{HalfRight}{
            "00B7, "2019, "201D, "2013, "2014, "2025, "2026, "2E3A
        }
        \usepackage{newunicodechar}
        \newunicodechar{π}{\ensuremath{\pi}}
        \newunicodechar{≤}{\ensuremath{\le}}
        \newunicodechar{≥}{\ensuremath{\ge}}
        \newunicodechar{♥}{\ensuremath{\heartsuit}}
        \newunicodechar{…}{\ensuremath{\ldots}}
    """,
}

# Grouping the document tree into LaTeX files. List of tuples
# (source start file, target name, title, author, document class [howto/manual]).
# latex_documents = []
latex_documents = [
    (
        "contents",
        "django.tex",
        "Django Documentation",
        "Django Software Foundation",
        "manual",
    ),
]

# The name of an image file (relative to this directory) to place at the top of
# the title page.
# latex_logo = None

# For "manual" documents, if this is true, then toplevel headings are parts,
# not chapters.
# latex_use_parts = False

# If true, show page references after internal links.
# latex_show_pagerefs = False

# If true, show URL addresses after external links.
# latex_show_urls = False

# Documents to append as an appendix to all manuals.
# latex_appendices = []

# If false, no module index is generated.
# latex_domain_indices = True


# -- Options for manual page output --------------------------------------------

# One entry per manual page. List of tuples
# (source start file, name, description, authors, manual section).
man_pages = [
    (
        "ref/django-admin",
        "django-admin",
        "Utility script for the Django web framework",
        ["Django Software Foundation"],
        1,
    )
]


# -- Options for Texinfo output ------------------------------------------------

# List of tuples (startdocname, targetname, title, author, dir_entry,
# description, category, toctree_only)
texinfo_documents = [
    (
        root_doc,
        "django",
        "",
        "",
        "Django",
        "Documentation of the Django framework",
        "Web development",
        False,
    )
]


# -- Options for Epub output ---------------------------------------------------

# Bibliographic Dublin Core info.
epub_title = project
epub_author = "Django Software Foundation"
epub_publisher = "Django Software Foundation"
epub_copyright = copyright

# The basename for the epub file. It defaults to the project name.
# epub_basename = 'Django'

# The HTML theme for the epub output. Since the default themes are not optimized
# for small screen space, using the same theme for HTML and epub output is
# usually not wise. This defaults to 'epub', a theme designed to save visual
# space.
epub_theme = "djangodocs-epub"

# The language of the text. It defaults to the language option
# or en if the language is not set.
# epub_language = ''

# The scheme of the identifier. Typical schemes are ISBN or URL.
# epub_scheme = ''

# The unique identifier of the text. This can be an ISBN number
# or the project homepage.
# epub_identifier = ''

# A unique identification for the text.
# epub_uid = ''

# A tuple containing the cover image and cover page html template filenames.
epub_cover = ("", "epub-cover.html")

# A sequence of (type, uri, title) tuples for the guide element of content.opf.
# epub_guide = ()

# HTML files that should be inserted before the pages created by sphinx.
# The format is a list of tuples containing the path and title.
# epub_pre_files = []

# HTML files that should be inserted after the pages created by sphinx.
# The format is a list of tuples containing the path and title.
# epub_post_files = []

# A list of files that should not be packed into the epub file.
# epub_exclude_files = []

# The depth of the table of contents in toc.ncx.
# epub_tocdepth = 3

# Allow duplicate toc entries.
# epub_tocdup = True

# Choose between 'default' and 'includehidden'.
# epub_tocscope = 'default'

# Fix unsupported image types using the PIL.
# epub_fix_images = False

# Scale large images.
# epub_max_image_width = 0

# How to display URL addresses: 'footnote', 'no', or 'inline'.
# epub_show_urls = 'inline'

# If false, no index is generated.
# epub_use_index = True

linkcode_resolve = functools.partial(
    github_links.github_linkcode_resolve,
    version=version,
    next_version=django_next_version,
)


================================================
File: docs/contents.txt
================================================
=============================
Django documentation contents
=============================

.. toctree::
    :hidden:

    index

.. toctree::
    :maxdepth: 3

    intro/index
    topics/index
    howto/index
    faq/index
    ref/index
    misc/index
    glossary
    releases/index
    internals/index

Indices, glossary and tables
============================

* :ref:`genindex`
* :ref:`modindex`
* :doc:`glossary`


================================================
File: docs/glossary.txt
================================================
========
Glossary
========

.. glossary::

    concrete model
        A non-abstract (:attr:`abstract=False
        <django.db.models.Options.abstract>`) model.

    field
        An attribute on a :term:`model`; a given field usually maps directly to
        a single database column.

        See :doc:`/topics/db/models`.

    generic view
        A higher-order :term:`view` function that provides an abstract/generic
        implementation of a common idiom or pattern found in view development.

        See :doc:`/topics/class-based-views/index`.

    model
        Models store your application's data.

        See :doc:`/topics/db/models`.

    MTV
        "Model-template-view"; a software pattern, similar in style to MVC, but
        a better description of the way Django does things.

        See :ref:`the FAQ entry <faq-mtv>`.

    MVC
        `Model-view-controller`__; a software pattern. Django :ref:`follows MVC
        to some extent <faq-mtv>`.

        __ https://en.wikipedia.org/wiki/Model-view-controller

    project
        A Python package -- i.e. a directory of code -- that contains all the
        settings for an instance of Django. This would include database
        configuration, Django-specific options and application-specific
        settings.

    property
        Also known as "managed attributes", and a feature of Python since
        version 2.2. This is a neat way to implement attributes whose usage
        resembles attribute access, but whose implementation uses method calls.

        See :class:`property`.

    queryset
        An object representing some set of rows to be fetched from the database.

        See :doc:`/topics/db/queries`.

    slug
        A short label for something, containing only letters, numbers,
        underscores or hyphens. They're generally used in URLs. For
        example, in a typical blog entry URL:

        .. parsed-literal::

            https://www.djangoproject.com/weblog/2008/apr/12/**spring**/

        the last bit (``spring``) is the slug.

    template
        A chunk of text that acts as formatting for representing data. A
        template helps to abstract the presentation of data from the data
        itself.

        See :doc:`/topics/templates`.

    view
        A function responsible for rendering a page.


================================================
File: docs/index.txt
================================================
====================
Django documentation
====================

.. rubric:: Everything you need to know about Django.

.. _index-first-steps:

First steps
===========

Are you new to Django or to programming? This is the place to start!

* **From scratch:**
  :doc:`Overview <intro/overview>` |
  :doc:`Installation <intro/install>`

* **Tutorial:**
  :doc:`Part 1: Requests and responses <intro/tutorial01>` |
  :doc:`Part 2: Models and the admin site <intro/tutorial02>` |
  :doc:`Part 3: Views and templates <intro/tutorial03>` |
  :doc:`Part 4: Forms and generic views <intro/tutorial04>` |
  :doc:`Part 5: Testing <intro/tutorial05>` |
  :doc:`Part 6: Static files <intro/tutorial06>` |
  :doc:`Part 7: Customizing the admin site <intro/tutorial07>` |
  :doc:`Part 8: Adding third-party packages <intro/tutorial08>`

* **Advanced Tutorials:**
  :doc:`How to write reusable apps <intro/reusable-apps>` |
  :doc:`Writing your first contribution to Django <intro/contributing>`

Getting help
============

Having trouble? We'd like to help!

* Try the :doc:`FAQ <faq/index>` -- it's got answers to many common questions.

* Looking for specific information? Try the :ref:`genindex`, :ref:`modindex` or
  the :doc:`detailed table of contents <contents>`.

* Not found anything? See :doc:`faq/help` for information on getting support
  and asking questions to the community.

* Report bugs with Django in our `ticket tracker`_.

.. _ticket tracker: https://code.djangoproject.com/

How the documentation is organized
==================================

Django has a lot of documentation. A high-level overview of how it's organized
will help you know where to look for certain things:

* :doc:`Tutorials </intro/index>` take you by the hand through a series of
  steps to create a web application. Start here if you're new to Django or web
  application development. Also look at the ":ref:`index-first-steps`".

* :doc:`Topic guides </topics/index>` discuss key topics and concepts at a
  fairly high level and provide useful background information and explanation.

* :doc:`Reference guides </ref/index>` contain technical reference for APIs and
  other aspects of Django's machinery. They describe how it works and how to
  use it but assume that you have a basic understanding of key concepts.

* :doc:`How-to guides </howto/index>` are recipes. They guide you through the
  steps involved in addressing key problems and use-cases. They are more
  advanced than tutorials and assume some knowledge of how Django works.

The model layer
===============

Django provides an abstraction layer (the "models") for structuring and
manipulating the data of your web application. Learn more about it below:

* **Models:**
  :doc:`Introduction to models <topics/db/models>` |
  :doc:`Field types <ref/models/fields>` |
  :doc:`Indexes <ref/models/indexes>` |
  :doc:`Meta options <ref/models/options>` |
  :doc:`Model class <ref/models/class>`

* **QuerySets:**
  :doc:`Making queries <topics/db/queries>` |
  :doc:`QuerySet method reference <ref/models/querysets>` |
  :doc:`Lookup expressions <ref/models/lookups>`

* **Model instances:**
  :doc:`Instance methods <ref/models/instances>` |
  :doc:`Accessing related objects <ref/models/relations>`

* **Migrations:**
  :doc:`Introduction to Migrations<topics/migrations>` |
  :doc:`Operations reference <ref/migration-operations>` |
  :doc:`SchemaEditor <ref/schema-editor>` |
  :doc:`Writing migrations <howto/writing-migrations>`

* **Advanced:**
  :doc:`Managers <topics/db/managers>` |
  :doc:`Raw SQL <topics/db/sql>` |
  :doc:`Transactions <topics/db/transactions>` |
  :doc:`Aggregation <topics/db/aggregation>` |
  :doc:`Search <topics/db/search>` |
  :doc:`Custom fields <howto/custom-model-fields>` |
  :doc:`Multiple databases <topics/db/multi-db>` |
  :doc:`Custom lookups <howto/custom-lookups>` |
  :doc:`Query Expressions <ref/models/expressions>` |
  :doc:`Conditional Expressions <ref/models/conditional-expressions>` |
  :doc:`Database Functions <ref/models/database-functions>`

* **Other:**
  :doc:`Supported databases <ref/databases>` |
  :doc:`Legacy databases <howto/legacy-databases>` |
  :doc:`Providing initial data <howto/initial-data>` |
  :doc:`Optimize database access <topics/db/optimization>` |
  :doc:`PostgreSQL specific features <ref/contrib/postgres/index>`

The view layer
==============

Django has the concept of "views" to encapsulate the logic responsible for
processing a user's request and for returning the response. Find all you need
to know about views via the links below:

* **The basics:**
  :doc:`URLconfs <topics/http/urls>` |
  :doc:`View functions <topics/http/views>` |
  :doc:`Shortcuts <topics/http/shortcuts>` |
  :doc:`Decorators <topics/http/decorators>` |
  :doc:`Asynchronous Support <topics/async>`

* **Reference:**
  :doc:`Built-in Views <ref/views>` |
  :doc:`Request/response objects <ref/request-response>` |
  :doc:`TemplateResponse objects <ref/template-response>`

* **File uploads:**
  :doc:`Overview <topics/http/file-uploads>` |
  :doc:`File objects <ref/files/file>` |
  :doc:`Storage API <ref/files/storage>` |
  :doc:`Managing files <topics/files>` |
  :doc:`Custom storage <howto/custom-file-storage>`

* **Class-based views:**
  :doc:`Overview <topics/class-based-views/index>` |
  :doc:`Built-in display views <topics/class-based-views/generic-display>` |
  :doc:`Built-in editing views <topics/class-based-views/generic-editing>` |
  :doc:`Using mixins <topics/class-based-views/mixins>` |
  :doc:`API reference <ref/class-based-views/index>` |
  :doc:`Flattened index<ref/class-based-views/flattened-index>`

* **Advanced:**
  :doc:`Generating CSV <howto/outputting-csv>` |
  :doc:`Generating PDF <howto/outputting-pdf>`

* **Middleware:**
  :doc:`Overview <topics/http/middleware>` |
  :doc:`Built-in middleware classes <ref/middleware>`

The template layer
==================

The template layer provides a designer-friendly syntax for rendering the
information to be presented to the user. Learn how this syntax can be used by
designers and how it can be extended by programmers:

* **The basics:**
  :doc:`Overview <topics/templates>`

* **For designers:**
  :doc:`Language overview <ref/templates/language>` |
  :doc:`Built-in tags and filters <ref/templates/builtins>` |
  :doc:`Humanization <ref/contrib/humanize>`

* **For programmers:**
  :doc:`Template API <ref/templates/api>` |
  :doc:`Custom tags and filters <howto/custom-template-tags>` |
  :doc:`Custom template backend <howto/custom-template-backend>`

Forms
=====

Django provides a rich framework to facilitate the creation of forms and the
manipulation of form data.

* **The basics:**
  :doc:`Overview <topics/forms/index>` |
  :doc:`Form API <ref/forms/api>` |
  :doc:`Built-in fields <ref/forms/fields>` |
  :doc:`Built-in widgets <ref/forms/widgets>`

* **Advanced:**
  :doc:`Forms for models <topics/forms/modelforms>` |
  :doc:`Integrating media <topics/forms/media>` |
  :doc:`Formsets <topics/forms/formsets>` |
  :doc:`Customizing validation <ref/forms/validation>`

The development process
=======================

Learn about the various components and tools to help you in the development and
testing of Django applications:

* **Settings:**
  :doc:`Overview <topics/settings>` |
  :doc:`Full list of settings <ref/settings>`

* **Applications:**
  :doc:`Overview <ref/applications>`

* **Exceptions:**
  :doc:`Overview <ref/exceptions>`

* **django-admin and manage.py:**
  :doc:`Overview <ref/django-admin>` |
  :doc:`Adding custom commands <howto/custom-management-commands>`

* **Testing:**
  :doc:`Introduction <topics/testing/index>` |
  :doc:`Writing and running tests <topics/testing/overview>` |
  :doc:`Included testing tools <topics/testing/tools>` |
  :doc:`Advanced topics <topics/testing/advanced>`

* **Deployment:**
  :doc:`Overview <howto/deployment/index>` |
  :doc:`WSGI servers <howto/deployment/wsgi/index>` |
  :doc:`ASGI servers <howto/deployment/asgi/index>` |
  :doc:`Deploying static files <howto/static-files/deployment>` |
  :doc:`Tracking code errors by email <howto/error-reporting>` |
  :doc:`Deployment checklist <howto/deployment/checklist>`

The admin
=========

Find all you need to know about the automated admin interface, one of Django's
most popular features:

* :doc:`Admin site <ref/contrib/admin/index>`
* :doc:`Admin actions <ref/contrib/admin/actions>`
* :doc:`Admin documentation generator<ref/contrib/admin/admindocs>`

Security
========

Security is a topic of paramount importance in the development of web
applications and Django provides multiple protection tools and mechanisms:

* :doc:`Security overview <topics/security>`
* :doc:`Disclosed security issues in Django <releases/security>`
* :doc:`Clickjacking protection <ref/clickjacking>`
* :doc:`Cross Site Request Forgery protection <ref/csrf>`
* :doc:`Cryptographic signing <topics/signing>`
* :ref:`Security Middleware <security-middleware>`

Internationalization and localization
=====================================

Django offers a robust internationalization and localization framework to
assist you in the development of applications for multiple languages and world
regions:

* :doc:`Overview <topics/i18n/index>` |
  :doc:`Internationalization <topics/i18n/translation>` |
  :ref:`Localization <how-to-create-language-files>` |
  :doc:`Localized web UI formatting and form input <topics/i18n/formatting>`
* :doc:`Time zones </topics/i18n/timezones>`

Performance and optimization
============================

There are a variety of techniques and tools that can help get your code running
more efficiently - faster, and using fewer system resources.

* :doc:`Performance and optimization overview <topics/performance>`

Geographic framework
====================

:doc:`GeoDjango <ref/contrib/gis/index>` intends to be a world-class geographic
web framework. Its goal is to make it as easy as possible to build GIS web
applications and harness the power of spatially enabled data.

Common web application tools
============================

Django offers multiple tools commonly needed in the development of web
applications:

* **Authentication:**
  :doc:`Overview <topics/auth/index>` |
  :doc:`Using the authentication system <topics/auth/default>` |
  :doc:`Password management <topics/auth/passwords>` |
  :doc:`Customizing authentication <topics/auth/customizing>` |
  :doc:`API Reference <ref/contrib/auth>`
* :doc:`Caching <topics/cache>`
* :doc:`Logging <topics/logging>`
* :doc:`Sending emails <topics/email>`
* :doc:`Syndication feeds (RSS/Atom) <ref/contrib/syndication>`
* :doc:`Pagination <topics/pagination>`
* :doc:`Messages framework <ref/contrib/messages>`
* :doc:`Serialization <topics/serialization>`
* :doc:`Sessions <topics/http/sessions>`
* :doc:`Sitemaps <ref/contrib/sitemaps>`
* :doc:`Static files management <ref/contrib/staticfiles>`
* :doc:`Data validation <ref/validators>`

Other core functionalities
==========================

Learn about some other core functionalities of the Django framework:

* :doc:`Conditional content processing <topics/conditional-view-processing>`
* :doc:`Content types and generic relations <ref/contrib/contenttypes>`
* :doc:`Flatpages <ref/contrib/flatpages>`
* :doc:`Redirects <ref/contrib/redirects>`
* :doc:`Signals <topics/signals>`
* :doc:`System check framework <topics/checks>`
* :doc:`The sites framework <ref/contrib/sites>`
* :doc:`Unicode in Django <ref/unicode>`

The Django open-source project
==============================

Learn about the development process for the Django project itself and about how
you can contribute:

* **Community:**
  :doc:`Contributing to Django <internals/contributing/index>` |
  :doc:`The release process <internals/release-process>` |
  :doc:`Team organization <internals/organization>` |
  :doc:`The Django source code repository <internals/git>` |
  :doc:`Security policies <internals/security>` |
  :doc:`Mailing lists and Forum<internals/mailing-lists>`

* **Design philosophies:**
  :doc:`Overview <misc/design-philosophies>`

* **Documentation:**
  :doc:`About this documentation <internals/contributing/writing-documentation>`

* **Third-party distributions:**
  :doc:`Overview <misc/distributions>`

* **Django over time:**
  :doc:`API stability <misc/api-stability>` |
  :doc:`Release notes and upgrading instructions <releases/index>` |
  :doc:`Deprecation Timeline <internals/deprecation>`


================================================
File: docs/make.bat
================================================
@ECHO OFF

REM Command file for Sphinx documentation

if "%SPHINXBUILD%" == "" (
	set SPHINXBUILD=sphinx-build
)
set BUILDDIR=_build
set ALLSPHINXOPTS=-n -d %BUILDDIR%/doctrees %SPHINXOPTS% .
if NOT "%PAPER%" == "" (
	set ALLSPHINXOPTS=-D latex_paper_size=%PAPER% %ALLSPHINXOPTS%
	set I18NSPHINXOPTS=-D latex_paper_size=%PAPER% %I18NSPHINXOPTS%
)

if "%1" == "" goto help

if "%1" == "help" (
	:help
	echo.Please use `make ^<target^>` where ^<target^> is one of
	echo.  html       to make standalone HTML files
	echo.  dirhtml    to make HTML files named index.html in directories
	echo.  singlehtml to make a single large HTML file
	echo.  pickle     to make pickle files
	echo.  json       to make JSON files
	echo.  htmlhelp   to make HTML files and a HTML help project
	echo.  qthelp     to make HTML files and a qthelp project
	echo.  devhelp    to make HTML files and a Devhelp project
	echo.  epub       to make an epub
	echo.  latex      to make LaTeX files, you can set PAPER=a4 or PAPER=letter
	echo.  text       to make text files
	echo.  man        to make manual pages
	echo.  texinfo    to make a Texinfo source file
	echo.  gettext    to make PO message catalogs
	echo.  changes    to make an overview over all changed/added/deprecated items
	echo.  linkcheck  to check all external links for integrity
	echo.  doctest    to run all doctests embedded in the documentation if enabled
	echo.  spelling   to check for typos in documentation
	echo.  black      to apply the black formatting to code blocks in documentation
	goto end
)

if "%1" == "clean" (
	for /d %%i in (%BUILDDIR%\*) do rmdir /q /s %%i
	del /q /s %BUILDDIR%\*
	goto end
)

if "%1" == "html" (
	%SPHINXBUILD% -b djangohtml %ALLSPHINXOPTS% %BUILDDIR%/html
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The HTML pages are in %BUILDDIR%/html.
	goto end
)

if "%1" == "dirhtml" (
	%SPHINXBUILD% -b dirhtml %ALLSPHINXOPTS% %BUILDDIR%/dirhtml
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The HTML pages are in %BUILDDIR%/dirhtml.
	goto end
)

if "%1" == "singlehtml" (
	%SPHINXBUILD% -b singlehtml %ALLSPHINXOPTS% %BUILDDIR%/singlehtml
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The HTML pages are in %BUILDDIR%/singlehtml.
	goto end
)

if "%1" == "pickle" (
	%SPHINXBUILD% -b pickle %ALLSPHINXOPTS% %BUILDDIR%/pickle
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished; now you can process the pickle files.
	goto end
)

if "%1" == "json" (
	%SPHINXBUILD% -b json %ALLSPHINXOPTS% %BUILDDIR%/json
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished; now you can process the JSON files.
	goto end
)

if "%1" == "htmlhelp" (
	%SPHINXBUILD% -b htmlhelp %ALLSPHINXOPTS% %BUILDDIR%/htmlhelp
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished; now you can run HTML Help Workshop with the ^
.hhp project file in %BUILDDIR%/htmlhelp.
	goto end
)

if "%1" == "qthelp" (
	%SPHINXBUILD% -b qthelp %ALLSPHINXOPTS% %BUILDDIR%/qthelp
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished; now you can run "qcollectiongenerator" with the ^
.qhcp project file in %BUILDDIR%/qthelp, like this:
	echo.^> qcollectiongenerator %BUILDDIR%\qthelp\django.qhcp
	echo.To view the help file:
	echo.^> assistant -collectionFile %BUILDDIR%\qthelp\django.qhc
	goto end
)

if "%1" == "devhelp" (
	%SPHINXBUILD% -b devhelp %ALLSPHINXOPTS% %BUILDDIR%/devhelp
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished.
	goto end
)

if "%1" == "epub" (
	%SPHINXBUILD% -b epub %ALLSPHINXOPTS% %BUILDDIR%/epub
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The epub file is in %BUILDDIR%/epub.
	goto end
)

if "%1" == "latex" (
	%SPHINXBUILD% -b latex %ALLSPHINXOPTS% %BUILDDIR%/latex
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished; the LaTeX files are in %BUILDDIR%/latex.
	goto end
)

if "%1" == "text" (
	%SPHINXBUILD% -b text %ALLSPHINXOPTS% %BUILDDIR%/text
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The text files are in %BUILDDIR%/text.
	goto end
)

if "%1" == "man" (
	%SPHINXBUILD% -b man %ALLSPHINXOPTS% %BUILDDIR%/man
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The manual pages are in %BUILDDIR%/man.
	goto end
)

if "%1" == "texinfo" (
	%SPHINXBUILD% -b texinfo %ALLSPHINXOPTS% %BUILDDIR%/texinfo
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The Texinfo files are in %BUILDDIR%/texinfo.
	goto end
)

if "%%1" == "gettext" (
	%SPHINXBUILD% -b gettext %I18NSPHINXOPTS% %BUILDDIR%/locale
	if errorlevel 1 exit /b 1
	echo.
	echo.Build finished. The message catalogs are in %BUILDDIR%/locale.
	goto end
)

if "%1" == "changes" (
	%SPHINXBUILD% -b changes %ALLSPHINXOPTS% %BUILDDIR%/changes
	if errorlevel 1 exit /b 1
	echo.
	echo.The overview file is in %BUILDDIR%/changes.
	goto end
)

if "%1" == "linkcheck" (
	%SPHINXBUILD% -b linkcheck %ALLSPHINXOPTS% %BUILDDIR%/linkcheck
	if errorlevel 1 exit /b 1
	echo.
	echo.Link check complete; look for any errors in the above output ^
or in %BUILDDIR%/linkcheck/output.txt.
	goto end
)

if "%1" == "doctest" (
	%SPHINXBUILD% -b doctest %ALLSPHINXOPTS% %BUILDDIR%/doctest
	if errorlevel 1 exit /b 1
	echo.
	echo.Testing of doctests in the sources finished, look at the ^
results in %BUILDDIR%/doctest/output.txt.
	goto end
)

if "%1" == "spelling" (
	%SPHINXBUILD% -b spelling %ALLSPHINXOPTS% %BUILDDIR%/spelling
	if errorlevel 1 exit /b 1
	echo.
	echo.Check finished. Wrong words can be found in %BUILDDIR%/^
spelling/output.txt.
	goto end
)

if "%1" == "black" (
	for /f "usebackq tokens=*" %%i in (`dir *.txt /s /b ^| findstr /v /c:"_build" /c:"_theme"`) do (
		blacken-docs --rst-literal-block %%i
	)
	echo.
	echo.Code blocks reformatted
)

:end


================================================
File: docs/requirements.txt
================================================
pyenchant
Sphinx>=4.5.0
sphinxcontrib-spelling
blacken-docs


================================================
File: docs/spelling_wordlist
================================================
à
accessor
accessors
Aceh
admindocs
affordances
Ai
Alchin
allowlist
alphanumerics
amet
arccosine
architected
arcsine
arctangent
arg
args
async
atomicity
auth
autocommit
autocomplete
autocompletion
autodetect
autodetectable
autodetection
autodetector
autodiscovery
autoescape
autoescaping
autoextend
autogenerated
autoincrement
autoreload
autovacuum
backend
backends
backport
backported
backports
backtick
backtraces
balancer
basename
Bcc
BCC'ed
bcrypt
Beaven
benchmarking
Benoit
Berners
Biggs
bitwise
Bjørn
blazingly
boilerplatish
Bokmål
Bonham
bookmarklet
bookmarklets
booleans
bpython
Bronn
bugfix
bugfixes
Byteorder
bytestring
bytestrings
cacheable
callables
camelCase
cardinality
centric
centroid
changelist
changeset
charset
checkboxes
checkin
checksums
clearable
clickjacking
cms
codebase
codec
codename
codenamed
coercible
commenters
conf
config
contenttypes
contrib
coroutine
coroutines
counterintuitive
criticals
cron
crontab
cryptographic
cryptographically
csrfmiddlewaretoken
csv
ctime
Ctrl
customizability
customizable
customizations
Dahl
Danga
Darussalam
databrowse
datafile
datetimes
declaratively
deduplicates
deduplication
deepcopy
deferrable
deprecations
deserialization
deserialize
deserialized
deserializer
deserializing
Deutsch
dev
dictConfig
dicts
Dimensionally
dimensioned
discoverable
Disqus
distro
django
djangoproject
dm
docstring
docstrings
doctests
doctype
documentational
DoS
Dreamweaver
drilldown
dropdown
dropdowns
Dunck
editability
encodings
Endian
Enero
enum
environ
esque
Ess
ETag
ETags
exfiltration
fallbacks
favicon
fieldset
fieldsets
filesystem
filesystems
flatpage
flatpages
focusable
formatter
formatters
formfield
formset
formsets
formtools
Frysian
geo
Geoff
geolocalized
geolocated
geolocation
georeference
georeferenced
georeferencing
geospatial
Gettext
GiB
gis
GiST
Googol
Greenhill
gunicorn
GZip
gzipped
hardcode
hardcoded
hardcoding
hashable
hasher
hashers
headerlist
Hoerner
Holovaty
Homebrew
hostname
hostnames
hstore
html
https
Hypercorn
ies
iframe
Igbo
indexable
ing
ini
init
inlines
instantiation
interdependencies
ipsum
IPv
IPython
ise
iso
iterable
iterables
iteratively
ize
Jinja
jQuery
Jupyter
jython
Kaplan
Kessler
keyservers
KiB
kilometre
Koziarski
kwarg
kwargs
Kyrgyz
latin
lawrence
Libera
lifecycle
lifecycles
linearize
linestring
linework
linter
Livni
localflavor
localhost
localizable
localizers
lookaround
lookups
loopback
lorem
lossy
lowercased
lowercasing
Luhn
macOS
Magee
Mako
manouche
Marino
memcache
memcached
metaclass
metaclasses
metre
MiB
micrometre
middleware
middlewares
millimetre
Minification
minified
minify
mis
misconfiguration
mitre
mixin
mixins
modelformset
monkeypatched
multicolumn
multijoins
multiline
multilinestring
multipolygon
multitenancy
multithreaded
multithreading
multivalued
mysql
mysqlclient
naïve
namespace
namespaced
namespaces
namespacing
Nanggroe
natively
nd
needsinfo
německy
nginx
noding
nonnegative
nullable
OAuth
OGC
OGR
ons
orderable
Orca
Orléans
orm
Outdim
outfile
paginator
parameterization
params
parens
parsers
PEM
perl
permalink
pessimization
Peucker
pgAdmin
picklable
picosecond
pingback
pingbacks
Pinney
Pinterest
plaintext
pluggable
pluralizations
pooler
postfix
postgres
pragma
pre
precisions
precomputation
preconfigured
preescaped
prefetch
prefetched
prefetches
prefetching
preload
preloaded
prepended
prepending
prepends
prepopulate
prepopulated
prepopulates
preprocess
preprocessed
preprocesses
preprocessing
programmatically
proxied
proxying
pseudocode
psycopg
Punycode
Puthraya
pyformat
pythonic
qs
queryset
querysets
querystring
queueing
Quickstart
quoteless
Radziej
rasters
rc
readded
reallow
reallowed
reallows
rebase
rebased
rebasing
recomputation
recursed
redeclare
redirections
redisplay
redisplayed
redisplaying
redisplays
reenable
reescape
referer
referers
reflow
registrable
reimplement
reindent
releaser
releasers
reloader
renderer
renderers
repo
reportable
reprojection
reraising
reST
reStructuredText
reusability
reverter
roadmap
Roald
rss
Sandvik
savepoint
savepoints
scalable
schemas
screencast
screencasts
semimajor
semiminor
serializability
serializer
serializers
shapefile
shapefiles
sharding
sitewide
sliceable
SMTP
Sorani
sortable
Spectre
Springmeyer
SSL
stacktrace
stateful
staticfile
staticfiles
storages
stylesheet
stylesheets
subclassed
subclasses
subclassing
subcommand
subcommands
subdir
subdirectories
subdirectory
subfields
sublanguage
sublist
submodule
submodules
subpath
subprocesses
subqueries
subquery
subselect
substring
subtemplate
subtemplates
subtransactions
subtype
subviews
subwidget
subwidgets
superclass
superclasses
superset
swappable
symlink
symlinks
syntaxes
systemwide
tablespace
tablespaces
Tajik
teardown
templating
testcase
textarea
th
Thejaswi
theming
This'll
threadlocals
timeframe
timesaving
timezones
titlecase
tokenized
toolkits
toolset
trac
tracebacks
Transifex
Tredinnick
triager
triagers
triaging
trigram
trigrams
Turkmen
tv
umask
unannotated
unapplied
unapplying
uncategorized
unclaim
uncopyable
unencoded
unencrypted
unescape
unescaped
unevaluated
unglamorous
ungrouped
unhandled
unharmful
unhashable
unioning
uniterated
unlocalized
unmanaged
unparseable
unparsed
unpickle
unpickled
unpickling
unpythonic
Unregisters
unrendered
unreproducible
Unreviewed
unsanitized
unselected
unsets
unsquashed
untar
untrusted
unvalidated
uppercased
url
urljoins
urlpatterns
urls
UTF
util
utils
Uvicorn
uWSGI
Uyghur
validator
validators
variadic
vendored
virtualized
whitespace
whitespaces
whizbang
Willison
wontfix
worksforme
wrappable
wsgi
www
xe
xxxxx
Zope


================================================
File: docs/_ext/djangodocs.py
================================================
"""
Sphinx plugins for Django documentation.
"""

import json
import os
import re

from docutils import nodes
from docutils.parsers.rst import Directive
from docutils.statemachine import ViewList
from sphinx import addnodes
from sphinx import version_info as sphinx_version
from sphinx.builders.html import StandaloneHTMLBuilder
from sphinx.directives.code import CodeBlock
from sphinx.domains.std import Cmdoption
from sphinx.errors import ExtensionError
from sphinx.util import logging
from sphinx.util.console import bold
from sphinx.writers.html import HTMLTranslator

logger = logging.getLogger(__name__)
# RE for option descriptions without a '--' prefix
simple_option_desc_re = re.compile(r"([-_a-zA-Z0-9]+)(\s*.*?)(?=,\s+(?:/|-|--)|$)")


def setup(app):
    app.add_crossref_type(
        directivename="setting",
        rolename="setting",
        indextemplate="pair: %s; setting",
    )
    app.add_crossref_type(
        directivename="templatetag",
        rolename="ttag",
        indextemplate="pair: %s; template tag",
    )
    app.add_crossref_type(
        directivename="templatefilter",
        rolename="tfilter",
        indextemplate="pair: %s; template filter",
    )
    app.add_crossref_type(
        directivename="fieldlookup",
        rolename="lookup",
        indextemplate="pair: %s; field lookup type",
    )
    app.add_object_type(
        directivename="django-admin",
        rolename="djadmin",
        indextemplate="pair: %s; django-admin command",
        parse_node=parse_django_admin_node,
    )
    app.add_directive("django-admin-option", Cmdoption)
    app.add_config_value("django_next_version", "0.0", True)
    app.add_directive("versionadded", VersionDirective)
    app.add_directive("versionchanged", VersionDirective)
    app.add_builder(DjangoStandaloneHTMLBuilder)
    app.set_translator("djangohtml", DjangoHTMLTranslator)
    app.set_translator("json", DjangoHTMLTranslator)
    app.add_node(
        ConsoleNode,
        html=(visit_console_html, None),
        latex=(visit_console_dummy, depart_console_dummy),
        man=(visit_console_dummy, depart_console_dummy),
        text=(visit_console_dummy, depart_console_dummy),
        texinfo=(visit_console_dummy, depart_console_dummy),
    )
    app.add_directive("console", ConsoleDirective)
    app.connect("html-page-context", html_page_context_hook)
    app.add_role("default-role-error", default_role_error)
    return {"parallel_read_safe": True}


class VersionDirective(Directive):
    has_content = True
    required_arguments = 1
    optional_arguments = 1
    final_argument_whitespace = True
    option_spec = {}

    def run(self):
        if len(self.arguments) > 1:
            msg = """Only one argument accepted for directive '{directive_name}::'.
            Comments should be provided as content,
            not as an extra argument.""".format(
                directive_name=self.name
            )
            raise self.error(msg)

        env = self.state.document.settings.env
        ret = []
        node = addnodes.versionmodified()
        ret.append(node)

        if self.arguments[0] == env.config.django_next_version:
            node["version"] = "Development version"
        else:
            node["version"] = self.arguments[0]

        node["type"] = self.name
        if self.content:
            self.state.nested_parse(self.content, self.content_offset, node)
        try:
            env.get_domain("changeset").note_changeset(node)
        except ExtensionError:
            # Sphinx < 1.8: Domain 'changeset' is not registered
            env.note_versionchange(node["type"], node["version"], node, self.lineno)
        return ret


class DjangoHTMLTranslator(HTMLTranslator):
    """
    Django-specific reST to HTML tweaks.
    """

    # Don't use border=1, which docutils does by default.
    def visit_table(self, node):
        self.context.append(self.compact_p)
        self.compact_p = True
        # Needed by Sphinx.
        self._table_row_indices.append(0)
        self.body.append(self.starttag(node, "table", CLASS="docutils"))

    def depart_table(self, node):
        self.compact_p = self.context.pop()
        self._table_row_indices.pop()
        self.body.append("</table>\n")

    def visit_desc_parameterlist(self, node):
        self.body.append("(")  # by default sphinx puts <big> around the "("
        self.optional_param_level = 0
        self.param_separator = node.child_text_separator
        # Counts 'parameter groups' being either a required parameter, or a set
        # of contiguous optional ones.
        required_params = [
            isinstance(c, addnodes.desc_parameter) for c in node.children
        ]
        # How many required parameters are left.
        self.required_params_left = sum(required_params)
        if sphinx_version < (7, 1):
            self.first_param = 1
        else:
            self.is_first_param = True
            self.params_left_at_level = 0
            self.param_group_index = 0
            self.list_is_required_param = required_params
            self.multi_line_parameter_list = False

    def depart_desc_parameterlist(self, node):
        self.body.append(")")

    #
    # Turn the "new in version" stuff (versionadded/versionchanged) into a
    # better callout -- the Sphinx default is just a little span,
    # which is a bit less obvious that I'd like.
    #
    # FIXME: these messages are all hardcoded in English. We need to change
    # that to accommodate other language docs, but I can't work out how to make
    # that work.
    #
    version_text = {
        "versionchanged": "Changed in Django %s",
        "versionadded": "New in Django %s",
    }

    def visit_versionmodified(self, node):
        self.body.append(self.starttag(node, "div", CLASS=node["type"]))
        version_text = self.version_text.get(node["type"])
        if version_text:
            title = "%s%s" % (version_text % node["version"], ":" if len(node) else ".")
            self.body.append('<span class="title">%s</span> ' % title)

    def depart_versionmodified(self, node):
        self.body.append("</div>\n")

    # Give each section a unique ID -- nice for custom CSS hooks
    def visit_section(self, node):
        old_ids = node.get("ids", [])
        node["ids"] = ["s-" + i for i in old_ids]
        node["ids"].extend(old_ids)
        super().visit_section(node)
        node["ids"] = old_ids


def parse_django_admin_node(env, sig, signode):
    command = sig.split(" ")[0]
    env.ref_context["std:program"] = command
    title = "django-admin %s" % sig
    signode += addnodes.desc_name(title, title)
    return command


class DjangoStandaloneHTMLBuilder(StandaloneHTMLBuilder):
    """
    Subclass to add some extra things we need.
    """

    name = "djangohtml"

    def finish(self):
        super().finish()
        logger.info(bold("writing templatebuiltins.js..."))
        xrefs = self.env.domaindata["std"]["objects"]
        templatebuiltins = {
            "ttags": [
                n
                for ((t, n), (k, a)) in xrefs.items()
                if t == "templatetag" and k == "ref/templates/builtins"
            ],
            "tfilters": [
                n
                for ((t, n), (k, a)) in xrefs.items()
                if t == "templatefilter" and k == "ref/templates/builtins"
            ],
        }
        outfilename = os.path.join(self.outdir, "templatebuiltins.js")
        with open(outfilename, "w") as fp:
            fp.write("var django_template_builtins = ")
            json.dump(templatebuiltins, fp)
            fp.write(";\n")


class ConsoleNode(nodes.literal_block):
    """
    Custom node to override the visit/depart event handlers at registration
    time. Wrap a literal_block object and defer to it.
    """

    tagname = "ConsoleNode"

    def __init__(self, litblk_obj):
        self.wrapped = litblk_obj

    def __getattr__(self, attr):
        if attr == "wrapped":
            return self.__dict__.wrapped
        return getattr(self.wrapped, attr)


def visit_console_dummy(self, node):
    """Defer to the corresponding parent's handler."""
    self.visit_literal_block(node)


def depart_console_dummy(self, node):
    """Defer to the corresponding parent's handler."""
    self.depart_literal_block(node)


def visit_console_html(self, node):
    """Generate HTML for the console directive."""
    if self.builder.name in ("djangohtml", "json") and node["win_console_text"]:
        # Put a mark on the document object signaling the fact the directive
        # has been used on it.
        self.document._console_directive_used_flag = True
        uid = node["uid"]
        self.body.append(
            """\
<div class="console-block" id="console-block-%(id)s">
<input class="c-tab-unix" id="c-tab-%(id)s-unix" type="radio" name="console-%(id)s" \
checked>
<label for="c-tab-%(id)s-unix" title="Linux/macOS">&#xf17c/&#xf179</label>
<input class="c-tab-win" id="c-tab-%(id)s-win" type="radio" name="console-%(id)s">
<label for="c-tab-%(id)s-win" title="Windows">&#xf17a</label>
<section class="c-content-unix" id="c-content-%(id)s-unix">\n"""
            % {"id": uid}
        )
        try:
            self.visit_literal_block(node)
        except nodes.SkipNode:
            pass
        self.body.append("</section>\n")

        self.body.append(
            '<section class="c-content-win" id="c-content-%(id)s-win">\n' % {"id": uid}
        )
        win_text = node["win_console_text"]
        highlight_args = {"force": True}
        linenos = node.get("linenos", False)

        def warner(msg):
            self.builder.warn(msg, (self.builder.current_docname, node.line))

        highlighted = self.highlighter.highlight_block(
            win_text, "doscon", warn=warner, linenos=linenos, **highlight_args
        )
        self.body.append(highlighted)
        self.body.append("</section>\n")
        self.body.append("</div>\n")
        raise nodes.SkipNode
    else:
        self.visit_literal_block(node)


class ConsoleDirective(CodeBlock):
    """
    A reStructuredText directive which renders a two-tab code block in which
    the second tab shows a Windows command line equivalent of the usual
    Unix-oriented examples.
    """

    required_arguments = 0
    # The 'doscon' Pygments formatter needs a prompt like this. '>' alone
    # won't do it because then it simply paints the whole command line as a
    # gray comment with no highlighting at all.
    WIN_PROMPT = r"...\> "

    def run(self):
        def args_to_win(cmdline):
            changed = False
            out = []
            for token in cmdline.split():
                if token[:2] == "./":
                    token = token[2:]
                    changed = True
                elif token[:2] == "~/":
                    token = "%HOMEPATH%\\" + token[2:]
                    changed = True
                elif token == "make":
                    token = "make.bat"
                    changed = True
                if "://" not in token and "git" not in cmdline:
                    out.append(token.replace("/", "\\"))
                    changed = True
                else:
                    out.append(token)
            if changed:
                return " ".join(out)
            return cmdline

        def cmdline_to_win(line):
            if line.startswith("# "):
                return "REM " + args_to_win(line[2:])
            if line.startswith("$ # "):
                return "REM " + args_to_win(line[4:])
            if line.startswith("$ ./manage.py"):
                return "manage.py " + args_to_win(line[13:])
            if line.startswith("$ manage.py"):
                return "manage.py " + args_to_win(line[11:])
            if line.startswith("$ ./runtests.py"):
                return "runtests.py " + args_to_win(line[15:])
            if line.startswith("$ ./"):
                return args_to_win(line[4:])
            if line.startswith("$ python3"):
                return "py " + args_to_win(line[9:])
            if line.startswith("$ python"):
                return "py " + args_to_win(line[8:])
            if line.startswith("$ "):
                return args_to_win(line[2:])
            return None

        def code_block_to_win(content):
            bchanged = False
            lines = []
            for line in content:
                modline = cmdline_to_win(line)
                if modline is None:
                    lines.append(line)
                else:
                    lines.append(self.WIN_PROMPT + modline)
                    bchanged = True
            if bchanged:
                return ViewList(lines)
            return None

        env = self.state.document.settings.env
        self.arguments = ["console"]
        lit_blk_obj = super().run()[0]

        # Only do work when the djangohtml HTML Sphinx builder is being used,
        # invoke the default behavior for the rest.
        if env.app.builder.name not in ("djangohtml", "json"):
            return [lit_blk_obj]

        lit_blk_obj["uid"] = str(env.new_serialno("console"))
        # Only add the tabbed UI if there is actually a Windows-specific
        # version of the CLI example.
        win_content = code_block_to_win(self.content)
        if win_content is None:
            lit_blk_obj["win_console_text"] = None
        else:
            self.content = win_content
            lit_blk_obj["win_console_text"] = super().run()[0].rawsource

        # Replace the literal_node object returned by Sphinx's CodeBlock with
        # the ConsoleNode wrapper.
        return [ConsoleNode(lit_blk_obj)]


def html_page_context_hook(app, pagename, templatename, context, doctree):
    # Put a bool on the context used to render the template. It's used to
    # control inclusion of console-tabs.css and activation of the JavaScript.
    # This way it's include only from HTML files rendered from reST files where
    # the ConsoleDirective is used.
    context["include_console_assets"] = getattr(
        doctree, "_console_directive_used_flag", False
    )


def default_role_error(
    name, rawtext, text, lineno, inliner, options=None, content=None
):
    msg = (
        "Default role used (`single backticks`): %s. Did you mean to use two "
        "backticks for ``code``, or miss an underscore for a `link`_ ?" % rawtext
    )
    logger.warning(msg, location=(inliner.document.current_source, lineno))
    return [nodes.Text(text)], []


================================================
File: docs/_ext/github_links.py
================================================
import ast
import functools
import importlib.util
import pathlib


class CodeLocator(ast.NodeVisitor):
    def __init__(self):
        super().__init__()
        self.current_path = []
        self.node_line_numbers = {}
        self.import_locations = {}

    @classmethod
    def from_code(cls, code):
        tree = ast.parse(code)
        locator = cls()
        locator.visit(tree)
        return locator

    def visit_node(self, node):
        self.current_path.append(node.name)
        self.node_line_numbers[".".join(self.current_path)] = node.lineno
        self.generic_visit(node)
        self.current_path.pop()

    def visit_FunctionDef(self, node):
        self.visit_node(node)

    def visit_ClassDef(self, node):
        self.visit_node(node)

    def visit_ImportFrom(self, node):
        for alias in node.names:
            if alias.asname:
                # Exclude linking aliases (`import x as y`) to avoid confusion
                # when clicking a source link to a differently named entity.
                continue
            if alias.name == "*":
                # Resolve wildcard imports.
                file = module_name_to_file_path(node.module)
                file_contents = file.read_text(encoding="utf-8")
                locator = CodeLocator.from_code(file_contents)
                self.import_locations.update(locator.import_locations)
                self.import_locations.update(
                    {n: node.module for n in locator.node_line_numbers if "." not in n}
                )
            else:
                self.import_locations[alias.name] = ("." * node.level) + (
                    node.module or ""
                )


@functools.lru_cache(maxsize=1024)
def get_locator(file):
    file_contents = file.read_text(encoding="utf-8")
    return CodeLocator.from_code(file_contents)


class CodeNotFound(Exception):
    pass


def module_name_to_file_path(module_name):
    # Avoid importlib machinery as locating a module involves importing its
    # parent, which would trigger import side effects.

    for suffix in [".py", "/__init__.py"]:
        file_path = pathlib.Path(__file__).parents[2] / (
            module_name.replace(".", "/") + suffix
        )
        if file_path.exists():
            return file_path

    raise CodeNotFound


def get_path_and_line(module, fullname):
    path = module_name_to_file_path(module_name=module)

    locator = get_locator(path)

    lineno = locator.node_line_numbers.get(fullname)

    if lineno is not None:
        return path, lineno

    imported_object = fullname.split(".", maxsplit=1)[0]
    try:
        imported_path = locator.import_locations[imported_object]
    except KeyError:
        raise CodeNotFound

    # From a statement such as:
    # from . import y.z
    # - either y.z might be an object in the parent module
    # - or y might be a module, and z be an object in y
    # also:
    # - either the current file is x/__init__.py, and z would be in x.y
    # - or the current file is x/a.py, and z would be in x.a.y
    if path.name != "__init__.py":
        # Look in parent module
        module = module.rsplit(".", maxsplit=1)[0]
    try:
        imported_module = importlib.util.resolve_name(
            name=imported_path, package=module
        )
    except ImportError as error:
        raise ImportError(
            f"Could not import '{imported_path}' in '{module}'."
        ) from error
    try:
        return get_path_and_line(module=imported_module, fullname=fullname)
    except CodeNotFound:
        if "." not in fullname:
            raise

        first_element, remainder = fullname.rsplit(".", maxsplit=1)
        # Retrying, assuming the first element of the fullname is a module.
        return get_path_and_line(
            module=f"{imported_module}.{first_element}", fullname=remainder
        )


def get_branch(version, next_version):
    if version == next_version:
        return "main"
    else:
        return f"stable/{version}.x"


def github_linkcode_resolve(domain, info, *, version, next_version):
    if domain != "py":
        return None

    if not (module := info["module"]):
        return None

    try:
        path, lineno = get_path_and_line(module=module, fullname=info["fullname"])
    except CodeNotFound:
        return None

    branch = get_branch(version=version, next_version=next_version)
    relative_path = path.relative_to(pathlib.Path(__file__).parents[2])
    # Use "/" explicitly to join the path parts since str(file), on Windows,
    # uses the Windows path separator which is incorrect for URLs.
    url_path = "/".join(relative_path.parts)
    return f"https://github.com/django/django/blob/{branch}/{url_path}#L{lineno}"


================================================
File: docs/_theme/djangodocs/genindex.html
================================================
{% extends "basic/genindex.html" %}

{% block bodyclass %}{% endblock %}
{% block sidebarwrapper %}{% endblock %}


================================================
File: docs/_theme/djangodocs/layout.html
================================================
{% extends "basic/layout.html" %}

{%- macro secondnav() %}
  {%- if prev %}
    &laquo; <a href="{{ prev.link|e }}" title="{{ prev.title|e }}">previous</a>
    {{ reldelim2 }}
  {%- endif %}
  {%- if parents %}
    <a href="{{ parents.0.link|e }}" title="{{ parents.0.title|e }}" accesskey="U">up</a>
  {%- else %}
    <a title="{{ docstitle }}" href="{{ pathto('index') }}" accesskey="U">up</a>
  {%- endif %}
  {%- if next %}
  {{ reldelim2 }}
    <a href="{{ next.link|e }}" title="{{ next.title|e }}">next</a> &raquo;
  {%- endif %}
{%- endmacro %}

{% block extrahead %}
{# When building htmlhelp (CHM format) disable jQuery inclusion, #}
{# as it causes problems in compiled CHM files.                  #}
{% if builder != "htmlhelp" %}
{{ super() }}
<script src="{{ pathto('templatebuiltins.js', 1) }}"></script>
<script>
(function($) {
    if (!django_template_builtins) {
       // templatebuiltins.js missing, do nothing.
       return;
    }
    $(document).ready(function() {
        // Hyperlink Django template tags and filters
        var base = "{{ pathto('ref/templates/builtins') }}";
        if (base == "#") {
            // Special case for builtins.html itself
            base = "";
        }
        // Tags are keywords, class '.k'
        $("div.highlight\\-html\\+django span.k").each(function(i, elem) {
             var tagname = $(elem).text();
             if ($.inArray(tagname, django_template_builtins.ttags) != -1) {
                 var fragment = tagname.replace(/_/, '-');
                 $(elem).html("<a href='" + base + "#" + fragment + "'>" + tagname + "</a>");
             }
        });
        // Filters are functions, class '.nf'
        $("div.highlight\\-html\\+django span.nf").each(function(i, elem) {
             var filtername = $(elem).text();
             if ($.inArray(filtername, django_template_builtins.tfilters) != -1) {
                 var fragment = filtername.replace(/_/, '-');
                 $(elem).html("<a href='" + base + "#" + fragment + "'>" + filtername + "</a>");
             }
        });
    });
})(jQuery);
{%- if include_console_assets -%}
(function($) {
    $(document).ready(function() {
        $(".c-tab-unix").on("click", function() {
            $("section.c-content-unix").show();
            $("section.c-content-win").hide();
            $(".c-tab-unix").prop("checked", true);
        });
        $(".c-tab-win").on("click", function() {
            $("section.c-content-win").show();
            $("section.c-content-unix").hide();
            $(".c-tab-win").prop("checked", true);
        });
    });
})(jQuery);
{%- endif -%}
</script>
{% endif %}
{%- if include_console_assets -%}
<link rel="stylesheet" href="{{ pathto('_static/console-tabs.css', 1) }}">
{%- endif -%}
{% endblock %}

{% block document %}
  <div id="custom-doc" class="{% block bodyclass %}{{ 'yui-t6' if pagename != 'index' else '' }}{% endblock %}">
    <div id="hd">
      <h1><a href="{{ pathto('index') }}">{{ docstitle }}</a></h1>
      <div id="global-nav">
        <a title="Home page" href="{{ pathto('index') }}">Home</a> {{ reldelim2 }}
        <a title="Table of contents" href="{{ pathto('contents') }}">Table of contents</a> {{ reldelim2 }}
        <a title="Global index" href="{{ pathto('genindex') }}">Index</a> {{ reldelim2 }}
        <a title="Module index" href="{{ pathto('py-modindex') }}">Modules</a>
      </div>
      <div class="nav">{{ secondnav() }}</div>
    </div>

    <div id="bd">
      <div id="yui-main">
        <div class="yui-b">
          <div class="yui-g" id="{{ pagename|replace('/', '-') }}">
            {% block body %}{% endblock %}
          </div>
        </div>
      </div>
      {% block sidebarwrapper %}
        {% if pagename != 'index' %}
          <div class="yui-b" id="sidebar">
            {{ sidebar() }}
            {%- if last_updated %}
              <h3>Last update:</h3>
              <p class="topless">{{ last_updated }}</p>
            {%- endif %}
          </div>
        {% endif %}
      {% endblock %}
    </div>

    <div id="ft">
      <div class="nav">{{ secondnav() }}</div>
    </div>
  </div>
{% endblock %}

{% block sidebarrel %}
  <h3>Browse</h3>
  <ul>
    {% if prev %}
      <li>Prev: <a href="{{ prev.link }}">{{ prev.title }}</a></li>
    {% endif %}
    {% if next %}
      <li>Next: <a href="{{ next.link }}">{{ next.title }}</a></li>
    {% endif %}
  </ul>
  <h3>You are here:</h3>
  <ul>
      <li>
        <a href="{{ pathto('index') }}">{{ docstitle }}</a>
        {% for p in parents %}
          <ul><li><a href="{{ p.link }}">{{ p.title }}</a>
        {% endfor %}
        <ul><li>{{ title }}</li></ul>
        {% for p in parents %}</li></ul>{% endfor %}
      </li>
  </ul>
{% endblock %}

{# Empty some default blocks out #}
{% block relbar1 %}{% endblock %}
{% block relbar2 %}{% endblock %}
{% block sidebar1 %}{% endblock %}
{% block sidebar2 %}{% endblock %}
{% block footer %}{% endblock %}


================================================
File: docs/_theme/djangodocs/modindex.html
================================================
{% extends "basic/modindex.html" %}
{% block bodyclass %}{% endblock %}
{% block sidebarwrapper %}{% endblock %}


================================================
File: docs/_theme/djangodocs/search.html
================================================
{% extends "basic/search.html" %}
{% block bodyclass %}{% endblock %}
{% block sidebarwrapper %}{% endblock %}


================================================
File: docs/_theme/djangodocs/theme.conf
================================================
[theme]
inherit = basic
stylesheet = default.css
pygments_style = trac


================================================
File: docs/_theme/djangodocs/static/console-tabs.css
================================================
@import url("{{ pathto('_static/fontawesome/css/fa-brands.min.css', 1) }}");

.console-block {
  text-align: right;
}

.console-block *:before,
.console-block *:after {
  box-sizing: border-box;
}

.console-block > section {
  display: none;
  text-align: left;
}

.console-block > input.c-tab-unix,
.console-block > input.c-tab-win {
  display: none;
}

.console-block > label {
  display: inline-block;
  padding: 4px 8px;
  font-weight: normal;
  text-align: center;
  color: #bbb;
  border: 1px solid transparent;
  font-family: fontawesome;
}

.console-block > input:checked + label {
  color: #555;
  border: 1px solid #ddd;
  border-top: 2px solid #ab5603;
  border-bottom: 1px solid #fff;
}

.console-block > .c-tab-unix:checked ~ .c-content-unix,
.console-block > .c-tab-win:checked  ~ .c-content-win {
  display: block;
}

.console-block pre {
  margin-top: 0px;
}


================================================
File: docs/_theme/djangodocs/static/default.css
================================================
@import url(reset-fonts-grids.css);
@import url(djangodocs.css);
@import url(homepage.css);


================================================
File: docs/_theme/djangodocs/static/djangodocs.css
================================================
/*** setup ***/
html { background:#092e20;}
body { font:12px/1.5 Verdana,sans-serif; background:#092e20; color: white;}
#custom-doc { width:76.54em;*width:74.69em;min-width:995px; max-width:100em; margin:auto; text-align:left; padding-top:16px; margin-top:0;}
#hd { padding: 4px 0 12px 0; }
#bd { background:#234F32; }
#ft { color:#487858; font-size:90%; padding-bottom: 2em; }

/*** links ***/
a {text-decoration: none;}
a img {border: none;}
a:link, a:visited { color:#ffc757; }
#bd a:link, #bd a:visited { color:#ab5603; text-decoration:underline; }
#bd #sidebar a:link, #bd #sidebar a:visited { color:#ffc757; text-decoration:none; }
a:hover { color:#ffe761; }
#bd a:hover { background-color:#E0FFB8; color:#234f32; text-decoration:none; }
#bd #sidebar a:hover { color:#ffe761; background:none; }
h2 a, h3 a, h4 a { text-decoration:none !important; }
a.reference em { font-style: normal; }

/*** sidebar ***/
#sidebar div.sphinxsidebarwrapper { font-size:92%; margin-right: 14px; }
#sidebar h3, #sidebar h4 { color: white; font-size: 125%; }
#sidebar a { color: white; }
#sidebar ul ul { margin-top:0; margin-bottom:0; }
#sidebar li { margin-top: 0.2em; margin-bottom: 0.2em; }

/*** nav ***/
div.nav { margin: 0; font-size: 11px; text-align: right; color: #487858;}
#hd div.nav { margin-top: -27px; }
#ft div.nav { margin-bottom: -18px; }
#hd h1 a { color: white; }
#global-nav { position:absolute; top:5px; margin-left: -5px; padding:7px 0; color:#263E2B; }
#global-nav a:link, #global-nav a:visited {color:#487858;}
#global-nav a {padding:0 4px;}
#global-nav a.about {padding-left:0;}
#global-nav:hover {color:#fff;}
#global-nav:hover a:link, #global-nav:hover a:visited  { color:#ffc757; }

/*** content ***/
#yui-main div.yui-b { position: relative; }
#yui-main div.yui-b { margin: 0 0 0 20px; background: white; color: black; padding: 0.3em 2em 1em 2em; }

/*** basic styles ***/
dd { margin-left:15px; }
h1,h2,h3,h4,h5,h6,h7,h8,h9,h10,h11,h12 { margin-top:1em; font-family:"Trebuchet MS",sans-serif; font-weight:normal; }
h1 { font-size:218%; margin-top:0.6em; margin-bottom:.4em; line-height:1.1em; }
h2 { font-size:175%; margin-bottom:.6em; line-height:1.2em; color:#092e20; }
h3 { font-size:150%; font-weight:bold; margin-bottom:.2em; color:#487858; }
h4 { font-size:125%; font-weight:bold; margin-top:1.5em; margin-bottom:3px; }
h5 { font-size:110%; font-weight:bold; margin-top:1em; margin-bottom:3px; }
h6,h7,h8,h9,h10,h11,h12 { font-weight:bold; margin-bottom:3px; }
div.figure { text-align: center; }
div.figure p.caption { font-size:1em; margin-top:0; margin-bottom:1.5em; color: #555;}
hr { color:#ccc; background-color:#ccc; height:1px; border:0; }
p, ul, dl { margin-top:.6em; margin-bottom:1em; padding-bottom: 0.1em;}
#yui-main div.yui-b img { max-width: 50em; margin-left: auto; margin-right: auto; display: block; }
caption { font-size:1em; font-weight:bold; margin-top:0.5em; margin-bottom:0.5em; margin-left: 2px; text-align: center; }
blockquote { padding: 0 1em; margin: 1em 0; font:125%/1.2em "Trebuchet MS", sans-serif; color:#234f32; border-left:2px solid #94da3a; }
strong { font-weight: bold; }
em { font-style: italic; }
ins { font-weight: bold; text-decoration: none; }

/*** lists ***/
ul { padding-left:30px; }
ol { padding-left:30px; }
ol.arabic li { list-style-type: decimal; }
ul li { list-style-type:square; margin-bottom:.4em; }
ul ul li { list-style-type:disc; }
ul ul ul li { list-style-type:circle; }
ol li { margin-bottom: .4em; }
ul ul { padding-left:1.2em; }
ul ul ul { padding-left:1em; }
ul.linklist, ul.toc { padding-left:0; }
ul.toc ul { margin-left:.6em; }
ul.toc ul li { list-style-type:square; }
ul.toc ul ul li { list-style-type:disc; }
ul.linklist li, ul.toc li { list-style-type:none; }
dt { font-weight:bold; margin-top:.5em; font-size:1.1em; }
dd { margin-bottom:.8em; }
ol.toc { margin-bottom: 2em; }
ol.toc li { font-size:125%; padding: .5em; line-height:1.2em; clear: right; }
ol.toc li.b { background-color: #E0FFB8; }
ol.toc li a:hover { background-color: transparent !important; text-decoration: underline !important; }
ol.toc span.release-date { color:#487858; float: right; font-size: 85%; padding-right: .5em; }
ol.toc span.comment-count { font-size: 75%; color: #999; }

/*** tables ***/
table { color:#000; margin-bottom: 1em; width: 100%; }
table.docutils td p { margin-top:0; margin-bottom:.5em; }
table.docutils td, table.docutils th { border-bottom:1px solid #dfdfdf; padding:4px 2px;}
table.docutils thead th { border-bottom:2px solid #dfdfdf; text-align:left; font-weight: bold; white-space: nowrap; }
table.docutils thead th p { margin: 0; padding: 0; }
table.docutils { border-collapse:collapse; }

/*** code blocks ***/
.literal { color:#234f32; white-space:nowrap; }
dt > tt.literal { white-space: normal; }
#sidebar .literal { color:white; background:transparent; font-size:11px; }
h4 .literal { color: #234f32; font-size: 13px; }
pre { font-size:small; background:#E0FFB8; border:1px solid #94da3a; border-width:1px 0; margin: 1em 0; padding: .3em .4em; overflow: hidden; line-height: 1.3em; white-space: pre-wrap;}
dt .literal, table .literal { background:none; }
#bd a.reference { text-decoration: none; }
#bd a.reference tt.literal { border-bottom: 1px #234f32 dotted; }
div.code-block-caption { color: white; background-color: #234F32; margin: 0; padding: 2px 5px; width: 100%; font-family: monospace; font-size: small; line-height: 1.3em; }
div.code-block-caption .literal {color: white; }
div.literal-block-wrapper pre { margin-top: 0; }

/* Restore colors of pygments hyperlinked code */
#bd .highlight .k a:link, #bd .highlight .k a:visited { color: #000000; text-decoration: none; border-bottom: 1px dotted #000000; }
#bd .highlight .nf a:link, #bd .highlight .nf a:visited { color: #990000; text-decoration: none; border-bottom: 1px dotted #990000; }


/*** notes & admonitions ***/
.note, .admonition { padding:.8em 1em .8em; margin: 1em 0; border:1px solid #94da3a; }
.admonition-title { font-weight:bold; margin-top:0 !important; margin-bottom:0 !important;}
.admonition .last { margin-bottom:0 !important; }
.note, .admonition { padding-left:65px; background:url(docicons-note.png) .8em .8em no-repeat;}
div.admonition-philosophy { padding-left:65px; background:url(docicons-philosophy.png) .8em .8em no-repeat;}
div.admonition-behind-the-scenes { padding-left:65px; background:url(docicons-behindscenes.png) .8em .8em no-repeat;}
.admonition.warning { background:url(docicons-warning.png) .8em .8em no-repeat; border:1px solid #ffc83c;}

/*** versionadded/changes ***/
div.versionadded, div.versionchanged {  }
div.versionadded span.title, div.versionchanged span.title, span.versionmodified { font-weight: bold; }
div.versionadded, div.versionchanged, div.deprecated { color:#555; }

/*** p-links ***/
a.headerlink { color: #c60f0f; font-size: 0.8em; margin-left: 4px; opacity: 0; text-decoration: none; }
h1:hover > a.headerlink, h2:hover > a.headerlink, h3:hover > a.headerlink, h4:hover > a.headerlink, h5:hover > a.headerlink, h6:hover > a.headerlink, dt:hover > a.headerlink { opacity: 1; }
a.headerlink:focus { opacity: 1; }

/*** index ***/
table.indextable td { text-align: left; vertical-align: top;}
table.indextable dl, table.indextable dd { margin-top: 0; margin-bottom: 0; }
table.indextable tr.pcap { height: 10px; }
table.indextable tr.cap { margin-top: 10px; background-color: #f2f2f2;}

/*** page-specific overrides ***/
div#contents ul { margin-bottom: 0;}
div#contents ul li { margin-bottom: 0;}
div#contents ul ul li { margin-top: 0.3em;}

/*** IE hacks ***/
* pre { width: 100%; }


================================================
File: docs/_theme/djangodocs/static/homepage.css
================================================
#index p.rubric { font-size:150%; font-weight:normal; margin-bottom:.2em; color:#487858; }

#index div.section dt { font-weight: normal; }

#index #s-getting-help { float: right; width: 35em; background: #E1ECE2; padding: 1em; margin: 2em 0 2em 2em; }
#index #s-getting-help h2 { margin: 0; }

#index #s-django-documentation div.section div.section h3 { margin: 0; }
#index #s-django-documentation div.section div.section { background: #E1ECE2; padding: 1em; margin: 2em 0 2em 40.3em; }
#index #s-django-documentation div.section div.section a.reference { white-space: nowrap; }

#index #s-using-django dl,
#index #s-add-on-contrib-applications dl,
#index #s-solving-specific-problems dl,
#index #s-reference dl
    { float: left; width: 41em; }

#index #s-add-on-contrib-applications,
#index #s-solving-specific-problems,
#index #s-reference,
#index #s-and-all-the-rest
    { clear: left; }


================================================
File: docs/_theme/djangodocs/static/reset-fonts-grids.css
================================================
/*
Copyright (c) 2008, Yahoo! Inc. All rights reserved.
Code licensed under the BSD License:
http://developer.yahoo.net/yui/license.txt
version: 2.5.1
*/
html{color:#000;background:#FFF;}body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,code,form,fieldset,legend,input,textarea,p,blockquote,th,td{margin:0;padding:0;}table{border-collapse:collapse;border-spacing:0;}fieldset,img{border:0;}address,caption,cite,code,dfn,em,strong,th,var{font-style:normal;font-weight:normal;}li{list-style:none;}caption,th{text-align:left;}h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal;}q:before,q:after{content:'';}abbr,acronym {border:0;font-variant:normal;}sup {vertical-align:text-top;}sub {vertical-align:text-bottom;}input,textarea,select{font-family:inherit;font-size:inherit;font-weight:inherit;}input,textarea,select{*font-size:100%;}legend{color:#000;}body {font:13px/1.231 arial,helvetica,clean,sans-serif;*font-size:small;*font:x-small;}table {font-size:inherit;font:100%;}pre,code,kbd,samp,tt{font-family:monospace;*font-size:108%;line-height:100%;}
body{text-align:center;}#ft{clear:both;}#doc,#doc2,#doc3,#doc4,.yui-t1,.yui-t2,.yui-t3,.yui-t4,.yui-t5,.yui-t6,.yui-t7{margin:auto;text-align:left;width:57.69em;*width:56.25em;min-width:750px;}#doc2{width:73.076em;*width:71.25em;}#doc3{margin:auto 10px;width:auto;}#doc4{width:74.923em;*width:73.05em;}.yui-b{position:relative;}.yui-b{_position:static;}#yui-main .yui-b{position:static;}#yui-main{width:100%;}.yui-t1 #yui-main,.yui-t2 #yui-main,.yui-t3 #yui-main{float:right;margin-left:-25em;}.yui-t4 #yui-main,.yui-t5 #yui-main,.yui-t6 #yui-main{float:left;margin-right:-25em;}.yui-t1 .yui-b{float:left;width:12.30769em;*width:12.00em;}.yui-t1 #yui-main .yui-b{margin-left:13.30769em;*margin-left:13.05em;}.yui-t2 .yui-b{float:left;width:13.8461em;*width:13.50em;}.yui-t2 #yui-main .yui-b{margin-left:14.8461em;*margin-left:14.55em;}.yui-t3 .yui-b{float:left;width:23.0769em;*width:22.50em;}.yui-t3 #yui-main .yui-b{margin-left:24.0769em;*margin-left:23.62em;}.yui-t4 .yui-b{float:right;width:13.8456em;*width:13.50em;}.yui-t4 #yui-main .yui-b{margin-right:14.8456em;*margin-right:14.55em;}.yui-t5 .yui-b{float:right;width:18.4615em;*width:18.00em;}.yui-t5 #yui-main .yui-b{margin-right:19.4615em;*margin-right:19.125em;}.yui-t6 .yui-b{float:right;width:23.0769em;*width:22.50em;}.yui-t6 #yui-main .yui-b{margin-right:24.0769em;*margin-right:23.62em;}.yui-t7 #yui-main .yui-b{display:block;margin:0 0 1em 0;}#yui-main .yui-b{float:none;width:auto;}.yui-gb .yui-u,.yui-g .yui-gb .yui-u,.yui-gb .yui-g,.yui-gb .yui-gb,.yui-gb .yui-gc,.yui-gb .yui-gd,.yui-gb .yui-ge,.yui-gb .yui-gf,.yui-gc .yui-u,.yui-gc .yui-g,.yui-gd .yui-u{float:left;}.yui-g .yui-u,.yui-g .yui-g,.yui-g .yui-gb,.yui-g .yui-gc,.yui-g .yui-gd,.yui-g .yui-ge,.yui-g .yui-gf,.yui-gc .yui-u,.yui-gd .yui-g,.yui-g .yui-gc .yui-u,.yui-ge .yui-u,.yui-ge .yui-g,.yui-gf .yui-g,.yui-gf .yui-u{float:right;}.yui-g div.first,.yui-gb div.first,.yui-gc div.first,.yui-gd div.first,.yui-ge div.first,.yui-gf div.first,.yui-g .yui-gc div.first,.yui-g .yui-ge div.first,.yui-gc div.first div.first{float:left;}.yui-g .yui-u,.yui-g .yui-g,.yui-g .yui-gb,.yui-g .yui-gc,.yui-g .yui-gd,.yui-g .yui-ge,.yui-g .yui-gf{width:49.1%;}.yui-gb .yui-u,.yui-g .yui-gb .yui-u,.yui-gb .yui-g,.yui-gb .yui-gb,.yui-gb .yui-gc,.yui-gb .yui-gd,.yui-gb .yui-ge,.yui-gb .yui-gf,.yui-gc .yui-u,.yui-gc .yui-g,.yui-gd .yui-u{width:32%;margin-left:1.99%;}.yui-gb .yui-u{*margin-left:1.9%;*width:31.9%;}.yui-gc div.first,.yui-gd .yui-u{width:66%;}.yui-gd div.first{width:32%;}.yui-ge div.first,.yui-gf .yui-u{width:74.2%;}.yui-ge .yui-u,.yui-gf div.first{width:24%;}.yui-g .yui-gb div.first,.yui-gb div.first,.yui-gc div.first,.yui-gd div.first{margin-left:0;}.yui-g .yui-g .yui-u,.yui-gb .yui-g .yui-u,.yui-gc .yui-g .yui-u,.yui-gd .yui-g .yui-u,.yui-ge .yui-g .yui-u,.yui-gf .yui-g .yui-u{width:49%;*width:48.1%;*margin-left:0;}.yui-g .yui-gb div.first,.yui-gb .yui-gb div.first{*margin-right:0;*width:32%;_width:31.7%;}.yui-g .yui-gc div.first,.yui-gd .yui-g{width:66%;}.yui-gb .yui-g div.first{*margin-right:4%;_margin-right:1.3%;}.yui-gb .yui-gc div.first,.yui-gb .yui-gd div.first{*margin-right:0;}.yui-gb .yui-gb .yui-u,.yui-gb .yui-gc .yui-u{*margin-left:1.8%;_margin-left:4%;}.yui-g .yui-gb .yui-u{_margin-left:1.0%;}.yui-gb .yui-gd .yui-u{*width:66%;_width:61.2%;}.yui-gb .yui-gd div.first{*width:31%;_width:29.5%;}.yui-g .yui-gc .yui-u,.yui-gb .yui-gc .yui-u{width:32%;_float:right;margin-right:0;_margin-left:0;}.yui-gb .yui-gc div.first{width:66%;*float:left;*margin-left:0;}.yui-gb .yui-ge .yui-u,.yui-gb .yui-gf .yui-u{margin:0;}.yui-gb .yui-gb .yui-u{_margin-left:.7%;}.yui-gb .yui-g div.first,.yui-gb .yui-gb div.first{*margin-left:0;}.yui-gc .yui-g .yui-u,.yui-gd .yui-g .yui-u{*width:48.1%;*margin-left:0;}s .yui-gb .yui-gd div.first{width:32%;}.yui-g .yui-gd div.first{_width:29.9%;}.yui-ge .yui-g{width:24%;}.yui-gf .yui-g{width:74.2%;}.yui-gb .yui-ge div.yui-u,.yui-gb .yui-gf div.yui-u{float:right;}.yui-gb .yui-ge div.first,.yui-gb .yui-gf div.first{float:left;}.yui-gb .yui-ge .yui-u,.yui-gb .yui-gf div.first{*width:24%;_width:20%;}.yui-gb .yui-ge div.first,.yui-gb .yui-gf .yui-u{*width:73.5%;_width:65.5%;}.yui-ge div.first .yui-gd .yui-u{width:65%;}.yui-ge div.first .yui-gd div.first{width:32%;}#bd:after,.yui-g:after,.yui-gb:after,.yui-gc:after,.yui-gd:after,.yui-ge:after,.yui-gf:after{content:".";display:block;height:0;clear:both;visibility:hidden;}#bd,.yui-g,.yui-gb,.yui-gc,.yui-gd,.yui-ge,.yui-gf{zoom:1;}

================================================
File: docs/_theme/djangodocs/static/fontawesome/README.md
================================================
# Font Awesome 5.0.4

Thanks for downloading Font Awesome! We're so excited you're here.

Our documentation is available online. Just head here:

https://fontawesome.com


================================================
File: docs/_theme/djangodocs/static/fontawesome/LICENSE.txt
================================================
Font Awesome Free License
-------------------------

Font Awesome Free is free, open source, and GPL friendly. You can use it for
commercial projects, open source projects, or really almost whatever you want.
Full Font Awesome Free license: https://fontawesome.com/license.

# Icons: CC BY 4.0 License (https://creativecommons.org/licenses/by/4.0/)
In the Font Awesome Free download, the CC BY 4.0 license applies to all icons
packaged as SVG and JS file types.

# Fonts: SIL OFL 1.1 License (https://scripts.sil.org/OFL)
In the Font Awesome Free download, the SIL OLF license applies to all icons
packaged as web and desktop font files.

# Code: MIT License (https://opensource.org/licenses/MIT)
In the Font Awesome Free download, the MIT license applies to all non-font and
non-icon files.

# Attribution
Attribution is required by MIT, SIL OLF, and CC BY licenses. Downloaded Font
Awesome Free files already contain embedded comments with sufficient
attribution, so you shouldn't need to do anything additional when using these
files normally.

We've kept attribution comments terse, so we ask that you do not actively work
to remove them from files, especially code. They're a great way for folks to 
learn about Font Awesome.

# Brand Icons
All brand icons are trademarks of their respective owners. The use of these
trademarks does not indicate endorsement of the trademark holder by Font
Awesome, nor vice versa. **Please do not use brand logos for any purpose except
to represent the company, product, or service to which they refer.**


================================================
File: docs/_theme/djangodocs-epub/epub-cover.html
================================================
{%- extends "epub/epub-cover.html" %}

{% block content %}
  <div class="epub-cover">
    <h1>Django Documentation</h1>
    <h2><em>Release {{ release }}</em></h2>
    <h3>{{ copyright }}</h3>
    <p>{{ last_updated }}</p>
  </div>
{% endblock %}


================================================
File: docs/_theme/djangodocs-epub/theme.conf
================================================
[theme]
inherit = epub
stylesheet = epub.css
pygments_style = trac

[options]
relbar1 = false
footer = false


================================================
File: docs/_theme/djangodocs-epub/static/epub.css
================================================
h1 { margin-top: 0; }

/* Keep lists a bit narrow to maximize page estate regarding width. */
ol, ul {
    margin: 0;
    padding: 0 0 0 1.3em;
}

/* Images should never exceed the width of the page. */
img { max-width: 100%; }

/* Don't display URL after links, this is not print. */
.link-target { display: none; }

/* This is the front cover page of the book. */
.epub-cover { text-align: center; }
.epub-cover h1 { margin: 4em 0 0 0; }
.epub-cover h2 { margin: 1em 0; }
.epub-cover h3 { margin: 3em 0 2em 0; }

/* Code examples should never exceed the width of the page, so wrap instead. */
pre, span.pre { white-space: pre-wrap; }

pre {
    background-color: #f6f6f6;
    border: 0;
    padding: 0.5em;
    font-size: 90%;
}

/* Header for some code blocks. */
.code-block-caption {
    background-color: #393939;
    color: white;
    margin: 0;
    padding: 0.5em;
    font: bold 90% monospace;
}
.literal-block-wrapper pre {
    margin-top: 0;
}

a:link, a:visited { color: #396623; }
a:hover { color: #1d3311; }

/* Use special styled note boxes from the default theme, but with the left side
fitted after the icon, to allow text resizing with breaking. */
.note, .admonition {
    background-position: 9px 0.8em;
    background-repeat: no-repeat;
    padding: 0.8em 1em 0.8em 65px;
    margin: 1em 0;
    border: 0.01em solid black;
}

.note, .admonition { background-image: url(docicons-note.png); }
div.admonition-philosophy { background-image: url(docicons-philosophy.png); }
div.admonition-behind-the-scenes { background-image: url(docicons-behindscenes.png); }
.admonition.warning { background-image: url(docicons-warning.png); }

.admonition-title {
    font-weight: bold;
    margin: 0;
}

.admonition .last { margin-bottom: 0; }


================================================
File: docs/faq/admin.txt
================================================
==============
FAQ: The admin
==============

I can't log in. When I enter a valid username and password, it just brings up the login page again, with no error messages.
===========================================================================================================================

The login cookie isn't being set correctly, because the domain of the cookie
sent out by Django doesn't match the domain in your browser. Try setting the
:setting:`SESSION_COOKIE_DOMAIN` setting to match your domain. For example, if
you're going to "https://www.example.com/admin/" in your browser, set
``SESSION_COOKIE_DOMAIN = 'www.example.com'``.

I can't log in. When I enter a valid username and password, it brings up the login page again, with a "Please enter a correct username and password" error.
===========================================================================================================================================================

If you're sure your username and password are correct, make sure your user
account has :attr:`~django.contrib.auth.models.User.is_active` and
:attr:`~django.contrib.auth.models.User.is_staff` set to True. The admin site
only allows access to users with those two fields both set to True.

How do I automatically set a field's value to the user who last edited the object in the admin?
===============================================================================================

The :class:`~django.contrib.admin.ModelAdmin` class provides customization hooks
that allow you to transform an object as it saved, using details from the
request. By extracting the current user from the request, and customizing the
:meth:`~django.contrib.admin.ModelAdmin.save_model` hook, you can update an
object to reflect the user that edited it. See :ref:`the documentation on
ModelAdmin methods <model-admin-methods>` for an example.

How do I limit admin access so that objects can only be edited by the users who created them?
=============================================================================================

The :class:`~django.contrib.admin.ModelAdmin` class also provides customization
hooks that allow you to control the visibility and editability of objects in the
admin. Using the same trick of extracting the user from the request, the
:meth:`~django.contrib.admin.ModelAdmin.get_queryset` and
:meth:`~django.contrib.admin.ModelAdmin.has_change_permission` can be used to
control the visibility and editability of objects in the admin.

My admin-site CSS and images showed up fine using the development server, but they're not displaying when using mod_wsgi.
=========================================================================================================================

See :ref:`serving the admin files <serving-the-admin-files>`
in the "How to use Django with mod_wsgi" documentation.

My "list_filter" contains a ManyToManyField, but the filter doesn't display.
============================================================================

Django won't bother displaying the filter for a ``ManyToManyField`` if there
are no related objects.

For example, if your :attr:`~django.contrib.admin.ModelAdmin.list_filter`
includes :doc:`sites </ref/contrib/sites>`, and there are no sites in your
database, it won't display a "Site" filter. In that case, filtering by site
would be meaningless.

Some objects aren't appearing in the admin.
===========================================

Inconsistent row counts may be caused by missing foreign key values or a
foreign key field incorrectly set to :attr:`null=False
<django.db.models.Field.null>`. If you have a record with a
:class:`~django.db.models.ForeignKey` pointing to a nonexistent object and
that foreign key is included is
:attr:`~django.contrib.admin.ModelAdmin.list_display`, the record will not be
shown in the admin changelist because the Django model is declaring an
integrity constraint that is not implemented at the database level.

How can I customize the functionality of the admin interface?
=============================================================

You've got several options. If you want to piggyback on top of an add/change
form that Django automatically generates, you can attach arbitrary JavaScript
modules to the page via the model's class Admin :ref:`js parameter
<modeladmin-asset-definitions>`. That parameter is a list of URLs, as strings,
pointing to JavaScript modules that will be included within the admin form via
a ``<script>`` tag.

If you want more flexibility than is feasible by tweaking the auto-generated
forms, feel free to write custom views for the admin. The admin is powered by
Django itself, and you can write custom views that hook into the authentication
system, check permissions and do whatever else they need to do.

If you want to customize the look-and-feel of the admin interface, read the
next question.

The dynamically-generated admin site is ugly! How can I change it?
==================================================================

We like it, but if you don't agree, you can modify the admin site's
presentation by editing the CSS stylesheet and/or associated image files. The
site is built using semantic HTML and plenty of CSS hooks, so any changes you'd
like to make should be possible by editing the stylesheet.

.. _admin-browser-support:

What browsers are supported for using the admin?
================================================

The admin provides a fully-functional experience to the recent versions of
modern, web standards compliant browsers. On desktop this means Chrome, Edge,
Firefox, Opera, Safari, and others.

On mobile and tablet devices, the admin provides a responsive experience for
web standards compliant browsers. This includes the major browsers on both
Android and iOS.

Depending on feature support, there *may* be minor stylistic differences
between browsers. These are considered acceptable variations in rendering.

What assistive technologies are supported for using the admin?
==============================================================

The admin is intended to be compatible with a wide range of assistive
technologies, but there are currently many blockers. The support target is all
latest versions of major assistive technologies, including Dragon, JAWS, NVDA,
Orca, TalkBack, Voice Control, VoiceOver iOS, VoiceOver macOS, Windows Contrast
Themes, ZoomText, and screen magnifiers.


================================================
File: docs/faq/contributing.txt
================================================
======================
FAQ: Contributing code
======================

.. _new-contributors-faq:

How can I get started contributing code to Django?
==================================================

Thanks for asking! We've written an entire document devoted to this question.
It's titled :doc:`Contributing to Django </internals/contributing/index>`.

I submitted a bug fix several weeks ago. Why are you ignoring my contribution?
==============================================================================

Don't worry: We're not ignoring you!

It's important to understand there is a difference between "a ticket is being
ignored" and "a ticket has not been attended to yet." Django's ticket system
contains hundreds of open tickets, of various degrees of impact on end-user
functionality, and Django's developers have to review and prioritize.

On top of that: the people who work on Django are all volunteers. As a result,
the amount of time that we have to work on the framework is limited and will
vary from week to week depending on our spare time. If we're busy, we may not
be able to spend as much time on Django as we might want.

The best way to make sure tickets do not get hung up on the way to checkin is
to make it dead easy, even for someone who may not be intimately familiar with
that area of the code, to understand the problem and verify the fix:

* Are there clear instructions on how to reproduce the bug? If this
  touches a dependency (such as Pillow), a contrib module, or a specific
  database, are those instructions clear enough even for someone not
  familiar with it?

* If there are several branches linked to the ticket, is it clear what each one
  does, which ones can be ignored and which matter?

* Does the change include a unit test? If not, is there a very clear
  explanation why not? A test expresses succinctly what the problem is,
  and shows that the branch actually fixes it.

If your contribution is not suitable for inclusion in Django, we won't ignore
it -- we'll close the ticket. So if your ticket is still open, it doesn't mean
we're ignoring you; it just means we haven't had time to look at it yet.

When and how might I remind the team of a change I care about?
==============================================================

A polite, well-timed message in the forum/branch is one way to get attention.
To determine the right time, you need to keep an eye on the schedule. If you
post your message right before a release deadline, you're not likely to get the
sort of attention you require.

Gentle reminders in the ``#contributing-getting-started`` channel in the
`Django Discord server`_ can work.

Another way to get traction is to pull several related tickets together. When
someone sits down to review a bug in an area they haven't touched for
a while, it can take a few minutes to remember all the fine details of how
that area of code works. If you collect several minor bug fixes together into
a similarly themed group, you make an attractive target, as the cost of coming
up to speed on an area of code can be spread over multiple tickets.

Please refrain from emailing anyone personally or repeatedly raising the same
issue over and over again. This sort of behavior will not gain you any
additional attention -- certainly not the attention that you need in order to
get your issue addressed.

.. _`Django Discord server`: https://chat.djangoproject.com

But I've reminded you several times and you keep ignoring my contribution!
==========================================================================

Seriously - we're not ignoring you. If your contribution is not suitable for
inclusion in Django, we will close the ticket. For all the other tickets, we
need to prioritize our efforts, which means that some tickets will be
addressed before others.

One of the criteria that is used to prioritize bug fixes is the number of
people that will likely be affected by a given bug. Bugs that have the
potential to affect many people will generally get priority over those that
are edge cases.

Another reason that a bug might be ignored for a while is if the bug is a
symptom of a larger problem. While we can spend time writing, testing and
applying lots of little changes, sometimes the right solution is to rebuild. If
a rebuild or refactor of a particular component has been proposed or is
underway, you may find that bugs affecting that component will not get as much
attention. Again, this is a matter of prioritizing scarce resources. By
concentrating on the rebuild, we can close all the little bugs at once, and
hopefully prevent other little bugs from appearing in the future.

Whatever the reason, please keep in mind that while you may hit a particular
bug regularly, it doesn't necessarily follow that every single Django user
will hit the same bug. Different users use Django in different ways, stressing
different parts of the code under different conditions. When we evaluate the
relative priorities, we are generally trying to consider the needs of the
entire community, instead of prioritizing the impact on one particular user.
This doesn't mean that we think your problem is unimportant -- just that in the
limited time we have available, we will always err on the side of making 10
people happy rather than making a single person happy.

I'm sure my ticket is absolutely 100% perfect, can I mark it as "Ready For Checkin" myself?
===========================================================================================

Sorry, no. It's always better to get another set of eyes on a ticket. If
you're having trouble getting that second set of eyes, see questions above.


================================================
File: docs/faq/general.txt
================================================
============
FAQ: General
============

Why does this project exist?
============================

Django grew from a very practical need: World Online, a newspaper web
operation, is responsible for building intensive web applications on journalism
deadlines. In the fast-paced newsroom, World Online often has only a matter of
hours to take a complicated web application from concept to public launch.

At the same time, the World Online web developers have consistently been
perfectionists when it comes to following best practices of web development.

In fall 2003, the World Online developers (Adrian Holovaty and Simon Willison)
ditched PHP and began using Python to develop its websites. As they built
intensive, richly interactive sites such as Lawrence.com, they began to extract
a generic web development framework that let them build web applications more
and more quickly. They tweaked this framework constantly, adding improvements
over two years.

In summer 2005, World Online decided to open-source the resulting software,
Django. Django would not be possible without a whole host of open-source
projects -- `Apache`_, `Python`_, and `PostgreSQL`_ to name a few -- and we're
thrilled to be able to give something back to the open-source community.

.. _Apache: https://httpd.apache.org/
.. _Python: https://www.python.org/
.. _PostgreSQL: https://www.postgresql.org/

What does "Django" mean, and how do you pronounce it?
=====================================================

Django is named after `Django Reinhardt`_, a jazz manouche guitarist from the 1930s
to early 1950s. To this day, he's considered one of the best guitarists of all time.

Listen to his music. You'll like it.

Django is pronounced **JANG**-oh. Rhymes with FANG-oh. The "D" is silent.

We've also recorded an `audio clip of the pronunciation`_.

.. _Django Reinhardt: https://en.wikipedia.org/wiki/Django_Reinhardt
.. _audio clip of the pronunciation: https://www.red-bean.com/~adrian/django_pronunciation.mp3

Is Django stable?
=================

Yes, it's quite stable. Companies like Disqus, Instagram, Pinterest, and
Mozilla have been using Django for many years. Sites built on Django have
weathered traffic spikes of over 50 thousand hits per second.

Does Django scale?
==================

Yes. Compared to development time, hardware is cheap, and so Django is
designed to take advantage of as much hardware as you can throw at it.

Django uses a "shared-nothing" architecture, which means you can add hardware
at any level -- database servers, caching servers or web/application servers.

The framework cleanly separates components such as its database layer and
application layer. And it ships with a simple-yet-powerful
:doc:`cache framework </topics/cache>`.

Who's behind this?
==================

Django was originally developed at World Online, the web department of a
newspaper in Lawrence, Kansas, USA. Django's now run by an international
`team of volunteers <https://www.djangoproject.com/foundation/teams/>`_.

How is Django licensed?
=======================

Django is distributed under :source:`the 3-clause BSD license <LICENSE>`. This
is an open source license granting broad permissions to modify and redistribute
Django.

Why does Django include Python's license file?
==============================================

Django includes code from the Python standard library. Python is distributed
under a permissive open source license. :source:`A copy of the Python license
<LICENSE.python>` is included with Django for compliance with Python's terms.

Which sites use Django?
=======================

`BuiltWithDjango.com`_ features a constantly growing list of Django-powered
sites.

.. _BuiltWithDjango.com: https://builtwithdjango.com/projects/

.. _faq-mtv:

Django appears to be a MVC framework, but you call the Controller the "view", and the View the "template". How come you don't use the standard names?
=====================================================================================================================================================

Well, the standard names are debatable.

In our interpretation of MVC, the "view" describes the data that gets presented
to the user. It's not necessarily *how* the data *looks*, but *which* data is
presented. The view describes *which data you see*, not *how you see it.* It's
a subtle distinction.

So, in our case, a "view" is the Python callback function for a particular URL,
because that callback function describes which data is presented.

Furthermore, it's sensible to separate content from presentation -- which is
where templates come in. In Django, a "view" describes which data is presented,
but a view normally delegates to a template, which describes *how* the data is
presented.

Where does the "controller" fit in, then? In Django's case, it's probably the
framework itself: the machinery that sends a request to the appropriate view,
according to the Django URL configuration.

If you're hungry for acronyms, you might say that Django is a "MTV" framework
-- that is, "model", "template", and "view." That breakdown makes much more
sense.

At the end of the day, it comes down to getting stuff done. And, regardless of
how things are named, Django gets stuff done in a way that's most logical to
us.

<Framework X> does <feature Y> -- why doesn't Django?
=====================================================

We're well aware that there are other awesome web frameworks out there, and
we're not averse to borrowing ideas where appropriate. However, Django was
developed precisely because we were unhappy with the status quo, so please be
aware that "because <Framework X> does it" is not going to be sufficient reason
to add a given feature to Django.

Why did you write all of Django from scratch, instead of using other Python libraries?
======================================================================================

When Django was originally written, Adrian and Simon spent quite a bit of time
exploring the various Python web frameworks available.

In our opinion, none of them were completely up to snuff.

We're picky. You might even call us perfectionists. (With deadlines.)

Over time, we stumbled across open-source libraries that did things we'd
already implemented. It was reassuring to see other people solving similar
problems in similar ways, but it was too late to integrate outside code: We'd
already written, tested and implemented our own framework bits in several
production settings -- and our own code met our needs delightfully.

In most cases, however, we found that existing frameworks/tools inevitably had
some sort of fundamental, fatal flaw that made us squeamish. No tool fit our
philosophies 100%.

Like we said: We're picky.

We've documented our philosophies on the
:doc:`design philosophies page </misc/design-philosophies>`.

Is Django a content-management-system (CMS)?
============================================

No, Django is not a CMS, or any sort of "turnkey product" in and of itself.
It's a web framework; it's a programming tool that lets you build websites.

For example, it doesn't make much sense to compare Django to something like
Drupal_, because Django is something you use to *create* things like Drupal.

Yes, Django's automatic admin site is fantastic and timesaving -- but the admin
site is one module of Django the framework. Furthermore, although Django has
special conveniences for building "CMS-y" apps, that doesn't mean it's not just
as appropriate for building "non-CMS-y" apps (whatever that means!).

.. _Drupal: https://www.drupal.org/

How can I download the Django documentation to read it offline?
===============================================================

The Django docs are available in the ``docs`` directory of each Django tarball
release. These docs are in reST (reStructuredText) format, and each text file
corresponds to a web page on the official Django site.

Because the documentation is :source:`stored in revision control <docs>`, you
can browse documentation changes just like you can browse code changes.

Technically, the docs on Django's site are generated from the latest development
versions of those reST documents, so the docs on the Django site may offer more
information than the docs that come with the latest Django release.

How do I cite Django?
=====================

It's difficult to give an official citation format, for two reasons: citation
formats can vary wildly between publications, and citation standards for
software are still a matter of some debate.

For example, `APA style`_,  would dictate something like:

.. code-block:: text

    Django (Version 1.5) [Computer Software]. (2013). Retrieved from https://www.djangoproject.com/.

However, the only true guide is what your publisher will accept, so get a copy
of those guidelines and fill in the gaps as best you can.

If your referencing style guide requires a publisher name, use "Django Software
Foundation".

If you need a publishing location, use "Lawrence, Kansas".

If you need a web address, use https://www.djangoproject.com/.

If you need a name, just use "Django", without any tagline.

If you need a publication date, use the year of release of the version you're
referencing (e.g., 2013 for v1.5)

.. _APA style: https://apastyle.apa.org/


================================================
File: docs/faq/help.txt
================================================
=================
FAQ: Getting Help
=================

How do I do X? Why doesn't Y work? Where can I go to get help?
==============================================================

First, please check if your question is answered on the :doc:`FAQ
</faq/index>`. Also, search for answers using your favorite search engine, and
in `the forum`_.

.. _`the forum`: https://forum.djangoproject.com/

If you can't find an answer, please take a few minutes to formulate your
question well. Explaining the problems you are facing clearly will help others
help you. See the StackOverflow guide on `asking good questions`_.

.. _`asking good questions`: https://stackoverflow.com/help/how-to-ask

Then, please post it in one of the following channels:

* The Django Forum section `"Using Django"`_. This is for web-based
  discussions.
* The |django-users| mailing list. This is for email-based discussions.
* The `Django Discord server`_ for chat-based discussions.

.. _`"Using Django"`: https://forum.djangoproject.com/c/users/6
.. _`Django Discord server`: https://chat.djangoproject.com

In all these channels please abide by the `Django Code of Conduct`_. In
summary, being friendly and patient, considerate, respectful, and careful in
your choice of words.

.. _Django Code of Conduct: https://www.djangoproject.com/conduct/

.. _message-does-not-appear-on-django-users:

Why hasn't my message appeared on *django-users*?
=================================================

|django-users| has a lot of subscribers. This is good for the community, as
it means many people are available to contribute answers to questions.
Unfortunately, it also means that |django-users| is an attractive target for
spammers.

In order to combat the spam problem, when you join the |django-users| mailing
list, we manually moderate the first message you send to the list. This means
that spammers get caught, but it also means that your first question to the
list might take a little longer to get answered. We apologize for any
inconvenience that this policy may cause.

Nobody answered my question! What should I do?
==============================================

Try making your question more specific, or provide a better example of your
problem.

As with most open-source projects, the folks on these channels are volunteers.
If nobody has answered your question, it may be because nobody knows the
answer, it may be because nobody can understand the question, or it may be that
everybody that can help is busy.

You can also try asking on a different channel. But please don't post your
question in all three channels in quick succession.

You might notice we have a second mailing list, called |django-developers|.
This list is for discussion of the development of Django itself. Please don't
email support questions to this mailing list. Asking a tech support question
there is considered impolite, and you will likely be directed to ask on
|django-users|.

I think I've found a bug! What should I do?
===========================================

Detailed instructions on how to handle a potential bug can be found in our
:ref:`Guide to contributing to Django <reporting-bugs>`.

I think I've found a security problem! What should I do?
========================================================

If you think you've found a security problem with Django, please send a message
to security@djangoproject.com. This is a private list only open to long-time,
highly trusted Django developers, and its archives are not publicly readable.

Due to the sensitive nature of security issues, we ask that if you think you
have found a security problem, *please* don't post a message on the forum, the
Discord server, IRC, or one of the public mailing lists. Django has a
:ref:`policy for handling security issues <reporting-security-issues>`;
while a defect is outstanding, we would like to minimize any damage that
could be inflicted through public knowledge of that defect.


================================================
File: docs/faq/index.txt
================================================
==========
Django FAQ
==========

.. toctree::
   :maxdepth: 2

   general
   install
   usage
   help
   models
   admin
   contributing
   troubleshooting


================================================
File: docs/faq/install.txt
================================================
=================
FAQ: Installation
=================

How do I get started?
=====================

#. `Download the code`_.
#. Install Django (read the :doc:`installation guide </intro/install>`).
#. Walk through the :doc:`tutorial </intro/tutorial01>`.
#. Check out the rest of the :doc:`documentation </index>`, and `ask questions`_ if you
   run into trouble.

.. _`Download the code`: https://www.djangoproject.com/download/
.. _ask questions: https://www.djangoproject.com/community/

What are Django's prerequisites?
================================

Django requires Python. See the table in the next question for the versions of
Python that work with each version of Django. Other Python libraries may be
required for some use cases, but you'll receive an error about them as they're
needed.

For a development environment -- if you just want to experiment with Django --
you don't need to have a separate web server installed or database server.

Django comes with its own :djadmin:`lightweight development server<runserver>`.
For a production environment, Django follows the WSGI spec, :pep:`3333`, which
means it can run on a variety of web servers. See :doc:`Deploying Django
</howto/deployment/index>` for more information.

Django runs `SQLite`_ by default, which is included in Python installations.
For a production environment, we recommend PostgreSQL_; but we also officially
support MariaDB_, MySQL_, `SQLite`_, and Oracle_. See :doc:`Supported Databases
</ref/databases>` for more information.

.. _Python: https://www.python.org/
.. _PostgreSQL: https://www.postgresql.org/
.. _MariaDB: https://mariadb.org/
.. _MySQL: https://www.mysql.com/
.. _`SQLite`: https://www.sqlite.org/
.. _Oracle: https://www.oracle.com/

.. _faq-python-version-support:

What Python version can I use with Django?
==========================================

============== ===============
Django version Python versions
============== ===============
4.2            3.8, 3.9, 3.10, 3.11, 3.12 (added in 4.2.8)
5.0            3.10, 3.11, 3.12
5.1            3.10, 3.11, 3.12, 3.13 (added in 5.1.3)
5.2            3.10, 3.11, 3.12, 3.13
6.0            3.12, 3.13
============== ===============

For each version of Python, only the latest micro release (A.B.C) is officially
supported. You can find the latest micro version for each series on the `Python
download page <https://www.python.org/downloads/>`_.

We will support a Python version up to and including the first Django LTS
release whose security support ends after security support for that version of
Python ends. For example, Python 3.9 security support ends in October 2025 and
Django 4.2 LTS security support ends in April 2026. Therefore Django 4.2 is the
last version to support Python 3.9.

What Python version should I use with Django?
=============================================

Since newer versions of Python are often faster, have more features, and are
better supported, the latest version of Python 3 is recommended.

You don't lose anything in Django by using an older release, but you don't take
advantage of the improvements and optimizations in newer Python releases.
Third-party applications for use with Django are free to set their own version
requirements.

Should I use the stable version or development version?
=======================================================

Generally, if you're using code in production, you should be using a
stable release. The Django project publishes a full stable release
every eight months or so, with bugfix updates in between. These stable
releases contain the API that is covered by our backwards
compatibility guarantees; if you write code against stable releases,
you shouldn't have any problems upgrading when the next official
version is released.


================================================
File: docs/faq/models.txt
================================================
=========================
FAQ: Databases and models
=========================

.. _faq-see-raw-sql-queries:

How can I see the raw SQL queries Django is running?
====================================================

Make sure your Django :setting:`DEBUG` setting is set to ``True``.
Then do this:

.. code-block:: pycon

    >>> from django.db import connection
    >>> connection.queries
    [{'sql': 'SELECT polls_polls.id, polls_polls.question, polls_polls.pub_date FROM polls_polls',
    'time': '0.002'}]

``connection.queries`` is only available if :setting:`DEBUG` is ``True``.
It's a list of dictionaries in order of query execution. Each dictionary has
the following:

* ``sql`` - The raw SQL statement
* ``time`` - How long the statement took to execute, in seconds.

``connection.queries`` includes all SQL statements -- INSERTs, UPDATES,
SELECTs, etc. Each time your app hits the database, the query will be recorded.

If you are using :doc:`multiple databases</topics/db/multi-db>`, you can use the
same interface on each member of the ``connections`` dictionary:

.. code-block:: pycon

    >>> from django.db import connections
    >>> connections["my_db_alias"].queries

If you need to clear the query list manually at any point in your functions,
call ``reset_queries()``, like this::

    from django.db import reset_queries

    reset_queries()

Can I use Django with a preexisting database?
=============================================

Yes. See :doc:`Integrating with a legacy database </howto/legacy-databases>`.

If I make changes to a model, how do I update the database?
===========================================================

Take a look at Django's support for :mod:`schema migrations
<django.db.migrations>`.

If you don't mind clearing data, your project's ``manage.py`` utility has a
:djadmin:`flush` option to reset the database to the state it was in
immediately after :djadmin:`migrate` was executed.

Do Django models support multiple-column primary keys?
======================================================

No. Only single-column primary keys are supported.

But this isn't an issue in practice, because there's nothing stopping you from
adding other constraints (using the ``unique_together`` model option or
creating the constraint directly in your database), and enforcing the
uniqueness at that level. Single-column primary keys are needed for things such
as the admin interface to work; e.g., you need a single value to specify
an object to edit or delete.

Does Django support NoSQL databases?
====================================

NoSQL databases are not officially supported by Django itself. There are,
however, a number of side projects and forks which allow NoSQL functionality in
Django.

You can take a look on `the wiki page`_ which discusses some projects.

.. _the wiki page: https://code.djangoproject.com/wiki/NoSqlSupport

How do I add database-specific options to my CREATE TABLE statements, such as specifying MyISAM as the table type?
==================================================================================================================

We try to avoid adding special cases in the Django code to accommodate all the
database-specific options such as table type, etc. If you'd like to use any of
these options, create a migration with a
:class:`~django.db.migrations.operations.RunSQL` operation that contains
``ALTER TABLE`` statements that do what you want to do.

For example, if you're using MySQL and want your tables to use the MyISAM table
type, use the following SQL:

.. code-block:: sql

    ALTER TABLE myapp_mytable ENGINE=MyISAM;


================================================
File: docs/faq/troubleshooting.txt
================================================
===============
Troubleshooting
===============

This page contains some advice about errors and problems commonly encountered
during the development of Django applications.

.. _troubleshooting-django-admin:

Problems running ``django-admin``
=================================

``command not found: django-admin``
-----------------------------------

:doc:`django-admin </ref/django-admin>` should be on your system path if you
installed Django via ``pip``. If it's not in your path, ensure you have your
virtual environment activated and you can try running the equivalent command
``python -m django``.

macOS permissions
-----------------

If you're using macOS, you may see the message "permission denied" when
you try to run ``django-admin``. This is because, on Unix-based systems like
macOS, a file must be marked as "executable" before it can be run as a program.
To do this, open Terminal.app and navigate (using the ``cd`` command) to the
directory where :doc:`django-admin </ref/django-admin>` is installed, then
run the command ``sudo chmod +x django-admin``.

Miscellaneous
=============

I'm getting a ``UnicodeDecodeError``. What am I doing wrong?
------------------------------------------------------------

This class of errors happen when a bytestring containing non-ASCII sequences is
transformed into a Unicode string and the specified encoding is incorrect. The
output generally looks like this:

.. code-block:: pytb

    UnicodeDecodeError: 'ascii' codec can't decode byte 0x?? in position ?:
    ordinal not in range(128)

The resolution mostly depends on the context, however here are two common
pitfalls producing this error:

* Your system locale may be a default ASCII locale, like the "C" locale on
  UNIX-like systems (can be checked by the ``locale`` command). If it's the
  case, please refer to your system documentation to learn how you can change
  this to a UTF-8 locale.

Related resources:

* :doc:`Unicode in Django </ref/unicode>`
* https://wiki.python.org/moin/UnicodeDecodeError


================================================
File: docs/faq/usage.txt
================================================
=================
FAQ: Using Django
=================

Why do I get an error about importing :envvar:`DJANGO_SETTINGS_MODULE`?
=======================================================================

Make sure that:

* The environment variable :envvar:`DJANGO_SETTINGS_MODULE` is set to a
  fully-qualified Python module (i.e. ``mysite.settings``).

* Said module is on ``sys.path`` (``import mysite.settings`` should work).

* The module doesn't contain syntax errors.

I can't stand your template language. Do I have to use it?
==========================================================

We happen to think our template engine is the best thing since chunky bacon,
but we recognize that choosing a template language runs close to religion.
There's nothing about Django that requires using the template language, so
if you're attached to Jinja2, Mako, or whatever, feel free to use those.

Do I have to use your model/database layer?
===========================================

Nope. Just like the template system, the model/database layer is decoupled from
the rest of the framework.

The one exception is: If you use a different database library, you won't get to
use Django's automatically-generated admin site. That app is coupled to the
Django database layer.

How do I use image and file fields?
===================================

Using a :class:`~django.db.models.FileField` or an
:class:`~django.db.models.ImageField` in a model takes a few steps:

#. In your settings file, you'll need to define :setting:`MEDIA_ROOT` as
   the full path to a directory where you'd like Django to store uploaded
   files. (For performance, these files are not stored in the database.)
   Define :setting:`MEDIA_URL` as the base public URL of that directory.
   Make sure that this directory is writable by the web server's user
   account.

#. Add the :class:`~django.db.models.FileField` or
   :class:`~django.db.models.ImageField` to your model, defining the
   :attr:`~django.db.models.FileField.upload_to` option to specify a
   subdirectory of :setting:`MEDIA_ROOT` to use for uploaded files.

#. All that will be stored in your database is a path to the file
   (relative to :setting:`MEDIA_ROOT`). You'll most likely want to use the
   convenience :attr:`~django.db.models.fields.files.FieldFile.url` attribute
   provided by Django. For example, if your
   :class:`~django.db.models.ImageField` is called ``mug_shot``, you can get
   the absolute path to your image in a template with
   ``{{ object.mug_shot.url }}``.

How do I make a variable available to all my templates?
=======================================================

Sometimes your templates all need the same thing. A common example would be
dynamically generated menus. At first glance, it seems logical to add a common
dictionary to the template context.

The best way to do this in Django is to use a ``RequestContext``. Details on
how to do this are here: :ref:`subclassing-context-requestcontext`.


================================================
File: docs/howto/auth-remote-user.txt
================================================
=========================================
How to authenticate using ``REMOTE_USER``
=========================================

This document describes how to make use of external authentication sources
(where the web server sets the ``REMOTE_USER`` environment variable) in your
Django applications.  This type of authentication solution is typically seen on
intranet sites, with single sign-on solutions such as IIS and Integrated
Windows Authentication or Apache and `mod_authnz_ldap`_, `CAS`_, `WebAuth`_,
`mod_auth_sspi`_, etc.

.. _mod_authnz_ldap: https://httpd.apache.org/docs/current/mod/mod_authnz_ldap.html
.. _CAS: https://www.apereo.org/projects/cas
.. _WebAuth: https://uit.stanford.edu/service/authentication
.. _mod_auth_sspi: https://sourceforge.net/projects/mod-auth-sspi

When the web server takes care of authentication it typically sets the
``REMOTE_USER`` environment variable for use in the underlying application.  In
Django, ``REMOTE_USER`` is made available in the :attr:`request.META
<django.http.HttpRequest.META>` attribute.  Django can be configured to make
use of the ``REMOTE_USER`` value using the ``RemoteUserMiddleware``
or ``PersistentRemoteUserMiddleware``, and
:class:`~django.contrib.auth.backends.RemoteUserBackend` classes found in
:mod:`django.contrib.auth`.

Configuration
=============

First, you must add the
:class:`django.contrib.auth.middleware.RemoteUserMiddleware` to the
:setting:`MIDDLEWARE` setting **after** the
:class:`django.contrib.auth.middleware.AuthenticationMiddleware`::

    MIDDLEWARE = [
        "...",
        "django.contrib.auth.middleware.AuthenticationMiddleware",
        "django.contrib.auth.middleware.RemoteUserMiddleware",
        "...",
    ]

Next, you must replace the :class:`~django.contrib.auth.backends.ModelBackend`
with :class:`~django.contrib.auth.backends.RemoteUserBackend` in the
:setting:`AUTHENTICATION_BACKENDS` setting::

    AUTHENTICATION_BACKENDS = [
        "django.contrib.auth.backends.RemoteUserBackend",
    ]

With this setup, ``RemoteUserMiddleware`` will detect the username in
``request.META['REMOTE_USER']`` and will authenticate and auto-login that user
using the :class:`~django.contrib.auth.backends.RemoteUserBackend`.

Be aware that this particular setup disables authentication with the default
``ModelBackend``. This means that if the ``REMOTE_USER`` value is not set
then the user is unable to log in, even using Django's admin interface.
Adding ``'django.contrib.auth.backends.ModelBackend'`` to the
``AUTHENTICATION_BACKENDS`` list will use ``ModelBackend`` as a fallback
if ``REMOTE_USER`` is absent, which will solve these issues.

Django's user management, such as the views in ``contrib.admin`` and
the :djadmin:`createsuperuser` management command, doesn't integrate with
remote users. These interfaces work with users stored in the database
regardless of ``AUTHENTICATION_BACKENDS``.

.. note::

    Since the ``RemoteUserBackend`` inherits from ``ModelBackend``, you will
    still have all of the same permissions checking that is implemented in
    ``ModelBackend``.

    Users with :attr:`is_active=False
    <django.contrib.auth.models.User.is_active>` won't be allowed to
    authenticate. Use
    :class:`~django.contrib.auth.backends.AllowAllUsersRemoteUserBackend` if
    you want to allow them to.

If your authentication mechanism uses a custom HTTP header and not
``REMOTE_USER``, you can subclass ``RemoteUserMiddleware`` and set the
``header`` attribute to the desired ``request.META`` key.  For example::

    from django.contrib.auth.middleware import RemoteUserMiddleware


    class CustomHeaderMiddleware(RemoteUserMiddleware):
        header = "HTTP_AUTHUSER"

.. warning::

    Be very careful if using a ``RemoteUserMiddleware`` subclass with a custom
    HTTP header. You must be sure that your front-end web server always sets or
    strips that header based on the appropriate authentication checks, never
    permitting an end-user to submit a fake (or "spoofed") header value. Since
    the HTTP headers ``X-Auth-User`` and ``X-Auth_User`` (for example) both
    normalize to the ``HTTP_X_AUTH_USER`` key in ``request.META``, you must
    also check that your web server doesn't allow a spoofed header using
    underscores in place of dashes.

    This warning doesn't apply to ``RemoteUserMiddleware`` in its default
    configuration with ``header = 'REMOTE_USER'``, since a key that doesn't
    start with ``HTTP_`` in ``request.META`` can only be set by your WSGI
    server, not directly from an HTTP request header.

If you need more control, you can create your own authentication backend
that inherits from :class:`~django.contrib.auth.backends.RemoteUserBackend` and
override one or more of its attributes and methods.

.. _persistent-remote-user-middleware-howto:

Using ``REMOTE_USER`` on login pages only
=========================================

The ``RemoteUserMiddleware`` authentication middleware assumes that the HTTP
request header ``REMOTE_USER`` is present with all authenticated requests. That
might be expected and practical when Basic HTTP Auth with ``htpasswd`` or
similar mechanisms are used, but with Negotiate (GSSAPI/Kerberos) or other
resource intensive authentication methods, the authentication in the front-end
HTTP server is usually only set up for one or a few login URLs, and after
successful authentication, the application is supposed to maintain the
authenticated session itself.

:class:`~django.contrib.auth.middleware.PersistentRemoteUserMiddleware`
provides support for this use case. It will maintain the authenticated session
until explicit logout by the user. The class can be used as a drop-in
replacement of :class:`~django.contrib.auth.middleware.RemoteUserMiddleware`
in the documentation above.


================================================
File: docs/howto/csrf.txt
================================================
.. _using-csrf:

===================================
How to use Django's CSRF protection
===================================

To take advantage of CSRF protection in your views, follow these steps:

#. The CSRF middleware is activated by default in the :setting:`MIDDLEWARE`
   setting. If you override that setting, remember that
   ``'django.middleware.csrf.CsrfViewMiddleware'`` should come before any view
   middleware that assume that CSRF attacks have been dealt with.

   If you disabled it, which is not recommended, you can use
   :func:`~django.views.decorators.csrf.csrf_protect` on particular views
   you want to protect (see below).

#. In any template that uses a POST form, use the :ttag:`csrf_token` tag inside
   the ``<form>`` element if the form is for an internal URL, e.g.:

   .. code-block:: html+django

       <form method="post">{% csrf_token %}

   This should not be done for POST forms that target external URLs, since
   that would cause the CSRF token to be leaked, leading to a vulnerability.

#. In the corresponding view functions, ensure that
   :class:`~django.template.RequestContext` is used to render the response so
   that ``{% csrf_token %}`` will work properly. If you're using the
   :func:`~django.shortcuts.render` function, generic views, or contrib apps,
   you are covered already since these all use ``RequestContext``.

.. _csrf-ajax:

Using CSRF protection with AJAX
===============================

While the above method can be used for AJAX POST requests, it has some
inconveniences: you have to remember to pass the CSRF token in as POST data with
every POST request. For this reason, there is an alternative method: on each
XMLHttpRequest, set a custom ``X-CSRFToken`` header (as specified by the
:setting:`CSRF_HEADER_NAME` setting) to the value of the CSRF token. This is
often easier because many JavaScript frameworks provide hooks that allow
headers to be set on every request.

First, you must get the CSRF token. How to do that depends on whether or not
the :setting:`CSRF_USE_SESSIONS` and :setting:`CSRF_COOKIE_HTTPONLY` settings
are enabled.

.. _acquiring-csrf-token-from-cookie:

Acquiring the token if :setting:`CSRF_USE_SESSIONS` and :setting:`CSRF_COOKIE_HTTPONLY` are ``False``
-----------------------------------------------------------------------------------------------------

The recommended source for the token is the ``csrftoken`` cookie, which will be
set if you've enabled CSRF protection for your views as outlined above.

The CSRF token cookie is named ``csrftoken`` by default, but you can control
the cookie name via the :setting:`CSRF_COOKIE_NAME` setting.

You can acquire the token like this:

.. code-block:: javascript

    function getCookie(name) {
        let cookieValue = null;
        if (document.cookie && document.cookie !== '') {
            const cookies = document.cookie.split(';');
            for (let i = 0; i < cookies.length; i++) {
                const cookie = cookies[i].trim();
                // Does this cookie string begin with the name we want?
                if (cookie.substring(0, name.length + 1) === (name + '=')) {
                    cookieValue = decodeURIComponent(cookie.substring(name.length + 1));
                    break;
                }
            }
        }
        return cookieValue;
    }
    const csrftoken = getCookie('csrftoken');

The above code could be simplified by using the `JavaScript Cookie library
<https://github.com/js-cookie/js-cookie/>`_ to replace ``getCookie``:

.. code-block:: javascript

    const csrftoken = Cookies.get('csrftoken');

.. note::

    The CSRF token is also present in the DOM in a masked form, but only if
    explicitly included using :ttag:`csrf_token` in a template. The cookie
    contains the canonical, unmasked token. The
    :class:`~django.middleware.csrf.CsrfViewMiddleware` will accept either.
    However, in order to protect against `BREACH`_ attacks, it's recommended to
    use a masked token.

.. warning::

    If your view is not rendering a template containing the :ttag:`csrf_token`
    template tag, Django might not set the CSRF token cookie. This is common in
    cases where forms are dynamically added to the page. To address this case,
    Django provides a view decorator which forces setting of the cookie:
    :func:`~django.views.decorators.csrf.ensure_csrf_cookie`.

.. _BREACH: https://www.breachattack.com/

.. _acquiring-csrf-token-from-html:

Acquiring the token if :setting:`CSRF_USE_SESSIONS` or :setting:`CSRF_COOKIE_HTTPONLY` is ``True``
--------------------------------------------------------------------------------------------------

If you activate :setting:`CSRF_USE_SESSIONS` or
:setting:`CSRF_COOKIE_HTTPONLY`, you must include the CSRF token in your HTML
and read the token from the DOM with JavaScript:

.. code-block:: html+django

    {% csrf_token %}
    <script>
    const csrftoken = document.querySelector('[name=csrfmiddlewaretoken]').value;
    </script>

Setting the token on the AJAX request
-------------------------------------

Finally, you'll need to set the header on your AJAX request. Using the
`fetch()`_ API:

.. code-block:: javascript

    const request = new Request(
        /* URL */,
        {
            method: 'POST',
            headers: {'X-CSRFToken': csrftoken},
            mode: 'same-origin' // Do not send CSRF token to another domain.
        }
    );
    fetch(request).then(function(response) {
        // ...
    });

.. _fetch(): https://developer.mozilla.org/en-US/docs/Web/API/fetch

Using CSRF protection in Jinja2 templates
=========================================

Django's :class:`~django.template.backends.jinja2.Jinja2` template backend
adds ``{{ csrf_input }}`` to the context of all templates which is equivalent
to ``{% csrf_token %}`` in the Django template language. For example:

.. code-block:: html+jinja

    <form method="post">{{ csrf_input }}

Using the decorator method
==========================

Rather than adding ``CsrfViewMiddleware`` as a blanket protection, you can use
the :func:`~django.views.decorators.csrf.csrf_protect` decorator, which has
exactly the same functionality, on particular views that need the protection.
It must be used **both** on views that insert the CSRF token in the output, and
on those that accept the POST form data. (These are often the same view
function, but not always).

Use of the decorator by itself is **not recommended**, since if you forget to
use it, you will have a security hole. The 'belt and braces' strategy of using
both is fine, and will incur minimal overhead.

.. _csrf-rejected-requests:

Handling rejected requests
==========================

By default, a '403 Forbidden' response is sent to the user if an incoming
request fails the checks performed by ``CsrfViewMiddleware``. This should
usually only be seen when there is a genuine Cross Site Request Forgery, or
when, due to a programming error, the CSRF token has not been included with a
POST form.

The error page, however, is not very friendly, so you may want to provide your
own view for handling this condition. To do this, set the
:setting:`CSRF_FAILURE_VIEW` setting.

CSRF failures are logged as warnings to the :ref:`django.security.csrf
<django-security-logger>` logger.

Using CSRF protection with caching
==================================

If the :ttag:`csrf_token` template tag is used by a template (or the
``get_token`` function is called some other way), ``CsrfViewMiddleware`` will
add a cookie and a ``Vary: Cookie`` header to the response. This means that the
middleware will play well with the cache middleware if it is used as instructed
(``UpdateCacheMiddleware`` goes before all other middleware).

However, if you use cache decorators on individual views, the CSRF middleware
will not yet have been able to set the Vary header or the CSRF cookie, and the
response will be cached without either one. In this case, on any views that
will require a CSRF token to be inserted you should use the
:func:`django.views.decorators.csrf.csrf_protect` decorator first::

  from django.views.decorators.cache import cache_page
  from django.views.decorators.csrf import csrf_protect


  @cache_page(60 * 15)
  @csrf_protect
  def my_view(request): ...

If you are using class-based views, you can refer to :ref:`Decorating
class-based views<decorating-class-based-views>`.

Testing and CSRF protection
===========================

The ``CsrfViewMiddleware`` will usually be a big hindrance to testing view
functions, due to the need for the CSRF token which must be sent with every POST
request. For this reason, Django's HTTP client for tests has been modified to
set a flag on requests which relaxes the middleware and the ``csrf_protect``
decorator so that they no longer rejects requests. In every other respect
(e.g. sending cookies etc.), they behave the same.

If, for some reason, you *want* the test client to perform CSRF
checks, you can create an instance of the test client that enforces
CSRF checks:

.. code-block:: pycon

    >>> from django.test import Client
    >>> csrf_client = Client(enforce_csrf_checks=True)

Edge cases
==========

Certain views can have unusual requirements that mean they don't fit the normal
pattern envisaged here. A number of utilities can be useful in these
situations. The scenarios they might be needed in are described in the following
section.

Disabling CSRF protection for just a few views
----------------------------------------------

Most views requires CSRF protection, but a few do not.

Solution: rather than disabling the middleware and applying ``csrf_protect`` to
all the views that need it, enable the middleware and use
:func:`~django.views.decorators.csrf.csrf_exempt`.

Setting the token when ``CsrfViewMiddleware.process_view()`` is not used
------------------------------------------------------------------------

There are cases when ``CsrfViewMiddleware.process_view`` may not have run
before your view is run - 404 and 500 handlers, for example - but you still
need the CSRF token in a form.

Solution: use :func:`~django.views.decorators.csrf.requires_csrf_token`

Including the CSRF token in an unprotected view
-----------------------------------------------

There may be some views that are unprotected and have been exempted by
``csrf_exempt``, but still need to include the CSRF token.

Solution: use :func:`~django.views.decorators.csrf.csrf_exempt` followed by
:func:`~django.views.decorators.csrf.requires_csrf_token`. (i.e. ``requires_csrf_token``
should be the innermost decorator).

Protecting a view for only one path
-----------------------------------

A view needs CSRF protection under one set of conditions only, and mustn't have
it for the rest of the time.

Solution: use :func:`~django.views.decorators.csrf.csrf_exempt` for the whole
view function, and :func:`~django.views.decorators.csrf.csrf_protect` for the
path within it that needs protection. Example::

    from django.views.decorators.csrf import csrf_exempt, csrf_protect


    @csrf_exempt
    def my_view(request):
        @csrf_protect
        def protected_path(request):
            do_something()

        if some_condition():
            return protected_path(request)
        else:
            do_something_else()

Protecting a page that uses AJAX without an HTML form
-----------------------------------------------------

A page makes a POST request via AJAX, and the page does not have an HTML form
with a :ttag:`csrf_token` that would cause the required CSRF cookie to be sent.

Solution: use :func:`~django.views.decorators.csrf.ensure_csrf_cookie` on the
view that sends the page.

CSRF protection in reusable applications
========================================

Because it is possible for the developer to turn off the ``CsrfViewMiddleware``,
all relevant views in contrib apps use the ``csrf_protect`` decorator to ensure
the security of these applications against CSRF. It is recommended that the
developers of other reusable apps that want the same guarantees also use the
``csrf_protect`` decorator on their views.


================================================
File: docs/howto/custom-file-storage.txt
================================================
===================================
How to write a custom storage class
===================================

.. currentmodule:: django.core.files.storage

If you need to provide custom file storage -- a common example is storing files
on some remote system -- you can do so by defining a custom storage class.
You'll need to follow these steps:

#. Your custom storage system must be a subclass of
   ``django.core.files.storage.Storage``::

        from django.core.files.storage import Storage


        class MyStorage(Storage): ...

#. Django must be able to instantiate your storage system without any arguments.
   This means that any settings should be taken from ``django.conf.settings``::

        from django.conf import settings
        from django.core.files.storage import Storage


        class MyStorage(Storage):
            def __init__(self, option=None):
                if not option:
                    option = settings.CUSTOM_STORAGE_OPTIONS
                ...

#. Your storage class must implement the :meth:`_open()` and :meth:`_save()`
   methods, along with any other methods appropriate to your storage class. See
   below for more on these methods.

   In addition, if your class provides local file storage, it must override
   the ``path()`` method.

#. Your storage class must be :ref:`deconstructible <custom-deconstruct-method>`
   so it can be serialized when it's used on a field in a migration. As long
   as your field has arguments that are themselves
   :ref:`serializable <migration-serializing>`, you can use the
   ``django.utils.deconstruct.deconstructible`` class decorator for this
   (that's what Django uses on FileSystemStorage).

By default, the following methods raise ``NotImplementedError`` and will
typically have to be overridden:

* :meth:`Storage.delete`
* :meth:`Storage.exists`
* :meth:`Storage.listdir`
* :meth:`Storage.size`
* :meth:`Storage.url`

Note however that not all these methods are required and may be deliberately
omitted. As it happens, it is possible to leave each method unimplemented and
still have a working Storage.

By way of example, if listing the contents of certain storage backends turns
out to be expensive, you might decide not to implement ``Storage.listdir()``.

Another example would be a backend that only handles writing to files. In this
case, you would not need to implement any of the above methods.

Ultimately, which of these methods are implemented is up to you. Leaving some
methods unimplemented will result in a partial (possibly broken) interface.

You'll also usually want to use hooks specifically designed for custom storage
objects. These are:

.. method:: _open(name, mode='rb')

**Required**.

Called by ``Storage.open()``, this is the actual mechanism the storage class
uses to open the file. This must return a ``File`` object, though in most cases,
you'll want to return some subclass here that implements logic specific to the
backend storage system. The :exc:`FileNotFoundError` exception should be raised
when a file doesn't exist.

.. method:: _save(name, content)

Called by ``Storage.save()``. The ``name`` will already have gone through
``get_valid_name()`` and ``get_available_name()``, and the ``content`` will be a
``File`` object itself.

Should return the actual name of the file saved (usually the ``name`` passed
in, but if the storage needs to change the file name return the new name
instead).

.. method:: get_valid_name(name)

Returns a filename suitable for use with the underlying storage system. The
``name`` argument passed to this method is either the original filename sent to
the server or, if ``upload_to`` is a callable, the filename returned by that
method after any path information is removed. Override this to customize how
non-standard characters are converted to safe filenames.

The code provided on ``Storage`` retains only alpha-numeric characters, periods
and underscores from the original filename, removing everything else.

.. method:: get_alternative_name(file_root, file_ext)

Returns an alternative filename based on the ``file_root`` and ``file_ext``
parameters. By default, an underscore plus a random 7 character alphanumeric
string is appended to the filename before the extension.

.. method:: get_available_name(name, max_length=None)

Returns a filename that is available in the storage mechanism, possibly taking
the provided filename into account. The ``name`` argument passed to this method
will have already cleaned to a filename valid for the storage system, according
to the ``get_valid_name()`` method described above.

The length of the filename will not exceed ``max_length``, if provided. If a
free unique filename cannot be found, a :exc:`SuspiciousFileOperation
<django.core.exceptions.SuspiciousOperation>` exception is raised.

If a file with ``name`` already exists, ``get_alternative_name()`` is called to
obtain an alternative name.

.. _using-custom-storage-engine:

Use your custom storage engine
==============================

The first step to using your custom storage with Django is to tell Django about
the file storage backend you'll be using. This is done using the
:setting:`STORAGES` setting. This setting maps storage aliases, which are a way
to refer to a specific storage throughout Django, to a dictionary of settings
for that specific storage backend. The settings in the inner dictionaries are
described fully in the :setting:`STORAGES` documentation.

Storages are then accessed by alias from the
:data:`django.core.files.storage.storages` dictionary::

    from django.core.files.storage import storages

    example_storage = storages["example"]


================================================
File: docs/howto/custom-lookups.txt
================================================
===========================
How to write custom lookups
===========================

.. currentmodule:: django.db.models

Django offers a wide variety of :ref:`built-in lookups <field-lookups>` for
filtering (for example, ``exact`` and ``icontains``). This documentation
explains how to write custom lookups and how to alter the working of existing
lookups. For the API references of lookups, see the :doc:`/ref/models/lookups`.

A lookup example
================

Let's start with a small custom lookup. We will write a custom lookup ``ne``
which works opposite to ``exact``. ``Author.objects.filter(name__ne='Jack')``
will translate to the SQL:

.. code-block:: sql

  "author"."name" <> 'Jack'

This SQL is backend independent, so we don't need to worry about different
databases.

There are two steps to making this work. Firstly we need to implement the
lookup, then we need to tell Django about it::

  from django.db.models import Lookup


  class NotEqual(Lookup):
      lookup_name = "ne"

      def as_sql(self, compiler, connection):
          lhs, lhs_params = self.process_lhs(compiler, connection)
          rhs, rhs_params = self.process_rhs(compiler, connection)
          params = lhs_params + rhs_params
          return "%s <> %s" % (lhs, rhs), params

To register the ``NotEqual`` lookup we will need to call ``register_lookup`` on
the field class we want the lookup to be available for. In this case, the lookup
makes sense on all ``Field`` subclasses, so we register it with ``Field``
directly::

  from django.db.models import Field

  Field.register_lookup(NotEqual)

Lookup registration can also be done using a decorator pattern::

    from django.db.models import Field


    @Field.register_lookup
    class NotEqualLookup(Lookup): ...

We can now use ``foo__ne`` for any field ``foo``. You will need to ensure that
this registration happens before you try to create any querysets using it. You
could place the implementation in a ``models.py`` file, or register the lookup
in the ``ready()`` method of an ``AppConfig``.

Taking a closer look at the implementation, the first required attribute is
``lookup_name``. This allows the ORM to understand how to interpret ``name__ne``
and use ``NotEqual`` to generate the SQL. By convention, these names are always
lowercase strings containing only letters, but the only hard requirement is
that it must not contain the string ``__``.

We then need to define the ``as_sql`` method. This takes a ``SQLCompiler``
object, called ``compiler``,  and the active database connection.
``SQLCompiler`` objects are not documented, but the only thing we need to know
about them is that they have a ``compile()`` method which returns a tuple
containing an SQL string, and the parameters to be interpolated into that
string. In most cases, you don't need to use it directly and can pass it on to
``process_lhs()`` and ``process_rhs()``.

A ``Lookup`` works against two values, ``lhs`` and ``rhs``, standing for
left-hand side and right-hand side. The left-hand side is usually a field
reference, but it can be anything implementing the :ref:`query expression API
<query-expression>`. The right-hand is the value given by the user. In the
example ``Author.objects.filter(name__ne='Jack')``, the left-hand side is a
reference to the ``name`` field of the ``Author`` model, and ``'Jack'`` is the
right-hand side.

We call ``process_lhs`` and ``process_rhs`` to convert them into the values we
need for SQL using the ``compiler`` object described before. These methods
return tuples containing some SQL and the parameters to be interpolated into
that SQL, just as we need to return from our ``as_sql`` method. In the above
example, ``process_lhs`` returns ``('"author"."name"', [])`` and
``process_rhs`` returns ``('"%s"', ['Jack'])``. In this example there were no
parameters for the left hand side, but this would depend on the object we have,
so we still need to include them in the parameters we return.

Finally we combine the parts into an SQL expression with ``<>``, and supply all
the parameters for the query. We then return a tuple containing the generated
SQL string and the parameters.

A transformer example
=====================

The custom lookup above is great, but in some cases you may want to be able to
chain lookups together. For example, let's suppose we are building an
application where we want to make use of the ``abs()`` operator.
We have an ``Experiment`` model which records a start value, end value, and the
change (start - end). We would like to find all experiments where the change
was equal to a certain amount (``Experiment.objects.filter(change__abs=27)``),
or where it did not exceed a certain amount
(``Experiment.objects.filter(change__abs__lt=27)``).

.. note::
    This example is somewhat contrived, but it nicely demonstrates the range of
    functionality which is possible in a database backend independent manner,
    and without duplicating functionality already in Django.

We will start by writing an ``AbsoluteValue`` transformer. This will use the SQL
function ``ABS()`` to transform the value before comparison::

  from django.db.models import Transform


  class AbsoluteValue(Transform):
      lookup_name = "abs"
      function = "ABS"

Next, let's register it for ``IntegerField``::

  from django.db.models import IntegerField

  IntegerField.register_lookup(AbsoluteValue)

We can now run the queries we had before.
``Experiment.objects.filter(change__abs=27)`` will generate the following SQL:

.. code-block:: sql

    SELECT ... WHERE ABS("experiments"."change") = 27

By using ``Transform`` instead of ``Lookup`` it means we are able to chain
further lookups afterward. So
``Experiment.objects.filter(change__abs__lt=27)`` will generate the following
SQL:

.. code-block:: sql

    SELECT ... WHERE ABS("experiments"."change") < 27

Note that in case there is no other lookup specified, Django interprets
``change__abs=27`` as ``change__abs__exact=27``.

This also allows the result to be used in ``ORDER BY`` and ``DISTINCT ON``
clauses. For example ``Experiment.objects.order_by('change__abs')`` generates:

.. code-block:: sql

    SELECT ... ORDER BY ABS("experiments"."change") ASC

And on databases that support distinct on fields (such as PostgreSQL),
``Experiment.objects.distinct('change__abs')`` generates:

.. code-block:: sql

    SELECT ... DISTINCT ON ABS("experiments"."change")

When looking for which lookups are allowable after the ``Transform`` has been
applied, Django uses the ``output_field`` attribute. We didn't need to specify
this here as it didn't change, but supposing we were applying ``AbsoluteValue``
to some field which represents a more complex type (for example a point
relative to an origin, or a complex number) then we may have wanted to specify
that the transform returns a ``FloatField`` type for further lookups. This can
be done by adding an ``output_field`` attribute to the transform::

    from django.db.models import FloatField, Transform


    class AbsoluteValue(Transform):
        lookup_name = "abs"
        function = "ABS"

        @property
        def output_field(self):
            return FloatField()

This ensures that further lookups like ``abs__lte`` behave as they would for
a ``FloatField``.

Writing an efficient ``abs__lt`` lookup
=======================================

When using the above written ``abs`` lookup, the SQL produced will not use
indexes efficiently in some cases. In particular, when we use
``change__abs__lt=27``, this is equivalent to ``change__gt=-27`` AND
``change__lt=27``. (For the ``lte`` case we could use the SQL ``BETWEEN``).

So we would like ``Experiment.objects.filter(change__abs__lt=27)`` to generate
the following SQL:

.. code-block:: sql

    SELECT .. WHERE "experiments"."change" < 27 AND "experiments"."change" > -27

The implementation is::

  from django.db.models import Lookup


  class AbsoluteValueLessThan(Lookup):
      lookup_name = "lt"

      def as_sql(self, compiler, connection):
          lhs, lhs_params = compiler.compile(self.lhs.lhs)
          rhs, rhs_params = self.process_rhs(compiler, connection)
          params = lhs_params + rhs_params + lhs_params + rhs_params
          return "%s < %s AND %s > -%s" % (lhs, rhs, lhs, rhs), params


  AbsoluteValue.register_lookup(AbsoluteValueLessThan)

There are a couple of notable things going on. First, ``AbsoluteValueLessThan``
isn't calling ``process_lhs()``. Instead it skips the transformation of the
``lhs`` done by ``AbsoluteValue`` and uses the original ``lhs``. That is, we
want to get ``"experiments"."change"`` not ``ABS("experiments"."change")``.
Referring directly to ``self.lhs.lhs`` is safe as ``AbsoluteValueLessThan``
can be accessed only from the ``AbsoluteValue`` lookup, that is the ``lhs``
is always an instance of ``AbsoluteValue``.

Notice also that  as both sides are used multiple times in the query the params
need to contain ``lhs_params`` and ``rhs_params`` multiple times.

The final query does the inversion (``27`` to ``-27``) directly in the
database. The reason for doing this is that if the ``self.rhs`` is something else
than a plain integer value (for example an ``F()`` reference) we can't do the
transformations in Python.

.. note::
    In fact, most lookups with ``__abs`` could be implemented as range queries
    like this, and on most database backends it is likely to be more sensible to
    do so as you can make use of the indexes. However with PostgreSQL you may
    want to add an index on ``abs(change)`` which would allow these queries to
    be very efficient.

A bilateral transformer example
===============================

The ``AbsoluteValue`` example we discussed previously is a transformation which
applies to the left-hand side of the lookup. There may be some cases where you
want the transformation to be applied to both the left-hand side and the
right-hand side. For instance, if you want to filter a queryset based on the
equality of the left and right-hand side insensitively to some SQL function.

Let's examine case-insensitive transformations here. This transformation isn't
very useful in practice as Django already comes with a bunch of built-in
case-insensitive lookups, but it will be a nice demonstration of bilateral
transformations in a database-agnostic way.

We define an ``UpperCase`` transformer which uses the SQL function ``UPPER()`` to
transform the values before comparison. We define
:attr:`bilateral = True <django.db.models.Transform.bilateral>` to indicate that
this transformation should apply to both ``lhs`` and ``rhs``::

  from django.db.models import Transform


  class UpperCase(Transform):
      lookup_name = "upper"
      function = "UPPER"
      bilateral = True

Next, let's register it::

  from django.db.models import CharField, TextField

  CharField.register_lookup(UpperCase)
  TextField.register_lookup(UpperCase)

Now, the queryset ``Author.objects.filter(name__upper="doe")`` will generate a case
insensitive query like this:

.. code-block:: sql

    SELECT ... WHERE UPPER("author"."name") = UPPER('doe')

Writing alternative implementations for existing lookups
========================================================

Sometimes different database vendors require different SQL for the same
operation. For this example we will rewrite a custom implementation for
MySQL for the NotEqual operator. Instead of ``<>`` we will be using ``!=``
operator. (Note that in reality almost all databases support both, including
all the official databases supported by Django).

We can change the behavior on a specific backend by creating a subclass of
``NotEqual`` with an ``as_mysql`` method::

  class MySQLNotEqual(NotEqual):
      def as_mysql(self, compiler, connection, **extra_context):
          lhs, lhs_params = self.process_lhs(compiler, connection)
          rhs, rhs_params = self.process_rhs(compiler, connection)
          params = lhs_params + rhs_params
          return "%s != %s" % (lhs, rhs), params


  Field.register_lookup(MySQLNotEqual)

We can then register it with ``Field``. It takes the place of the original
``NotEqual`` class as it has the same ``lookup_name``.

When compiling a query, Django first looks for ``as_%s % connection.vendor``
methods, and then falls back to ``as_sql``. The vendor names for the in-built
backends are ``sqlite``, ``postgresql``, ``oracle`` and ``mysql``.

How Django determines the lookups and transforms which are used
===============================================================

In some cases you may wish to dynamically change which ``Transform`` or
``Lookup`` is returned based on the name passed in, rather than fixing it. As
an example, you could have a field which stores coordinates or an arbitrary
dimension, and wish to allow a syntax like ``.filter(coords__x7=4)`` to return
the objects where the 7th coordinate has value 4. In order to do this, you
would override ``get_lookup`` with something like::

    class CoordinatesField(Field):
        def get_lookup(self, lookup_name):
            if lookup_name.startswith("x"):
                try:
                    dimension = int(lookup_name.removeprefix("x"))
                except ValueError:
                    pass
                else:
                    return get_coordinate_lookup(dimension)
            return super().get_lookup(lookup_name)

You would then define ``get_coordinate_lookup`` appropriately to return a
``Lookup`` subclass which handles the relevant value of ``dimension``.

There is a similarly named method called ``get_transform()``. ``get_lookup()``
should always return a ``Lookup`` subclass, and ``get_transform()`` a
``Transform`` subclass. It is important to remember that ``Transform``
objects can be further filtered on, and ``Lookup`` objects cannot.

When filtering, if there is only one lookup name remaining to be resolved, we
will look for a ``Lookup``. If there are multiple names, it will look for a
``Transform``. In the situation where there is only one name and a ``Lookup``
is not found, we look for a ``Transform`` and then the ``exact`` lookup on that
``Transform``. All call sequences always end with a ``Lookup``. To clarify:

- ``.filter(myfield__mylookup)`` will call ``myfield.get_lookup('mylookup')``.
- ``.filter(myfield__mytransform__mylookup)`` will call
  ``myfield.get_transform('mytransform')``, and then
  ``mytransform.get_lookup('mylookup')``.
- ``.filter(myfield__mytransform)`` will first call
  ``myfield.get_lookup('mytransform')``, which will fail, so it will fall back
  to calling ``myfield.get_transform('mytransform')`` and then
  ``mytransform.get_lookup('exact')``.


================================================
File: docs/howto/custom-management-commands.txt
================================================
==============================================
How to create custom ``django-admin`` commands
==============================================

.. module:: django.core.management

Applications can register their own actions with ``manage.py``. For example,
you might want to add a ``manage.py`` action for a Django app that you're
distributing. In this document, we will be building a custom ``closepoll``
command for the ``polls`` application from the
:doc:`tutorial</intro/tutorial01>`.

To do this, add a ``management/commands`` directory to the application. Django
will register a ``manage.py`` command for each Python module in that directory
whose name doesn't begin with an underscore. For example:

.. code-block:: text

    polls/
        __init__.py
        models.py
        management/
            __init__.py
            commands/
                __init__.py
                _private.py
                closepoll.py
        tests.py
        views.py

In this example, the ``closepoll`` command will be made available to any project
that includes the ``polls`` application in :setting:`INSTALLED_APPS`.

The ``_private.py`` module will not be available as a management command.

The ``closepoll.py`` module has only one requirement -- it must define a class
``Command`` that extends :class:`BaseCommand` or one of its
:ref:`subclasses<ref-basecommand-subclasses>`.

.. admonition:: Standalone scripts

    Custom management commands are especially useful for running standalone
    scripts or for scripts that are periodically executed from the UNIX crontab
    or from Windows scheduled tasks control panel.

To implement the command, edit ``polls/management/commands/closepoll.py`` to
look like this::

    from django.core.management.base import BaseCommand, CommandError
    from polls.models import Question as Poll


    class Command(BaseCommand):
        help = "Closes the specified poll for voting"

        def add_arguments(self, parser):
            parser.add_argument("poll_ids", nargs="+", type=int)

        def handle(self, *args, **options):
            for poll_id in options["poll_ids"]:
                try:
                    poll = Poll.objects.get(pk=poll_id)
                except Poll.DoesNotExist:
                    raise CommandError('Poll "%s" does not exist' % poll_id)

                poll.opened = False
                poll.save()

                self.stdout.write(
                    self.style.SUCCESS('Successfully closed poll "%s"' % poll_id)
                )

.. _management-commands-output:

.. note::
    When you are using management commands and wish to provide console
    output, you should write to ``self.stdout`` and ``self.stderr``,
    instead of printing to ``stdout`` and ``stderr`` directly. By
    using these proxies, it becomes much easier to test your custom
    command. Note also that you don't need to end messages with a newline
    character, it will be added automatically, unless you specify the ``ending``
    parameter::

        self.stdout.write("Unterminated line", ending="")

The new custom command can be called using ``python manage.py closepoll
<poll_ids>``.

The ``handle()`` method takes one or more ``poll_ids`` and sets ``poll.opened``
to ``False`` for each one. If the user referenced any nonexistent polls, a
:exc:`CommandError` is raised. The ``poll.opened`` attribute does not exist in
the :doc:`tutorial</intro/tutorial02>` and was added to
``polls.models.Question`` for this example.

.. _custom-commands-options:

Accepting optional arguments
============================

The same ``closepoll`` could be easily modified to delete a given poll instead
of closing it by accepting additional command line options. These custom
options can be added in the :meth:`~BaseCommand.add_arguments` method like this::

    class Command(BaseCommand):
        def add_arguments(self, parser):
            # Positional arguments
            parser.add_argument("poll_ids", nargs="+", type=int)

            # Named (optional) arguments
            parser.add_argument(
                "--delete",
                action="store_true",
                help="Delete poll instead of closing it",
            )

        def handle(self, *args, **options):
            # ...
            if options["delete"]:
                poll.delete()
            # ...

The option (``delete`` in our example) is available in the options dict
parameter of the handle method. See the :py:mod:`argparse` Python documentation
for more about ``add_argument`` usage.

In addition to being able to add custom command line options, all
:doc:`management commands</ref/django-admin>` can accept some default options
such as :option:`--verbosity` and :option:`--traceback`.

.. _management-commands-and-locales:

Management commands and locales
===============================

By default, management commands are executed with the current active locale.

If, for some reason, your custom management command must run without an active
locale (for example, to prevent translated content from being inserted into
the database), deactivate translations using the ``@no_translations``
decorator on your :meth:`~BaseCommand.handle` method::

    from django.core.management.base import BaseCommand, no_translations


    class Command(BaseCommand):
        ...

        @no_translations
        def handle(self, *args, **options): ...

Since translation deactivation requires access to configured settings, the
decorator can't be used for commands that work without configured settings.

Testing
=======

Information on how to test custom management commands can be found in the
:ref:`testing docs <topics-testing-management-commands>`.

.. _overriding-commands:

Overriding commands
===================

Django registers the built-in commands and then searches for commands in
:setting:`INSTALLED_APPS` in reverse. During the search, if a command name
duplicates an already registered command, the newly discovered command
overrides the first.

In other words, to override a command, the new command must have the same name
and its app must be before the overridden command's app in
:setting:`INSTALLED_APPS`.

Management commands from third-party apps that have been unintentionally
overridden can be made available under a new name by creating a new command in
one of your project's apps (ordered before the third-party app in
:setting:`INSTALLED_APPS`) which imports the ``Command`` of the overridden
command.

Command objects
===============

.. class:: BaseCommand

The base class from which all management commands ultimately derive.

Use this class if you want access to all of the mechanisms which
parse the command-line arguments and work out what code to call in
response; if you don't need to change any of that behavior,
consider using one of its :ref:`subclasses<ref-basecommand-subclasses>`.

Subclassing the :class:`BaseCommand` class requires that you implement the
:meth:`~BaseCommand.handle` method.

Attributes
----------

All attributes can be set in your derived class and can be used in
:class:`BaseCommand`’s :ref:`subclasses<ref-basecommand-subclasses>`.

.. attribute:: BaseCommand.help

    A short description of the command, which will be printed in the
    help message when the user runs the command
    ``python manage.py help <command>``.

.. attribute:: BaseCommand.missing_args_message

    If your command defines mandatory positional arguments, you can customize
    the message error returned in the case of missing arguments. The default is
    output by :py:mod:`argparse` ("too few arguments").

.. attribute:: BaseCommand.output_transaction

    A boolean indicating whether the command outputs SQL statements; if
    ``True``, the output will automatically be wrapped with ``BEGIN;`` and
    ``COMMIT;``. Default value is ``False``.

.. attribute:: BaseCommand.requires_migrations_checks

    A boolean; if ``True``, the command prints a warning if the set of
    migrations on disk don't match the migrations in the database. A warning
    doesn't prevent the command from executing. Default value is ``False``.

.. attribute:: BaseCommand.requires_system_checks

    A list or tuple of tags, e.g. ``[Tags.staticfiles, Tags.models]``. System
    checks :ref:`registered in the chosen tags <registering-labeling-checks>`
    will be checked for errors prior to executing the command. The value
    ``'__all__'`` can be used to specify that all system checks should be
    performed. Default value is ``'__all__'``.

.. attribute:: BaseCommand.style

    An instance attribute that helps create colored output when writing to
    ``stdout`` or ``stderr``. For example::

        self.stdout.write(self.style.SUCCESS("..."))

    See :ref:`syntax-coloring` to learn how to modify the color palette and to
    see the available styles (use uppercased versions of the "roles" described
    in that section).

    If you pass the :option:`--no-color` option when running your command, all
    ``self.style()`` calls will return the original string uncolored.

.. attribute:: BaseCommand.suppressed_base_arguments

    The default command options to suppress in the help output. This should be
    a set of option names (e.g. ``'--verbosity'``). The default values for the
    suppressed options are still passed.

Methods
-------

:class:`BaseCommand` has a few methods that can be overridden but only
the :meth:`~BaseCommand.handle` method must be implemented.

.. admonition:: Implementing a constructor in a subclass

    If you implement ``__init__`` in your subclass of :class:`BaseCommand`,
    you must call :class:`BaseCommand`’s ``__init__``::

        class Command(BaseCommand):
            def __init__(self, *args, **kwargs):
                super().__init__(*args, **kwargs)
                # ...

.. method:: BaseCommand.create_parser(prog_name, subcommand, **kwargs)

    Returns a ``CommandParser`` instance, which is an
    :class:`~argparse.ArgumentParser` subclass with a few customizations for
    Django.

    You can customize the instance by overriding this method and calling
    ``super()`` with ``kwargs`` of :class:`~argparse.ArgumentParser` parameters.

.. method:: BaseCommand.add_arguments(parser)

    Entry point to add parser arguments to handle command line arguments passed
    to the command. Custom commands should override this method to add both
    positional and optional arguments accepted by the command. Calling
    ``super()`` is not needed when directly subclassing ``BaseCommand``.

.. method:: BaseCommand.get_version()

    Returns the Django version, which should be correct for all built-in Django
    commands. User-supplied commands can override this method to return their
    own version.

.. method:: BaseCommand.execute(*args, **options)

    Tries to execute this command, performing system checks if needed (as
    controlled by the :attr:`requires_system_checks` attribute). If the command
    raises a :exc:`CommandError`, it's intercepted and printed to ``stderr``.

.. admonition:: Calling a management command in your code

    ``execute()`` should not be called directly from your code to execute a
    command. Use :func:`~django.core.management.call_command` instead.

.. method:: BaseCommand.handle(*args, **options)

    The actual logic of the command. Subclasses must implement this method.

    It may return a string which will be printed to ``stdout`` (wrapped
    by ``BEGIN;`` and ``COMMIT;`` if :attr:`output_transaction` is ``True``).

.. method:: BaseCommand.check(app_configs=None, tags=None,display_num_errors=False, include_deployment_checks=False, fail_level=checks.ERROR, databases=None)

    Uses the system check framework to inspect the entire Django project for
    potential problems. Serious problems are raised as a :exc:`CommandError`;
    warnings are output to ``stderr``; minor notifications are output to
    ``stdout``.

    If ``app_configs`` and ``tags`` are both ``None``, all system checks are
    performed except deployment and database related checks. ``tags`` can be a
    list of check tags, like ``compatibility`` or ``models``.

    You can pass ``include_deployment_checks=True`` to also perform deployment
    checks, and list of database aliases in the ``databases`` to run database
    related checks against them.

.. method:: BaseCommand.get_check_kwargs(options)

    .. versionadded:: 5.2

    Supplies kwargs for the call to :meth:`check`, including transforming the
    value of :attr:`requires_system_checks` to the ``tag`` kwarg.

    Override this method to change the values supplied to :meth:`check`. For
    example, to opt into database related checks you can override
    ``get_check_kwargs()`` as follows::

        def get_check_kwargs(self, options):
            kwargs = super().get_check_kwargs(options)
            return {**kwargs, "databases": [options["database"]]}

.. _ref-basecommand-subclasses:

``BaseCommand`` subclasses
--------------------------

.. class:: AppCommand

A management command which takes one or more installed application labels as
arguments, and does something with each of them.

Rather than implementing :meth:`~BaseCommand.handle`, subclasses must
implement :meth:`~AppCommand.handle_app_config`, which will be called once for
each application.

.. method:: AppCommand.handle_app_config(app_config, **options)

    Perform the command's actions for ``app_config``, which will be an
    :class:`~django.apps.AppConfig` instance corresponding to an application
    label given on the command line.

.. class:: LabelCommand

A management command which takes one or more arbitrary arguments (labels) on
the command line, and does something with each of them.

Rather than implementing :meth:`~BaseCommand.handle`, subclasses must implement
:meth:`~LabelCommand.handle_label`, which will be called once for each label.

.. attribute:: LabelCommand.label

    A string describing the arbitrary arguments passed to the command. The
    string is used in the usage text and error messages of the command.
    Defaults to ``'label'``.

.. method:: LabelCommand.handle_label(label, **options)

    Perform the command's actions for ``label``, which will be the string as
    given on the command line.

Command exceptions
------------------

.. exception:: CommandError(returncode=1)

Exception class indicating a problem while executing a management command.

If this exception is raised during the execution of a management command from a
command line console, it will be caught and turned into a nicely-printed error
message to the appropriate output stream (i.e., ``stderr``); as a result,
raising this exception (with a sensible description of the error) is the
preferred way to indicate that something has gone wrong in the execution of a
command. It accepts the optional ``returncode`` argument to customize the exit
status for the management command to exit with, using :func:`sys.exit`.

If a management command is called from code through
:func:`~django.core.management.call_command`, it's up to you to catch the
exception when needed.


================================================
File: docs/howto/custom-model-fields.txt
================================================
=================================
How to create custom model fields
=================================

.. currentmodule:: django.db.models

Introduction
============

The :doc:`model reference </topics/db/models>` documentation explains how to use
Django's standard field classes -- :class:`~django.db.models.CharField`,
:class:`~django.db.models.DateField`, etc. For many purposes, those classes are
all you'll need. Sometimes, though, the Django version won't meet your precise
requirements, or you'll want to use a field that is entirely different from
those shipped with Django.

Django's built-in field types don't cover every possible database column type --
only the common types, such as ``VARCHAR`` and ``INTEGER``. For more obscure
column types, such as geographic polygons or even user-created types such as
`PostgreSQL custom types`_, you can define your own Django ``Field`` subclasses.

.. _PostgreSQL custom types: https://www.postgresql.org/docs/current/sql-createtype.html

Alternatively, you may have a complex Python object that can somehow be
serialized to fit into a standard database column type. This is another case
where a ``Field`` subclass will help you use your object with your models.

Our example object
------------------

Creating custom fields requires a bit of attention to detail. To make things
easier to follow, we'll use a consistent example throughout this document:
wrapping a Python object representing the deal of cards in a hand of Bridge_.
Don't worry, you don't have to know how to play Bridge to follow this example.
You only need to know that 52 cards are dealt out equally to four players, who
are traditionally called *north*, *east*, *south* and *west*.  Our class looks
something like this::

    class Hand:
        """A hand of cards (bridge style)"""

        def __init__(self, north, east, south, west):
            # Input parameters are lists of cards ('Ah', '9s', etc.)
            self.north = north
            self.east = east
            self.south = south
            self.west = west

        # ... (other possibly useful methods omitted) ...

.. _Bridge: https://en.wikipedia.org/wiki/Contract_bridge

This is an ordinary Python class, with nothing Django-specific about it.
We'd like to be able to do things like this in our models (we assume the
``hand`` attribute on the model is an instance of ``Hand``)::

    example = MyModel.objects.get(pk=1)
    print(example.hand.north)

    new_hand = Hand(north, east, south, west)
    example.hand = new_hand
    example.save()

We assign to and retrieve from the ``hand`` attribute in our model just like
any other Python class. The trick is to tell Django how to handle saving and
loading such an object.

In order to use the ``Hand`` class in our models, we **do not** have to change
this class at all. This is ideal, because it means you can easily write
model support for existing classes where you cannot change the source code.

.. note::
    You might only be wanting to take advantage of custom database column
    types and deal with the data as standard Python types in your models;
    strings, or floats, for example. This case is similar to our ``Hand``
    example and we'll note any differences as we go along.

Background theory
=================

Database storage
----------------

Let's start with model fields. If you break it down, a model field provides a
way to take a normal Python object -- string, boolean, ``datetime``, or
something more complex like ``Hand`` -- and convert it to and from a format
that is useful when dealing with the database. (Such a format is also useful
for serialization, but as we'll see later, that is easier once you have the
database side under control).

Fields in a model must somehow be converted to fit into an existing database
column type. Different databases provide different sets of valid column types,
but the rule is still the same: those are the only types you have to work
with. Anything you want to store in the database must fit into one of
those types.

Normally, you're either writing a Django field to match a particular database
column type, or you will need a way to convert your data to, say, a string.

For our ``Hand`` example, we could convert the card data to a string of 104
characters by concatenating all the cards together in a predetermined order --
say, all the *north* cards first, then the *east*, *south* and *west* cards. So
``Hand`` objects can be saved to text or character columns in the database.

What does a field class do?
---------------------------

All of Django's fields (and when we say *fields* in this document, we always
mean model fields and not :doc:`form fields </ref/forms/fields>`) are subclasses
of :class:`django.db.models.Field`. Most of the information that Django records
about a field is common to all fields -- name, help text, uniqueness and so
forth. Storing all that information is handled by ``Field``. We'll get into the
precise details of what ``Field`` can do later on; for now, suffice it to say
that everything descends from ``Field`` and then customizes key pieces of the
class behavior.

It's important to realize that a Django field class is not what is stored in
your model attributes. The model attributes contain normal Python objects. The
field classes you define in a model are actually stored in the ``Meta`` class
when the model class is created (the precise details of how this is done are
unimportant here). This is because the field classes aren't necessary when
you're just creating and modifying attributes. Instead, they provide the
machinery for converting between the attribute value and what is stored in the
database or sent to the :doc:`serializer </topics/serialization>`.

Keep this in mind when creating your own custom fields. The Django ``Field``
subclass you write provides the machinery for converting between your Python
instances and the database/serializer values in various ways (there are
differences between storing a value and using a value for lookups, for
example). If this sounds a bit tricky, don't worry -- it will become clearer in
the examples below. Just remember that you will often end up creating two
classes when you want a custom field:

* The first class is the Python object that your users will manipulate.
  They will assign it to the model attribute, they will read from it for
  displaying purposes, things like that. This is the ``Hand`` class in our
  example.

* The second class is the ``Field`` subclass. This is the class that knows
  how to convert your first class back and forth between its permanent
  storage form and the Python form.

Writing a field subclass
========================

When planning your :class:`~django.db.models.Field` subclass, first give some
thought to which existing :class:`~django.db.models.Field` class your new field
is most similar to. Can you subclass an existing Django field and save yourself
some work? If not, you should subclass the :class:`~django.db.models.Field`
class, from which everything is descended.

Initializing your new field is a matter of separating out any arguments that are
specific to your case from the common arguments and passing the latter to the
``__init__()`` method of :class:`~django.db.models.Field` (or your parent
class).

In our example, we'll call our field ``HandField``. (It's a good idea to call
your :class:`~django.db.models.Field` subclass ``<Something>Field``, so it's
easily identifiable as a :class:`~django.db.models.Field` subclass.) It doesn't
behave like any existing field, so we'll subclass directly from
:class:`~django.db.models.Field`::

    from django.db import models


    class HandField(models.Field):
        description = "A hand of cards (bridge style)"

        def __init__(self, *args, **kwargs):
            kwargs["max_length"] = 104
            super().__init__(*args, **kwargs)

Our ``HandField`` accepts most of the standard field options (see the list
below), but we ensure it has a fixed length, since it only needs to hold 52
card values plus their suits; 104 characters in total.

.. note::

    Many of Django's model fields accept options that they don't do anything
    with. For example, you can pass both
    :attr:`~django.db.models.Field.editable` and
    :attr:`~django.db.models.DateField.auto_now` to a
    :class:`django.db.models.DateField` and it will ignore the
    :attr:`~django.db.models.Field.editable` parameter
    (:attr:`~django.db.models.DateField.auto_now` being set implies
    ``editable=False``). No error is raised in this case.

    This behavior simplifies the field classes, because they don't need to
    check for options that aren't necessary. They pass all the options to
    the parent class and then don't use them later on. It's up to you whether
    you want your fields to be more strict about the options they select, or to
    use the more permissive behavior of the current fields.

The ``Field.__init__()`` method takes the following parameters:

* :attr:`~django.db.models.Field.verbose_name`
* ``name``
* :attr:`~django.db.models.Field.primary_key`
* :attr:`~django.db.models.CharField.max_length`
* :attr:`~django.db.models.Field.unique`
* :attr:`~django.db.models.Field.blank`
* :attr:`~django.db.models.Field.null`
* :attr:`~django.db.models.Field.db_index`
* ``rel``: Used for related fields (like :class:`ForeignKey`). For advanced
  use only.
* :attr:`~django.db.models.Field.default`
* :attr:`~django.db.models.Field.editable`
* ``serialize``: If ``False``, the field will not be serialized when the model
  is passed to Django's :doc:`serializers </topics/serialization>`. Defaults to
  ``True``.
* :attr:`~django.db.models.Field.unique_for_date`
* :attr:`~django.db.models.Field.unique_for_month`
* :attr:`~django.db.models.Field.unique_for_year`
* :attr:`~django.db.models.Field.choices`
* :attr:`~django.db.models.Field.help_text`
* :attr:`~django.db.models.Field.db_column`
* :attr:`~django.db.models.Field.db_tablespace`: Only for index creation, if the
  backend supports :doc:`tablespaces </topics/db/tablespaces>`. You can usually
  ignore this option.
* :attr:`~django.db.models.Field.auto_created`: ``True`` if the field was
  automatically created, as for the :class:`~django.db.models.OneToOneField`
  used by model inheritance. For advanced use only.

All of the options without an explanation in the above list have the same
meaning they do for normal Django fields. See the :doc:`field documentation
</ref/models/fields>` for examples and details.

.. _custom-field-deconstruct-method:

Field deconstruction
--------------------

The counterpoint to writing your ``__init__()`` method is writing the
:meth:`~.Field.deconstruct` method. It's used during :doc:`model migrations
</topics/migrations>` to tell Django how to take an instance of your new field
and reduce it to a serialized form - in particular, what arguments to pass to
``__init__()`` to recreate it.

If you haven't added any extra options on top of the field you inherited from,
then there's no need to write a new ``deconstruct()`` method. If, however,
you're changing the arguments passed in ``__init__()`` (like we are in
``HandField``), you'll need to supplement the values being passed.

``deconstruct()`` returns a tuple of four items: the field's attribute name,
the full import path of the field class, the positional arguments (as a list),
and the keyword arguments (as a dict). Note this is different from the
``deconstruct()`` method :ref:`for custom classes <custom-deconstruct-method>`
which returns a tuple of three things.

As a custom field author, you don't need to care about the first two values;
the base ``Field`` class has all the code to work out the field's attribute
name and import path. You do, however, have to care about the positional
and keyword arguments, as these are likely the things you are changing.

For example, in our ``HandField`` class we're always forcibly setting
max_length in ``__init__()``. The ``deconstruct()`` method on the base ``Field``
class will see this and try to return it in the keyword arguments; thus,
we can drop it from the keyword arguments for readability::

    from django.db import models


    class HandField(models.Field):
        def __init__(self, *args, **kwargs):
            kwargs["max_length"] = 104
            super().__init__(*args, **kwargs)

        def deconstruct(self):
            name, path, args, kwargs = super().deconstruct()
            del kwargs["max_length"]
            return name, path, args, kwargs

If you add a new keyword argument, you need to write code in ``deconstruct()``
that puts its value into ``kwargs`` yourself. You should also omit the value
from ``kwargs`` when it isn't necessary to reconstruct the state of the field,
such as when the default value is being used::

    from django.db import models


    class CommaSepField(models.Field):
        "Implements comma-separated storage of lists"

        def __init__(self, separator=",", *args, **kwargs):
            self.separator = separator
            super().__init__(*args, **kwargs)

        def deconstruct(self):
            name, path, args, kwargs = super().deconstruct()
            # Only include kwarg if it's not the default
            if self.separator != ",":
                kwargs["separator"] = self.separator
            return name, path, args, kwargs

More complex examples are beyond the scope of this document, but remember -
for any configuration of your Field instance, ``deconstruct()`` must return
arguments that you can pass to ``__init__`` to reconstruct that state.

Pay extra attention if you set new default values for arguments in the
``Field`` superclass; you want to make sure they're always included, rather
than disappearing if they take on the old default value.

In addition, try to avoid returning values as positional arguments; where
possible, return values as keyword arguments for maximum future compatibility.
If you change the names of things more often than their position in the
constructor's argument list, you might prefer positional, but bear in mind that
people will be reconstructing your field from the serialized version for quite
a while (possibly years), depending how long your migrations live for.

You can see the results of deconstruction by looking in migrations that include
the field, and you can test deconstruction in unit tests by deconstructing and
reconstructing the field::

    name, path, args, kwargs = my_field_instance.deconstruct()
    new_instance = MyField(*args, **kwargs)
    self.assertEqual(my_field_instance.some_attribute, new_instance.some_attribute)

.. _custom-field-non_db_attrs:

Field attributes not affecting database column definition
---------------------------------------------------------

You can override ``Field.non_db_attrs`` to customize attributes of a field that
don't affect a column definition. It's used during model migrations to detect
no-op ``AlterField`` operations.

For example::

    class CommaSepField(models.Field):
        @property
        def non_db_attrs(self):
            return super().non_db_attrs + ("separator",)


Changing a custom field's base class
------------------------------------

You can't change the base class of a custom field because Django won't detect
the change and make a migration for it. For example, if you start with::

    class CustomCharField(models.CharField): ...

and then decide that you want to use ``TextField`` instead, you can't change
the subclass like this::

    class CustomCharField(models.TextField): ...

Instead, you must create a new custom field class and update your models to
reference it::

    class CustomCharField(models.CharField): ...


    class CustomTextField(models.TextField): ...

As discussed in :ref:`removing fields <migrations-removing-model-fields>`, you
must retain the original ``CustomCharField`` class as long as you have
migrations that reference it.

Documenting your custom field
-----------------------------

As always, you should document your field type, so users will know what it is.
In addition to providing a docstring for it, which is useful for developers,
you can also allow users of the admin app to see a short description of the
field type via the :doc:`django.contrib.admindocs
</ref/contrib/admin/admindocs>` application. To do this provide descriptive
text in a :attr:`~Field.description` class attribute of your custom field. In
the above example, the description displayed by the ``admindocs`` application
for a ``HandField`` will be 'A hand of cards (bridge style)'.

In the :mod:`django.contrib.admindocs` display, the field description is
interpolated with ``field.__dict__`` which allows the description to
incorporate arguments of the field. For example, the description for
:class:`~django.db.models.CharField` is::

    description = _("String (up to %(max_length)s)")

Useful methods
--------------

Once you've created your :class:`~django.db.models.Field` subclass, you might
consider overriding a few standard methods, depending on your field's behavior.
The list of methods below is in approximately decreasing order of importance,
so start from the top.

.. _custom-database-types:

Custom database types
~~~~~~~~~~~~~~~~~~~~~

Say you've created a PostgreSQL custom type called ``mytype``. You can
subclass ``Field`` and implement the :meth:`~Field.db_type` method, like so::

    from django.db import models


    class MytypeField(models.Field):
        def db_type(self, connection):
            return "mytype"

Once you have ``MytypeField``, you can use it in any model, just like any other
``Field`` type::

    class Person(models.Model):
        name = models.CharField(max_length=80)
        something_else = MytypeField()

If you aim to build a database-agnostic application, you should account for
differences in database column types. For example, the date/time column type
in PostgreSQL is called ``timestamp``, while the same column in MySQL is called
``datetime``. You can handle this in a :meth:`~Field.db_type` method by
checking the ``connection.vendor`` attribute. Current built-in vendor names
are: ``sqlite``, ``postgresql``, ``mysql``, and ``oracle``.

For example::

    class MyDateField(models.Field):
        def db_type(self, connection):
            if connection.vendor == "mysql":
                return "datetime"
            else:
                return "timestamp"

The :meth:`~Field.db_type` and :meth:`~Field.rel_db_type` methods are called by
Django when the framework constructs the ``CREATE TABLE`` statements for your
application -- that is, when you first create your tables. The methods are also
called when constructing a ``WHERE`` clause that includes the model field --
that is, when you retrieve data using QuerySet methods like ``get()``,
``filter()``, and ``exclude()`` and have the model field as an argument.

Some database column types accept parameters, such as ``CHAR(25)``, where the
parameter ``25`` represents the maximum column length. In cases like these,
it's more flexible if the parameter is specified in the model rather than being
hard-coded in the ``db_type()`` method. For example, it wouldn't make much
sense to have a ``CharMaxlength25Field``, shown here::

    # This is a silly example of hard-coded parameters.
    class CharMaxlength25Field(models.Field):
        def db_type(self, connection):
            return "char(25)"


    # In the model:
    class MyModel(models.Model):
        # ...
        my_field = CharMaxlength25Field()

The better way of doing this would be to make the parameter specifiable at run
time -- i.e., when the class is instantiated. To do that, implement
``Field.__init__()``, like so::

    # This is a much more flexible example.
    class BetterCharField(models.Field):
        def __init__(self, max_length, *args, **kwargs):
            self.max_length = max_length
            super().__init__(*args, **kwargs)

        def db_type(self, connection):
            return "char(%s)" % self.max_length


    # In the model:
    class MyModel(models.Model):
        # ...
        my_field = BetterCharField(25)

Finally, if your column requires truly complex SQL setup, return ``None`` from
:meth:`.db_type`. This will cause Django's SQL creation code to skip
over this field. You are then responsible for creating the column in the right
table in some other way, but this gives you a way to tell Django to get out of
the way.

The :meth:`~Field.rel_db_type` method is called by fields such as ``ForeignKey``
and ``OneToOneField`` that point to another field to determine their database
column data types. For example, if you have an ``UnsignedAutoField``, you also
need the foreign keys that point to that field to use the same data type::

    # MySQL unsigned integer (range 0 to 4294967295).
    class UnsignedAutoField(models.AutoField):
        def db_type(self, connection):
            return "integer UNSIGNED AUTO_INCREMENT"

        def rel_db_type(self, connection):
            return "integer UNSIGNED"

.. _converting-values-to-python-objects:

Converting values to Python objects
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If your custom :class:`~Field` class deals with data structures that are more
complex than strings, dates, integers, or floats, then you may need to override
:meth:`~Field.from_db_value` and :meth:`~Field.to_python`.

If present for the field subclass, ``from_db_value()`` will be called in all
circumstances when the data is loaded from the database, including in
aggregates and :meth:`~django.db.models.query.QuerySet.values` calls.

``to_python()`` is called by deserialization and during the
:meth:`~django.db.models.Model.clean` method used from forms.

As a general rule, ``to_python()`` should deal gracefully with any of the
following arguments:

* An instance of the correct type (e.g., ``Hand`` in our ongoing example).

* A string

* ``None`` (if the field allows ``null=True``)

In our ``HandField`` class, we're storing the data as a ``VARCHAR`` field in
the database, so we need to be able to process strings and ``None`` in the
``from_db_value()``. In ``to_python()``, we need to also handle ``Hand``
instances::

    import re

    from django.core.exceptions import ValidationError
    from django.db import models
    from django.utils.translation import gettext_lazy as _


    def parse_hand(hand_string):
        """Takes a string of cards and splits into a full hand."""
        p1 = re.compile(".{26}")
        p2 = re.compile("..")
        args = [p2.findall(x) for x in p1.findall(hand_string)]
        if len(args) != 4:
            raise ValidationError(_("Invalid input for a Hand instance"))
        return Hand(*args)


    class HandField(models.Field):
        # ...

        def from_db_value(self, value, expression, connection):
            if value is None:
                return value
            return parse_hand(value)

        def to_python(self, value):
            if isinstance(value, Hand):
                return value

            if value is None:
                return value

            return parse_hand(value)

Notice that we always return a ``Hand`` instance from these methods. That's the
Python object type we want to store in the model's attribute.

For ``to_python()``, if anything goes wrong during value conversion, you should
raise a :exc:`~django.core.exceptions.ValidationError` exception.

.. _converting-python-objects-to-query-values:

Converting Python objects to query values
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Since using a database requires conversion in both ways, if you override
:meth:`~Field.from_db_value` you also have to override
:meth:`~Field.get_prep_value` to convert Python objects back to query values.

For example::

    class HandField(models.Field):
        # ...

        def get_prep_value(self, value):
            return "".join(
                ["".join(l) for l in (value.north, value.east, value.south, value.west)]
            )

.. warning::

    If your custom field uses the ``CHAR``, ``VARCHAR`` or ``TEXT``
    types for MySQL, you must make sure that :meth:`.get_prep_value`
    always returns a string type. MySQL performs flexible and unexpected
    matching when a query is performed on these types and the provided
    value is an integer, which can cause queries to include unexpected
    objects in their results. This problem cannot occur if you always
    return a string type from :meth:`.get_prep_value`.

.. _converting-query-values-to-database-values:

Converting query values to database values
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some data types (for example, dates) need to be in a specific format
before they can be used by a database backend.
:meth:`~Field.get_db_prep_value` is the method where those conversions should
be made. The specific connection that will be used for the query is
passed as the ``connection`` parameter. This allows you to use
backend-specific conversion logic if it is required.

For example, Django uses the following method for its
:class:`BinaryField`::

    def get_db_prep_value(self, value, connection, prepared=False):
        value = super().get_db_prep_value(value, connection, prepared)
        if value is not None:
            return connection.Database.Binary(value)
        return value

In case your custom field needs a special conversion when being saved that is
not the same as the conversion used for normal query parameters, you can
override :meth:`~Field.get_db_prep_save`.

.. _preprocessing-values-before-saving:

Preprocessing values before saving
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you want to preprocess the value just before saving, you can use
:meth:`~Field.pre_save`. For example, Django's
:class:`~django.db.models.DateTimeField` uses this method to set the attribute
correctly in the case of :attr:`~django.db.models.DateField.auto_now` or
:attr:`~django.db.models.DateField.auto_now_add`.

If you do override this method, you must return the value of the attribute at
the end. You should also update the model's attribute if you make any changes
to the value so that code holding references to the model will always see the
correct value.

.. _specifying-form-field-for-model-field:

Specifying the form field for a model field
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To customize the form field used by :class:`~django.forms.ModelForm`, you can
override :meth:`~Field.formfield`.

The form field class can be specified via the ``form_class`` and
``choices_form_class`` arguments; the latter is used if the field has choices
specified, the former otherwise. If these arguments are not provided,
:class:`~django.forms.CharField` or :class:`~django.forms.TypedChoiceField`
will be used.

All of the ``kwargs`` dictionary is passed directly to the form field's
``__init__()`` method. Normally, all you need to do is set up a good default
for the ``form_class`` (and maybe ``choices_form_class``) argument and then
delegate further handling to the parent class. This might require you to write
a custom form field (and even a form widget). See the :doc:`forms documentation
</topics/forms/index>` for information about this.

If you wish to exclude the field from the :class:`~django.forms.ModelForm`, you
can override the :meth:`~Field.formfield` method to return ``None``.

Continuing our ongoing example, we can write the :meth:`~Field.formfield` method
as::

    class HandField(models.Field):
        # ...

        def formfield(self, **kwargs):
            # Exclude the field from the ModelForm when some condition is met.
            some_condition = kwargs.get("some_condition", False)
            if some_condition:
                return None

            # Set up some defaults while letting the caller override them.
            defaults = {"form_class": MyFormField}
            defaults.update(kwargs)
            return super().formfield(**defaults)

This assumes we've imported a ``MyFormField`` field class (which has its own
default widget). This document doesn't cover the details of writing custom form
fields.

.. _helper functions: ../forms/#generating-forms-for-models
.. _forms documentation: ../forms/

.. _emulating-built-in-field-types:

Emulating built-in field types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have created a :meth:`.db_type` method, you don't need to worry about
:meth:`.get_internal_type` -- it won't be used much. Sometimes, though, your
database storage is similar in type to some other field, so you can use that
other field's logic to create the right column.

For example::

    class HandField(models.Field):
        # ...

        def get_internal_type(self):
            return "CharField"

No matter which database backend we are using, this will mean that
:djadmin:`migrate` and other SQL commands create the right column type for
storing a string.

If :meth:`.get_internal_type` returns a string that is not known to Django for
the database backend you are using -- that is, it doesn't appear in
``django.db.backends.<db_name>.base.DatabaseWrapper.data_types`` -- the string
will still be used by the serializer, but the default :meth:`~Field.db_type`
method will return ``None``. See the documentation of :meth:`~Field.db_type`
for reasons why this might be useful. Putting a descriptive string in as the
type of the field for the serializer is a useful idea if you're ever going to
be using the serializer output in some other place, outside of Django.

.. _converting-model-field-to-serialization:

Converting field data for serialization
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To customize how the values are serialized by a serializer, you can override
:meth:`~Field.value_to_string`. Using :meth:`~Field.value_from_object` is the
best way to get the field's value prior to serialization. For example, since
``HandField`` uses strings for its data storage anyway, we can reuse some
existing conversion code::

    class HandField(models.Field):
        # ...

        def value_to_string(self, obj):
            value = self.value_from_object(obj)
            return self.get_prep_value(value)

Some general advice
-------------------

Writing a custom field can be a tricky process, particularly if you're doing
complex conversions between your Python types and your database and
serialization formats. Here are a couple of tips to make things go more
smoothly:

#. Look at the existing Django fields (in
   :source:`django/db/models/fields/__init__.py`) for inspiration. Try to find
   a field that's similar to what you want and extend it a little bit,
   instead of creating an entirely new field from scratch.

#. Put a ``__str__()`` method on the class you're wrapping up as a field. There
   are a lot of places where the default behavior of the field code is to call
   ``str()`` on the value. (In our examples in this document, ``value`` would
   be a ``Hand`` instance, not a ``HandField``). So if your ``__str__()``
   method automatically converts to the string form of your Python object, you
   can save yourself a lot of work.

Writing a ``FileField`` subclass
================================

In addition to the above methods, fields that deal with files have a few other
special requirements which must be taken into account. The majority of the
mechanics provided by ``FileField``, such as controlling database storage and
retrieval, can remain unchanged, leaving subclasses to deal with the challenge
of supporting a particular type of file.

Django provides a ``File`` class, which is used as a proxy to the file's
contents and operations. This can be subclassed to customize how the file is
accessed, and what methods are available. It lives at
``django.db.models.fields.files``, and its default behavior is explained in the
:doc:`file documentation </ref/files/file>`.

Once a subclass of ``File`` is created, the new ``FileField`` subclass must be
told to use it. To do so, assign the new ``File`` subclass to the special
``attr_class`` attribute of the ``FileField`` subclass.

A few suggestions
-----------------

In addition to the above details, there are a few guidelines which can greatly
improve the efficiency and readability of the field's code.

#. The source for Django's own ``ImageField`` (in
   :source:`django/db/models/fields/files.py`) is a great example of how to
   subclass ``FileField`` to support a particular type of file, as it
   incorporates all of the techniques described above.

#. Cache file attributes wherever possible. Since files may be stored in
   remote storage systems, retrieving them may cost extra time, or even
   money, that isn't always necessary. Once a file is retrieved to obtain
   some data about its content, cache as much of that data as possible to
   reduce the number of times the file must be retrieved on subsequent
   calls for that information.


================================================
File: docs/howto/custom-shell.txt
================================================
======================================
How to customize the ``shell`` command
======================================

The Django :djadmin:`shell` is an interactive Python environment that provides
access to models and settings, making it useful for testing code, experimenting
with queries, and interacting with application data.

Customizing the :djadmin:`shell` command allows adding extra functionality or
pre-loading specific modules. To do this, create a new management command that
subclasses ``django.core.management.commands.shell.Command`` and overrides the
existing ``shell`` management command. For more details, refer to the guide on
:ref:`overriding commands <overriding-commands>`.

.. _customizing-shell-auto-imports:

Customize automatic imports
===========================

.. versionadded:: 5.2

To customize the automatic import behavior of the :djadmin:`shell` management
command, override the ``get_auto_imports()`` method. This method should return
a sequence of import paths for objects or modules available in the application.
For example:

.. code-block:: python
    :caption: ``polls/management/commands/shell.py``

    from django.core.management.commands import shell


    class Command(shell.Command):
        def get_auto_imports(self):
            return super().get_auto_imports() + [
                "django.urls.reverse",
                "django.urls.resolve",
            ]

The customization above adds :func:`~django.urls.resolve` and
:func:`~django.urls.reverse` to the default namespace, which already includes
all models from the apps listed in :setting:`INSTALLED_APPS`. These objects
will be available in the ``shell`` without requiring a manual import.

Running this customized ``shell`` command with ``verbosity=2`` would show:

.. console::

    8 objects imported automatically:

      from django.contrib.admin.models import LogEntry
      from django.contrib.auth.models import Group, Permission, User
      from django.contrib.contenttypes.models import ContentType
      from django.contrib.sessions.models import Session
      from django.urls import resolve, reverse

If an overridden ``shell`` command includes paths that cannot be imported,
these errors are shown when ``verbosity`` is set to ``1`` or higher.

Note that automatic imports can be disabled for a specific ``shell`` session
using the :option:`--no-imports <shell --no-imports>` flag. To permanently
disable automatic imports, override ``get_auto_imports()`` to return ``None``::

    class Command(shell.Command):
        def get_auto_imports(self):
            return None


================================================
File: docs/howto/custom-template-backend.txt
================================================
==========================================
How to implement a custom template backend
==========================================

Custom backends
---------------

Here's how to implement a custom template backend in order to use another
template system. A template backend is a class that inherits
``django.template.backends.base.BaseEngine``. It must implement
``get_template()`` and optionally ``from_string()``. Here's an example for a
fictional ``foobar`` template library::

    from django.template import TemplateDoesNotExist, TemplateSyntaxError
    from django.template.backends.base import BaseEngine
    from django.template.backends.utils import csrf_input_lazy, csrf_token_lazy

    import foobar


    class FooBar(BaseEngine):
        # Name of the subdirectory containing the templates for this engine
        # inside an installed application.
        app_dirname = "foobar"

        def __init__(self, params):
            params = params.copy()
            options = params.pop("OPTIONS").copy()
            super().__init__(params)

            self.engine = foobar.Engine(**options)

        def from_string(self, template_code):
            try:
                return Template(self.engine.from_string(template_code))
            except foobar.TemplateCompilationFailed as exc:
                raise TemplateSyntaxError(exc.args)

        def get_template(self, template_name):
            try:
                return Template(self.engine.get_template(template_name))
            except foobar.TemplateNotFound as exc:
                raise TemplateDoesNotExist(exc.args, backend=self)
            except foobar.TemplateCompilationFailed as exc:
                raise TemplateSyntaxError(exc.args)


    class Template:
        def __init__(self, template):
            self.template = template

        def render(self, context=None, request=None):
            if context is None:
                context = {}
            if request is not None:
                context["request"] = request
                context["csrf_input"] = csrf_input_lazy(request)
                context["csrf_token"] = csrf_token_lazy(request)
            return self.template.render(context)

See `DEP 182`_ for more information.

.. _template-debug-integration:

Debug integration for custom engines
------------------------------------

The Django debug page has hooks to provide detailed information when a template
error arises. Custom template engines can use these hooks to enhance the
traceback information that appears to users. The following hooks are available:

.. _template-postmortem:

Template postmortem
~~~~~~~~~~~~~~~~~~~

The postmortem appears when :exc:`~django.template.TemplateDoesNotExist` is
raised. It lists the template engines and loaders that were used when trying to
find a given template. For example, if two Django engines are configured, the
postmortem will appear like:

.. image:: _images/postmortem.png

Custom engines can populate the postmortem by passing the ``backend`` and
``tried`` arguments when raising :exc:`~django.template.TemplateDoesNotExist`.
Backends that use the postmortem :ref:`should specify an origin
<template-origin-api>` on the template object.

Contextual line information
~~~~~~~~~~~~~~~~~~~~~~~~~~~

If an error happens during template parsing or rendering, Django can display
the line the error happened on. For example:

.. image:: _images/template-lines.png

Custom engines can populate this information by setting a ``template_debug``
attribute on exceptions raised during parsing and rendering. This attribute is
a :class:`dict` with the following values:

* ``'name'``: The name of the template in which the exception occurred.

* ``'message'``: The exception message.

* ``'source_lines'``: The lines before, after, and including the line the
  exception occurred on. This is for context, so it shouldn't contain more than
  20 lines or so.

* ``'line'``: The line number on which the exception occurred.

* ``'before'``: The content on the error line before the token that raised the
  error.

* ``'during'``: The token that raised the error.

* ``'after'``: The content on the error line after the token that raised the
  error.

* ``'total'``: The number of lines in ``source_lines``.

* ``'top'``: The line number where ``source_lines`` starts.

* ``'bottom'``: The line number where ``source_lines`` ends.

Given the above template error, ``template_debug`` would look like::

    {
        "name": "/path/to/template.html",
        "message": "Invalid block tag: 'syntax'",
        "source_lines": [
            (1, "some\n"),
            (2, "lines\n"),
            (3, "before\n"),
            (4, "Hello {% syntax error %} {{ world }}\n"),
            (5, "some\n"),
            (6, "lines\n"),
            (7, "after\n"),
            (8, ""),
        ],
        "line": 4,
        "before": "Hello ",
        "during": "{% syntax error %}",
        "after": " {{ world }}\n",
        "total": 9,
        "bottom": 9,
        "top": 1,
    }

.. _template-origin-api:

Origin API and 3rd-party integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Django templates have an :class:`~django.template.base.Origin` object available
through the ``template.origin`` attribute. This enables debug information to be
displayed in the :ref:`template postmortem <template-postmortem>`, as well as
in 3rd-party libraries, like the :pypi:`Django Debug Toolbar
<django-debug-toolbar>`.

Custom engines can provide their own ``template.origin`` information by
creating an object that specifies the following attributes:

* ``'name'``: The full path to the template.

* ``'template_name'``: The relative path to the template as passed into the
  template loading methods.

* ``'loader_name'``: An optional string identifying the function or class used
  to load the template, e.g. ``django.template.loaders.filesystem.Loader``.

.. _DEP 182: https://github.com/django/deps/blob/main/final/0182-multiple-template-engines.rst


================================================
File: docs/howto/custom-template-tags.txt
================================================
==============================================
How to create custom template tags and filters
==============================================

Django's template language comes with a wide variety of :doc:`built-in
tags and filters </ref/templates/builtins>` designed to address the
presentation logic needs of your application. Nevertheless, you may
find yourself needing functionality that is not covered by the core
set of template primitives. You can extend the template engine by
defining custom tags and filters using Python, and then make them
available to your templates using the :ttag:`{% load %}<load>` tag.

Code layout
===========

The most common place to specify custom template tags and filters is inside
a Django app. If they relate to an existing app, it makes sense to bundle them
there; otherwise, they can be added to a new app. When a Django app is added
to :setting:`INSTALLED_APPS`, any tags it defines in the conventional location
described below are automatically made available to load within templates.

The app should contain a ``templatetags`` directory, at the same level as
``models.py``, ``views.py``, etc. If this doesn't already exist, create it -
don't forget the ``__init__.py`` file to ensure the directory is treated as a
Python package.

.. admonition:: Development server won't automatically restart

    After adding the ``templatetags``  module, you will need to restart your
    server before you can use the tags or filters in templates.

Your custom tags and filters will live in a module inside the ``templatetags``
directory. The name of the module file is the name you'll use to load the tags
later, so be careful to pick a name that won't clash with custom tags and
filters in another app.

For example, if your custom tags/filters are in a file called
``poll_extras.py``, your app layout might look like this:

.. code-block:: text

    polls/
        __init__.py
        models.py
        templatetags/
            __init__.py
            poll_extras.py
        views.py

And in your template you would use the following:

.. code-block:: html+django

    {% load poll_extras %}

The app that contains the custom tags must be in :setting:`INSTALLED_APPS` in
order for the :ttag:`{% load %}<load>` tag to work. This is a security feature:
It allows you to host Python code for many template libraries on a single host
machine without enabling access to all of them for every Django installation.

There's no limit on how many modules you put in the ``templatetags`` package.
Just keep in mind that a :ttag:`{% load %}<load>` statement will load
tags/filters for the given Python module name, not the name of the app.

To be a valid tag library, the module must contain a module-level variable
named ``register`` that is a ``template.Library`` instance, in which all the
tags and filters are registered. So, near the top of your module, put the
following::

    from django import template

    register = template.Library()

Alternatively, template tag modules can be registered through the
``'libraries'`` argument to
:class:`~django.template.backends.django.DjangoTemplates`. This is useful if
you want to use a different label from the template tag module name when
loading template tags. It also enables you to register tags without installing
an application.

.. admonition:: Behind the scenes

    For a ton of examples, read the source code for Django's default filters
    and tags. They're in :source:`django/template/defaultfilters.py` and
    :source:`django/template/defaulttags.py`, respectively.

    For more information on the :ttag:`load` tag, read its documentation.

.. _howto-writing-custom-template-filters:

Writing custom template filters
===============================

Custom filters are Python functions that take one or two arguments:

* The value of the variable (input) -- not necessarily a string.
* The value of the argument -- this can have a default value, or be left
  out altogether.

For example, in the filter ``{{ var|foo:"bar" }}``, the filter ``foo`` would be
passed the variable ``var`` and the argument ``"bar"``.

Since the template language doesn't provide exception handling, any exception
raised from a template filter will be exposed as a server error. Thus, filter
functions should avoid raising exceptions if there is a reasonable fallback
value to return. In case of input that represents a clear bug in a template,
raising an exception may still be better than silent failure which hides the
bug.

Here's an example filter definition::

    def cut(value, arg):
        """Removes all values of arg from the given string"""
        return value.replace(arg, "")

And here's an example of how that filter would be used:

.. code-block:: html+django

    {{ somevariable|cut:"0" }}

Most filters don't take arguments. In this case, leave the argument out of your
function::

    def lower(value):  # Only one argument.
        """Converts a string into all lowercase"""
        return value.lower()

Registering custom filters
--------------------------

.. method:: django.template.Library.filter()

Once you've written your filter definition, you need to register it with
your ``Library`` instance, to make it available to Django's template language::

    register.filter("cut", cut)
    register.filter("lower", lower)

The ``Library.filter()`` method takes two arguments:

1. The name of the filter -- a string.
2. The compilation function -- a Python function (not the name of the
   function as a string).

You can use ``register.filter()`` as a decorator instead::

    @register.filter(name="cut")
    def cut(value, arg):
        return value.replace(arg, "")


    @register.filter
    def lower(value):
        return value.lower()

If you leave off the ``name`` argument, as in the second example above, Django
will use the function's name as the filter name.

Finally, ``register.filter()`` also accepts three keyword arguments,
``is_safe``, ``needs_autoescape``, and ``expects_localtime``. These arguments
are described in :ref:`filters and auto-escaping <filters-auto-escaping>` and
:ref:`filters and time zones <filters-timezones>` below.

Template filters that expect strings
------------------------------------

.. method:: django.template.defaultfilters.stringfilter()

If you're writing a template filter that only expects a string as the first
argument, you should use the decorator ``stringfilter``. This will
convert an object to its string value before being passed to your function::

    from django import template
    from django.template.defaultfilters import stringfilter

    register = template.Library()


    @register.filter
    @stringfilter
    def lower(value):
        return value.lower()

This way, you'll be able to pass, say, an integer to this filter, and it
won't cause an ``AttributeError`` (because integers don't have ``lower()``
methods).

.. _filters-auto-escaping:

Filters and auto-escaping
-------------------------

When writing a custom filter, give some thought to how the filter will interact
with Django's auto-escaping behavior. Note that two types of strings can be
passed around inside the template code:

* **Raw strings** are the native Python strings. On output, they're escaped if
  auto-escaping is in effect and presented unchanged, otherwise.

* **Safe strings** are strings that have been marked safe from further
  escaping at output time. Any necessary escaping has already been done.
  They're commonly used for output that contains raw HTML that is intended
  to be interpreted as-is on the client side.

  Internally, these strings are of type
  :class:`~django.utils.safestring.SafeString`. You can test for them
  using code like::

      from django.utils.safestring import SafeString

      if isinstance(value, SafeString):
          # Do something with the "safe" string.
          ...

Template filter code falls into one of two situations:

1. Your filter does not introduce any HTML-unsafe characters (``<``, ``>``,
   ``'``, ``"`` or ``&``) into the result that were not already present. In
   this case, you can let Django take care of all the auto-escaping
   handling for you. All you need to do is set the ``is_safe`` flag to ``True``
   when you register your filter function, like so::

       @register.filter(is_safe=True)
       def myfilter(value):
           return value

   This flag tells Django that if a "safe" string is passed into your
   filter, the result will still be "safe" and if a non-safe string is
   passed in, Django will automatically escape it, if necessary.

   You can think of this as meaning "this filter is safe -- it doesn't
   introduce any possibility of unsafe HTML."

   The reason ``is_safe`` is necessary is because there are plenty of
   normal string operations that will turn a ``SafeData`` object back into
   a normal ``str`` object and, rather than try to catch them all, which would
   be very difficult, Django repairs the damage after the filter has completed.

   For example, suppose you have a filter that adds the string ``xx`` to
   the end of any input. Since this introduces no dangerous HTML characters
   to the result (aside from any that were already present), you should
   mark your filter with ``is_safe``::

       @register.filter(is_safe=True)
       def add_xx(value):
           return "%sxx" % value

   When this filter is used in a template where auto-escaping is enabled,
   Django will escape the output whenever the input is not already marked
   as "safe".

   By default, ``is_safe`` is ``False``, and you can omit it from any filters
   where it isn't required.

   Be careful when deciding if your filter really does leave safe strings
   as safe. If you're *removing* characters, you might inadvertently leave
   unbalanced HTML tags or entities in the result. For example, removing a
   ``>`` from the input might turn ``<a>`` into ``<a``, which would need to
   be escaped on output to avoid causing problems. Similarly, removing a
   semicolon (``;``) can turn ``&amp;`` into ``&amp``, which is no longer a
   valid entity and thus needs further escaping. Most cases won't be nearly
   this tricky, but keep an eye out for any problems like that when
   reviewing your code.

   Marking a filter ``is_safe`` will coerce the filter's return value to
   a string.  If your filter should return a boolean or other non-string
   value, marking it ``is_safe`` will probably have unintended
   consequences (such as converting a boolean False to the string
   'False').

2. Alternatively, your filter code can manually take care of any necessary
   escaping. This is necessary when you're introducing new HTML markup into
   the result. You want to mark the output as safe from further
   escaping so that your HTML markup isn't escaped further, so you'll need
   to handle the input yourself.

   To mark the output as a safe string, use
   :func:`django.utils.safestring.mark_safe`.

   Be careful, though. You need to do more than just mark the output as
   safe. You need to ensure it really *is* safe, and what you do depends on
   whether auto-escaping is in effect. The idea is to write filters that
   can operate in templates where auto-escaping is either on or off in
   order to make things easier for your template authors.

   In order for your filter to know the current auto-escaping state, set the
   ``needs_autoescape`` flag to ``True`` when you register your filter function.
   (If you don't specify this flag, it defaults to ``False``). This flag tells
   Django that your filter function wants to be passed an extra keyword
   argument, called ``autoescape``, that is ``True`` if auto-escaping is in
   effect and ``False`` otherwise. It is recommended to set the default of the
   ``autoescape`` parameter to ``True``, so that if you call the function
   from Python code it will have escaping enabled by default.

   For example, let's write a filter that emphasizes the first character of
   a string::

      from django import template
      from django.utils.html import conditional_escape
      from django.utils.safestring import mark_safe

      register = template.Library()


      @register.filter(needs_autoescape=True)
      def initial_letter_filter(text, autoescape=True):
          first, other = text[0], text[1:]
          if autoescape:
              esc = conditional_escape
          else:
              esc = lambda x: x
          result = "<strong>%s</strong>%s" % (esc(first), esc(other))
          return mark_safe(result)

   The ``needs_autoescape`` flag and the ``autoescape`` keyword argument mean
   that our function will know whether automatic escaping is in effect when the
   filter is called. We use ``autoescape`` to decide whether the input data
   needs to be passed through ``django.utils.html.conditional_escape`` or not.
   (In the latter case, we use the identity function as the "escape" function.)
   The ``conditional_escape()`` function is like ``escape()`` except it only
   escapes input that is **not** a ``SafeData`` instance. If a ``SafeData``
   instance is passed to ``conditional_escape()``, the data is returned
   unchanged.

   Finally, in the above example, we remember to mark the result as safe
   so that our HTML is inserted directly into the template without further
   escaping.

   There's no need to worry about the ``is_safe`` flag in this case
   (although including it wouldn't hurt anything). Whenever you manually
   handle the auto-escaping issues and return a safe string, the
   ``is_safe`` flag won't change anything either way.

.. warning:: Avoiding XSS vulnerabilities when reusing built-in filters

    Django's built-in filters have ``autoescape=True`` by default in order to
    get the proper autoescaping behavior and avoid a cross-site script
    vulnerability.

    In older versions of Django, be careful when reusing Django's built-in
    filters as ``autoescape`` defaults to ``None``. You'll need to pass
    ``autoescape=True`` to get autoescaping.

    For example, if you wanted to write a custom filter called
    ``urlize_and_linebreaks`` that combined the :tfilter:`urlize` and
    :tfilter:`linebreaksbr` filters, the filter would look like::

        from django.template.defaultfilters import linebreaksbr, urlize


        @register.filter(needs_autoescape=True)
        def urlize_and_linebreaks(text, autoescape=True):
            return linebreaksbr(urlize(text, autoescape=autoescape), autoescape=autoescape)

    Then:

    .. code-block:: html+django

        {{ comment|urlize_and_linebreaks }}

    would be equivalent to:

    .. code-block:: html+django

        {{ comment|urlize|linebreaksbr }}

.. _filters-timezones:

Filters and time zones
----------------------

If you write a custom filter that operates on :class:`~datetime.datetime`
objects, you'll usually register it with the ``expects_localtime`` flag set to
``True``::

    @register.filter(expects_localtime=True)
    def businesshours(value):
        try:
            return 9 <= value.hour < 17
        except AttributeError:
            return ""

When this flag is set, if the first argument to your filter is a time zone
aware datetime, Django will convert it to the current time zone before passing
it to your filter when appropriate, according to :ref:`rules for time zones
conversions in templates <time-zones-in-templates>`.

.. _howto-writing-custom-template-tags:

Writing custom template tags
============================

Tags are more complex than filters, because tags can do anything. Django
provides a number of shortcuts that make writing most types of tags easier.
First we'll explore those shortcuts, then explain how to write a tag from
scratch for those cases when the shortcuts aren't powerful enough.

.. _howto-custom-template-tags-simple-tags:

Simple tags
-----------

.. method:: django.template.Library.simple_tag()

Many template tags take a number of arguments -- strings or template variables
-- and return a result after doing some processing based solely on
the input arguments and some external information. For example, a
``current_time`` tag might accept a format string and return the time as a
string formatted accordingly.

To ease the creation of these types of tags, Django provides a helper function,
``simple_tag``. This function, which is a method of
``django.template.Library``, takes a function that accepts any number of
arguments, wraps it in a ``render`` function and the other necessary bits
mentioned above and registers it with the template system.

Our ``current_time`` function could thus be written like this::

    import datetime
    from django import template

    register = template.Library()


    @register.simple_tag
    def current_time(format_string):
        return datetime.datetime.now().strftime(format_string)

A few things to note about the ``simple_tag`` helper function:

* Checking for the required number of arguments, etc., has already been
  done by the time our function is called, so we don't need to do that.
* The quotes around the argument (if any) have already been stripped away,
  so we receive a plain string.
* If the argument was a template variable, our function is passed the
  current value of the variable, not the variable itself.

Unlike other tag utilities, ``simple_tag`` passes its output through
:func:`~django.utils.html.conditional_escape` if the template context is in
autoescape mode, to ensure correct HTML and protect you from XSS
vulnerabilities.

If additional escaping is not desired, you will need to use
:func:`~django.utils.safestring.mark_safe` if you are absolutely sure that your
code does not contain XSS vulnerabilities. For building small HTML snippets,
use of :func:`~django.utils.html.format_html` instead of ``mark_safe()`` is
strongly recommended.

If your template tag needs to access the current context, you can use the
``takes_context`` argument when registering your tag::

    @register.simple_tag(takes_context=True)
    def current_time(context, format_string):
        timezone = context["timezone"]
        return your_get_current_time_method(timezone, format_string)

Note that the first argument *must* be called ``context``.

For more information on how the ``takes_context`` option works, see the section
on :ref:`inclusion tags<howto-custom-template-tags-inclusion-tags>`.

If you need to rename your tag, you can provide a custom name for it::

    register.simple_tag(lambda x: x - 1, name="minusone")


    @register.simple_tag(name="minustwo")
    def some_function(value):
        return value - 2

``simple_tag`` functions may accept any number of positional or keyword
arguments. For example::

    @register.simple_tag
    def my_tag(a, b, *args, **kwargs):
        warning = kwargs["warning"]
        profile = kwargs["profile"]
        ...
        return ...

Then in the template any number of arguments, separated by spaces, may be
passed to the template tag. Like in Python, the values for keyword arguments
are set using the equal sign ("``=``") and must be provided after the
positional arguments. For example:

.. code-block:: html+django

    {% my_tag 123 "abcd" book.title warning=message|lower profile=user.profile %}

It's possible to store the tag results in a template variable rather than
directly outputting it. This is done by using the ``as`` argument followed by
the variable name. Doing so enables you to output the content yourself where
you see fit:

.. code-block:: html+django

    {% current_time "%Y-%m-%d %I:%M %p" as the_time %}
    <p>The time is {{ the_time }}.</p>

.. _howto-custom-template-tags-simple-block-tags:

Simple block tags
-----------------

.. versionadded:: 5.2

.. method:: django.template.Library.simple_block_tag()

When a section of rendered template needs to be passed into a custom tag,
Django provides the ``simple_block_tag`` helper function to accomplish this.
Similar to :meth:`~django.template.Library.simple_tag()`, this function accepts
a custom tag function, but with the additional ``content`` argument, which
contains the rendered content as defined inside the tag. This allows dynamic
template sections to be easily incorporated into custom tags.

For example, a custom block tag which creates a chart could look like this::

    from django import template
    from myapp.charts import render_chart

    register = template.Library()


    @register.simple_block_tag
    def chart(content):
        return render_chart(source=content)

The ``content`` argument contains everything in between the ``{% chart %}``
and ``{% endchart %}`` tags:

.. code-block:: html+django

    {% chart %}
      digraph G {
          label = "Chart for {{ request.user }}"
          A -> {B C}
      }
    {% endchart %}

If there are other template tags or variables inside the ``content`` block,
they will be rendered before being passed to the tag function. In the example
above, ``request.user`` will be resolved by the time ``render_chart`` is
called.

Block tags are closed with ``end{name}`` (for example, ``endchart``). This can
be customized with the ``end_name`` parameter::

    @register.simple_block_tag(end_name="endofchart")
    def chart(content):
        return render_chart(source=content)

Which would require a template definition like this:

.. code-block:: html+django

    {% chart %}
      digraph G {
          label = "Chart for {{ request.user }}"
          A -> {B C}
      }
    {% endofchart %}

A few things to note about ``simple_block_tag``:

* The first argument must be called ``content``, and it will contain the
  contents of the template tag as a rendered string.
* Variables passed to the tag are not included in the rendering context of the
  content, as would be when using the ``{% with %}`` tag.

Just like :ref:`simple_tag<howto-custom-template-tags-simple-tags>`,
``simple_block_tag``:

* Validates the quantity and quality of the arguments.
* Strips quotes from arguments if necessary.
* Escapes the output accordingly.
* Supports passing ``takes_context=True`` at registration time to access
  context. Note that in this case, the first argument to the custom function
  *must* be called ``context``, and ``content`` must follow.
* Supports renaming the tag by passing the ``name`` argument when registering.
* Supports accepting any number of positional or keyword arguments.
* Supports storing the result in a template variable using the ``as`` variant.

.. admonition::  Content Escaping

    ``simple_block_tag`` behaves similarly to ``simple_tag`` regarding
    auto-escaping. For details on escaping and safety, refer to ``simple_tag``.
    Because the ``content`` argument has already been rendered by Django, it is
    already escaped.

A complete example
~~~~~~~~~~~~~~~~~~

Consider a custom template tag that generates a message box that supports
multiple message levels and content beyond a simple phrase. This could be
implemented using a ``simple_block_tag`` as follows:

.. code-block:: python
    :caption: ``testapp/templatetags/testapptags.py``

    from django import template
    from django.utils.html import format_html


    register = template.Library()


    @register.simple_block_tag(takes_context=True)
    def msgbox(context, content, level):
        format_kwargs = {
            "level": level.lower(),
            "level_title": level.capitalize(),
            "content": content,
            "open": " open" if level.lower() == "error" else "",
            "site": context.get("site", "My Site"),
        }
        result = """
        <div class="msgbox {level}">
          <details{open}>
            <summary>
              <strong>{level_title}</strong>: Please read for <i>{site}</i>
            </summary>
            <p>
              {content}
            </p>
          </details>
        </div>
        """
        return format_html(result, **format_kwargs)

When combined with a minimal view and corresponding template, as shown here:

.. code-block:: python
    :caption: ``testapp/views.py``

    from django.shortcuts import render


    def simpleblocktag_view(request):
        return render(request, "test.html", context={"site": "Important Site"})


.. code-block:: html+django
    :caption: ``testapp/templates/test.html``

    {% extends "base.html" %}

    {% load testapptags %}

    {% block content %}

      {% msgbox level="error" %}
        Please fix all errors. Further documentation can be found at
        <a href="http://example.com">Docs</a>.
      {% endmsgbox %}

      {% msgbox level="info" %}
        More information at: <a href="http://othersite.com">Other Site</a>/
      {% endmsgbox %}

    {% endblock %}

The following HTML is produced as the rendered output:

.. code-block:: html

    <div class="msgbox error">
      <details open>
        <summary>
          <strong>Error</strong>: Please read for <i>Important Site</i>
        </summary>
        <p>
          Please fix all errors. Further documentation can be found at
          <a href="http://example.com">Docs</a>.
        </p>
      </details>
    </div>

    <div class="msgbox info">
      <details>
        <summary>
          <strong>Info</strong>: Please read for <i>Important Site</i>
        </summary>
        <p>
          More information at: <a href="http://othersite.com">Other Site</a>
        </p>
      </details>
    </div>

.. _howto-custom-template-tags-inclusion-tags:

Inclusion tags
--------------

.. method:: django.template.Library.inclusion_tag()

Another common type of template tag is the type that displays some data by
rendering *another* template. For example, Django's admin interface uses custom
template tags to display the buttons along the bottom of the "add/change" form
pages. Those buttons always look the same, but the link targets change
depending on the object being edited -- so they're a perfect case for using a
small template that is filled with details from the current object. (In the
admin's case, this is the ``submit_row`` tag.)

These sorts of tags are called "inclusion tags".

Writing inclusion tags is probably best demonstrated by example. Let's write a
tag that outputs a list of choices for a given ``Poll`` object, such as was
created in the :ref:`tutorials <creating-models>`. We'll use the tag like this:

.. code-block:: html+django

    {% show_results poll %}

...and the output will be something like this:

.. code-block:: html

    <ul>
      <li>First choice</li>
      <li>Second choice</li>
      <li>Third choice</li>
    </ul>

First, define the function that takes the argument and produces a dictionary of
data for the result. The important point here is we only need to return a
dictionary, not anything more complex. This will be used as a template context
for the template fragment. Example::

    def show_results(poll):
        choices = poll.choice_set.all()
        return {"choices": choices}

Next, create the template used to render the tag's output. This template is a
fixed feature of the tag: the tag writer specifies it, not the template
designer. Following our example, the template is very short:

.. code-block:: html+django

    <ul>
    {% for choice in choices %}
        <li> {{ choice }} </li>
    {% endfor %}
    </ul>

Now, create and register the inclusion tag by calling the ``inclusion_tag()``
method on a ``Library`` object. Following our example, if the above template is
in a file called ``results.html`` in a directory that's searched by the
template loader, we'd register the tag like this::

    # Here, register is a django.template.Library instance, as before
    @register.inclusion_tag("results.html")
    def show_results(poll): ...

Alternatively it is possible to register the inclusion tag using a
:class:`django.template.Template` instance::

    from django.template.loader import get_template

    t = get_template("results.html")
    register.inclusion_tag(t)(show_results)

...when first creating the function.

Sometimes, your inclusion tags might require a large number of arguments,
making it a pain for template authors to pass in all the arguments and remember
their order. To solve this, Django provides a ``takes_context`` option for
inclusion tags. If you specify ``takes_context`` in creating a template tag,
the tag will have no required arguments, and the underlying Python function
will have one argument -- the template context as of when the tag was called.

For example, say you're writing an inclusion tag that will always be used in a
context that contains ``home_link`` and ``home_title`` variables that point
back to the main page. Here's what the Python function would look like::

    @register.inclusion_tag("link.html", takes_context=True)
    def jump_link(context):
        return {
            "link": context["home_link"],
            "title": context["home_title"],
        }

Note that the first parameter to the function *must* be called ``context``.

In that ``register.inclusion_tag()`` line, we specified ``takes_context=True``
and the name of the template. Here's what the template ``link.html`` might look
like:

.. code-block:: html+django

    Jump directly to <a href="{{ link }}">{{ title }}</a>.

Then, any time you want to use that custom tag, load its library and call it
without any arguments, like so:

.. code-block:: html+django

    {% jump_link %}

Note that when you're using ``takes_context=True``, there's no need to pass
arguments to the template tag. It automatically gets access to the context.

The ``takes_context`` parameter defaults to ``False``. When it's set to
``True``, the tag is passed the context object, as in this example. That's the
only difference between this case and the previous ``inclusion_tag`` example.

``inclusion_tag`` functions may accept any number of positional or keyword
arguments. For example::

    @register.inclusion_tag("my_template.html")
    def my_tag(a, b, *args, **kwargs):
        warning = kwargs["warning"]
        profile = kwargs["profile"]
        ...
        return ...

Then in the template any number of arguments, separated by spaces, may be
passed to the template tag. Like in Python, the values for keyword arguments
are set using the equal sign ("``=``") and must be provided after the
positional arguments. For example:

.. code-block:: html+django

    {% my_tag 123 "abcd" book.title warning=message|lower profile=user.profile %}

Advanced custom template tags
-----------------------------

Sometimes the basic features for custom template tag creation aren't enough.
Don't worry, Django gives you complete access to the internals required to build
a template tag from the ground up.

A quick overview
----------------

The template system works in a two-step process: compiling and rendering. To
define a custom template tag, you specify how the compilation works and how
the rendering works.

When Django compiles a template, it splits the raw template text into
''nodes''. Each node is an instance of ``django.template.Node`` and has
a ``render()`` method. A compiled template is a list of ``Node`` objects. When
you call ``render()`` on a compiled template object, the template calls
``render()`` on each ``Node`` in its node list, with the given context.  The
results are all concatenated together to form the output of the template.

Thus, to define a custom template tag, you specify how the raw template tag is
converted into a ``Node`` (the compilation function), and what the node's
``render()`` method does.

Writing the compilation function
--------------------------------

For each template tag the template parser encounters, it calls a Python
function with the tag contents and the parser object itself. This function is
responsible for returning a ``Node`` instance based on the contents of the tag.

For example, let's write a full implementation of our template tag,
``{% current_time %}``, that displays the current date/time, formatted according
to a parameter given in the tag, in :func:`~time.strftime` syntax. It's a good
idea to decide the tag syntax before anything else. In our case, let's say the
tag should be used like this:

.. code-block:: html+django

    <p>The time is {% current_time "%Y-%m-%d %I:%M %p" %}.</p>

The parser for this function should grab the parameter and create a ``Node``
object::

    from django import template


    def do_current_time(parser, token):
        try:
            # split_contents() knows not to split quoted strings.
            tag_name, format_string = token.split_contents()
        except ValueError:
            raise template.TemplateSyntaxError(
                "%r tag requires a single argument" % token.contents.split()[0]
            )
        if not (format_string[0] == format_string[-1] and format_string[0] in ('"', "'")):
            raise template.TemplateSyntaxError(
                "%r tag's argument should be in quotes" % tag_name
            )
        return CurrentTimeNode(format_string[1:-1])

Notes:

* ``parser`` is the template parser object. We don't need it in this
  example.

* ``token.contents`` is a string of the raw contents of the tag. In our
  example, it's ``'current_time "%Y-%m-%d %I:%M %p"'``.

* The ``token.split_contents()`` method separates the arguments on spaces
  while keeping quoted strings together. The more straightforward
  ``token.contents.split()`` wouldn't be as robust, as it would naively
  split on *all* spaces, including those within quoted strings. It's a good
  idea to always use ``token.split_contents()``.

* This function is responsible for raising
  ``django.template.TemplateSyntaxError``, with helpful messages, for
  any syntax error.

* The ``TemplateSyntaxError`` exceptions use the ``tag_name`` variable.
  Don't hard-code the tag's name in your error messages, because that
  couples the tag's name to your function. ``token.contents.split()[0]``
  will ''always'' be the name of your tag -- even when the tag has no
  arguments.

* The function returns a ``CurrentTimeNode`` with everything the node needs
  to know about this tag. In this case, it passes the argument --
  ``"%Y-%m-%d %I:%M %p"``. The leading and trailing quotes from the
  template tag are removed in ``format_string[1:-1]``.

* The parsing is very low-level. The Django developers have experimented
  with writing small frameworks on top of this parsing system, using
  techniques such as EBNF grammars, but those experiments made the template
  engine too slow. It's low-level because that's fastest.

Writing the renderer
--------------------

The second step in writing custom tags is to define a ``Node`` subclass that
has a ``render()`` method.

Continuing the above example, we need to define ``CurrentTimeNode``::

    import datetime
    from django import template


    class CurrentTimeNode(template.Node):
        def __init__(self, format_string):
            self.format_string = format_string

        def render(self, context):
            return datetime.datetime.now().strftime(self.format_string)

Notes:

* ``__init__()`` gets the ``format_string`` from ``do_current_time()``.
  Always pass any options/parameters/arguments to a ``Node`` via its
  ``__init__()``.

* The ``render()`` method is where the work actually happens.

* ``render()`` should generally fail silently, particularly in a production
  environment. In some cases however, particularly if
  ``context.template.engine.debug`` is ``True``, this method may raise an
  exception to make debugging easier. For example, several core tags raise
  ``django.template.TemplateSyntaxError`` if they receive the wrong number or
  type of arguments.

Ultimately, this decoupling of compilation and rendering results in an
efficient template system, because a template can render multiple contexts
without having to be parsed multiple times.

.. _tags-auto-escaping:

Auto-escaping considerations
----------------------------

The output from template tags is **not** automatically run through the
auto-escaping filters (with the exception of
:meth:`~django.template.Library.simple_tag` as described above). However, there
are still a couple of things you should keep in mind when writing a template
tag.

If the ``render()`` method of your template tag stores the result in a context
variable (rather than returning the result in a string), it should take care
to call ``mark_safe()`` if appropriate. When the variable is ultimately
rendered, it will be affected by the auto-escape setting in effect at the
time, so content that should be safe from further escaping needs to be marked
as such.

Also, if your template tag creates a new context for performing some
sub-rendering, set the auto-escape attribute to the current context's value.
The ``__init__`` method for the ``Context`` class takes a parameter called
``autoescape`` that you can use for this purpose. For example::

    from django.template import Context


    def render(self, context):
        # ...
        new_context = Context({"var": obj}, autoescape=context.autoescape)
        # ... Do something with new_context ...

This is not a very common situation, but it's useful if you're rendering a
template yourself. For example::

    def render(self, context):
        t = context.template.engine.get_template("small_fragment.html")
        return t.render(Context({"var": obj}, autoescape=context.autoescape))

If we had neglected to pass in the current ``context.autoescape`` value to our
new ``Context`` in this example, the results would have *always* been
automatically escaped, which may not be the desired behavior if the template
tag is used inside a :ttag:`{% autoescape off %}<autoescape>` block.

.. _template_tag_thread_safety:

Thread-safety considerations
----------------------------

Once a node is parsed, its ``render`` method may be called any number of times.
Since Django is sometimes run in multi-threaded environments, a single node may
be simultaneously rendering with different contexts in response to two separate
requests. Therefore, it's important to make sure your template tags are thread
safe.

To make sure your template tags are thread safe, you should never store state
information on the node itself. For example, Django provides a builtin
:ttag:`cycle` template tag that cycles among a list of given strings each time
it's rendered:

.. code-block:: html+django

    {% for o in some_list %}
        <tr class="{% cycle 'row1' 'row2' %}">
            ...
        </tr>
    {% endfor %}

A naive implementation of ``CycleNode`` might look something like this::

    import itertools
    from django import template


    class CycleNode(template.Node):
        def __init__(self, cyclevars):
            self.cycle_iter = itertools.cycle(cyclevars)

        def render(self, context):
            return next(self.cycle_iter)

But, suppose we have two templates rendering the template snippet from above at
the same time:

#. Thread 1 performs its first loop iteration, ``CycleNode.render()``
   returns 'row1'
#. Thread 2 performs its first loop iteration, ``CycleNode.render()``
   returns 'row2'
#. Thread 1 performs its second loop iteration, ``CycleNode.render()``
   returns 'row1'
#. Thread 2 performs its second loop iteration, ``CycleNode.render()``
   returns 'row2'

The CycleNode is iterating, but it's iterating globally. As far as Thread 1
and Thread 2 are concerned, it's always returning the same value. This is
not what we want!

To address this problem, Django provides a ``render_context`` that's associated
with the ``context`` of the template that is currently being rendered. The
``render_context`` behaves like a Python dictionary, and should be used to
store ``Node`` state between invocations of the ``render`` method.

Let's refactor our ``CycleNode`` implementation to use the ``render_context``::

    class CycleNode(template.Node):
        def __init__(self, cyclevars):
            self.cyclevars = cyclevars

        def render(self, context):
            if self not in context.render_context:
                context.render_context[self] = itertools.cycle(self.cyclevars)
            cycle_iter = context.render_context[self]
            return next(cycle_iter)

Note that it's perfectly safe to store global information that will not change
throughout the life of the ``Node`` as an attribute. In the case of
``CycleNode``, the ``cyclevars`` argument doesn't change after the ``Node`` is
instantiated, so we don't need to put it in the ``render_context``. But state
information that is specific to the template that is currently being rendered,
like the current iteration of the ``CycleNode``, should be stored in the
``render_context``.

.. note::
    Notice how we used ``self`` to scope the ``CycleNode`` specific information
    within the ``render_context``. There may be multiple ``CycleNodes`` in a
    given template, so we need to be careful not to clobber another node's
    state information. The easiest way to do this is to always use ``self`` as
    the key into ``render_context``. If you're keeping track of several state
    variables, make ``render_context[self]`` a dictionary.

Registering the tag
-------------------

Finally, register the tag with your module's ``Library`` instance, as explained
in :ref:`writing custom template tags<howto-writing-custom-template-tags>`
above. Example::

    register.tag("current_time", do_current_time)

The ``tag()`` method takes two arguments:

1. The name of the template tag -- a string. If this is left out, the
   name of the compilation function will be used.
2. The compilation function -- a Python function (not the name of the
   function as a string).

As with filter registration, it is also possible to use this as a decorator::

    @register.tag(name="current_time")
    def do_current_time(parser, token): ...


    @register.tag
    def shout(parser, token): ...

If you leave off the ``name`` argument, as in the second example above, Django
will use the function's name as the tag name.

Passing template variables to the tag
-------------------------------------

Although you can pass any number of arguments to a template tag using
``token.split_contents()``, the arguments are all unpacked as
string literals. A little more work is required in order to pass dynamic
content (a template variable) to a template tag as an argument.

While the previous examples have formatted the current time into a string and
returned the string, suppose you wanted to pass in a
:class:`~django.db.models.DateTimeField` from an object and have the template
tag format that date-time:

.. code-block:: html+django

    <p>This post was last updated at {% format_time blog_entry.date_updated "%Y-%m-%d %I:%M %p" %}.</p>

Initially, ``token.split_contents()`` will return three values:

1. The tag name ``format_time``.
2. The string ``'blog_entry.date_updated'`` (without the surrounding
   quotes).
3. The formatting string ``'"%Y-%m-%d %I:%M %p"'``. The return value from
   ``split_contents()`` will include the leading and trailing quotes for
   string literals like this.

Now your tag should begin to look like this::

    from django import template


    def do_format_time(parser, token):
        try:
            # split_contents() knows not to split quoted strings.
            tag_name, date_to_be_formatted, format_string = token.split_contents()
        except ValueError:
            raise template.TemplateSyntaxError(
                "%r tag requires exactly two arguments" % token.contents.split()[0]
            )
        if not (format_string[0] == format_string[-1] and format_string[0] in ('"', "'")):
            raise template.TemplateSyntaxError(
                "%r tag's argument should be in quotes" % tag_name
            )
        return FormatTimeNode(date_to_be_formatted, format_string[1:-1])

You also have to change the renderer to retrieve the actual contents of the
``date_updated`` property of the ``blog_entry`` object.  This can be
accomplished by using the ``Variable()`` class in ``django.template``.

To use the ``Variable`` class, instantiate it with the name of the variable to
be resolved, and then call ``variable.resolve(context)``. So, for example::

    class FormatTimeNode(template.Node):
        def __init__(self, date_to_be_formatted, format_string):
            self.date_to_be_formatted = template.Variable(date_to_be_formatted)
            self.format_string = format_string

        def render(self, context):
            try:
                actual_date = self.date_to_be_formatted.resolve(context)
                return actual_date.strftime(self.format_string)
            except template.VariableDoesNotExist:
                return ""

Variable resolution will throw a ``VariableDoesNotExist`` exception if it
cannot resolve the string passed to it in the current context of the page.

Setting a variable in the context
---------------------------------

The above examples output a value. Generally, it's more flexible if your
template tags set template variables instead of outputting values. That way,
template authors can reuse the values that your template tags create.

To set a variable in the context, use dictionary assignment on the context
object in the ``render()`` method. Here's an updated version of
``CurrentTimeNode`` that sets a template variable ``current_time`` instead of
outputting it::

    import datetime
    from django import template


    class CurrentTimeNode2(template.Node):
        def __init__(self, format_string):
            self.format_string = format_string

        def render(self, context):
            context["current_time"] = datetime.datetime.now().strftime(self.format_string)
            return ""

Note that ``render()`` returns the empty string. ``render()`` should always
return string output. If all the template tag does is set a variable,
``render()`` should return the empty string.

Here's how you'd use this new version of the tag:

.. code-block:: html+django

    {% current_time "%Y-%m-%d %I:%M %p" %}<p>The time is {{ current_time }}.</p>

.. admonition:: Variable scope in context

    Any variable set in the context will only be available in the same
    ``block`` of the template in which it was assigned. This behavior is
    intentional; it provides a scope for variables so that they don't conflict
    with context in other blocks.

But, there's a problem with ``CurrentTimeNode2``: The variable name
``current_time`` is hard-coded. This means you'll need to make sure your
template doesn't use ``{{ current_time }}`` anywhere else, because the
``{% current_time %}`` will blindly overwrite that variable's value. A cleaner
solution is to make the template tag specify the name of the output variable,
like so:

.. code-block:: html+django

    {% current_time "%Y-%m-%d %I:%M %p" as my_current_time %}
    <p>The current time is {{ my_current_time }}.</p>

To do that, you'll need to refactor both the compilation function and ``Node``
class, like so::

    import re


    class CurrentTimeNode3(template.Node):
        def __init__(self, format_string, var_name):
            self.format_string = format_string
            self.var_name = var_name

        def render(self, context):
            context[self.var_name] = datetime.datetime.now().strftime(self.format_string)
            return ""


    def do_current_time(parser, token):
        # This version uses a regular expression to parse tag contents.
        try:
            # Splitting by None == splitting by spaces.
            tag_name, arg = token.contents.split(None, 1)
        except ValueError:
            raise template.TemplateSyntaxError(
                "%r tag requires arguments" % token.contents.split()[0]
            )
        m = re.search(r"(.*?) as (\w+)", arg)
        if not m:
            raise template.TemplateSyntaxError("%r tag had invalid arguments" % tag_name)
        format_string, var_name = m.groups()
        if not (format_string[0] == format_string[-1] and format_string[0] in ('"', "'")):
            raise template.TemplateSyntaxError(
                "%r tag's argument should be in quotes" % tag_name
            )
        return CurrentTimeNode3(format_string[1:-1], var_name)

The difference here is that ``do_current_time()`` grabs the format string and
the variable name, passing both to ``CurrentTimeNode3``.

Finally, if you only need to have a simple syntax for your custom
context-updating template tag, consider using the
:meth:`~django.template.Library.simple_tag` shortcut, which supports assigning
the tag results to a template variable.

Parsing until another block tag
-------------------------------

Template tags can work in tandem. For instance, the standard
:ttag:`{% comment %}<comment>` tag hides everything until ``{% endcomment %}``.
To create a template tag such as this, use ``parser.parse()`` in your
compilation function.

Here's how a simplified ``{% comment %}`` tag might be implemented::

    def do_comment(parser, token):
        nodelist = parser.parse(("endcomment",))
        parser.delete_first_token()
        return CommentNode()


    class CommentNode(template.Node):
        def render(self, context):
            return ""

.. note::
    The actual implementation of :ttag:`{% comment %}<comment>` is slightly
    different in that it allows broken template tags to appear between
    ``{% comment %}`` and ``{% endcomment %}``. It does so by calling
    ``parser.skip_past('endcomment')`` instead of ``parser.parse(('endcomment',))``
    followed by ``parser.delete_first_token()``, thus avoiding the generation of a
    node list.

``parser.parse()`` takes a tuple of names of block tags ''to parse until''. It
returns an instance of ``django.template.NodeList``, which is a list of
all ``Node`` objects that the parser encountered ''before'' it encountered
any of the tags named in the tuple.

In ``"nodelist = parser.parse(('endcomment',))"`` in the above example,
``nodelist`` is a list of all nodes between the ``{% comment %}`` and
``{% endcomment %}``, not counting ``{% comment %}`` and ``{% endcomment %}``
themselves.

After ``parser.parse()`` is called, the parser hasn't yet "consumed" the
``{% endcomment %}`` tag, so the code needs to explicitly call
``parser.delete_first_token()``.

``CommentNode.render()`` returns an empty string. Anything between
``{% comment %}`` and ``{% endcomment %}`` is ignored.

Parsing until another block tag, and saving contents
----------------------------------------------------

In the previous example, ``do_comment()`` discarded everything between
``{% comment %}`` and ``{% endcomment %}``. Instead of doing that, it's
possible to do something with the code between block tags.

For example, here's a custom template tag, ``{% upper %}``, that capitalizes
everything between itself and ``{% endupper %}``.

Usage:

.. code-block:: html+django

    {% upper %}This will appear in uppercase, {{ your_name }}.{% endupper %}

As in the previous example, we'll use ``parser.parse()``. But this time, we
pass the resulting ``nodelist`` to the ``Node``::

    def do_upper(parser, token):
        nodelist = parser.parse(("endupper",))
        parser.delete_first_token()
        return UpperNode(nodelist)


    class UpperNode(template.Node):
        def __init__(self, nodelist):
            self.nodelist = nodelist

        def render(self, context):
            output = self.nodelist.render(context)
            return output.upper()

The only new concept here is the ``self.nodelist.render(context)`` in
``UpperNode.render()``.

For more examples of complex rendering, see the source code of
:ttag:`{% for %}<for>` in :source:`django/template/defaulttags.py` and
:ttag:`{% if %}<if>` in :source:`django/template/smartif.py`.


================================================
File: docs/howto/delete-app.txt
================================================
==================================
How to delete a Django application
==================================

Django provides the ability to group sets of features into Python packages
called :doc:`applications</ref/applications/>`. When requirements change, apps
may become obsolete or unnecessary. The following steps will help you delete an
application safely.

#. Remove all references to the app (imports, foreign keys etc.).

#. Remove all models from the corresponding ``models.py`` file.

#. Create relevant migrations by running :djadmin:`makemigrations`. This step
   generates a migration that deletes tables for the removed models, and any
   other required migration for updating relationships connected to those
   models.

#. :ref:`Squash <migration-squashing>` out references to the app in other apps'
   migrations.

#. Apply migrations locally, runs tests, and verify the correctness of your
   project.

#. Deploy/release your updated Django project.

#. Remove the app from :setting:`INSTALLED_APPS`.

#. Finally, remove the app's directory.


================================================
File: docs/howto/error-reporting.txt
================================================
=============================
How to manage error reporting
=============================

When you're running a public site you should always turn off the
:setting:`DEBUG` setting. That will make your server run much faster, and will
also prevent malicious users from seeing details of your application that can be
revealed by the error pages.

However, running with :setting:`DEBUG` set to ``False`` means you'll never see
errors generated by your site -- everyone will instead see your public error
pages. You need to keep track of errors that occur in deployed sites, so Django
can be configured to create reports with details about those errors.

Email reports
=============

Server errors
-------------

When :setting:`DEBUG` is ``False``, Django will email the users listed in the
:setting:`ADMINS` setting whenever your code raises an unhandled exception and
results in an internal server error (strictly speaking, for any response with
an HTTP status code of 500 or greater). This gives the administrators immediate
notification of any errors. The :setting:`ADMINS` will get a description of the
error, a complete Python traceback, and details about the HTTP request that
caused the error.

.. note::

   In order to send email, Django requires a few settings telling it
   how to connect to your mail server. At the very least, you'll need
   to specify :setting:`EMAIL_HOST` and possibly
   :setting:`EMAIL_HOST_USER` and :setting:`EMAIL_HOST_PASSWORD`,
   though other settings may be also required depending on your mail
   server's configuration. Consult :doc:`the Django settings
   documentation </ref/settings>` for a full list of email-related
   settings.

By default, Django will send email from root@localhost. However, some mail
providers reject all email from this address. To use a different sender
address, modify the :setting:`SERVER_EMAIL` setting.

To activate this behavior, put the email addresses of the recipients in the
:setting:`ADMINS` setting.

.. seealso::

    Server error emails are sent using the logging framework, so you can
    customize this behavior by :doc:`customizing your logging configuration
    </topics/logging>`.

404 errors
----------

Django can also be configured to email errors about broken links (404 "page
not found" errors). Django sends emails about 404 errors when:

* :setting:`DEBUG` is ``False``;

* Your :setting:`MIDDLEWARE` setting includes
  :class:`django.middleware.common.BrokenLinkEmailsMiddleware`.

If those conditions are met, Django will email the users listed in the
:setting:`MANAGERS` setting whenever your code raises a 404 and the request has
a referer. It doesn't bother to email for 404s that don't have a referer --
those are usually people typing in broken URLs or broken web bots. It also
ignores 404s when the referer is equal to the requested URL, since this
behavior is from broken web bots too.

.. note::

    :class:`~django.middleware.common.BrokenLinkEmailsMiddleware` must appear
    before other middleware that intercepts 404 errors, such as
    :class:`~django.middleware.locale.LocaleMiddleware` or
    :class:`~django.contrib.flatpages.middleware.FlatpageFallbackMiddleware`.
    Put it toward the top of your :setting:`MIDDLEWARE` setting.

You can tell Django to stop reporting particular 404s by tweaking the
:setting:`IGNORABLE_404_URLS` setting. It should be a list of compiled
regular expression objects. For example::

    import re

    IGNORABLE_404_URLS = [
        re.compile(r"\.(php|cgi)$"),
        re.compile(r"^/phpmyadmin/"),
    ]

In this example, a 404 to any URL ending with ``.php`` or ``.cgi`` will *not* be
reported. Neither will any URL starting with ``/phpmyadmin/``.

The following example shows how to exclude some conventional URLs that browsers and
crawlers often request::

    import re

    IGNORABLE_404_URLS = [
        re.compile(r"^/apple-touch-icon.*\.png$"),
        re.compile(r"^/favicon\.ico$"),
        re.compile(r"^/robots\.txt$"),
    ]

(Note that these are regular expressions, so we put a backslash in front of
periods to escape them.)

If you'd like to customize the behavior of
:class:`django.middleware.common.BrokenLinkEmailsMiddleware` further (for
example to ignore requests coming from web crawlers), you should subclass it
and override its methods.

.. seealso::

    404 errors are logged using the logging framework. By default, these log
    records are ignored, but you can use them for error reporting by writing a
    handler and :doc:`configuring logging </topics/logging>` appropriately.

.. _filtering-error-reports:

Filtering error reports
=======================

.. warning::

    Filtering sensitive data is a hard problem, and it's nearly impossible to
    guarantee that sensitive data won't leak into an error report. Therefore,
    error reports should only be available to trusted team members and you
    should avoid transmitting error reports unencrypted over the internet
    (such as through email).

Filtering sensitive information
-------------------------------

.. currentmodule:: django.views.decorators.debug

Error reports are really helpful for debugging errors, so it is generally
useful to record as much relevant information about those errors as possible.
For example, by default Django records the `full traceback`_ for the
exception raised, each `traceback frame`_’s local variables, and the
:class:`~django.http.HttpRequest`’s :ref:`attributes<httprequest-attributes>`.

However, sometimes certain types of information may be too sensitive and thus
may not be appropriate to be kept track of, for example a user's password or
credit card number. So in addition to filtering out settings that appear to be
sensitive as described in the :setting:`DEBUG` documentation, Django offers a
set of function decorators to help you control which information should be
filtered out of error reports in a production environment (that is, where
:setting:`DEBUG` is set to ``False``): :func:`sensitive_variables` and
:func:`sensitive_post_parameters`.

.. _`full traceback`: https://en.wikipedia.org/wiki/Stack_trace
.. _`traceback frame`: https://en.wikipedia.org/wiki/Stack_frame

.. function:: sensitive_variables(*variables)

    If a function (either a view or any regular callback) in your code uses
    local variables susceptible to contain sensitive information, you may
    prevent the values of those variables from being included in error reports
    using the ``sensitive_variables`` decorator::

        from django.views.decorators.debug import sensitive_variables


        @sensitive_variables("user", "pw", "cc")
        def process_info(user):
            pw = user.pass_word
            cc = user.credit_card_number
            name = user.name
            ...

    In the above example, the values for the ``user``, ``pw`` and ``cc``
    variables will be hidden and replaced with stars (``**********``)
    in the error reports, whereas the value of the ``name`` variable will be
    disclosed.

    To systematically hide all local variables of a function from error logs,
    do not provide any argument to the ``sensitive_variables`` decorator::

        @sensitive_variables()
        def my_function(): ...

    .. admonition:: When using multiple decorators

        If the variable you want to hide is also a function argument (e.g.
        '``user``’ in the following example), and if the decorated function has
        multiple decorators, then make sure to place ``@sensitive_variables``
        at the top of the decorator chain. This way it will also hide the
        function argument as it gets passed through the other decorators::

            @sensitive_variables("user", "pw", "cc")
            @some_decorator
            @another_decorator
            def process_info(user): ...

.. function:: sensitive_post_parameters(*parameters)

    If one of your views receives an :class:`~django.http.HttpRequest` object
    with :attr:`POST parameters<django.http.HttpRequest.POST>` susceptible to
    contain sensitive information, you may prevent the values of those
    parameters from being included in the error reports using the
    ``sensitive_post_parameters`` decorator::

        from django.views.decorators.debug import sensitive_post_parameters


        @sensitive_post_parameters("pass_word", "credit_card_number")
        def record_user_profile(request):
            UserProfile.create(
                user=request.user,
                password=request.POST["pass_word"],
                credit_card=request.POST["credit_card_number"],
                name=request.POST["name"],
            )
            ...

    In the above example, the values for the ``pass_word`` and
    ``credit_card_number`` POST parameters will be hidden and replaced with
    stars (``**********``) in the request's representation inside the
    error reports, whereas the value of the ``name`` parameter will be
    disclosed.

    To systematically hide all POST parameters of a request in error reports,
    do not provide any argument to the ``sensitive_post_parameters`` decorator::

        @sensitive_post_parameters()
        def my_view(request): ...

    All POST parameters are systematically filtered out of error reports for
    certain :mod:`django.contrib.auth.views` views (``login``,
    ``password_reset_confirm``, ``password_change``, and ``add_view`` and
    ``user_change_password`` in the ``auth`` admin) to prevent the leaking of
    sensitive information such as user passwords.

.. _custom-error-reports:

Custom error reports
--------------------

All :func:`sensitive_variables` and :func:`sensitive_post_parameters` do is,
respectively, annotate the decorated function with the names of sensitive
variables and annotate the ``HttpRequest`` object with the names of sensitive
POST parameters, so that this sensitive information can later be filtered out
of reports when an error occurs. The actual filtering is done by Django's
default error reporter filter:
:class:`django.views.debug.SafeExceptionReporterFilter`. This filter uses the
decorators' annotations to replace the corresponding values with stars
(``**********``) when the error reports are produced. If you wish to
override or customize this default behavior for your entire site, you need to
define your own filter class and tell Django to use it via the
:setting:`DEFAULT_EXCEPTION_REPORTER_FILTER` setting::

    DEFAULT_EXCEPTION_REPORTER_FILTER = "path.to.your.CustomExceptionReporterFilter"

You may also control in a more granular way which filter to use within any
given view by setting the ``HttpRequest``’s ``exception_reporter_filter``
attribute::

    def my_view(request):
        if request.user.is_authenticated:
            request.exception_reporter_filter = CustomExceptionReporterFilter()
        ...

.. currentmodule:: django.views.debug

Your custom filter class needs to inherit from
:class:`django.views.debug.SafeExceptionReporterFilter` and may override the
following attributes and methods:

.. class:: SafeExceptionReporterFilter

    .. attribute:: cleansed_substitute

        The string value to replace sensitive value with. By default it
        replaces the values of sensitive variables with stars
        (``**********``).

    .. attribute:: hidden_settings

        A compiled regular expression object used to match settings and
        ``request.META`` values considered as sensitive. By default equivalent
        to::

            import re

            re.compile(r"API|AUTH|TOKEN|KEY|SECRET|PASS|SIGNATURE|HTTP_COOKIE", flags=re.IGNORECASE)

        .. versionchanged:: 5.2

            The term ``AUTH`` was added.

    .. method:: is_active(request)

        Returns ``True`` to activate the filtering in
        :meth:`get_post_parameters` and :meth:`get_traceback_frame_variables`.
        By default the filter is active if :setting:`DEBUG` is ``False``. Note
        that sensitive ``request.META`` values are always filtered along with
        sensitive setting values, as described in the :setting:`DEBUG`
        documentation.

    .. method:: get_post_parameters(request)

        Returns the filtered dictionary of POST parameters. Sensitive values
        are replaced with :attr:`cleansed_substitute`.

    .. method:: get_traceback_frame_variables(request, tb_frame)

        Returns the filtered dictionary of local variables for the given
        traceback frame. Sensitive values are replaced with
        :attr:`cleansed_substitute`.

If you need to customize error reports beyond filtering you may specify a
custom error reporter class by defining the
:setting:`DEFAULT_EXCEPTION_REPORTER` setting::

    DEFAULT_EXCEPTION_REPORTER = "path.to.your.CustomExceptionReporter"

The exception reporter is responsible for compiling the exception report data,
and formatting it as text or HTML appropriately. (The exception reporter uses
:setting:`DEFAULT_EXCEPTION_REPORTER_FILTER` when preparing the exception
report data.)

Your custom reporter class needs to inherit from
:class:`django.views.debug.ExceptionReporter`.

.. class:: ExceptionReporter

    .. attribute:: html_template_path

        Property that returns a :class:`pathlib.Path` representing the absolute
        filesystem path to a template for rendering the HTML representation of
        the exception. Defaults to the Django provided template.

    .. attribute:: text_template_path

        Property that returns a :class:`pathlib.Path` representing the absolute
        filesystem path to a template for rendering the plain-text
        representation of the exception. Defaults to the Django provided
        template.

    .. method:: get_traceback_data()

        Return a dictionary containing traceback information.

        This is the main extension point for customizing exception reports, for
        example::

            from django.views.debug import ExceptionReporter


            class CustomExceptionReporter(ExceptionReporter):
                def get_traceback_data(self):
                    data = super().get_traceback_data()
                    # ... remove/add something here ...
                    return data

    .. method:: get_traceback_html()

        Return HTML version of exception report.

        Used for HTML version of debug 500 HTTP error page.

    .. method:: get_traceback_text()

        Return plain text version of exception report.

        Used for plain text version of debug 500 HTTP error page and email
        reports.

As with the filter class, you may control which exception reporter class to use
within any given view by setting the ``HttpRequest``’s
``exception_reporter_class`` attribute::

    def my_view(request):
        if request.user.is_authenticated:
            request.exception_reporter_class = CustomExceptionReporter()
        ...

.. seealso::

    You can also set up custom error reporting by writing a custom piece of
    :ref:`exception middleware <exception-middleware>`. If you do write custom
    error handling, it's a good idea to emulate Django's built-in error handling
    and only report/log errors if :setting:`DEBUG` is ``False``.


================================================
File: docs/howto/index.txt
================================================
=============
How-to guides
=============

Practical guides covering common tasks and problems.

Models, data and databases
==========================

.. toctree::
   :maxdepth: 1

   initial-data
   legacy-databases
   custom-model-fields
   writing-migrations
   custom-lookups

Templates and output
====================

.. toctree::
   :maxdepth: 1

   outputting-csv
   outputting-pdf
   overriding-templates
   custom-template-backend
   custom-template-tags

Project configuration and management
====================================

.. toctree::
   :maxdepth: 1

   static-files/index
   logging
   error-reporting
   delete-app

Installing, deploying and upgrading
===================================

.. toctree::
   :maxdepth: 1

   upgrade-version
   windows
   deployment/index
   static-files/deployment

Other guides
============

.. toctree::
   :maxdepth: 1

   auth-remote-user
   csrf
   custom-file-storage
   custom-management-commands
   custom-shell

.. seealso::

    The `Django community aggregator`_, where we aggregate content from the
    global Django community. Many writers in the aggregator write this sort of
    how-to material.

    .. _django community aggregator: https://www.djangoproject.com/community/


================================================
Fi