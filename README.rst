######
Exitwp
######

This fork of `exitwp <https://github.com/thomasf/exitwp>`_ tries to ease the migration from wordpress to `pelican <http://pelican.notmyidea.org/>`_.

Changes:
   * extension of generated files is .md not .markdown
   * Header in a format pelican likes
   * previous categories are added to the tags, as pelican cannot cope with
     more than categorie per entry (category in now 'blog' for all posts'

By default it will try to convert as much information as possible from wordpress but can also be told to filter the amount of data it converts.


Getting started
===============
 * `Download <https://github.com/thomasf/exitwp/zipball/master>`_ or clone using ``git clone https://github.com/thomasf/exitwp``
 * Export one or more wordpress blogs using the wordpress exporter under tools/export in wordpress admin.
 * Put all wordpress xml files in the ``wordpress-xml`` directory
 * Special note for Wordpress 3.1, you need to add a missing namespace in rss tag : ``xmlns:atom="http://www.w3.org/2005/Atom"``
 * Run xmllint on your export file and fix errors if there are.
 * Run the converter by typing ``python exitwp.py`` in the console from the directory of the unzipped archive
 * You should now have all the blogs converted into separate directories under the ``build`` directory

Runtime dependencies
====================
 * `Python <http://python.org/>`_ 2.6, 2.7, ???
 * `html2text <http://www.aaronsw.com/2002/html2text/>`_ :  converts HTML to markdown (python)
 * `Beautiful soup <http://www.crummy.com/software/BeautifulSoup/>`_ : Parsing and downloading of post images/attachments (python)


Installing dependencies in ubuntu/debian
----------------------------------------

   ``sudo apt-get install python-beautifulsoup python-html2text``

Installing Python dependencies using python package installer (pip)
-------------------------------------------------------------------

From the checked out root for this project, type:

   ``sudo pip install --upgrade  -r pip_requirements.txt``

Note that PyYAML will require other packages to compile correctly under ubuntu/debian, these are installed by typing:

   ``sudo apt-get install libyaml-dev python-dev build-essential``


Configuration/Customization
===========================

See the `configuration file <https://github.com/thomasf/exitwp/blob/master/config.yaml>`_ for all configurable options.

Some things like custom handling of non standard post types is not fully configurable through the config file. You might have to modify the `source code <https://github.com/thomasf/exitwp/blob/master/exitwp.py>`_ to add custom parsing behaviour.

Known issues
============
 * Target file names are some times less than optimal.
 * Rewriting of image/attachment links if they are downloaded would be a good feature
 * Meaningful translation/filtering of wikipedia publish statuses into something that usable within a fairly standard jekyll setup.
 * There will probably be issues when migrating non utf-8 encoded wordpress dump files (if they exist).

Other Tools
===========
 * A Gist to convert WP-Footnotes style footnotes to PHP Markdown Extra style footnotes: https://gist.github.com/1246047
