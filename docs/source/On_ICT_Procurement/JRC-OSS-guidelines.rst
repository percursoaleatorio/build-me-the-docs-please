:orphan:

.. contents:: 

.. note::

   This is an **abridged and edited version** 
   of the EU Joint Research Center Guidelines on Open Source Software (September 2010).
   The original document is available online at:
   <https://joinup.ec.europa.eu/sites/default/files/OSS-guidelines-v-DIGIT-2.pdf>

   This version has been prepared for internal use only 
   and should not be distributed publicly.

   Further references:

   A similar guide, also available, in the 22 official languages of the EU.
   <http://joinup.ec.europa.eu/system/files/guidelines/EUPL%201.1%20Guidelines%20EN.pdf>

   An updated compatibility matrix between EUPL and other FOSS licences:
   <http://joinup.ec.europa.eu/software/page/licence_compatibility_and_interoperability%20>
   <https://joinup.ec.europa.eu/software/page/eupl/eupl-compatible-open-source-licences>

   Guideline For Public Administrations On Partnering With Free Software Developers
   http://ec.europa.eu/idabc/servlets/Docbe59.pdf?id=28128

   Guideline on Public Procurement of Open Source Software
   http://joinup.ec.europa.eu/sites/default/files/OSS-procurement-guideline%20-final.pdf

   
.. _jrc-oss-guidelines:

*******************************
Open Source Software Guidelines
*******************************

Early Determination Principle
=============================

The following guidelines are meant to help developers
managing Open Source Software
('OSS') in the JRC development projects.

Early determination of distribution policy
------------------------------------------


There are basically three options concerning distribution of software
developed or contributions made to existing software:

#. No distribution (software development for internal use only);

#. « Proprietary » distribution (grant of individual licenses, either free of charge or with a license fee);

#. distribution under an Open Source license.

Early determination of the Open Source license
----------------------------------------------

If the Open Source model is chosen as the desired distribution policy,
the type of license under which software in development will be released
must also be determined at the earliest stage of the project.

[An] Open Source license was specifically drafted
at the initiative of the European Commission.

This license, named EUPL (European Union Public License)
is designed to use the concepts of European law
and to respect the legal and linguistic diversity
of the Member States of the European Union.

In this case, the EUPL will most often be chosen,
but other licenses could also be used in certain situations.

OSS Guidelines for Developers
=============================

Document your work
------------------

This is probably the most important requirement:
when you insert pre-existing OSS in your own software
or use OSS and want to adapt it,
you must carefully document your use of OSS in the JRC projects.
You must always record:

*  The origin of any OSS component used,
   the date of its download,
   its version number and the license under which it is released;
*  The 'place' in the code where you inserted pieces of OSS;
*  The identification and description of your developments
   and of the modifications that you have made in OSS source code,
   and the date(s);

The contractors and collaborators
who are involved in the software development project
[must] follow the above instructions.

Where can you get Open Source Software?
---------------------------------------

*  Download OSS directly on its official author’s,
   editor’s or project’s website, if there is any;
*  Download OSS from OSOR.EU if functionally relevant software is available;
*  If not, choose repositories that are largely accepted
   and recognized through the OSS community.

Use of OSS development tools or environments
--------------------------------------------

Certain OSS are development tools (like compilers or automated test tools)
or environments (like website environments or operating systems of workstations).

The use of such tools or environments in software development projects
is not problematic from a legal point of view.

Incorporation of Open Source code in a project
----------------------------------------------

“Incorporate” here means both include pieces of OSS code
into software that you are developing and/or modify existing OSS
in order to create new or customized software.
The result is the same: you intend to integrate pre-existing OSS code
into the project which you are working on.

There is no direct answer to the question
whether to include or not OSS code in a project;
the answer [depends] on 2 elements:

*  The distribution scheme chosen for this project
   [namely if it will be distributed] under an Open Source license;
*  The license of OSS which you want to incorporate or modify.

Linking the software to OSS libraries
-------------------------------------

Some of the OSS available are released as libraries.

Instead of incorporating it into the software,
you may want to create links between your software and
these (unmodified) libraries and to distribute them along with your software,
either by compiling them together (“static linking”) or not (“dynamic linking”).

There are cases where dynamic linking to OSS libraries is allowed while static linking is not.
It depends from the Open Source license under which such library is released.
A case-by-case approach is thus necessary.

Just like what is indicated above about “incorporating” OSS in projects,
the possibility to link certain parts of OSS libraries to projects
depends on the distribution scheme chosen for the project
and the license under which such OSS is released.

Copyright notices and disclaimer
--------------------------------

OSS usually contains copyright notices and disclaimers
in their source code or in attached files.

They typically indicate the name and version number of these software,
the identity of the creator (or of the different contributors),
the reference (or the full text) of the license under which it is released
and a disclaimer.

You must **always copy such copyright notices and disclaimers**
along with the pieces of code that you insert or use in your project.

Keep and send copies of your code for archiving purposes
--------------------------------------------------------

A copy of all software developed is kept for legal archiving purposes.

You must send a copy of the code of all software developed
and subsequent (major) versions thereof.
This also applies to OSS developed or modified.

You should also check with your project manager/action leader
whether the developed software should be uploaded
on online repositories or forges (e.g. OSOR.eu).

Relationships with external developers
--------------------------------------

Some (parts of) software developed may come from external developers,
usually contractors, their sub-contractors or other providers.
If they are dealing with OSS, they will be asked to follow similar guidelines.
If you have contacts with such external developers during the course of your work,
do not hesitate to draw their attention on these guidelines
and to require from them the relevant documentation about their own use of OSS.
Such requirement should be stipulated in the relevant contract with the contractor.
If while examining part of software developed by external developers,
you notice that the current guidelines have not been respected
(e.g. the copyright notices are not present,
the use of OSS inserted is not documented,
the software contains parts of code released under a license
that is not allowed for this type of project, etc.),
you must refer to your action leader/project manager.

Use of these guidelines in tenders and contracts
------------------------------------------------

The principles set out in these guidelines
must also be respected in case of software procurement
from external developers or contractors.
Make sure that calls for tenders and contracts oblige the contractors
to respect these guidelines, which must be annexed thereto.
Such calls for tenders and contracts
should also indicate the specific requirements about the use of OSS
in the concerned project (if any) and oblige the tenderers and contractors
to explain and document in advance the use of OSS that they intend to make.

Checklist
=========

*  Did you determine if you intend to distribute externally your software?
*  Did you decide the type of license
   you are going to use for distributing the software?
*  Did you document, or ask your contractors/collaborators to document
   the use of pre-existing OSS-code in the development project?
*  Did you check the compatibility of the licenses in case of modification,
   insertion or linking of pre-existing OSS components?
*  Did you copy all copyright notices and disclaimers
   appearing on the pre-existing software used in your project?
*  Did you send copies of your code for legal archiving
   and check whether such code should be made available in online repositories?

Open Source Licences
====================


Copyright and conditions of use
-------------------------------

Like any software, OSS is protected by intellectual property rights
– in particular copyright – of its creator,
which grant him certain exclusive rights
(e.g. exclusivity to copy it, to modify it, etc.).
The particularity of Open Source Software is that the owner of copyright
chooses to allow others to exercise such prerogatives,
instead of preserving its exclusivity.
However, these permitted uses are generally granted
subject to the respect by the user of certain conditions.
The permitted uses of OSS and the conditions of use are determined in licenses.
There exist dozens of Open Source licenses,
although some of them are more widespread than others (e.g. the GPL-family).

The use of OSS is legal as long as
the user stays inside the limits of the permitted uses
and respects the conditions imposed by the OSS-licenses.
It is thus essential to know and respect the terms of licenses
which govern OSS parts used in the projects.

Copyleft effect
---------------

Some Open Source licenses oblige the user who distributes the original software
and any derivative work thereof to do so under the same license terms.
The GPL and the EUPL are examples of licenses containing such obligation.
Examples of practical consequences are the following:

*  You modify software released under the GPL
   and you want to distribute the modified work:
   you are obliged to release it under the GPL.

*  You integrate some lines of code of software
   released under the GPL into a bigger work.
   If you want to distribute it,
   you are obliged to release the whole resulting work under the GPL,
   as it will be considered as a “derivative work” of the GPL software,
   even if only a small part of it is used.

Licenses which contain such obligation are said “copyleft” licenses
and are often referred to as having a “viral effect”,
because they propagate through derivative works.
At the opposite, licenses that do not contain such obligations and let you choose
under which conditions you want to distribute derivative software are said “permissive”.

Compatibility
-------------

An Open Source license A is said “compatible” with an Open Source License B
when software originally licensed under a license A may be re-distributed
under a license B after modification or merger with other software.

Compatibility is not necessary reciprocal:
it is possible that a license A is compatible with a license B,
while license B is not compatible with the license A.

Examples of compatibility /incompatibility
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Merger between two parts of software, one released under BSD and the other under the EUPL.

BSD + EUPL = EUPL     (OK)

In this case, software originally released under the BSD license is integrated into a final result which is distributed under the EUPL license after merger with other software.
The terms of the BSD license authorize this subsequent change of license.
One could say that BSD is compatible with EUPL.

BSD + EUPL = BSD  (Not possible)

This case is exactly the same as previous operation, but you want to distribute the final result under the BSD license.
This is not possible, because the terms of the EUPL impose that derivative works of software released under the EUPL are also released under the EUPL (copyleft).
One could say that EUPL is not compatible with BSD.
This is thus a case where compatibility between BSD and EUPL is not reciprocal.


2. Merger of two parts of software, one released under EUPL and the other under the GPL v2.

GPLv2 + EUPL = EUPL (Not possible)

The GPL v2 imposes that the final result, which is a “derivative work” is released under the GPL v2.
This operation is thus impossible without infringing the terms of the GPL v2.
The GPL v2 is not compatible with the EUPL.

This case seems exactly the same as the previous, because the EUPL also imposes that derivative works are released under the EUPL.
But the EUPL contains a clause which explicitly allows releasing derivative works under the GPL v2 in case of merger between EUPL and GPL v2 pieces of software.

This is a case of *express compatibility*: The EUPL is compatible with the
GPL v2.

Here again, one could note that compatibility between EUPL and GPL v2 is not reciprocal.
