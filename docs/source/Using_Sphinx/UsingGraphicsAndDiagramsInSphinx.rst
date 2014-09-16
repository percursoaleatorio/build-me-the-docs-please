:tocdepth: 2

.. highlight:: none

.. metadata-placeholder

   :DC.Title:
   	Using Graphics and Diagrams in Sphinx
   :DC.Creator:
   	Nery, Fernanda
   :DC.Date:
   	2013-10-01
   :DC.Description:
      Overview of some available alternatives for
      producing and including SVG graphics and UML diagrams in Sphinx.
   :DC.Language:
   	en
   :DC.Format:
   	text/x-rst

.. _rst-diagrams-ref:

Creating diagrams in Sphinx
***************************

Using Graphviz
==============

Besides using raster images (PNG, JPG, etc.),
diagrams can be included with
the `sphinx.ext.graphviz`_ extension.

Graphviz_ is an open source graph visualisation software.
Graph visualisation is a way of representing structural information
as diagrams of abstract graphs and networks.

It must be installed before the extension can be used.

Due to current (2013.10) compatibility issues with PlantUML,
it may be preferable to install GraphViz 2.28 instead.

Including the extension in the project configuration file
---------------------------------------------------------

The Graphviz extension is included with Sphinx,
but the extension must be enabled in the ``conf.py`` file::

   extensions = ['sphinx.ext.graphviz']
   
.. admonition:: Changing the configuration file

   Extensions local to a project should be put within the project’s directory structure.
   Set Python’s module search path, sys.path, accordingly so that Sphinx can find them.
   E.g., if your extension foo.py lies in the exts subdirectory of the project root,
   put into conf.py::
   
      import sys, os
      sys.path.append(os.path.abspath('exts'))
      extensions = ['foo']
   
   You can also install extensions anywhere else on sys.path, e.g. in the site-packages directory.

Examples
--------

This code:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :lines: 73-77

has this result:

.. graphviz::

   digraph {
      "From" -> "To";
   }

This code:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :lines: 86-100
   
has this result:

.. graphviz::

   digraph Flatland {
   
      a -> b -> c -> g; 
      a  [shape=polygon,sides=4]
      b  [shape=polygon,sides=5]
      c  [shape=polygon,sides=6]
   
      g [peripheries=3,color=yellow];
      s [shape=invtriangle,peripheries=1,color=red,style=filled];
      w  [shape=triangle,peripheries=1,color=blue,style=filled];
      
      }

Numerous examples are available online:

*  https://en.wikipedia.org/wiki/DOT_(graph_description_language)
*  http://www.graphviz.org/pdf/dotguide.pdf
*  http://graphs.grevian.org/example.html

Using PlantUML
==============

The `Sphinx PlantUML extension`_ (in this case a contributed extension) allows
Sphinx to embed UML diagrams by using PlantUML.

PlantUML_ is a Java component that allows to quickly write simple UML diagrams:

*  use case diagrams,
*  class diagrams,
*  activity diagrams,
*  state diagrams,
*  component diagrams,
*  sequence diagrams,
*  object diagram.

Diagrams are defined using a simple and intuitive language.
This can be used within many other tools.
Images can be generated in PNG or SVG format.

Installing the extension
------------------------

The module is installed with the following command::
   
   pip install sphinxcontrib-plantuml

Including the extension in the project configuration file
---------------------------------------------------------

The extension must be enabled in the ``conf.py`` file::

   extensions = ['sphinxcontrib.plantuml']

The path to the PlantUML file may have to be specified
(assuming that Java itself is already in the search path)::
   
   plantuml = 'java -jar ../utils/plantum.jar'

PlantUML requires Graphviz and an environment variable may have to be defined,
pointing to the ``dot`` executable. For example (in Linux or OS-X)::

   setenv GRAPHVIZ_DOT /usr/local/bin/graphviz/dot
   export GRAPHVIZ_DOT

.. note:: For Ubuntu users

   Files with the .sh extension in the /etc/profile.d directory get executed 
   whenever a bash login shell is entered (e.g. when logging in from the console or over ssh), 
   as well as by the DisplayManager when the desktop session loads::
   
      /etc/profile.d/*.sh
      
   You can for instance create the file /etc/profile.d/myenvvars.sh and set variables like this::

      export GRAPHVIZ_DOT=/usr/bin/dot

.. note:: For Windows users

   Regardless of the existence of the GRAPHVIZ_DOT environment variable,
   the path to the Graphviz bin folder is apparently required
   to be in the PATH variable as well.  

Examples
--------

In the Sphinx reST documents,
simply begin the PlantUML code with the ``uml`` directive.


.. begin-plantuml-first-example

.. uml:: 
   
   @startuml
   user -> (use PlantUML)

   note left of user
      Hello!   
   end note
   @enduml

.. end-plantuml-first-example

This is the code for the example above:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :language: rst
   :start-after: begin-plantuml-first-example
   :end-before: end-plantuml-first-example


Another example:

.. begin-plantuml-second-example

.. uml::
   
   @startuml 
   Alice -> Bob: Hi!
   Alice <- Bob: How are you?
   @enduml

.. end-plantuml-second-example

This is the code for the example above:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :language: rst
   :start-after: begin-plantuml-second-example
   :end-before: end-plantuml-second-example


.. include:: PlantUMLExamples.exc.rst

.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt
