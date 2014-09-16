:tocdepth: 2

.. highlight:: rst

.. metadata-placeholder

   :DC.Title:
   	Pan-European Monitoring System - Background information on the use of reStructuredText
   :DC.Creator:
   	Nery, Fernanda
   :DC.Date:
   	2013-05-01
   :DC.Description:
      Brief introduction to reStructuredText (reST) concepts and syntax.
      This is a modified version of Sphinx's reStructuredText Primer
      (http://sphinx-doc.org/).
   :DC.Language:
   	en
   :DC.Format:
   	text/x-rst
   :DC.Rights:
   	Public.
   :DC.RightsHolder:
      Copyright (c) 2007-2011 by Georg Brandl
      Copyright (c) 2007-2013 by the Sphinx team

.. admonition:: Source

   This document is an abridged and modified version of `Sphinx's reStructuredText Primer`_.
   
Sphinx's reStructuredText primer
********************************

.. topic:: Abstract



.. _rst-primer-ref:

Introduction
============

A reStructuredText document is simply a plain text file
with some markup to specify the format or the semantics of the text.

There are two types of markup:

*  inline markup: for example, ``*the surrounding asterisks would mark
   this text as italics*``, like *this*.

*  explicit markup: is used for text that need special handling,
   such as footnotes, tables, or generic directives.
   Explicit markup blocks always start with ``..`` followed by whitespace.

.. _rst-paragraphs-ref:

Paragraphs
==========

The paragraph is the basic block in a reST document.

Paragraphs are simply chunks of text separated by one or more blank lines.

Indentation is significant in reST,
so all lines of the same paragraph
must be left-aligned to the same level of indentation.

.. admonition:: This is a style convention.

   Try to keep each line with a maximum of 78 characters.
   Remember that changing to next line does not create a paragraph,
   unless the chunks of text is separated by a blank line.
   
   Try to keep each phrase in a different line.
   It improves readability 
   and facilitates the translation process.
   
   Remember that consecutive blank lines 
   will be ignored in the HTML output.
   
   
Quoted paragraphs
-----------------

Quoted paragraphs are created by
just indenting them more than the surrounding paragraphs::

   Normal paragraph.
      
      Indented paragraph.

.. admonition:: This is a style convention.

   Each indentation level is created with 3 whitespaces.
   Do not use tabs.
      
Line breaks
-----------

Line blocks are a way of preserving line breaks
(the equivalent of using ``Shift+Enter`` to break a line
in Microsoft Word or LibreOffice Writer)::

   | These lines are
   | broken exactly like in
   | the source file.


.. _rst-sections-ref: 
  
Sections
========

Section are created by underlining (and optionally overlining)
the section title with a punctuation character::

   This is a heading
   =================

Any punctuation character can be used to define a section title.
The underlining (and overlining) must be at least as long as the text itself.
Sections must be properly nested.

.. admonition:: This is a style convention.
   
   Use the following punctuation characters in the section titles:

   *  ``#`` for Parts
   *  ``*`` for Chapters
   *  ``=`` for sections ("Heading 1")
   *  ``-`` for subsections ("Heading 2")
   *  ``^`` for subsubsections ("Heading 3")
   *  ``"`` for paragraphs ("Heading 4")

   Please note that, 
   when converting to ``HTML`` format, 
   sections are automatically converted to an appropriate heading tag 
   (for example: ``<h2>Heading text</h2>``).
   
   When converting to ``ODT`` or ``DOCX``, an appropriate Heading style is 
   applied.

.. _rst-inlinemarkup-ref:

Inline markup
=============

Bold, italics, monospace
------------------------

The markup is quite simple:

*  use one asterisk for italics: ``*text*``
   (the equivalent of using ``Ctrl+i`` in Microsoft Word or LibreOffice Writer),
*  use two asterisks for strong emphasis (boldface): ``**text**``
*  use backquotes for text literals: ````text````

Be aware of some restrictions:

*  The markup may not be nested.
   For example, this markup is wrong: ``*italics with **bold** inside*``
*  The text content within the markup may not start or end with whitespace.
   For example, this markup is wrong: ``* text*``

*  The markup must be separated from surrounding text
   by non-word characters (whitespace or punctuation).
   Use a backslash-escaped-space to work around that.
   For example: ``thisis\ *one*\ word`` is rendered like thisis\ *one*\ word.
*  If asterisks or backquotes appear in running text
   and could be confused with inline markup delimiters,
   they have to be escaped with a backslash.

Subscript and superscript
-------------------------

Subscript is marked with ``:sub:`subscript text```.
Superscript is marked with ``:sup:`superscript text```.

.. admonition:: This is a tip.

   Whitespace or punctuation is required around interpreted text, 
   but often not desired with subscripts & superscripts. 
   Backslash-escaped whitespace can be used; 
   the whitespace will be removed from the processed document::
   
      The chemical formula for molecular oxygen is O\ :sub:`2`. 
   
   To improve the readability of the text, the use backslash-escapes is discouraged.
   If possible, use :ref:`rst-substitutions-ref` instead::
   
      The chemical formula for pure water is |H2O|.
      
      .. |H2O| replace:: H\ :sub:`2`\ O
   
   Keep all substitutions together (e.g. at the end of the file).
      
.. _rst-lists-ref:

Lists
=====

Bulleted lists
--------------

List markup is natural:
just place an asterisk at the start of a paragraph and indent properly::

   *  This is a bulleted list.
   *  It has two items, the second
      item uses two lines.

Nested lists are possible,
but be aware that they must be separated
from the parent list items by blank lines::

   * this is
   * a list

     * with a nested list
     * and some sub-items

   * and here the parent list continues

Numbered lists
--------------

The same goes for numbered lists;
they can also be auto-numbered using a ``#`` sign::


   1. This is a numbered list.
   2. It has two items too.

   #. This is a numbered list.
   #. It has two items too.

.. _rst-definitionlists-ref: 

Definition lists
----------------

Definition lists are created as follows::

   term (up to a line of text)
      Definition of the term, which must be indented

      and can even consist of multiple paragraphs

   next term
      Description.

The Sphinx_ documentation generator
provides a more flexible alternative to definition lists
(see :ref:`rst-glossaries-ref`).

.. _rst-glossaries-ref: 

Glossaries
----------

The Sphinx ``..glossary::`` directive
contains a reST definition-list-like markup
with terms and definitions.

See the following example::

   .. glossary::

      environment
         A structure where information about all documents under the root is
         saved, and used for cross-referencing.  The environment is pickled
         after the parsing stage, so that successive runs only need to read
         and parse new and changed documents.

      source directory
         The directory which, including its subdirectories, contains all
         source files for one Sphinx project.

The definitions will then be used in cross-references with the ``:term:`` role.
For example:: 

   The :term:`source directory` for this project is ...
         
In contrast to regular definition lists,
a glossary supports *multiple* terms per entry
and inline markup is allowed in terms.
You can link to all of the terms.  For example::

   .. glossary::

      term 1
      term 2
         Definition of both terms.

When the glossary is sorted, the first term determines the sort order.

To automatically sort a glossary, include the following flag::

   .. glossary::
      :sorted:

.. _rst-fieldlists-ref:

Field lists
-----------

Field lists are two-column table-like structures
resembling database records (label & data pairs).
For example::

   :Date: 2001-08-16
   :Version: 1
   :Authors: - Me
             - Myself
             - I
   :Indentation: Since the field marker may be quite long, the second
      and subsequent lines of the field body do not have to line up
      with the first line, but they must be indented relative to the
      field name marker, and they must line up with each other.
   :Parameter i: integer

.. admonition:: This is a style convention.

   In this project, 
   field lists are used to include metadata in each document.
   
   The basic `Dublin Core`_ metadata fields
   should be included in the very beginning of each document
   (like a header to the text file),
   like this::
   
      .. metadata-placeholder
   
      :DC.Title: 
         Document title
      :DC.Creator:
         Author
      :DC.Date:
         Date yyyy-mm-dd
      :DC.Description:
         Abstract
      :DC.Language:
         en
      :DC.Format:
         text/x-rst
      :DC.Rights:
         Access rights
      :DC.RightsHolder:
         Copyright.

   Note that these metadata field names 
   are not automatically recognised by the Sphinx parser, 
   so the text itself will not be visible in the HTML pages (for example). 
   The metadata fields are the equivalent 
   to the *Document properties* fields in a ``DOCX`` file or an ``ODT`` file.
   
   docutils_ recognises a number of Bibliographic Fields 
   (such as ``docinfo``, ``author``, ``authors``, 
   ``organization``, ``contact``, ``version``, ``status``, 
   ``date``, ``copyright``, ``field``, ``topic``).

.. admonition:: This is an advanced topic

   Some metadata filed are recognised by Sphinx. For example:

   *  ``:tocdepth:`` indicates the maximum number of levels in the Sphinx sidebar
      table of contents for the file.
   
   *  ``:orphan:``   indicates that, even if the file is not included in any 
      ``.. toctree::`` directive, no warning should be produced by Sphinx.
      
.. _rst-tables-ref:

Tables
======

The reStructuredText markup supports two basic types of tables.
For *grid tables*,
you have to "paint" the cell grid yourself.
They look like this::

   +------------------------+------------+----------+----------+
   | Header row, column 1   | Header 2   | Header 3 | Header 4 |
   | (header rows optional) |            |          |          |
   +========================+============+==========+==========+
   | body row 1, column 1   | column 2   | column 3 | column 4 |
   +------------------------+------------+----------+----------+
   | body row 2             | ...        | ...      |          |
   +------------------------+------------+----------+----------+

*Simple tables* are easier to write, but limited:
they must contain more than one row,
and the first column cannot contain multiple lines.
They look like this::

   =====  =====  =======
   A      B      A and B
   =====  =====  =======
   False  False  False
   True   False  False
   False  True   False
   True   True   True
   =====  =====  =======

.. admonition:: This is a tip.
 
   These are the basic types of tables, which are rather clumsy. 
   Also available (and easier to use) are :ref:`special tables <rst-specialtables-ref>`, 
   namely list-tables and CSV-tables.
   
   An exceltable_ extension can also be used with Sphinx_,
   which allows the inclusion of ``XLS`` spreadsheets, 
   or part of them, into a reST document.

.. _rst-hyperlinks-ref:

Hyperlinks
==========

External links
--------------

Use ```link text <http://example.com/>`_`` for inline web links.
If the link text should be the web address,
you don't need special markup at all,
the parser finds links and mail addresses in ordinary text (with no markup).

You can also separate the link and the target definition, like this::

   This is a paragraph that contains `a link`_.

   .. _a link: http://example.com/

.. admonition:: This is a tip.

   The use of inline web links is discouraged, 
   to improve the readability of the reST text.
   
   Simple links (e.g. to institutional sites, software sites, and so on)
   should be kept together at the end of the text file 
   (this is merely a way to simplify the editing procedure, 
   and the update and verification of the links).

.. _rst-internallinks-ref:
   
Internal links
--------------

To support cross-referencing to arbitrary locations in any document,
the standard reST labels are used.
For this to work,
the label names must be unique throughout the entire documentation.
There are two ways in which you can refer to labels:

*  If you place a label directly before a section title,
   you can reference to it with ``:ref:`label-name```.
   Example::

      .. _my-label-ref:

      Section to cross-reference
      --------------------------

      This is the text of the section.

      In the end of this phrase is a reference to the section title, see :ref:`my-label-ref`.

   The ``:ref:`` role would then generate a link to the section, 
   with the link  title being "Section to cross-reference".  
   This works just as well 
   when section and reference are in different source files.

   Automatic labels also work with :ref:`figures <rst-figures-ref>`::

      .. _my-figure-ref:

      .. figure:: my-image.png

         My figure caption

   A reference like ``:ref:`my-figure-ref``` 
   would insert a reference to the figure
   with link text "My figure caption".

   The same works for :ref:`tables <rst-specialtables-ref>` 
   that are given an explicit caption using the ``table`` directive.

*  Labels that aren't placed before a section title can still be referenced
   to, but you must provide the text for the link, using this syntax:
   ``:ref:`Link text <label-name>```.

Using ``:ref:`` is advised over standard reStructuredText links to sections
(like ```Section title`_``) because it works across files, when section
headings are changed, and for all builders that support cross-references.

.. _rst-sourcecode-ref:

Source Code
===========

Literal code blocks are introduced by ending a
paragraph with the special marker ``::``.
The literal block must be indented
(and, like all paragraphs, separated from the surrounding ones by blank lines)::

   This is a normal text paragraph. The next paragraph is a code sample::

      It is not processed in any way, except
      that the indentation is removed.

      It can span multiple lines.

   This is a normal text paragraph again.

The handling of the ``::`` marker is smart:

*  If it occurs as a paragraph of its own, that paragraph is completely left
   out of the document.
*  If it is preceded by whitespace, the marker is removed.
*  If it is preceded by non-whitespace, the marker is replaced by a single
   colon.

That way, the second sentence in the above example's first paragraph would be
rendered as "The next paragraph is a code sample:".

.. _rst-explicitmarkup-ref:
      
Explicit Markup
===============

Explicit markup is used in reStructuredText
for most constructs that need special handling,
such as footnotes,
specially-highlighted paragraphs,
comments,
and generic directives.

An explicit markup block begins with a line starting with ``..``
followed by whitespace
and is terminated by the next paragraph
at the same level of indentation.
(There needs to be a blank line
between explicit markup and normal paragraphs.
This may all sound a bit complicated,
but it is intuitive enough when you write it.)

.. _rst-directives-ref:

Directives
----------

A directive is a generic block of explicit markup.

The directive content follows after a blank line
and is indented relative to the directive start.

Basically, a directive consists of a name, arguments, options and content.

Look at this example::

   .. contents:: This is my Table of Contents
      :depth: 2
      
The directive starts with ``..`` followed by one whitespace.
The name of the directive is ``contents`` (it creates a table of contents).
This directive takes one argument:
the table of contents' title ("This is my Table of Contents").
The option ``depth`` specifies
the number of section levels that are collected in the table of contents.

Options are given in the lines immediately following the arguments
and are indicated by the colons.
Options must be indented to the same level as the directive content.

Docutils_ supports the following directives:

*  Admonitions: ``attention``, ``caution``, ``danger``,
   ``error``, ``hint``, ``important``, ``note``,
   ``tip``, ``warning`` and the generic ``admonition``.
   (Most themes style only ``note`` and ``warning`` specially.)

*  Images:

   *  ``image`` - see the images_ section;
   *  ``figure`` - an image with caption and optional legend.

*  Additional body elements:

   *  ``contents <table-of-contents>`` -
      a local table of contents for the sections in the current file only;
   *  ``rubric`` -
      a heading without relation to the document's sections
      that won't be included in any table of contents;
   *  ``topic`` and ``sidebar`` - special highlighted body elements;
   *  ``epigraph`` - a block quote with optional attribution line;
   *  ``container`` -   a container with a custom class,
      useful to generate an outer ````<div>```` in HTML output.

*  :ref:`rst-specialtables-ref`:

   *  ``table``   -  a table with title;
   *  ``csv-table``  -  a table generated from comma-separated values;
   *  ``list-table`` -  a table generated from a list of lists.

*  Special directives:

   *  ``include`` - include reStructuredText from another file;
   *  ``raw`` -  include raw target-format markup, such as LaTeX;
   *  ``class`` - assign a class attribute to the next element.

.. _rst-contents-ref:

Table of contents
-----------------

To include a table of contents within a given document,
use the directive ``contents``.
The following example creates a local table of contents
with a maximum of two levels (below the level where it is located)::

   
   Part II
   #######
   
   Chapter 1
   *********
      
   .. contents::
      :depth: 2
      :local: 

   Heading 1
   =========
   
The ``toctree`` directive creates a table of contents
that collets information from several files.
The following example creates a table of contents
from the sections of various documents (up to a depth of 3 levels).
The ``:glob:`` option allows all documents in the 'chapter2' folder
to be included (sorted according to their name)::
   
   .. toctree::
      :glob:
      :maxdepth: 3
      
      preamble
      chapter1/part1
      chapter1/conclusion
      chapter2/*
      references 

.. Note:: 
   
   When building HTML pages from the default template, 
   a ``<div class="sphinxsidebar">`` is created that holds a 
   'table of contents' with links to the document sections.
   The number of levels in the sidebar can be controlled.
   For example, placing ``:tocdepth: 3`` 
   in the beggining of the document restricts the number of levels to 3.   
   
     
   
.. _rst-images-ref:

Images
------

reST supports an image directive, used like so::

   .. image:: gnu.png
      (options)

The file name given (here ``gnu.png``)
must either be relative to the source file,
or absolute (which means that they are relative to the top source directory).

For example, the file ``sketch/spam.rst``
could refer to the image ``images/spam.png``
as ``../images/spam.png``
or as ``/images/spam.png``.

The image size options (``width`` and ``height``)
should be specified in points (``pt``),
as that will best support output to different formats
(``HTML``, ``LaTeX``).

.. _rst-figures-ref:

Figures
-------

A ``figure`` consists of image data (including image options),
an optional caption (a single paragraph),
and an optional legend (arbitrary body elements)::

   .. figure:: picture.png
      :scale: 50 %
      :alt: map to buried treasure

      This is the caption of the figure (a simple paragraph).

      The legend consists of all elements after the caption.  In this
      case, the legend consists of this paragraph and the following
      table:

      +-----------------------+-----------------------+
      | Symbol                | Meaning               |
      +=======================+=======================+
      | .. image:: tent.png   | Campground            |
      +-----------------------+-----------------------+
      | .. image:: waves.png  | Lake                  |
      +-----------------------+-----------------------+
      | .. image:: peak.png   | Mountain              |
      +-----------------------+-----------------------+

There must be blank lines before the caption paragraph and before the legend.
To specify a legend without a caption,
use an empty comment (``..``) in place of the caption.

.. _rst-specialtables-ref:

Special tables
--------------

The ``table`` directive associates a title with the following table::

   .. table:: User list

      ==========  =========
      First name  Last name
      ==========  =========
      John        Doe
      Jane        Dove
      ==========  =========

A ``list-table`` is created from a uniform two-level bullet list::

   .. list-table:: User list
      :header-rows:1
      
      *  - First name
         - Last name
      *  - John
         - Doe
      *  - Jane
         - Dove

A ``csv-table`` is created from comma-separated values
(either in the document or in an external file)::

   .. csv-table:: User list
      :header:"First name","Last name"
      
      "John","Doe"
      "Jane","Dove"
      
Another example of ``csv-table``, using and external file::

   .. csv-table:: Table 1 - Legend of the table goes here...
      :header-rows: 1
      :stub-columns: 1
      :file: ../tables/table1.csv
      

An ``exceltable`` can also be used::

   .. exceltable:: Table 1 - Legend of the table goes here...
      :file: ../tables/tables.xls
      :sheet: table1
      :selection: A1:C20
      :header: 1
      
Using Excel tables requires an additional module `sphinxcontrib.exceltable`
that is an extension for Sphinx, that adds support for including spreadsheets, or part of them, into Sphinx document.
It can be installed using pip::

   pip install sphinxcontrib-exceltable

Then the project ``conf.py`` file needs to be updated::

   # Add ``sphinxcontrib.exceltable`` into extension list
   extensions = ['sphinxcontrib.exceltable']
   
Another alternative is xmltable (https://pythonhosted.org/rusty/xmltable.html).

.. _rst-footnotes-ref:

Footnotes
---------

For footnotes, use ``[#name]_`` to mark the footnote
location, and add the footnote body at the bottom of the document after a
"Footnotes" rubric heading, like so::

   Lorem ipsum [#first-footnote-name]_ dolor sit amet [#second-footnote-name]_

   .. rubric:: Footnotes

   .. [#first-footnote-name] Text of the first footnote.
   .. [#fsecond-footnote-name] Text of the second footnote.

You can also explicitly number the footnotes (``[1]_``) or use auto-numbered
footnotes without names (``[#]_``).

.. admonition:: This is a tip.

   To facilitate editing, auto-numbered footnotes should **not** be used. 
   Instead, use short descriptive names (that simplify cross-referencing).    
   
.. _rst-citations-ref:  
   
Citations
---------

Standard reST citations are supported::

   Lorem ipsum [Ref]_ dolor sit amet.

   .. [Ref] Book or article reference, URL or whatever.

Citation usage is similar to footnote usage,
but with a label that is not numeric or begins with ``#``.

When the documentation is built using the Sphinx_  document generator,
the citations are "global",
meaning that every citation can be referenced from any .rst files.
In this case, a separate file may be created (e.g. a ``references.rst`` file).

.. admonition:: This is a tip.

   See :ref:`rst-biblio-ref` for further information.
   
.. _rst-substitutions-ref:
   
Substitutions
-------------

reST supports "substitutions",
which are pieces of text and/or markup referred to in the text by ``|name|``.
They are defined like footnotes with explicit markup blocks, like this::

   .. |name| replace:: replacement *text*

or this::

   .. |caution| image:: warning.png
                :alt: Warning!


If you want to use some substitutions for all documents,
put them into a separate file
(e.g. ``substitutions.txt``)
and include it into all documents you want to use them in,
using the ``include`` directive.

Be sure to use a file name extension
which different from that of other source files,
to avoid Sphinx finding it as a standalone document.
For example, use the ``.rst`` file extension for the source files,
and the ``.txt`` file extension for the files which are to be included.

.. admonition:: This is a tip.

   This is useful in technical documentation such as User's Manuals, 
   where a substitution file can be built for each localised version 
   of the interface elements (menus, messages, etc), 
   guaranteeing the consistency of the document translation 
   with the software's human user interface.


.. admonition:: Warning.

   Substitutions do NOT work inside directives (or inside the options of a directive).
   
   Do not try to google for a solution (...been there). 
   It is a design limitation: RST markup can not be nested. Period.

.. _rst-comments-ref:

Comments
--------

Every explicit markup block
which isn't a valid markup construct is regarded as a comment.
For example::

   .. This is a comment.

You can indent text after a comment start to form multiline comments::

   ..
      This whole indented block
      is a comment.

      Still in the comment.

.. admonition:: This is a style convention.
      
   Comments can also be used as placeholders 
   to mark places within the document. 
   For example:

   *  the ``.. links-placeholder`` can mark the place 
      where hyperlinks are kept together at the end of the document;
      
   *  the ``.. metadata-placeholder`` can mark the place 
      where document metadata (author, date, etc) 
      is kept together at the beginning of the document.
   
.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt
