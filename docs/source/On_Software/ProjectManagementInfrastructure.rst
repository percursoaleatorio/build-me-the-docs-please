.. metadata-placeholder

:DC.Title:
	Selection of the Technical Infrastructure for Collaboration
:DC.Creator:
	Nery, Fernanda
:DC.Date:
	2013-05-01
:DC.Description:
   Information on the selection of the COTS components for project management, issue tracking, version control system, document generator.
   Based on previous R&D projects.
   Excluded free (for FOSS) non-EUPL compatible software (such Atlassian Confluence).
   Included Redmine (there is no dedicated project site, can use the project management product instead)
:DC.Language:
	en
:DC.Format:
	text/x-rst
:DC.Rights:

:DC.RightsHolder:
   Fernanda Néry 2009-2013 © CC BY-SA 3.0 http://creativecommons.org/licenses/by-sa/3.0/



.. _sw-technical-infrastructure-ref:

Project Management Infrastructure
*********************************

A software portfolio was selected to support the project's
technical infrastructure for collaboration, namely:

   *  a `version control`_ system to keep track of changes to the
      project's documentation (and source code);
   *  a `documentation generator <wikipedia-comparison-of-documentation-generators>`_ to automate the production
      of user manuals (and documents such as this one);
   *  an `issue tracking`_ and generic `project management`_ system.

The following topic provides an overview
of the **required components** and **key functionalities**
for the technical infrastructure.

It contains an abridged version of section 2.2 in [SWLH11]_
with minor terminology changes and editing.

A similar but more detailed overview is available in [Foge09]_
(Chapter 3).

.. topic:: Technical Infrastructure for Collaboration

   Since collaboration among widely-distributed contributors is key to OTD 
   (Open Technology Development), 
   projects must establish a project site with the technical infrastructure 
   needed for collaboration. 
   The project site must enable the shared development 
   of the software, test suites, and documentation 
   (including user, installation, administration, and design documentation), 
   though the details of how these occur often vary between projects. 

   It must be possible for all potential contributors and users 
   to use the tools easily. 
   For example, if security restrictions make it too difficult 
   for people to participate, they will not participate.
   
   Projects should prefer to use widely-used OSS collaboration tools 
   that work well with any standards-compliant web browser. 
   Unusual tools create an unnecessary barrier to entry, 
   as they require users to learn how to use new tools instead of simply contributing. 
   (Even if users have learned how to use a tool, users will be 
   more willing if the tool is widely used because their learning time is amortised.) 

   OSS tools should be strongly preferred; 
   they can be configured for special needs, 
   tend to be inexpensive to deploy, 
   and tend to be especially good at OTD-style collaboration 
   since they are often used for that purpose. 

   Maximising access via standards-compliant web browsers 
   increases the ability for others to interact with the product, 
   e.g., they can interact from the field.

   Contractors must expect that this technical infrastructure 
   means that the government and other contractors 
   will have continuous access to intermediate progress. 
   This transparency is by design.

   **Key Functions**

   The central project site must support 
   the collaboration of ongoing improvements 
   and should provide the following functions:

   #. *Web Site*. 
      The central project site must provide a single starting point 
      for those interested in the project, 
      enabling people to learn about the project 
      and find all related information. 
      This is normally a web site with a simple fixed URL.
      
   #. *Bug and Feature Tracking*. 
      The central project site must provide a mechanism for users 
      to submit bug reports and feature requests, 
      and for developers to determine how (or if) to resolve them.
      
      This is often implemented through specialised tools 
      such Bugzilla, Trac, or Redmine, 
      but other tools (such as wikis) can be used. 
      There may need to be a special process for reporting security 
      vulnerabilities to prevent their disclosure before a repair is available.

   #. *Version Control System* (VCS). 
      The central project site must provide a mechanism for tracking changes,
      including at least the software and often test suites and some documentation. 
      It should at least provide a method for seeing and 
      tracking the “main development branch” and each major release. 
      The VCS must make it possible to see who made each change, 
      when, and what the change was.
      
      There are two major types of VCS systems: 
      centralised (e.g., Subversion_ aka SVN) 
      and distributed (e.g., Git_ and Mercurial_). 
      Distributed systems (such as Git_) 
      have significant advantages and should be preferred for VCS of OTD projects.

   #. *Community interaction*.
      The central project site must provide a mechanism 
      for users and developers to discuss issues. 
      Mailing lists and wikis tend to be easier to use.
      Be sure to archive discussions in a way that later participants can find them, 
      or important discussions will be lost. 
      
   #. *Release downloads*. 
      The central project site must provide 
      a mechanism for download of major releases.

   **Public access and classification control**

   Where possible, determine which components 
   can be released to the public as OSS ahead-of-time, 
   and establish the project outside in the public from the beginning.
   
   There is no legal requirement wait until the project is “feature complete” 
   before this release occurs, and if it is to be public anyway, 
   the sooner it is publicly released the better.

   Some components are classified, 
   and thus their development may only take place 
   on systems authorised for classified processing.

   Where possible, divide components based on their sensitivity to limit 
   what must be protected by security classification control. 

   Projects should seriously consider using a distributed VCS (such as “git”) 
   where there may be varying levels of classification. 
   Distributed VCS software make it much easier to create separate external branches 
   and later provide them to others for merging if approval is granted.

   **Hosting**

   Each project must determine if it will be based on some existing 
   collaboration hosting service that provides pre-configured functionality, 
   or if it will establish its own system, obtain the necessary tools, 
   and host the project itself. 
   Whatever the decision about hosting, you must be able to compete and 
   change who does hosting support down the line. 
   Do not be locked into a single supplier. 
   
   A key criterion for the evaluation of hosting services 
   is to determine how difficult it would be to copy the data 
   (e.g., bug reports, source code, etc.) 
   elsewhere so that if the hosting service is inadequate, the project can easily move.

   Small projects are often well-served by using an existing collaboration 
   hosting service, as they cannot justify the resources 
   to specially configure their infrastructure. 
   
   Ideally, if a project is to be publicly available as OSS, 
   it should be established as a public project before the design is created. 
   
   Source: [SWLH11]_ 

.. links-placeholder 

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt
