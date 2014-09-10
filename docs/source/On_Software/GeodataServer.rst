.. metadata-placeholder

:DC.Title:
	Selection of the Geospatial Data Server
:DC.Creator:
	Nery, Fernanda
:DC.Date:
	2013-05-01
:DC.Description:
   Information on the selection of the Geospatial Data and Metadata Server.
   Based on previous R&D projects.
   Removed GeoNetwork - metadata catalog server (won't be required).
   Removed dedicated tile servers (won't be required, will consume 3rd party services).
   Updated review of MapServer (the TinyOWS WFS Server has been integrated in the MapServer Suite project).
   Updated review of Deegree (now has available online documentation).
   Brief review of QuantumGIS Server (still does not comply with the maturity constraints).
:DC.Language:
	en
:DC.Format:
	text/x-rst
:DC.Rights:
	Access restricted to project members.
:DC.RightsHolder:
   Fernanda Néry 2009-2013 © CC BY-SA 3.0 http://creativecommons.org/licenses/by-sa/3.0/


.. _sw-geowebserver-ref:

Geospatial Data Server
**********************

Requirements
============

The selected geospatial data server is GeoServer_ 2.3.2+

**Iff** required:

*  GeoWebCache_ 1.3.0+ can be deployed as a standalone or integrated
   map tiles server.
*  GeoNetwork_ 2.10.0+ (which itself includes an integrated GeoServer_ server),
   can be used a spatial data catalogue system.

Rationale
=========

The purpose of the geodata server component is simply to provide
a layer of standardised geowebservices between the database
and the various possible client applications
(GIS desktop clients, web mapping applications, other geodata servers, etc.).

The geospatial data server must comply with the :ref:`sw-constraints-ref`
set on licence compatibility, portability and acquisition cost.

It must also be compatible with / supported on
the software stack that was previously selected:

*  Microsoft Windows, Ubuntu, CentOS (see :ref:`sw-operating-systems-ref`)
*  PostgreSQL + PostGIS (see :ref:`sw-database-ref`)

.. _sw-ogc-webservices-ref:

Compliance with Open Geospatial Consortium (OGC_) WMS, WFS and WFS-T
standards is a basic technical interoperability requisite.

*  In Portugal, compliance with the
   OGC Web Feature Service (WFS_) Interface Standard and the
   OGC Web Map Service (WMS_) Interface Standard
   is also a legal requisite established by the
   National Regulation on Digital Interoperability (Open Standards). [RNID12]_

*  In the European Union, and under the provisions of the INSPIRE_ Directive,
   Member States must share spatial datasets relevant for environmental policy
   (34 spatial data themes, that include *inter alia*
   geographical names, administrative units, addresses, and population and demography).

   Member States are also required to create web services
   for accessing these datasets, and these must be OGC-compliant services
   (see `INSPIRE Implementing Rules`_ for details)


Analysis of alternatives
========================

Again, progressive filtering was based on maturity and sustainability criteria.

To simplify the triage of candidate solutions,
only `OSGEO Foundation`_ projects where considered.
The `OSGEO incubation process`_
is essentially a peer-reviewed evaluation
inspired by the CMMI maturity levels [CMMI10]_:
graduated projects comply with an adequate
`set of criteria <OSGEO graduation criteria>`_
focused on maturity and sustainability aspects.

The candidate set includes:

*  deegree_ (
   initial release in `2002 <http://deegree.org/About>`__
   OSGEO graduated project in `02.2010 <http://www.osgeo.org/node/1004>`__
   ), under a LGPLv2 licence.

*  GeoServer_ (
   initial release in `2002 <http://sourceforge.net/projects/geoserver/files/GeoServer/>`__,
   OSGEO graduated project in `03.2013 <http://www.osgeo.org/news/geoserver-graduation>`__
   ), under a GPLv2+ licence.

*  MapServer_ (
   first release as FOSS in `1999 <https://github.com/mapserver/mapserver/wiki/MapServerHistory>`__,
   OSGEO graduated project in `12.2008 <http://lists.osgeo.org/pipermail/announce/2008-December/000112.html>`__
   ), under a Mapserver licence. [#mapserver-licence]_

.. rubric:: Non-functional considerations

#. deegree_ and GeoServer_ are written in Java,
   a factor that weights positively
   in the current selection procedure:
   given that EuroStat's SDMX tools are available for the Java platform,
   a compatible software stack (e.g. the Java servlet container) can be used
   and a less disparate portfolio of software
   and software administration skills is required.
   The same applies to programming skills, should Java be adopted as the
   implementation language for any additional software components. [#geotools]_

#. Similarly, an alternative solution based on MapServer_ and TinyOWS_
   can be deemed more adequate in projects where:

   *  a PHP web development framework is adopted;

   *  the PHP MapScript component
      is used/required for the developed of interactive mapping applications.

#. Currently, there is considerably less available documentation
   (notably 3rd parties tutorials, books, etc.) and service providers
   for deegree_ than for GeoServer_ or MapServer_.
   A similar trend is observable by comparing the activity on the
   `discussion lists <http://osgeo-org.1560.x6.nabble.com/OSGeo-Software-and-Data-Projects-f3741872.html>`__
   of the three products.

   Also, there are no publicly available comparative benchmarks of deegree_
   against the other geodata server products.

#. Performance benchmarks [#benchmarks]_ of MapServer vs. GeoServer
   show superior throughput of MapServer
   when using FastCGI on Linux Operating Systems
   (MapServer results on Windows machines are erratic --
   specially when there is an higher number of concurrent requests --
   and, for some request types, throughtput is inferior to GeoServer's
   when there are less than 4 concurrent clients). [#mapnik-portability]_.

As a result of this preliminary evaluation,
deegree_ was considered a dominated solution in the candidate set.
The evaluation is not based on the product's intrinsic features and capabilities.
It is merely the result of a lower score on QSOS maturity criteria and
also a smaller user community and relative scarcity of real-world use cases
(the notable exception being the choice of deegree to support the
`EU INSPIRE geoportal <http://ted.europa.eu/udl?uri=TED:NOTICE:96422-2011:TEXT:EN:HTML>`__).

.. rubric:: Support for OGC W*S interfaces
   
The basic type of geowebservices to be considered are:

*  Web Map Services (see `WMS overview`_): allow the visual display of spatial data
   (without necessarily providing access to the features that comprise those data).
*  Web Feature Services (see `WFS overview`_): read-only vector spatial features (i.e. points, lines or polygons,
   typically with associated alphanumeric information);
*  Transactional WFS (WFS-T): editable vector spatial features where
   editing permissions can be controlled through
   user authentication and authorisation (
   the mechanism of authorisation and the supported granularity of control
   varies in different products).

MapServer_ does not support WFS-T,
as stated in the current MapServer 6.2.1 documentation:

.. epigraph::
   This is just a basic WFS (read-only): 
   transaction requests are not supported 
   and probably never will given the nature of MapServer. 
   GeoServer or TinyOWS is recommended for those needing WFS-T support.
   
   Source: http://mapserver.org/ogc/wfs_server.html
   
TinyOWS_ is a WFS server that has recently been incorporated
into the MapServer Suite, to address the lack of WFS-T services.
Currently, PostGIS is the only spatial database back-end supported by TinyOWS.
Such limitation is not relevant from this specific project but
diminishes the reusability of the component
(e.g. potential users may care to publish other geospatial data stored in
common proprietary databases, such as Oracle Spatial and Graph or ESRI ArcSDE
spatially-enabled databases).

In Geoserver_, fine-grained access authorisation (e.g. for edit operations)
can be delegated in and controlled by the database system [#GeoServer-auth-DBMS]_,
an option currently under discussion in the MapServer community [#TinyOWS-auth-DBMS]_.

As stated before, deegree_ provides the required W*S interfaces,
albeit directed towards a rather more technical user profile than GeoServer,
due to the relative paucity of documentation and graphical user interfaces.

.. rubric:: Conclusions

The evaluation results are:

*  MapServer+TinyOWS or deegree are adequate and sufficient
   solutions for the identified W*S requirements
*  GeoServer is equally adequate, better documented (than deegree),
   easier to configure and publish services (than deegree or MapServer)
   and supports a larger number of database back-ends (than TinyOWS), namely
   PostGIS, H2, ArcSDE, DB2, MySQL, Oracle, Microsoft SQL Server and SQL Azure.

The following excerpt provides an adequate overview of the 3 products:

.. epigraph::
   
   GeoServer, MapServer and Deegree are open-source map server products 
   focusing on Internet mapping applications using OGC webGIS standards. 
   These OGC interoperability standards such as WMS, WFS and WFS-T 
   allow for the cross-platform exchange of geographic information 
   over the Internet. 
   Using these standards, 
   map data stored in Oracle Spatial, PostGIS or ArcSDE databases 
   can be accessed over the Internet with a standard web browser 
   or GIS client software. 
   With WMS, map data can be accessed and displayed as an image 
   that can be overlaid with GIS data from other data sources 
   to produce composite maps. 
   With WFS, users can access the actual geographic features in vector format, 
   while WFS-T allows for creation, deletion and updating of features. 
   MapServer, GeoServer and Deegree are server-based “map engines” 
   to display spatial data 
   (maps, images or vector data depending on the OGC web service) 
   over the Internet to users based on their requests. [...] 
   MapServer has proved to be a very mature and reliable product 
   to distribute maps from GIS data sources over the Internet 
   through the WMS, WCS and other OGC interoperability standards. 
   GeoServer and Deegree are more recent projects built with Java technology. 
   While comparable to MapServer in many ways, 
   GeoServer and Deegree go further by supporting transactional WFS services, 
   allowing users to insert, delete and modify geographical data 
   at the source from remote locations through the Internet.
   
   -- Source: [Piep10]_   
   

Real-world use
==============

The following table lists a sample of projects using GeoServer.

.. list-table::
   :widths: 90 10 
      
   *  - **Organization, system or project**
      - **References**

   *  - Instituto Geográfico Nacional (MCA), Spain                                   
      - [#es_nma]_  
   *  - Gestione Integrata e Interoperativa dei Dati Ambientali (SDI), Italy
      - [#it_giita1]_ [#it_giita2]_
   *  - Global Disaster Alert and Coordination System (SDI), UN & EC-JRC             
      - [#jrc_disaster]_   
   *  - Global Monitoring for Environment and Security, EC-JRC                          
      - [#jrc_gmes]_
   *  - Paikkatietoikkuna (SDI), Finland                                             
      - [#fi_sdi]_
   *  - UK Location Programme
      - [#uk-location-geoserver]_

Final notes
===========

.. rubric:: Note on support for map tile services

Support for WMTS_ services is not considered a *must-have* requirement
for this project:  the spatial information can be stored as vector data
in the database, and served using WMS or WFS services.
It is not foreseable that a large number of concurrent requests will
require a Map Tile server.
Consumption of 3rd-party map tile services (e.g. Mapquest, Google Maps, etc.)
will be required in the web mapping component, but it is unlikely that a
WMTS server will be strictly necessary.
If, for performance reasons, a map tile server becomes necessary,
two simple options exist:

*  Geoserver includes an integrated version of GeoWebCache_,
   a tiling server that runs as a proxy between a map client and map server,
   caching (storing) tiles as they are requested,
   eliminating redundant request processing and reducing response time,
*  GeoWebCache_ (under a LGPL licence) can also be deployed
   as a standalone product to implement WMS-C, WMTS, TMS or Google Maps KML
   service interfaces (e.g. to expose some map services to the public through
   a different server).

.. rubric:: Note on support for spatial catalogue services

Support for `CSW`_ services is not considered a *must-have* requirement
for this project, although metadata should stored for the various datasources.
If a spatial data catalog is required, the obvious option is to use another
Java application, Geonetwork_, which was developed for, and is used by,
various United Nations offices and programmes (FAO_, OCHA_, UNEP_ and  WFP_).

.. rubric:: Note on portability

All required GIS components are avaliable for
and supported on Linux distributions:

*  Currently, the 'Debian family' has the most inclusive and up-to-date
   distribution of FOSS GIS applications and libraries.
   Repositories maintained by the DebianGIS_ project
   and the UbuntuGIS_ project
   (the latter does the repackaging for the Ubuntu distribution,
   and also includes some software packages that do not comply
   with the stricter `Debian Policy`_).

*  For the 'Red Hat family', RPM repositories are available
   via the ELGIS_ project and the EPEL_ Fedora project
   (for packages that are not part of the
   standard Red Hat Enterprise Linux distribution).

.. rubric:: Output formats 
   
The following excerpt lists output formats supported by GeoServer
in response to W*S requests.
As can be noticed, some of the output formats (GeoJSON, GML, KML, SVG)
are also supported directly by PostGIS_.
However, the use of a web service interface (either WMS or WFS) provides
an additional level of abstraction that isolates client applications
from the database and provides a standardized grammar for obtaining the information
(e.g. allowing the use of desktop GIS applications to
explore the data, or the development of independent data visualizations tools).

.. topic:: GeoServer output formats

   **Image Outputs**

   All image outputs can be initiated from a WMS getMap request on either a raster,
   vector or coverage data. 

   .. list-table::
      :widths: 10 90 

      * - **Format**
        - **Description**
        
      * - KML
        - KML (Keyhole Markup Language) is an XML-based language schema for expressing geographic data in an Earth browser, such as Google Earth or Google Maps. KML uses a tag-based structure with nested elements and attributes. For GeoServer, KML files are distributed as a KMZ, which is a zipped KML file.
      * - JPEG
        - WMS output in raster format. The JPEG is a compressed graphic file format, with some loss of quality due to compression. It is best used for photos and not recommended for exact reproduction of data.  
      * - GIF
        - WMS output in raster format. The GIF (Graphics Interchange Format) is a bitmap image format best suited for sharp-edged line art with a limited number of colors. This takes advantage of the format's lossless compression, which favors flat areas of uniform color with well defined edges (in contrast to JPEG, which favors smooth gradients and softer images). GIF is limited to an 8-bit palette, or 256 colors.
      * - SVG
        - WMS output in vector format. SVG (Scalable Vector Graphics) is a language for modeling two-dimensional graphics in XML. It differs from the GIF and JPEG in that it uses graphic objects rather than individual points.     
      * - TIFF
        - WMS output in raster format. TIFF (Tagged Image File Format) is a flexible, adaptable format for handling multiple data in a single file. GeoTIFF containts geographic data embedded as tags within the TIFF file.
      * - PNG
        - WMS output in raster format. The PNG (Portable Network Graphics) file format was created as the free, open-source successor to the GIF. The PNG file format supports truecolor (16 million colors) while the GIF supports only 256 colors. The PNG file excels when the image has large, uniformly coloured areas.       
      * - OpenLayers
        - WMS GetMap request outputs a simple OpenLayers preview window. OpenLayers_ is an open source JavaScript library for displaying map data in web browsers. The OpenLayers output has some advanced filters that are not available when using a standalone version of OpenLayers. Further, the generated preview contains a header with easy  configuration options for display.
      * - PDF
        - A PDF (Portable Document Format) encapsulates a complete description of a fixed-layout 2D document,including any text, fonts, raster images, and 2D vector graphics.  
    
   **Text Outputs**

   .. list-table::
      :widths: 10 90 

      * - **Format**
        - **Description**

      * - AtomPub
        - WMS output of spatial data in XML format. The AtomPub (Atom Publishing Protocol) is an application-level protocol for publishing and editing Web Resources using HTTP and XML. Developed as a replacement for the RSS family of standards for content syndication, Atom allows subscription of geo data.
      * - GeoRss
        - WMS GetMap request output of vector data in XML format. RSS (Rich Site Summary) is an XML format for delivering regularly changing web content. `GeoRss <http://www.georss.org>`_ is a  standard for encoding location as part of a RSS feed.supports  Layers Preview produces a RSS 2.0 documents, with GeoRSS Simple geometries using Atom. 
      * - GeoJSON
        - `JavaScript Object Notation <http://json.org/>`_ (JSON) is a lightweight data-interchange format based on the JavaScript programming language. This makes it an ideal interchange format for browser based applications since it can be parsed directly and easily in to javascript. GeoJSON is a plain text output format that add geographic types to JSON. 
      * - CSV
        - WFS GetFeature output in comma-delimited text. CSV (Comma Separated Values) files are text files containing rows of data. Data values in each row are separated by commas. CSV files also contain a comma-separated header row explaining each row's value ordering. GeoServer's CSVs are fully streaming, with no limitation on the amount of data that can be outputted. 

   **Data Outputs**

   All data outputs are initiated from a WFS GetFeature request on vector data.

   .. list-table::
      :widths: 10 90 

      * - **Format**
        - **Description**

      * - GML2/3
        - GML (Geography Markup Language) is the XML grammar defined by the `Open Geospatial Consortium <http://en.wikipedia.org/wiki/Open_Geospatial_Consortium>`_ (OGC) to express geographical features. GML serves as a modeling language for geographic systems as well as an open interchange format for geographic data sharing. GML2 is the default (Common) output format, while GML3 is available from the "All Formats" menu.
      * - Shapefile
        - The ESRI Shapefile, or simply a shapefile, is the most commonly used format for exchanging GIS data. GeoServer outputs shapefiles in zip format, with a directory of .cst, .dbf, .prg, .shp, and .shx files. 

   
----

.. rubric:: Footnotes 

.. [#mapserver-licence] The `MapServer licence <http://mapserver.org/copyright.html>`_ 
   is an `MIT like <http://opensource.org/licenses/MIT>`__ permissive licence. 

.. [#geotools] Geoserver incorporates GeoTools_, 
   an open source (LGPL) Java code library which provides 
   standards compliant methods for the manipulation of geospatial data, 
   that is used in several GIS applications.

.. [#benchmarks] Benchmark data are available at http://wiki.osgeo.org/wiki/FOSS4G_Benchmark.

      For products supporting WMTS services ('GoogleMaps-like' tiled map services), 
      the following links provide useful information:
      http://www.esdm.co.uk/mapserver-and-geoserver-and-tilecache-comparison-serving-ordnance-survey-raster-maps,
      http://www.esdm.co.uk/further-load-testing-of-geoserver-and-mapserver-and-tilecache and 
      http://developmentseed.org/blog/2010/oct/19/qa-mapnik-performance-just-important-its-beauty/.

.. [#mapnik-portability] It should be noted that, for high-demand image map services (WMS), 
      both products where outperformed by mapnik_. 
      Mapnik is not fully supported in Microsoft Windows operating systems.
      
.. [#GeoServer-auth-DBMS] URL: http://docs.geoserver.org/stable/en/user/data/database/sqlsession.html#using-sql-session-scripts-to-control-authorizations-at-the-database-level
.. [#TinyOWS-auth-DBMS] URL: https://github.com/mapserver/tinyows/issues/43

.. [#uk-location-geoserver] URL: http://data.gov.uk/sites/default/files/Data-Publisher-How-To-Guide-Establish-a-Reference-Implementation-for-an-INSPIRE-View-Service-using-a-GeoServer.pdf
.. [#jrc_gmes] URL: http://rslab.disi.unitn.it/papers/R72-JSTAR-Brunner.pdf
.. [#es_nma] URL: http://inspire.jrc.ec.europa.eu/events/conferences/inspire_2012/presentations/143.pdf
.. [#jrc_disaster] URL: http://meetingorganizer.copernicus.org/EGU2012/EGU2012-7404.pdf
.. [#it_giita1] URL: http://www.minambiente.it/export/sites/default/archivio/allegati/INSPIRE_state_of_play_2011_ITALY.pdf
.. [#it_giita2] URL: http://www.gdmc.nl/zlatanova/Gi4DM2010/gi4dm/Pdf/p116.pdf
.. [#fi_sdi] URL: http://www.oskari.org/trac/wiki/DocumentationBackend


----

.. rubric:: References

.. [CMMI10] CMMI Product Team (2010). Capability Maturity Model® Integration for Development, Version 1.3, Improving processes for developing better products and services. no. CMU/SEI-2010-TR-033. Software Engineering Institute. URL: http://www.sei.cmu.edu/library/abstracts/reports/10tr033.cfm
.. [Weic13] Weichand, Jurgen (2013). Entwicklung und Anwendung von Downloaddiensten im Kontext der europäischen Geodateninfrastruktur INSPIRE. 
.. [Kolo04] Kolodziej, Kris (ed.) (2004). OpenGIS® Web Map Server Cookbook. OGC Document Number: 03-050r1 Version: 1.0.2 URL: http://portal.opengeospatial.org/files/?artifact_id=7769
.. [Piep10] Pieper, Gertrude (2010). Existing Open-Source Tools - Possibilities for Cadastral Systems. in Steudler, D; Torhonen, M-P and Pieper, G. (2010) (ed.) - FLOSS in Cadastre and Land Registration. Opportunities and Risks. y Food and Agriculture Organization of the United Nations (FAO) and the International Federation of Surveyors (FIG). :24-32

.. links-placeholder       

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt

.. _INSPIRE Implementing Rules: http://inspire.jrc.ec.europa.eu/index.cfm/pageid/47
.. _INSPIRE: http://inspire.jrc.ec.europa.eu/
.. _OGC: http://live.osgeo.org/en/standards/standards.html

.. _Debian Policy: http://www.debian.org/doc/debian-policy/

.. _FAO: http://www.fao.org/
.. _WFP: http://www.wfp.org/
.. _OCHA: http://www.unocha.org
.. _UNEP: http://www.unep.org

.. _OSGEO Foundation: http://www.osgeo.org/content/foundation/about.html
.. _OSGEO incubation process: http://www.osgeo.org/incubator
.. _OSGEO graduation criteria: http://www.osgeo.org/incubator/process/project_graduation_checklist.html


