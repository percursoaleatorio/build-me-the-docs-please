:tocdepth: 2

.. metadata-placeholder

   :DC.Title:
      Pan-European Monitoring System - Background information on editors for reStructuredText
   :DC.Creator:
      Nery, Fernanda
   :DC.Date:
      2013-09-01
   :DC.Description:
      Brief introduction to reStructuredText (reST) editors and applications
      (http://sphinx-doc.org/).
   :DC.Language:
      en
   :DC.Format:
      text/x-rst
   :DC.Rights:
      Public.

Tools for reStructuredText
**************************

Introduction
============

This document presents some of the tools available for working with
reStructuredText.

It is divided in the following parts:

*  Editors: simple text editors providing syntax highlight for reST documents.

*  Builder and Converters: tools that automatically convert reST documents
   to other formats such as HTML, PDF, DOC, ODT, etc.

*  Integrated solutions:
   tools that allow the user to produce, build and convert documents
   using a single integrated environment.

Editors
=======

reStructuredText documents are text files, and can be edited with any text editor
or word processor (provided they are always saved as text files).

JEdit
-----

`jEdit`_ is a FOSS text editor, written in Java (so it runs in Windows, Mac OS X, Linux, etc.).
ReST is among the 211 languages supported natively by jEdit.

.. figure:: img/jEdit.png
   :alt: This document opened in jEdit.
   :width: 50%

Notepad++
---------

`Notepad++`_ is a FOSS text editor for **MS Windows OS** only.

reStructuredText is not among the languages natively recognised by Notepad++,
but it can be added using a `User Defined Language File`_
(see install instructions below the list of available language files).

Follow the link to download the `ReST syntax file`_.

Notepad++ is simpler and more user friendly than jEdit.

.. figure:: img/NotepadPlusPlus.png
   :alt: This document opened in Notepad++.
   :width: 50%
   
ReText
------

`ReText`_ is a simple editor that reads your text with MarkDown or HTML markup and saves it as plain text, HTML or PDF.
It is written in Python using Qt libraries.

.. _ReText: http://sourceforge.net/projects/retext/

Visual Studio Code
------------------

`Visual Studio Code <http://code.visualstudio.com>`_ is a FOSS text editor, written in TypeScript (so it runs in Windows, Mac OS X, Linux, etc.).
ReST is not among the languages natively supported by Visual Studio Code, but it can be added using `an extension from LeXtudio <https://github.com/lextm/vscode-restructuredtext>`_.

.. figure:: img/vscode.png
   :alt: This document opened in Visual Studio Code.
   :width: 50%

Builders and converters
=======================

.. todo::

   Section on Builders and Converters such as Sphinx and Pandoc.

Sphinx
------

`Sphinx`_ is a Python documentation generator.

It requires `Python`_, which is installed by default in Linux and Mac OS X systems.
For Microsoft Windows systems, see :ref:`installing-python-on-windows-ref` if you need help installing Python
and two useful installation utilities (`easy_install` and `pip`).

After you have Python installed, simply use the following command (in a command window)::

   easy_install -U Sphinx

Elevated privileges (i.e. administration rights) should not be required.

The Sphinx builder can produce a number of output formats (e.g. HTML, PDF).
PDF files can be produced using the LaTeX builder (more complicated)
or using the a direct PDF builder called rst2pdf (see below).


Rst2Pdf
-------

rst2pdf is a tool for transforming reStructuredText to PDF using ReportLab.
To install rst2pdf on Windows you also need Python_ because rst2pdf is coded in python.

Rst2pdf uses `ReportLab <http://www.reportlab.com/opensource/>`_, which can be installed using::

   easy_install reportlab
   
Again, in Windows, there may be a problem with the required Microsoft Visual Studio version.
While running setup.py for package installations, Python 2.7 searches for an installed Visual Studio 2008.
The solution is to define VS90COMNTOOLS variable to point to Tools directory of Visual Studio::

   SET VS90COMNTOOLS=%VS100COMNTOOLS%   

How to install rst2pdf on Windows?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Download rst2pdf source from https://code.google.com/p/rst2pdf/downloads/list
#. Unzip the file to an rst2pdf folder.
#. Goto the the rst2pdf folder which contains setup.py file.
#. Run ``python setup.py install`` command and it will be installed.
#. To convert any .rst file to PDF file Run rst2pdf myfile.rst command and you are done.

*  http://rst2pdf.ralsina.me/
*  User Manual: http://ralsina.me/static/manual.pdf


Pandoc
------


.. hidden

   The ``exclude_patterns`` parameter in the ``conf.py`` file 
   can be used, if files are to be ignored - i.e. such files not built ).
   
   In this project, **.txt files are ignored.

Integrated solutions
====================

ReST Editor for Eclipse
-----------------------

The `ReST editor for Eclipse`_
is a plug-in for the Eclipse IDE.
If Sphinx_ is installed, it can also be used to create (and build) Sphinx projects
from within Eclipse.
The following `presentation
<http://www.slideshare.net/tcalmant/rest-editor-eclipse-demo-camp-grenoble-2011>`__
documents the use of the editor.

This ReST editor has several advantages, namely:

*  integrated spell-checking using Hunspell4Eclipse
*  contextual ReST syntax help
*  sections outline rearrangement

.. figure:: img/ReSTEditor.png
   :alt: This document opened in the Eclipse ReST Editor.
   :width: 50%
   
.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt

