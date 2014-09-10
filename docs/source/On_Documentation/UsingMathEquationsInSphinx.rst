:tocdepth: 2

.. highlight:: rst

.. metadata-placeholder

   :DC.Title:
      Creating Equations in Sphinx
   :DC.Creator:
      Nery, Fernanda
   :DC.Date:
      2013-10-01
   :DC.Description:
      Overview of some available alternatives for
      producing and including equations in Sphinx.
      
      See http://sphinx-doc.org/ext/math.html
   :DC.Language:
      en
   :DC.Format:
      text/x-rst
   :DC.Rights:
      Public.

Creating equations in Sphinx
############################

LaTeX
*****

The syntax for writing equations is LaTeX.

Only brief examples are included here,
since LaTeX as a rather steep learning curve,
and AMS LaTeX is only concerned with math support.

The following links are useful:

*  See ftp://ftp.ams.org/pub/tex/doc/amsmath/short-math-guide.pdf
   for a not-so-short but clear syntax guide.

*  See http://www.ams.org/publications/authors/tex/amslatex
   for complete references.

*  See http://mirrors.fe.up.pt/pub/CTAN/info/examples/mil/mil.pdf
   for a not-so-gentle introduction to LaTeX.

MathJax
*******

In Sphinx, the rendering (display) of the equations
can be done in different ways,
that will not be discussed here.

The selected option is to use the ``sphinx.ext.mathjax`` extension.
This extension uses the JavaScript package MathJax_
to transform the LaTeX markup to readable math live in the browser.

The disadvantages are the (large) size and load time of the MathJax library.

The ``mathjax_path`` in the ``conf.py`` file
indicates where the MathJax library resides.
By default, this is the MathJax site,
but the path can be changed no cross-site scripting is allowed.

Equation editors or previewers
******************************

Given that LaTeX syntax may be daunting,
a WYSIWYG math editor can be useful, or at least an interactive previewer:

*  If the objective is simply to preview the result,
   the online `Interactive LaTeX Editor`_ is very good option
   and includes numerous equations as examples.

*  LyX_ is a user-friendly LaTeX processor
   that includes an equation editor.

   In the long run, LyX may be the best choice:
   it as the same dependencies as EqualX,
   a larger development and user community,
   and does not require virtually any LaTeX knowledge.

*  EqualX_ is a LaTeX equation editor (not a document processor as LyX):
   it can be used to create the equations
   and then paste the code into the ReST document.

   Like LyX_, EqualX requires a LaTeX distribution
   (in Linux, the dependencies are automatically installed
   and TeXLive_ is included in the official repositories of all major distributions;
   for Windows systems, MiKTeX_ is a possible alternative).

Examples
********

See additional examples at http://sphinx-doc.org/ext/math.html.

Code:: 

      If :math:`\sigma_{1}` equals :math:`\sigma_{2}` then etc, etc. 
   
Output:

      If :math:`\sigma_{1}` equals :math:`\sigma_{2}` then etc, etc.

Code:: 

      :math:`\underline{x}=[  x_{1}, ...,  x_{n}]^{T}`
      
Output:

      :math:`\underline{x}=[  x_{1}, ...,  x_{n}]^{T}`

Code:

.. code-block:: latex
   
   \langle \alpha, \beta  \rangle 
   \in 
   \Biggl \lbrace 
   { 
   M,\text{ if } 
      {
       l(\underline{x}) = 
         \frac { p(\underline{x}|M ) } { p(\underline{x}|U) } 
         \geq
          \frac { p(U) }{ p(M) } }
   \atop 
   U, \text{ otherwise } 
   }

Output:

.. math::

   \langle \alpha, \beta  \rangle 
   \in 
   \Biggl \lbrace 
   { 
   M,\text{ if } 
      {
       l(\underline{x}) = 
         \frac { p(\underline{x}|M ) } { p(\underline{x}|U) } 
         \geq
          \frac { p(U) }{ p(M) } }
   \atop 
   U, \text{ otherwise } 
   }

.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt
