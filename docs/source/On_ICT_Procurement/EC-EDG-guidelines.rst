:orphan:

.. metadata-placeholder:

.. _EC-EDG-guidelines-ref:

Guideline for public administrations on partnering with free software developers
================================================================================

.. admonition:: Note

   This is an excerpt of the following advice report.
   
   European Commission - Enterprise Directorate General 
   
   IDA/GPOSS 
   Encouraging Good Practice in the use of Open Source Software in Public Administrations 
   
   GUIDELINE FOR PUBLIC ADMINISTRATIONS ON PARTNERING WITH FREE SOFTWARE DEVELOPERS 
   
   Revised Final version: December 2005 

   URL: http://ec.europa.eu/idabc/servlets/Docbe59.pdf?id=28128   

Case #1: Solution developed from scratch for the PA
---------------------------------------------------

The RFP (request for proposal) will therefore:

*  Indicate the license chosen by the administration
   in case the administration wants to distribute the solution (see hereafter)

*  Check and clarify all copyrights questions:

   *  The moral rights (to the “brand name” of the solution, to disclosure of
      rights and to the respect and integrity of the work that has been done).

   *  The propriety rights:

      *  who can “represent the solution” on web sites, events and other communications
      *  who can reproduce (as is), modify, redistribute,
      *  what about redistribution fees (as in general no open source license
         forbid to sell the redistribution…).

   The recommended best practice (clause to include in the RFP) is that:

   1. The PA has the exclusive right of disclosure and the proprietary rights
      of representation and reproduction of the software.

   2. The service provider keeps the right to be identified as the author.
      However, he can only reuse the results, commercially or free of
      charge, with the entity’s express permission, so he cannot
      automatically redistribute freely: the PA keeps the decision to
      redistribute or not.

*  Determine the development and interoperability standards (highly recommended).
   If a precise indication of all standards cannot be done, precise that any standards
   must be:

   *  Non proprietary or at least licensed for free, for any use or redistribution
   *  Endorsed by a neutral, acknowledged international (or European)
      normalisation association or specialised administration.

*  Impose to the service partner to use only software components and standards that
   are fully compatible with the above (e.g. your service partner cannot integer
   GNU/GPL components if the PA has decided to distribute under a BSD license).
   The service partner must issue a certificate to confirm this conformity.

Case #2: Specific open source software, found externally
--------------------------------------------------------

In this case the PA is looking for using and adapting an existing FLOSS project,
that has already a community of developers (and if delivered, of users),
responding to a specific purpose (e.g. a content management,
a collaborative work environment,
a workflow system that could be used by various PA but also for other business)

*  Identify the community and its leaders
*  Identify the licenses and check that it is conform to the PA needs (negotiate
   appropriate license if possible).
*  Deploy contractual or extra-contractual incentives:

   *  Contracting a service level agreement ensuring support (this is only
      possible if the author is an organised body or a company)
   *  “Ex Ante” funds to orient developments in the desired direction (this is
      also only possible if the counterpart is an organised body or a company)
   *  Deploying incentives (especially if the supporting community is not an
      organised legal body).

Case #3: Solution developed by a PA, with possible pooling or reuse
-------------------------------------------------------------------

As said within the POSS study published on the IDA site, the decision of
distributing solutions under open source license by the PA creating it must be made on a
case-by-case basis according to the benefits of the software for a group of users.

Going open source in a multi-lingual environment may represent an important extra investment
(e.g. multiply by 3 the initial cost) and if the software does not clearly meet the needs of
other PA’s, it is preferable not to bear the extra burden of distribution.

The process will be, first:

*  Choosing the license in case the administration wants to distribute the solution
   (see hereafter). This has to be done from scratch as it has an impact on the
   components that developers may reuse or not.

*  Assemble full information and certify license compliance for all use of FLOSS
   components during the project. If these components are used, document carefully
   their license, as the actions to comply with it.

*  At the end of the project, consolidate the compliance report and indicate the name
   of the server on which the software is distributed as free software, the date when it
   will be made available.

*  Notify the software existence and copyright to a competent copyright organisation
   and to the FLOSS organisation as the Open source or the Free Software
   Foundation, (especially when the PA wants to benefit from support coordinated
   by that organisation).

Two main options may be reasonable:

*  If the PA wants to “give” its software for all type of re-use, including the
   incorporation in proprietary commercial solution (with the purpose of facilitating
   software business or software industry), a BSD type license should be chosen.
   This will not impeach the open source community to distribute the original code
   freely, and to fork its own improved versions under a GPL license (for example).
   However, improvements and new versions created by the proprietary industry
   may definitively escape to the open source world.
   In addition, this choice of a licence where “appropriation is tolerated” exclude the
   use of GPL components (about 50% of available components) and would mean
   retaining only components under licences in the same family – tolerating
   appropriation (BSD, MIT, Apache, Python, Zope, etc).

*  If the PA wants to reserve its software for open source use (this does not restraint
   any form of commercialisation, but it restraint exclusive appropriation), then the
   GPL or a copyleft license fully compatible with the GPL is recommended (French
   open sources communities have recently promoted the CeCILL license, said to be
   more compatible with European law than the American GPL).
   The decision to produce a software development under a GPL license allows
   integration of components of GPL origin or nearly any other origin. It does not
   imply any obligation to distribute the software produced if it is produced entirely
   by the entity (to keep developments secrets, simply do not license this version).
   The use of the GPL may be less appreciated or questioned by some
   representatives of the industry, however it may ensure the largest volunteers
   support inside the open source community.

   (Dual licensing can also be used:) Trolltech
   released Qt under a dual license that specifies that if the application that links to it is
   GPL, Qt is licensed under the GPL. The licensing problem was solved successfully.
