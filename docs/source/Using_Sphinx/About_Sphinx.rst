
   Sphinx_ is a document generator based on docutils_
   (an open-source text processing system, 
   for processing plain text documentation into useful formats, 
   such as HTML_, LaTeX_, ODT_ or XML_).
   
   In Sphinx, content (the text) is separated from presentation (formatting):
   
   *  Content is stored in plain text files using a simple markup language 
      (reStructuredText). 
      
   *  Presentation is defined using themes and templates 
      for each type of output (HTML, LaTeX, PDF).
      
   This separation allows the author of the document to focus 
   on the content and not on the presentation or the output format(s).
   Also, if the documentation needs to be localised to another language,
   the text can be translated (using translation tools, if required),
   and all the formatting is applied later 
   (without requiring further changes to the localised documents).

   This document provides an introduction to reStructuredText (or reST), 
   the markup language used by Sphinx.
   The authoritative reference is the `reStructuredText User Documentation`_.  

   Most of the markup used by Sphinx is standard reST markup.
   Exceptions (i.e. markup specific to Sphinx) are signalled in the text.
   
   In this document, some (arbitrary) style conventions are proposed
   to try and keep the project's documentation as consistent as possible.
   Again, these conventions are signalled in the text.