:Author: nery
:Copyright: CC BY-NC-SA 2.0 <http://creativecommons.org/licenses/by-nc-sa/2.0/>
:Date: $Date: 2013-10 $
:Revision: $Revision: 0.0.1 $
:Description: Notes on Eclipse

Eclipse
*******

.. epigraph::
   
   The Eclipse Platform is a generic foundation for an IDE
   That is, the platform is an IDE without any particular programming language in mind. 
   You can create generic projects, edit files in a generic text editor, 
   and share the projects and files with a version control system. 
   The platform is essentially a glorified version of a file-system browser.
   
   [from http://www.ohloh.net/p/eclipse]

The current version is Eclipse 4.3 Kepler.

The basic platform is indeed "a glorified version of a file-system browser".
All functionality is provided through plug-ins.

In Eclipse Kepler, the following two plug-ins are already incorporated
in the base product (installation is no longer required):

*  Mylyn, the task-focused interface for Eclipse;
*  Egit, the Eclipse Team provider for the Git version control system.

Numerous other plug-ins are available.
In some cases, packages are provided
that bundle together a number of useful plug-ins
for a specific purpose.

For example, the Eclipse Java EE IDE for Web Developers
also includes the Web Tool Platform
(that will be required for XSD and XML creation and validation, CSS editing, etc.).
It is the selected option.

The StatET http://www.walware.de/goto/statet

Other plug-ins may be required, and are described below...



Mylyn
=====

Mylyn (http://www.eclipse.org/mylyn/).


Install Mylyn Connectors
------------------------

Mylyn can use a local **task** repository or a remote one.

If the remote task repository is associated with an issue tracking system,
a 'connector' is required.
By default, a Bugzilla connector is included with Mylyn (and Eclipse).

A long list of different connectors is available
at http://wiki.eclipse.org/Mylyn/Extensions.
It includes connectors for Trac and Redmine, GitHub and Bitbucket, etc...

Connectors can be installed in different ways:

#. Some (stable) connectors are available through the Mylyn Task List window:

   *  Add repository > Install more connectors...

   For example, the Trac connector is available in this list.

#. Other connectors (alpha versions, etc) can be installed using
   the standard plug-in install procedure inside Eclipse:

   *  Goto Help > Install new software...

   *  Providing the link to the update site
      (available in the connector description in the Mylyn/Extensions wiki page).

   This is the case for:

   *  The Bitbucket Mylyn Connector, which is alpha status
      and is available at http://www.mylynbitbucketconnector.xpg.com.br/update

   *  The GitHub Connector (egit-github), also in alpha status
      and available at http://download.eclipse.org/egit/github/updates-nightly

Specifically for my projects, two connectors are required:

*  The Trac connector
*  The Bitbucket connector
   (currently 2013.10.21 not working properly due to an identified but not yet fixed bug)

How to...
---------

A basic tutorial on Mylyn is available at: http://www.vogella.com/articles/Mylyn/article.html.

A generic introduction is available at: http://www.youtube.com/watch?v=bSYVpjom4pU

Use tags in code comments to generate tasks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Tags in source code comments can be used to generate tasks.
The following Window > Preferences can be enabled:

*  General > Structured Text Editors > Task Tags

   Enable searching for Task Tags

*  Java > Compiler > Task Tags

*  JavaScript > Validator > Task Tags

*  PyDev > Task Tags

*  StatET > Task Tags

.. epigraph:: 

   The Tasks view includes a helpful customization for Java developers. 
   When a Java project is built, the parser automatically scans for Java task tags in your code comments. 
   You can configure the task tag names and their priorities using the Java > Task Tags preferences. 
   Three tags are provided by default (FIXME, TODO, and XXX), and we added a STORY tag to support our agile development process.

   Eclipse Distilled, by David Carlson 
 

Workarounds
-----------

If the task list disappears...
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The workaround is:

1. Goto the drop-down menu in the Task List pane
   (or right-click to see the contextual menu).
#. Select Restore tasks from history...
#. Select either a zip file (if you've exported the task list before)
   or an adequate snapshot.

Tasks can be exported from the Task list pane (right-click to see the contextual menu)
using the Import and Export... > Export option.

This apparently can occur when updating and restarting Eclipse
(see https://bugs.eclipse.org/bugs/show_bug.cgi?id=403467).

Git integration
===============

.. TODO

How to
------

Import the content of an existing git repository
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Open the Git Repository Exploring perspective

#. If the repository isn't already listed, then
   Add a repository (using the drop-down menu)

#. Select the repository in the list, right-click and select
   Import projects...

#. Choose Import as a general project... and follow the wizard.

PlantUML
========

PlantUML is a component that allows to quickly write :

*  sequence diagram,
*  use case diagram,
*  class diagram,
*  activity diagram,
*  component diagram,
*  state diagram
*  object diagram

Diagrams are defined using a simple and intuitive language.
The documentation is available here::

   http://sourceforge.net/projects/plantuml/files/PlantUML%20Language%20Reference%20Guide.pdf/download

Images can be generated in PNG or SVG format.

The Eclipse plug-in is described here::
   
   http://plantuml.sourceforge.net/eclipse.html

Install
-------

It is not clear if the PlantUML plug-in works with the Eclipse Kepler version (4.3).

The update site for Eclipse Juno (4.2) is::

   http://plantuml.sourceforge.net/updatesitejuno/

Let's try it. It's working!

Note that the Graphviz software must be installed.

.. hidden-text

   C:\Program Files (x86)\Graphviz 2.28

How to...
---------

#. Goto Window > Show View > Other > PlantUML to open a visualisation tab.

#. Insert the following text into a document (or inside a multiline code comment)::

      @startuml
      
         user -> (use PlantUML)
         
         note left of user
            Hello!   
         end note
      
      @enduml

#. The diagram will be displayed the the PlantUML visualisation pane,
   where it can be exported to a graphic file.


Papyrus
=======

Papyrus is graphical editing tool for UML2 as defined by OMG.

It can be used as a simple plug-in or as a part of the Eclipse Modelling Tools package.
It provides a graphical editor for the Eclipse UML2 project.

.. epigraph:: 
   
   UML2 is an EMF-based implementation of the Unified Modeling Language (UML) 2.x OMG metamodel for the Eclipse platform.

   The objectives of the UML2 component are:
   *  to provide a usable implementation of the UML metamodel to support the development of modeling tools
   *  a common XMI schema to facilitate interchange of semantic models
   *  test cases as a means of validating the specification
   *  validation rules as a means of defining and enforcing levels of compliance
   
   Although MDT/UML2 provides the metamodel, it does not provide UML modelling tools themselves. 
   One implementation is Papyrus. An older, no longer supported implementation is UML2Tools (http://wiki.eclipse.org/MDT-UML2Tools).

   [http://wiki.eclipse.org/MDT-UML2Tools]


Install
-------

1. Start Eclipse
#. Goto Help > Install New Software
#. Press Add... to add a new resource and specify a name and the URL
   (the link below is for the Eclipse Kepler version)::

      NAME: Papyrus
      URL:  http://download.eclipse.org/modeling/mdt/papyrus/updates/releases/kepler

How to
------

Tutorial on the Eclipse Modelling Framework (not on Papyrus, but it will be useful later on):
http://www.vogella.com/articles/EclipseEMF/article.html

Python IDE
==========

PyDev_ is a Python IDE for Eclipse,
which may be used in Python, Jython and IronPython development.

Install
-------

Python 2.7 is assumed to be installed.

1. Start Eclipse
#. Goto Help > Install New Software
#. Press Add... to add a new resource and specify a name and the URL::

    NAME: PyDevEnv
    URL:  http://pydev.org/updates

#. Select PyDev and PyDev Mylyn Integration from the list and press Next.
#. Acept the licence terms when the download ends.
#. Restart Eclipse.

Configure
---------

1. Goto Window > Preferences > PyDev > Editor  > Interpreter Python
#. Eclipse can configure the options automatically (press Auto Config)
   or the location of the Python interpreter can be specified.
   (in Linux, usually that would be /usr/bin/python)
#. Press OK to finish the configuration.

Start new project
-----------------

1. Goto File > New > Project and select 'Pydev project'
#. Create a new file (goto File > New > File) HelloWorld.py
#. Add the code
#. Press Run or ``Ctrl + F11``

Python projects will be associated with a "Python perspective",
i.e. a customised layout of windows and GUI elements.

References:
`1  <http://www.linoob.com/2011/09/starting-with-python-on-eclipse-in-ubuntu/>`__ ;
`2 <http://blog.moonflare.com/2011/11/23/installing-eclipse-with-pydev-for-python-development-in-ubuntu/>`__ .

How to...
---------

A generic tutorial covering all the above steps is available at: http://www.vogella.com/articles/Python/article.html

ReST Editor
===========

ReST Editor is an Eclipse plug-in providing support to edit reStructuredText files

reStructuredText is a markup language that can be transformed in various output formats
with tools like the Sphinx documentation generator, rst2pdf, rst2beamer, ...

More information here : http://resteditor.sourceforge.net/

Install
-------

This plug-in can be installed through the Eclipse Marketplace (Help > Eclipse Marketplace...)
or through the standard plug-in installation:

1. Goto Help > Install new software...
#. Add the project update site: http://resteditor.sourceforge.net/eclipse
#. Select the ReST Editor plug-in

Configure
---------

The plug-in is configured under Window > Preferences > ReST Editor.

The following options are important:

*  The preferred section markers order, that will be used to automatically correct any improper sequence: #*=-^"

*  The tab length (3) and the option to insert spaces instead of tabs.

*  The spell checking options (see :ref:`hunspell4eclipse-ref`).

Start a new Sphinx project
--------------------------

The ReST Editor plug-in can be used to create a new Sphinx project:

1. Goto File > New > Project > ReST Editor > Sphinx project
#. Follow the wizard's instructions...

If Sphinx is installed, then ReST documents can be built from within Eclipse (using the make.bat or the makefile).

.. _hunspell4eclipse-ref:

Hunspell4Eclipse
================

Hunspell4Eclipse is a plug-in that integrates Hunspell into Eclipse’s Spell Checking Service.
It is useful if Eclipse is used as for general purpose document editing.

Install
-------

This plug-in can be installed through the Eclipse Marketplace (Help > Eclipse Marketplace...)
or through the standard plug-in installation procedure.

Configure
---------

No dictionaries are included. The plug-in uses Hunspell or Myspell dictionaries.
These are also used by LibreOffice,
and are available in the extensions directory
(for example, "C:\Program Files (x86)\LibreOffice 4.0\share\extensions").

Preferences per workspace can be configured in:
1. Preferences - General - Editors > TextEditors > Spelling

#. Select Hunspell4Eclipse

#. Browse... and select a dictionary(.dic) file

Useful links:

*  https://code.google.com/p/hunspell4eclipse/

*  https://wiki.mozilla.org/L10n:Dictionaries

Build a Sphinx project
----------------------

*  Right-click on the make.bat file and goto Run as > Run Configurations...
*  Select the option ``Sphinx (via make file)``
*  Create a new configuration:
   *  Specify the working directory, for example ``${project_loc}/docs``
   *  Specify the type of Sphinx output, for example ``html``

The new configuration will be accessible through the button bar
(in the Run button drop-down options).

The console pane will show the Sphinx output.

.. statet-ref:

StatET for R
============

.. note: 

   I haven't used this IDE. It is one of my R IDE candidates - the others is RStudio. 
   
   RStudio has a very nice interface, but the discussion 
   `here <http://support.rstudio.org/help/discussions/suggestions/3762-why-i-am-switching-to-statet-in-a-single-photo>`__,
   suggests that staying within Eclipse is the best option - which would also be my first guess...
   Architect (http://www.openanalytics.eu/architect) is perhaps another option, based on StatET.  
  
   StatIDE is maintained by only one person and does not use a recognizable OSI licence.
   Must check this out.  

Install
-------

Dependencies (for the stable version StatET 3.3 in Eclipse 4.3):

.. list-table::

   *  -  Java
      -  6 or higher
   *  -  GNU R 
      -  2.13 to 3.0
   *  -  R package RJ
      -  1.1

.. admonition:: For Windows users
   
   The path where R is installed should not contain spaces.
   For example, install in "C:\Programs\R" but not in "C:\Programs Files\R".
   
   Otherwise, strange things are likely to happen, such as packages not getting installed properly... 
      
To install the R Packages of RJ 1.1 (StatET 3.0-3.3), use the following command in a common R Term console::
   
   install.packages(c("rj", "rj.gd"), repos="http://download.walware.de/rj-1.1")

In Eclipse, use the standard plug-in installation procedure:

#. Goto Help > Install New Software
#. Press Add... to add a new resource and specify a name and the URL::

    NAME: StatET
    URL:  http://download.walware.de/eclipse-4.3

#. For most users it is recommend to select only StatET (and Add-ons/Utilities, if desired),
   but no Libraries; the dependencies are resolved automatically.

Tutorials
---------

*  `Eclipse and StatET – a working environment for R
   <http://lukemiller.org/index.php/2010/04/eclipse-and-statet-a-nice-working-environment-for-r/>`_

*  `A guide to Eclipse and the R plug-in StatET
   <http://www.splusbook.com/RIntro/R_Eclipse_StatET.pdf>`_

Toad Extension for Eclipse 1.9.0 Community Edition
==================================================

.. TODO

Eclipse: how to...
==================

Change the encoding to UTF-8
----------------------------

*  For a specific project: File > Properties > Text file encoding

*  Goto Window > Preferences > General > Content types
   and change the `Default encoding` for each type.

*  Goto Window > Preferences > General > Workspaces > Text file encoding

Show a print margin
-------------------

*  Goto Window > Preferences > General > Editors > Text Editors > Show print margin (80)

.. link-placeholder

.. _Eclipse: http://www.eclipse.org/
.. _PyDev: http://pydev.org/ 
