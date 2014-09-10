
Tools for reStructuredText
**************************

Introduction
============

Sphinx_ documentation can be hosted online.

Dropbox
=======




Google drive
============

.. note:: Sources

   https://kb.wisc.edu/helpdesk/page.php?id=38083
   
   https://support.google.com/drive/answer/2881970?hl=en
   
   https://developers.google.com/drive/web/publish-site

#. Create a folder in Google Drive and share it as ``Public on the Web``

   .. figure:: img/GoogleDrive_2.png
      :scale: 50%

#. Upload the folder containing the HTML build, Javascript, and CSS files to this folder.

#. Find the shareable link of the HTML folder and copy the unique identifier

   .. figure:: img/GoogleDrive_3.png
      :scale: 50%

   For example, if the link is ``https://drive.google.com/folderview?id=0B8AmLQ1728LmeHpwbEd1N0U4YTQ&usp=sharing``
   then the unique id is ``0B8AmLQ1728LmeHpwbEd1N0U4YTQ``.

#. So the link to your documentation will be

   www.googledrive.com/host/the-unique-identifier-that-you-just-copied/index.thml

   For example, the link to these pages is:

   www.googledrive.com/host/0B8AmLQ1728LmeHpwbEd1N0U4YTQ/index.html


Read The Docs
=============


Github.io
=========

.. note:: Sources

   http://lucasbardella.com/blog/2010/02/hosting-your-sphinx-docs-in-github
   
   http://daler.github.io/sphinxdoc-test/index.html


Turning Jekill off
------------------

.. note:: Source

   https://help.github.com/articles/using-jekyll-with-pages#turning-jekyll-off

You can completely opt out of Jekyll processing by creating a file named ``.nojekyll``
in the root of your Page repository and pushing that file to GitHub.

This should only be necessary if your site uses directories that begin with an underscore,
as Jekyll sees these as special directories and does not copy them to the final destination.

Since Sphinx_ puts all the static files in a ``_static`` folder,
this needs to be done, otherwise the stylesheets, etc,
won't be uploaded to the html site.