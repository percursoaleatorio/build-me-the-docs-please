.. metadata-placeholder

:DC.Title:
	Selection of the Database Management System
:DC.Creator:
	Nery, Fernanda
:DC.Date:
	2013-05-01
:DC.Description:
   Information on the selection of the Relational DBMS.
   Based on previous R&D projects.
   Updated with Ingres and OpenVirtuoso status. Updated with MariaDB share.
   Updated to MoSy requirements:
   GeoJSON and TopoJSON for data visualisation, if not mediated by OGC W*S;
   integration with R (modules for SDC on microdata and aggregated data).
   Updated with reference to clustering and replication
   (not a project requirement, but requested by the infrastructure provider).
:DC.Language:
	en
:DC.Format:
	text/x-rst
:DC.Rights:
	Access restricted to project members.
:DC.RightsHolder:
   Fernanda Néry 2009-2013 © CC BY-SA 3.0 http://creativecommons.org/licenses/by-sa/3.0/


.. _sw-database-ref:

Database Management System
**************************

Requirements
============

The selected spatial object-relational database management system
is PostgreSQL_ 9.2+ with PostGIS_ 2.0+.

Rationale
=========

The database management system must comply with the :ref:`sw-constraints-ref`
set on licence compatibility, portability and acquisition cost.

Compliance with ANSI-SQL:2008 [ISO.IEC_9075:2008]_
is a basic technical interoperability requisite.

*  In Portugal, this is also a legal requisite
   for Public Administration IT systems development and procurement
   as established by the
   National Regulation on Digital Interoperability (Open Standards). [RNID12]_

Project specific functional requirements
(further discussed in the analysis of alternatives) are:

*  Support for spatial data types and spatial analysis
*  Support for (or coupling to) statistical computing tools
*  Support for key-value data storage and/or XML data storage

Analysis of alternatives
========================

Progressive filtering is based on maturity and sustainability criteria
that are not specific to this project,
but guarantee that the chosen solution
can be used at enterprise level in distinct projects,
indirectly reducing the cost of support, database administration, etc.

Detailed information on the nature, characteristics and
market share of major RDBMS products
is available in Section B (Databases) of the Competitive Assessment in the
`European Commission's Report on the Oracle/Sun Microsystems merger`_.

The `proprietary DBMS market share`_ estimates vary.
The following ranking is based on annual revenue:

* Oracle_ (circa 50%),
* IBM DB2_ (circa 20%),
* Microsoft `SQL Server`_ (circa 17%).

Three additional open source RDBMS are identified in the `EC Report`_:

* MySQL_
* PostgreSQL_
* Ingres_

MySQL_ (and its various clones and forks,
such as MariaDB_, Drizzle_ and `Percona Server`_)
has the largest market share of open source RDBMS.

Oracle's evaluation of the relative technical merits
of the three open source RDBMS
is quoted in the `EC Report`_:

.. epigraph::

   The notifying party argues that the database products 
   Ingres and PostgreSQL are also available under open source licenses 
   and are technically superior to MySQL, 
   in particular with regard to higher-end enterprise usage 
   targeting existing Oracle customers.    
   Therefore if any open source database product 
   were able to exercise a competitive constraint on Oracle, 
   it would be Ingres or PostgreSQL rather than MySQL.
   
   -- §662

Presently, Ingres_ could not be included in the candidate set,
as the community version does not appear to be under active development.
Ingres_ utilises a dual licensing model:
the open source (community) version is available
without charge to the end users under GPLv2;
a proprietary version is commercialised by Actian_.
The information available at the `Ingres Community`_ site
does not provide a clear separation between the
the community and the enterprise versions.
Furthermore, an analysis the `Ingres commit activity`_
on the `Ingres source code repository`_
indicates that no commits have been made to the main branch in the past 12 months.
Regarding the `IngresGeospatial`_ component,
the available roadmap also indicates
that there is no recent activity on the project.

The `EC report`_ provides an overview of the total cost of ownership (TCO),
based on 3rd party evaluations performed in 2009, stating that:

.. epigraph::

   MySQL and PostgreSQL are comparable in terms of price 
   for the smallest deployments, 
   and have by far the lowest prices for the largest.   
   While the price levels of MySQL and PostgreSQL 
   are directly comparable with each other, 
   none of the other [proprietary] vendors comes close 
   to either of these software packages for a large deployment.
   
   -- §243 et seq.
   
OpenVirtuoso_, another object relational database management system,
meets the minimum maturity criteria and is included in the candidate set of alternatives
(OpenVirtuoso is not mentioned in the EC report
that focuses on direct competitors to Oracle and MySQL).

The candidate set includes:

*  MySQL_
*  PostgreSQL_
*  and OpenVirtuoso_.

.. rubric:: Spatial data support
   
Support for the spatial components is a project-specific requirement
that, in practice, allows a decision between the 3 candidates.

The selected RDBMS **must** support spatial data:

*  OGC Well-Known Text (WKT) and OGC Well-Known Binary (WKB) datatypes [ISO_19125-1:2004]_
*  Geography Markup Language (GML) import/export  [ISO_19136:2007]_ [ISO.IEC_13249-3:2011]_
*  Spatial Reference System transformations [ISO.IEC_13249-3:2011]_
*  DE-9IM spatial operators (Clementini/Egenhofer Operators) [ISO_19125-2:2004]_

MySQL_ currently lacks a full implementation of the spatial components.

The spatial components of OpenVirtuoso_ are only available
in the proprietary version of the program.

PostgreSQL_ + PostGIS_ is the selected option:

*  PostGIS is the extension to PostgreSQL
   that allows spatial objects to be stored in the database,
   using the OGC WKT and WKB formats.
   (PostgreSQL is an object relational database that allows the definition
   of complex user datatypes).

*  Spatial data can be exported to GML,
   the XML grammar defined by OCG
   as a data modelling and open interchange format for geographic information.
   GML is used in the EU INSPIRE data models and data exchange specifications.
   [Inspire]_.

*  Support for the Dimensionally Extended 9 Intersection Model (`DE-9IM`_)
   basically guarantees that all relevant topological predicates
   (functions to check topological relations between two geometries)
   are implemented.

*  PostGIS also supports GeoJSON_ and TopoJSON_,
   that may be useful for map visualisation purposes
   (e.g. using Javascript libraries such as `D3.js`_).

*  Finally, PostGIS includes support for GiST-based R-Tree spatial indexes.

.. note::
   If or where only a simple SQL database engine is required, 
   while maintaining support for spatial data and operators,
   the recommended option is SQLite_ + SpatiaLite_. 

   SpatiaLite is available under an `MPLv1.1`_ licence, 
   which if fully compatible with EUPLv1.1.
         
   SQLite is under a `Public Domain`_ licence, 
   that is not an `OSI-approved licence`_: 
   that may require the acquisition of licence from the `Hwaci`_ 
   (depending on the specific legal requirements of a Member State).   

.. rubric:: Statistical computing support
   
Another project-specific requirement is also supported by PostgreSQL:
the support for statistical analysis.

At least two alternatives exist (see [Conw11]_ for examples):

*  Using PL/R, a loadable procedural language extension
   that supports writing PostgreSQL functions and triggers
   in the `GNU R`_ statistical computing language;

*  Accessing the database using RPostgreSQL_,
   the `GNU R`_ interface to the PostgreSQL database system.

Basically this means that, if required:

*  The statistical capabilities provided by GNU R
   can be called by the PostgreSQL database
   in a way that database programmers are familiar with;

*  The data stored in the PostgreSQL database
   can be accessed by GNU R
   in a way that statisticians are familiar with.

Implicit in the above discussion in the adoption of `GNU R`_ (GPLv2)
should any 'out-of-the-ordinary' statistical procedures be required
(e.g. for statistical disclosure control). [#GNU_R]_

.. rubric:: Key-value and/or XML data storage

Support for either key-value data storage or XML data storage
is a (plausible) functional project requirement.

A common data model at national level can be specified
based on well-known *a priori* requirements,
namely the need to produce the Eurostat THB indicators data cubes
and, consequently, to store the appropriate variables at microdata level.

However, it is likely that different countries
will need/want to store additional variables regarding victims, traffickers,
routes, etc., to comply with national reporting requirements.
These needs can not be foreseen and accommodated
into a single and canonical relational database model.
Two alternatives exist (which may complement each other):

*  a `NoSQL`_-like approach, whereby the additional data
   is stored as a semi-structured set of key-value pairs;

*  an SDMX-like approach,
   whereby the structure of the data is described using an XML schema
   and the data itself is stored in XML structured text.

PostgreSQL provides basic functionality to support either option:
key-value data storage using the hstore_ module (that defines the hstore datatype and functions)
and XML data storage using the native XML datatype and functions
(that use the xmllib2_ parser and toolkit).

.. rubric:: Note on portability and support
   
#. PostgreSQL is included by default in the main Linux distributions
   (Debian/Ubuntu and RedHat/CentOS/Fedora/Scientific), although
   the version maintained in each Linux distribution's official repository
   may not be the last one.
   However, all PostgreSQL releases are available
   in the PostgreSQL Apt Repository (for the Debian family)
   and the PostgreSQL Yum Repository (for the Red Hat family).

   PostgreSQL is also available for Microsoft Windows and Mac OS X.

#. As with the selected FOSS operating systems,
   both PostgreSQL and PostGIS are free of charge,
   but commercial versions and technical support are available for PostgreSQL
   (*inter alia*, by one of main developers, EnterpriseDB_)
   and for PostGIS
   (*inter alia*, by one of the main developers, `Refractions Research`_).

Real-world use
==============

The following table lists a sample of projects running on PostgreSQL + PostGIS solutions.

The selection is (completely) biased toward spatial data systems:
it focuses on national mapping and cadastral (land surveying) agencies,
spatial data infrastructures, and security and emergency response systems.

However, spatial data types are more complex than text, numeric or date data types
and spatial databases generally support a heavier workload than non-spatial databases.
So, even if a given system will not have a major spatial component,
these examples can be seen as 'stress testing' results for the proposed solution.

.. list-table::
   :widths: 90 10 

   *  - **Organization, system or project**
      - **References**
     
   *  -  `Eurogeographics`_ (MCA)
      - [#eurogeo]_
   *  - `Gestione Integrata e Interoperativa dei Dati Ambientali`_ (SDI), Italy
      - [#it_giita1]_ [#it_giita2]_
   *  - `Geodatastyrelsen`_ (MCA), Denmark                                              
      - [#dk_nma]_
   *  - `Global Disaster Alert and Coordination System`_ (SDI), UN & EC-JRC             
      - [#jrc_disaster]_
   *  - Global Monitoring for Environment and Security, EC-JRC                          
      - [#jrc_gmes]_
   *  - `Institut national de l’information géographique et forestière`_ (MCA), France  
      - [#fr_nma]_
   *  - `Instituto Geográfico Nacional`_ (MCA), Spain                                   
      - [#es_nma]_
   *  - `Landesamt für Vermessung und Geoinformation Bayern`_ (MCA), Germany            
      - [#de_fma]_
   *  - `Maanmittauslaitos`_ (MCA), Finland                                             
      - [#fi_nma]_ 
   *  - `Ordnance Survey`_ (MCA), UK                                                    
      - [#uk_nma]_
   *  - `Paikkatietoikkuna`_ (SDI), Finland                                             
      - [#fi_sdi]_
   *  - `Police Crime Map`_, UK                                                         
      - [#uk_police]_
   *  - `Publieke Dienstverlening op de Kaart`_ (SDI), Netherlands                      
      - [#nl_sdi]_
   *  - `Statens Kartverk`_ (MCA), Norway                                               
      - [#no_nma1]_ [#no_nma2]_

MCA: Mapping/Cadastral Agency

SDI: Spatial Data Infrastructure

----

.. rubric:: Footnotes
               
.. [#GNU_R] A discussion/comparison of statistical software packages is beyond the scope of this document. In this context, it is also deemed unnecessary as the GNU R Project is the *de facto* standard in statistical computing.
.. [#eurogeo] URL: http://inspire.jrc.ec.europa.eu/events/conferences/inspire_2011/presentations/workshops/269/ESDIN_D5_2_EuroGeographics_Technical_Architecture.pdf
.. [#it_giita1] URL: http://www.minambiente.it/export/sites/default/archivio/allegati/INSPIRE_state_of_play_2011_ITALY.pdf
.. [#it_giita2] URL: http://www.gdmc.nl/zlatanova/Gi4DM2010/gi4dm/Pdf/p116.pdf
.. [#dk_nma] URL: http://www.eurosdr.net/workshops/PostGIS/7_Rasmussen_de_Martino_Nielsen_KMS_Denmark.pdf
.. [#jrc_disaster] URL: http://meetingorganizer.copernicus.org/EGU2012/EGU2012-7404.pdf
.. [#jrc_gmes] URL: http://rslab.disi.unitn.it/papers/R72-JSTAR-Brunner.pdf
.. [#fr_nma] URL: http://postgis.net/2012/10/18/ign
.. [#es_nma] URL: http://inspire.jrc.ec.europa.eu/events/conferences/inspire_2012/presentations/143.pdf
.. [#de_fma] URL: http://www.fig.net/pub/fao/floss_cadastre.pdf.        
.. [#fi_nma] URL: http://www.paikkatietoikkuna.fi/web/en/open-spatial-data
.. [#uk_nma] URL: http://www.eurosdr.net/workshops/PostGIS/8_Bennett_Ordnance_Survey_UK.pdf
.. [#fi_sdi] URL: http://www.oskari.org/trac/wiki/DocumentationBackend
.. [#uk_police] URL: https://www.gov.uk/government/uploads/system/uploads/attachment_data/file/78964/Open_Source_Options_v2_0.pdf 
.. [#nl_sdi] URL: http://www.tudelft.nl//fileadmin/Faculteit/LR/Documenten/Onderwijszaken/lecture_postgis.pdf. 
.. [#no_nma1] URL: http://joinup.ec.europa.eu/sites/default/files/studies/IDABC-case-study-Norwegian%20Mapping%20Authority-final-version.pdf 
.. [#no_nma2] URL: http://www.eurosdr.net/workshops/PostGIS/6_Pedersen_Statkart_Norway.pdf
.. [#no_sdi] URL: http://norgedigitalt.no/norge_digitalt/engelsk/about_norway_digital/      


      
      
      
.. rubric:: References

.. [Conw11] Conway (2011) - PL/R - The Fast Path to Advanced Analytics.  URL: http://bunsen.credativ.com/~jco/2011/plr-PostgresOpen-2011.pdf http://bunsen.credativ.com/~jco/2011/plr-PGEast-2011.pdf
.. [Inspire] Directive 2007/2/EC of the European Parliament and of the Council of 14 March 2007 establishing an Infrastructure for Spatial Information in the European Community (INSPIRE) URL: http://inspire.jrc.ec.europa.eu
.. [ISO.IEC_13249-3:2011] "Information technology -- Database languages -- SQL multimedia and application packages -- Part 3: Spatial" URL: http://webstore.iec.ch/preview/info_isoiec13249-3%7Bed4.0%7Den.pdf 
.. [ISO.IEC_9075:2008] "Information technology -- Database languages -- SQL" 
.. [ISO_19125-1:2004] "Geographic information -- Simple feature access -- Part 1: Common architecture." URL: http://portal.opengeospatial.org/files/?artifact_id=25355
.. [ISO_19125-2:2004] "Geographic information -- Simple feature access -- Part 2: SQL option" URL: http://portal.opengeospatial.org/files/?artifact_id=25354
.. [ISO_19136:2007] "Geographic information -- Geography Markup Language (GML)" URL: http://www.opengeospatial.org/standards/gml




.. links-Placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt

.. _ORDBMS: http://publib.boulder.ibm.com/infocenter/idshelp/v115/index.jsp?topic=%2Fcom.ibm.gsg.doc%2Fids_gsg_416.htm
.. _DE-9IM: http://postgis.refractions.net/documentation/manual-1.5SVN/ch04.html#DE-9IM
.. _GeoJSON: http://www.geojson.org/
.. _TopoJSON: https://github.com/mbostock/topojson/wiki/Specification
.. _nosql: https://en.wikipedia.org/wiki/NoSQL

.. _xmllib2: http://www.xmlsoft.org/

.. _Ingres Community: http://community.actian.com/wiki/Welcome_to_the_Ingres_Community 
.. _Ingres source code repository: http://code.ingres.com/ingres/
.. _Ingres commit activity: http://www.ohloh.net/p/ingres
.. _IngresGeospatial: http://community.actian.com/wiki/IngresGeospatial

.. _Open Source Software for SDMX developed by EuroStat: https://webgate.ec.europa.eu/fpfis/mwikis/sdmx/index.php
.. _EUPLv1.1 licence compatibility: http://joinup.ec.europa.eu/software/page/eupl/eupl-compatible-open-source-licences
.. _European Commission's Report on the Oracle/Sun Microsystems merger: http://ec.europa.eu/competition/mergers/cases/decisions/m5529_20100121_20682_en.pdf
.. _EC Report: `European Commission's Report on the Oracle/Sun Microsystems merger`_

.. _MPLv1.1: http://www.mozilla.org/MPL/MPL-1.1.html

.. _Public Domain: http://creativecommons.org/licenses/publicdomain/
.. _distribution of GIS applications and libraries: http://pkg-grass.alioth.debian.org/debiangis-status.html
.. _proprietary DBMS market share: http://itknowledgeexchange.techtarget.com/eye-on-oracle/oracle-the-clear-leader-in-24-billion-rdbms-market/
.. _OSI-approved licence: http://opensource.org/licenses/alphabetical
.. _Hwaci: http://www.hwaci.com/cgi-bin/license-step1

.. _Eurogeographics: http://www.eurogeographics.org/
.. _Gestione Integrata e Interoperativa dei Dati Ambientali: http://www.dta.cnr.it/
.. _Geodatastyrelsen: http://www.gst.dk/English/
.. _Global Disaster Alert and Coordination System: http://www.gdacs.org/
.. _Institut national de l’information géographique et forestière:  http://www.ign.fr
.. _Instituto Geográfico Nacional: http://www.ign.es/ign/main/index.do
.. _Landesamt für Vermessung und Geoinformation Bayern: http://vermessung.bayern.de/
.. _Maanmittauslaitos: http://www.maanmittauslaitos.fi/en/file_download_service
.. _Ordnance Survey: https://www.ordnancesurvey.co.uk/oswebsite/products/os-mastermap/index.html
.. _Paikkatietoikkuna: http://www.paikkatietoikkuna.fi/web/fi
.. _Police Crime Map: http://www.police.uk/ 
.. _Publieke Dienstverlening op de Kaart: https://www.pdok.nl
.. _Statens Kartverk: http://www.statkart.no/en/

