.. |ss| raw:: html

   <strike>

.. |se| raw:: html

   </strike>

Forked version
--------------

This is the (from time to time) updated fork of the `original version <https://github.com/instaloader/instaloader>`__ plus changes that I needed for myself.
So far they are:

- 200 api requests/hr (000-follow-api-limits-better)

  - IG allows only 200 api calls per hour for non-logged in users
  
- Set the modification dates of already downloaded files to the post's date (000-correct-timestamps)

  - New option ``--correct-timestamps``
  - Set the modification dates of already downloaded files to the post's date.
  - This is handy for updating backups downloaded with erroneous tools.

- Add functionality to do iterator backups after every page load (000-do-regular-iterator-backups)

  - If Instaloader is stopped by anything except Ctrl+C, the current state isn't saved and Instaloader starts at the first post again.
  - The new code saves the iterator's state, before a new page is loaded.
  - Attention: It interferes with the option ``--fast-update`` and should be implemented as an additional option that should be used only while doing your initial download of the profile and not on later updates.

- |ss| Update the query_hash for post downloads (000-new-query_hash-for-post-downloads) |se|

  - |ss| It's necessary because for the old query_hash IG isn't returning the full structure any more. |se|

- Load existing GraphSidecar json instead of downloading again (000-reload-graphsidecar-json)

  - Previously for every GraphSidecar node that had videos in it, a graph query was executed.
  - Instead of downloading that json again, just load it from disk if it has been downloaded and saved before.
  - Note: It doesn't get updates (caption, tags, location or alt text) for historic posts, but that's something I was not intereseted in.
  - Update: The original version has been updated with a new query_hash and for now it doesn't do these many additional queries.

|
|
|

.. image:: https://raw.githubusercontent.com/instaloader/instaloader/master/docs/logo_heading.png

.. badges-start

|pypi| |pyversion| |license| |aur| |contributors| |downloads|

.. |pypi| image:: https://img.shields.io/pypi/v/instaloader.svg
   :alt: Instaloader PyPI Project Page
   :target: https://pypi.org/project/instaloader/

.. |license| image:: https://img.shields.io/github/license/instaloader/instaloader.svg
   :alt: MIT License
   :target: https://github.com/instaloader/instaloader/blob/master/LICENSE

.. |pyversion| image:: https://img.shields.io/pypi/pyversions/instaloader.svg
   :alt: Supported Python Versions

.. |contributors| image:: https://img.shields.io/github/contributors/instaloader/instaloader.svg
   :alt: Contributor Count
   :target: https://github.com/instaloader/instaloader/graphs/contributors

.. |aur| image:: https://img.shields.io/aur/version/instaloader.svg
   :alt: Arch User Repository Package
   :target: https://aur.archlinux.org/packages/instaloader/

.. |downloads| image:: https://pepy.tech/badge/instaloader/month
   :alt: PyPI Download Count
   :target: https://pepy.tech/project/instaloader

.. badges-end

::

    $ pip3 install instaloader

    $ instaloader profile [profile ...]

**Instaloader**

- downloads **public and private profiles, hashtags, user stories,
  feeds and saved media**,

- downloads **comments, geotags and captions** of each post,

- automatically **detects profile name changes** and renames the target
  directory accordingly,

- allows **fine-grained customization** of filters and where to store
  downloaded media,

- automatically **resumes previously-interrupted** download iterations.

::

    instaloader [--comments] [--geotags]
                [--stories] [--highlights] [--tagged] [--igtv]
                [--login YOUR-USERNAME] [--fast-update]
                profile | "#hashtag" | :stories | :feed | :saved

`Instaloader Documentation <https://instaloader.github.io/>`__


How to Automatically Download Pictures from Instagram
-----------------------------------------------------

To **download all pictures and videos of a profile**, as well as the
**profile picture**, do

::

    instaloader profile [profile ...]

where ``profile`` is the name of a profile you want to download. Instead
of only one profile, you may also specify a list of profiles.

To later **update your local copy** of that profiles, you may run

::

    instaloader --fast-update profile [profile ...]

If ``--fast-update`` is given, Instaloader stops when arriving at the
first already-downloaded picture.

Alternatively, you can use ``--latest-stamps`` to have Instaloader store
the time each profile was last downloaded and only download newer media:

::

    instaloader --latest-stamps -- profile [profile ...]

With this option it's possible to move or delete downloaded media and still keep
the archive updated.

When updating profiles, Instaloader
automatically **detects profile name changes** and renames the target directory
accordingly.

Instaloader can also be used to **download private profiles**. To do so,
invoke it with

::

    instaloader --login=your_username profile [profile ...]

When logging in, Instaloader **stores the session cookies** in a file in your
temporary directory, which will be reused later the next time ``--login``
is given.  So you can download private profiles **non-interactively** when you
already have a valid session cookie file.

`Instaloader Documentation <https://instaloader.github.io/basic-usage.html>`__

Contributing
------------

As an open source project, Instaloader heavily depends on the contributions from
its community. See
`contributing <https://instaloader.github.io/contributing.html>`__
for how you may help Instaloader to become an even greater tool.

Supporters
----------

.. current-sponsors-start

| Instaloader is proudly sponsored by
|  `@rocketapi-io <https://github.com/rocketapi-io>`__

See `Alex' GitHub Sponsors <https://github.com/sponsors/aandergr>`__ page for
how you can sponsor the development of Instaloader!

.. current-sponsors-end

It is a pleasure for us to share our Instaloader to the world, and we are proud
to have attracted such an active and motivating community, with so many users
who share their suggestions and ideas with us. Buying a community-sponsored beer
or coffee from time to time is very likely to further raise our passion for the
development of Instaloader.

| For Donations, we provide GitHub Sponsors page, a PayPal.Me link and a Bitcoin address.
|  GitHub Sponsors: `Sponsor @aandergr on GitHub Sponsors <https://github.com/sponsors/aandergr>`__
|  PayPal: `PayPal.me/aandergr <https://www.paypal.me/aandergr>`__
|  BTC: 1Nst4LoadeYzrKjJ1DX9CpbLXBYE9RKLwY

Disclaimer
----------

.. disclaimer-start

Instaloader is in no way affiliated with, authorized, maintained or endorsed by Instagram or any of its affiliates or
subsidiaries. This is an independent and unofficial project. Use at your own risk.

Instaloader is licensed under an MIT license. Refer to ``LICENSE`` file for more information.

.. disclaimer-end
