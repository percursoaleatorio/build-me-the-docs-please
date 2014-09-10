.. metadata-placeholder

:DC.Title:
	Selection of compatible operating systems
:DC.Creator:
	Nery, Fernanda
:DC.Date:
	2013-05-01
:DC.Description:
   Information on the selection of compatible operating systems (portability constraint).
   Based on previous R&D projects.
   Updated on release versions.
   Substituted Fedora for CentOS
   (the infrastructure provider has required compatibility with the Red Hat distribution).
:DC.Language:
	en
:DC.Format:
	text/x-rst
:DC.Rights:
	Access restricted to project members.
:DC.RightsHolder:
   Fernanda Néry 2009-2013 © CC BY-SA 3.0 http://creativecommons.org/licenses/by-sa/3.0/


.. _sw-operating-systems-ref:

Operating Systems
*****************

Requirements
============

Commercial Off-the-shelf (COTS) components **must** be available for:

*  Microsoft Windows Server and Windows 7
*  Ubuntu_ 12.04.02 LTS
*  CentOS_ 6

Software components to be developed **must** be supported/tested/accepted in:

*  Microsoft Windows Server and Windows 7
*  Ubuntu 12.04.02 LTS **or** CentOS 6

Rationale
=========

.. rubric:: Portability

Cross-platform compatibility is a non-functional project requirement:
the objective is to facilitate the sharing, reuse and future improvement
of the software solution to be developed
(and of existing software components it may incorporate).

For the end users, the majority of the interfaces
will probably be web-based user interfaces (WUI):
thus web browser compatibility will be a more stringent requirement
than operating system compatibility.

Nevertheless, when software is available for different platforms,
potential users may install and test the server-side components
in their local machines, thus promoting reuse and adoption.

Analysis of alternatives
========================

The selected software components must have cross-platform compatibility and
must be available for and supported on the most common operating systems.
Thus, it must be determined which are the *most common operating systems*.

Except for proprietary operating systems
(e.g. Microsoft Windows and Mac OS X)
no reliable market share statistics exist.
Most FOSS (Free and Open Source Software) operating systems
can be freely downloaded and installed
and do not require any kind of user registration:
thus, only indirect estimates of their use are available.

*  For the server segment,
   the `W3Techs report on web servers operating systems`_
   provides a rough estimate:

   * 65% are UNIX systems, 50% of which are Linux distributions
   * 35% are Microsoft Windows systems
   * less than 0.1% are Mac OS systems.

   Among the 3  major `Linux families`_, the relative proportion is:

   *  57% for the 'Debian family', including
      Debian_ (approximately 58% of the Debian-based distributions)
      and Ubuntu_ (42%)
   *  39% for the 'Red Hat family', including
      CentOS_ (70%), `Red Hat`_ (23%) and Fedora_ (7%);
   *  1.8% for the 'Slackware family', that includes
      SUSE_ (99.9%).

   These values do not include servers
   that are not exposed to the Internet
   (e.g. database servers in corporate intranets).

*  For the desktop/mobile user segment,
   the `Wikipedia request statistics`_
   provides another rough estimate:

   * 68% are Microsoft Windows systems
   * 20% are Apple Mac OS or iOS systems
   * 7% are Linux systems (including Android)

   If only non-mobile Linux systems are considered,
   the available sample again reveals the 3 major Linux families:

   *  96% for the 'Debian family', represented by
      Ubuntu (98% of the Debian-based distributions),
      Mint and Debian (both with less than 1%);
   *  3% for the 'Red Hat family', divided among
      Fedora (59%), Mandriva (22%), CentOS (10%) and Red Hat (9%);
   *  less than 2% for the 'Slackware family', represented by
      SUSE (99.9%) and OpenSUSE (0.1%).

   These values reflect a specific type of use
   (Wikipedia queries) by (mostly) domestic users.
   However, the usage ranking of operating systems is similar
   to that obtained in other indirect sources like `Google Trends on operating systems`_
   or the `StatOWL Operating System Market Share`_ report.
   Based on the StatOWL's data,
   the relative proportion of the 7 most frequent Linux distributions is:

   *  97% for the 'Debian family', including
      Ubuntu (98% of the Debian-based distributions)
      Mint (1%) and Debian (<1%);
   *  2% for the 'Red Hat family', including
      Fedora (40%), CentOS (40%) and Red Hat (20%);
   *  1% for the 'Slackware family',
      represented only by SUSE.

The global patterns that may be inferred from these data sources are:

*  The operating systems' usage share is completely different
   on the server segment and the user segment.

*  On the server segment, Microsoft Windows and Linux distributions
   such as Debian, Ubuntu and CentOS are common.

*  On the user segment, proprietary systems (Microsoft Windows, Mac OS X)
   are dominant. The (largely) dominant Linux distribution is Ubuntu.

These patterns support the following conclusions:

*  Server-side software components **should** be available for:

   *  Microsoft Windows Server 2008 R2
   *  The 'Debian family' and 'Red Hat family' Linux distributions;
   *  Mac OS X support is not a requirement,
      but may be a nice-to-have feature for developers.

*  Client-side software components **should** be available for:

   *  Microsoft Windows (at least for Windows 7);
   *  The 'Debian family' distributions,
      at least for Ubuntu 12.04.2 LTS
      (a Debian-based distribution that
      has Long Term Support releases with longer support life-cycles);
   *  The 'Red Hat family' distributions,
      at least for CentOS 6
      (a free Red Hat Enterprise Linux clone
      that has a longer life-cycle than Fedora);
   *  Mac OS X (although this OS is uncommon
      in the European public administration).

These conclusions can further be synthesised in the following **must** requirements:

*  Software components **must** be available for:

   *  Microsoft Windows Server 2008 R2 and Windows 7
   *  Ubuntu 12.04.02 LTS
   *  CentOS 6

*  Software components to be developed **must** be tested/accepted in:

   *  Microsoft Windows Server 2012 and Windows 7
   *  Ubuntu 12.04.02 LTS **or** CentOS 6

Regarding the two selected Linux operating systems:

*  Software distribution in Ubuntu is based on DEB packages
   (as in all of the 'Debian family');
   in CentOS, it is based on RPM packages
   (as in all of the 'Red Hat family').
   Software packaging requirements are distinct
   for the two types (DEB and RPM):
   no packaging requirements will be defined for the project,
   other then the common .tar.gz (compressed tar archives) file type
   for source code distribution (when applicable/required).

*  Both operating systems are gratis,
   but commercial technical support is available for Ubuntu
   (e.g. by its main developer, Canonical_) and
   CentOS is basically a free clone of the commercial Red Hat distribution
   (so any organisation requiring commercial support
   can acquire and use the `Red Hat`_ distribution).

.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt

.. _W3Techs report on web servers operating systems: http://w3techs.com/technologies/overview/operating_system/all
.. _Wikipedia request statistics: http://stats.wikimedia.org/archive/squid_reports/2012-12/SquidReportOperatingSystems.htm 
.. _Linux families: http://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg
.. _StatOWL Operating System Market Share: http://www.statowl.com/operating_system_market_share.php
.. _Google Trends on operating systems: http://www.google.com/trends/explore#cat=0-5&q=Ubuntu%20Linux%2C%20Mint%20Linux%2C%20Fedora%20Linux%2C%20CentOS%20Linux%2C%20SUSE%20Linux&date=today%2012-m&cmpt=q
