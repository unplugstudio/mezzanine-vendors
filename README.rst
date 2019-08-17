
Mezzanine Vendors
=================

A Django / Mezzanine application to manage a vendor catalog. Features:

- CSV imports
- Uses the Google Maps API to determine coordinates from human-readable addresses
- Categorize vendors by service type and subject

Install
-------

1. Add your Google Maps API Key in your ``settings.py`` as ``GOOGLE_MAPS_API_KEY``
2. Install via pip: ``pip install mezzanine-vendors``.
3. Add ``django_google_maps`` and ``import_export`` to ``INSTALLED_APPS``.
4. Also add ``vendors`` after them.
5. Add to your urlconf: ``url(r"^vendors/", include("vendors.urls", namespace="vendors"))``.
6. Run migrations: ``python manage.py migrate vendors``.
7. Create Vendors, Subjects, and Types using the admin interface.
8. Access the vendor list by visiting `/vendors/`.

Management Command
------------------

Run ``python manage.py add_vendor_locations`` to add coordinates to vendors that are missing them (for example, vendors added via admin import which only have a human-readable address). This uses Google's GeoCoder API and will fail if the address cannot be parsed. It will also count towards the usage limit of your Google Maps API key.

You can periodically run this command in a cronjob to make sure vendors added using the import feature have a valid geolocation.

Contributing
------------

Review contribution guidelines at CONTRIBUTING.md_.

.. _CONTRIBUTING.md: CONTRIBUTING.md
