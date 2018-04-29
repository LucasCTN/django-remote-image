=================
Django-remote-image
=================

.. image:: https://img.shields.io/pypi/v/django-remote-image.svg
   :target: https://pypi.python.org/pypi/django-remote-image
   :alt: PyPI

Django-remote-image is a Django app that adds a new form field for images.
The default widget is a text input, that accepts a URL of a image.

The image is downloaded and can be passed to a ``ImageField`` in a model. `Pillow <https://pypi.org/project/Pillow/>`_ needs to be installed.

It is possible to whitelist and blacklist file extensions.

Examples are shown below.

Quick start
-----------

.. code:: bash

   $ pip install Pillow
   $ pip install django-remote-image

Using
-----------
Django-remote-image adds a new form field named ``RemoteImageField`` that can be used to download images from a URL.

Examples
^^^^^^^^^^^
Using the field ``RemoteImageField`` in a form (all image extensions allowed):

.. code:: python

   from remote_image import RemoteImageField

   class ExampleForm(forms.Form):
      image = RemoteImageField()

Whitelisting file extensions (the ones NOT included in the list will raise a validation error message):

.. code:: python

    from remote_image import RemoteImageField

    class ExampleForm(forms.Form):
        image = RemoteImageField(ext_whitelist=['png', 'jpg'])

Blacklisting file extensions (the ones included in the list will raise a validation error message):

.. code:: python

    from remote_image import RemoteImageField

    class ExampleForm(forms.Form):
        image = RemoteImageField(ext_blacklist=['png', 'jpg'])
