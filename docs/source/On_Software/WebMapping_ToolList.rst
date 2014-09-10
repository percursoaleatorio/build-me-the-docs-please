.. _sw-list-webmapping-tools-ref:

OSGEO list of webmapping tools
##############################

.. note::

   For completeness sake, the original of the following list was retrieved from 
   http://wiki.osgeo.org/wiki/A\_comprehensive\_list\_of\_webmapping\_toolkits.

   
.. list-table::
   :widths: 10 10 40 10 10 10
 
   *  -  **Software**
      -  **Last release (date)**
      -  **Description**
      -  **Licence**
      -  **Map engines and protocols**
      -  **Language**

   *  -  AtlasMapper_
      -  1.3 (2012-11)
      -  The AtlasMapper is a cross platform JavaScript/Java mapping application 
         that allows a catalogue of map layers 
         to be easily browsed, layered, re-styled and compared side-by-side in a web browser.
      -  GPLv3
      -  WMS, NCWMS, ArcGIS Server, XYZ / OSM
      -  Java, JavaScript (GetExt, Openlayers, Ext JS)
      
   *  -  CartoWeb_ 
      -  3.5.0 (2008-09-04) **Inactive**
      -  CartoWeb is a comprehensive and ready-to-use Web-GIS as well as a 
         convenient framework for building advanced and customised applications.
      -  GPLv2.0+
      -  See MapServer_
      -  PHP_

   *  -  Chameleon_ 
      -  2.4.1 (2006.09.06) **Inactive**
      -  Chameleon is a distributed, highly configurable, environment for
         developing Web Mapping applications. It is built on MapServer as the
         core mapping engine and works with all MapServer supported data formats
         through a regular MAP file.
      -  MIT
      -  See MapServer_, WMS
      -  PHP_
      
   *  -  collective.geo_ (Plone Maps) 
      -  **Active**
      -  The goal is to provide a comprehensive set of tools to manage and
         publish geospatial data into the Plone_, using
         existing and proven technologies as much as possible.
      -  GPLv2.0
      -  (See OpenLayers_, Polymaps_)
      -  Python_, JavaScript_, OpenLayers_      
     
   *  -  dbox_ 
      -  0.9a1 (2006-05-08) **Inactive** 
      -  dbox is really a collection of DHTML-based libraries for building highly
         interactive web-based mapping applications. The tools are meant to work
         directly with the MapServer_ web mapping system. They provide relatively
         autonomous functionality without restricting overall design. In fact,
         they were designed to be used with old fashioned elements like tables.
      -  ?
      -  MapServer_
      -  JavaScript_, DHTML

   *  -  Dracones_
      -  1.1.3 (2010-12-06) **Inactive**
      -  Dracones is a MapServer_-based web mapping framework. Core components: A
         lightweight map widget, with a smooth navigation interface; Map layers
         with interactive behaviours, like mouse selection or tooltip (mouseover)
         information; Flexible query/extension mechanism; Handy other services
         like map image export, and history navigation
      -  BSD
      -  See MapServer_, WMS
      -  PHP_, Python_
      
   *  -  Flexlayers_
      -  Unknown (2009) **Inactive**
      -  Partial port of the OpenLayers mapping API from its native JavaScript to ActionScript 3
      -  LGPLv3 
      -  WMS, WMS-C, and WFS
      -  ActionScript 3

   *  -  Fusion_ 
      -  2.2.0 (2011-06-01) **Active**
      -  Fusion is a web-mapping application development framework for MapGuide
         OS and MapServer built primarily in JavaScript. It allows non-spatial
         web developers to build rich mapping applications quickly and easily.
      -  MIT
      -  See MapServer_, MapGuide_
      -  PHP_, JavaScript_ (Openlayers_)

   *  -  GeoExt_ 
      -  1.1 (2011.12.22) **Active**
      -  GeoExt is a JavaScript Toolkit for Rich Web Mapping Applications      
         that combines the OpenLayers library (for mapping components) 
         with the Ext JS JavaScript Framework. 
         See for example GeoExplorer_.
      -  BSD-3-Clause
      -  See OpenLayers_
      -  JavaScript_, (OpenLayers_, `Ext JS`_)

   *  -  geojsp_ 
      -  Unknown (Unknown) **No public sourceforge**
      -  geojsp is an open source (GPL) component that integrates geographic
         elements in your business intelligence infrastructure (geo-BI): thematic
         maps; flow maps; indicators; graphics (bar charts, pie chart, etc.)
      -  GPL
      -  See OpenLayers_
      -  Java

   *  -  GeoMondrian_ 
      -  1.0 (Unknown) **Last commit in 2012-04**
      -  GeoMondrian is a spatially-enabled version of Pentaho_ Analysis Services
         Mondrian_. It provides a consistent
         integration of spatial objects into the OLAP data cube structure,
         instead of fetching them from a separate spatial database, web service
         or GIS file.
      -  EPL
      -  See OpenLayers_
      -  Java

   *  -  GeoMOOSE_ 
      -  2.6.1 (2012-02-12) **Active: OSGEO Incubation**
      -  GeoMOOSE is a Web Client JavaScript Framework for displaying distributed
         cartographic data. GeoMOOSE has a number of strengths including
         modularity, configurability, and delivers a number of core
         functionalities in its packages.
         GeoMOOSE is built MapServer_, OpenLayers_ and the Dojo Toolkit.
      -  MIT
      -  MapServer, see OpenLayers_
      -  JavaScript, PHP

   *  -  GeoPrisma_ 
      -  1.6.3 (2012-11-27) **No information**
      -  GeoPrisma is a Web mapping application featuring Access Control 
         (Permissions) to geospatial data (Resources). 
         A single Resource can be served by multiple different 
         geodata servers (Services), such as WMS, TileCache, MapServer, 
         FeatureServer, etc. 
      -  BSD-3-clause
      -  see OpenLayers_
      -  PHP

   *  -  GeoShield_ 
      -  0.3.0 (2012-04) **Immature**
      -  GeoShield is a project born to offer a centralised way to define
         security access-control to geo-services. It acts like a proxy,
         intercepting all the communications between clients and OGC compliant
         services
      -  BSD-3-clause
      -  See GeoServer_, WMS, WFS, WPS, SOS
      -  Java

   *  -  GeoWebCache_ 
      -  1.4.0 (2013-07-09) **Active**
      -  GeoWebCache is a Java web application used to cache map tiles coming
         from a variety of sources such as OGC Web Map Service (WMS). It
         implements various service interfaces (such as WMS-C, WMTS, TMS, Google
         Maps KML, Virtual Earth) in order to accelerate and optimise map image
         delivery. It can also recombine tiles to work with regular WMS clients.
      -  LGPL
      -  WMS, WMS-C, TMS, WMTS
      -  Java
   
   *  -  GisClient_
      -  3.5.3 (2012-06-2012) **Inactive?**
      -  Web authoring tool configurator for MapServer that enables the user  
         both to build Mapfiles and to  provide OpenLayers maps.
      -  GPLv3
      -  See Mapserver_
      -  AJAX, Javascript, PHP/MapScript

   *  -  GPAAMP_ (Global Protected Areas Assessment and Monitoring Pilot)
      -  0.7 (2010-10) **Inactive**
      -  Supporting viewing and download services, 
         it functions primarily as a means for visualising information 
         from disparate sources delivered through standards-based web services. 
         It is based on the stack ExtJS, OpenLayers and GeoExt.
      -  Apache Licence 2.0
      -  See OpenLayers_
      -  Javascript (GeoExt, OpenLayers, ExtJs)

   *  -  `Heron Mapping Client`_
      -  0.73 (2013-06-07) **Active**
      -  GeoExt is a toolkit that combines OpenLayers with Ext JS 
         to help build desktop style GIS apps on the web with JavaScript. 
         The Heron MC leverages these frameworks by providing high-level 
         components and a convention to quickly assemble applications 
         merely through configuration (“Look ma no programming”).
      -  GPLv3
      -  See OpenLayers_
      -  Javascript_ (GeoExt_, OpenLayers_, `Ext JS`_)

   *  -  HSLayers_
      -  3.4.0 (2012-11-02) **Inactive**
      -  HSLayers combines OpenLayers (for mapping part) and ExtJS (for the
         graphical user interface) for complete desktop-like WebGIS toolkit in
         JavaScript. It also has several server-side little script for support of
         the web interface.
      -  GPL
      -  See OpenLayers_, MapServer_, WCS and WFS
      -  JavaScript, Python

   *  -  i3geo_
      -  Unknown (Unknown) **Active**
      -  i3geo provides a set of navigation tools, generation of analysis,
         sharing and generation of maps on demand.
      -  GPLv2.0+
      -  See MapServer_
      -  PHP_, JavaScript_

   *  -  ka-Map_ 
      -  1.0 (2007-05-02) **Inactive**
      -  ka-Map is an open source project that is aimed at providing a JavaScript
         API for developing highly interactive web-mapping interfaces using
         features available in modern web browsers.
      -  MapServer licence
      -  MapServer_
      -  PHP_, JavaScript_

   *  -  leaflet_ 
      -  0.6 (2013-06-26) **Active**
      -  Leaflet is a modern, lightweight JavaScript library for making
         tile-based interactive maps for both desktop and mobile web browsers.
      -  BSD-2-Clause
      -  tiled layers, WMS
      -  JavaScript_

   *  -  Mapbender_ 
      -  3.0.0 (2013-05-29) **Active: OSGEO project**
      -  Mapbender is the back office software and client framework for spatial
         data infrastructures. It provides a data model and web based interfaces
         for displaying, navigating and querying OGC compliant map services.
         It if based on the frameworks Symfony2, JQuery_ and OpenLayers_
      -  GPL, BSD
      -  WMS, WFS
      -  PHP_, JavaScript_

   *  -  MapFish_
      -  2.2 (2011-06-27) **Inactive**
      -  MapFish is a flexible and complete framework for building rich
         web-mapping applications. It emphasises high productivity, and
         high-quality development.
      -  BSD-3-Clause
      -  WMS, WFS
      -  Python_, JavaScript_

   *  -  MapProxy_
      -  1.5.0 (2012-12-05) **Active**
      -  It caches, accelerates and transforms data from existing map services
         and serves any desktop or web GIS client. MapProxy is a tile cache
         solution, but also offers many new and innovative features like full
         support for WMS clients.
      -  ASLv2.0
      -  WMS, TMS
      -  Python_

   *  -  MapQuery_ 
      -  0.1 (2011-07-28) **Inactive**
      -  MapQuery is a jQuery_ plug-in that you can use to add mapping to your
         website. Whether you quickly want to add a simple map to a page, or
         build a feature rich web application, MapQuery is just the thing you
         need.
      -  MIT
      -  See OpenLayers_
      -  JavaScript_

   *  -  `Modest Maps`_
      -  Unknown (Unknown) **Very low activity**
      -  Modest Maps is a small, extensible, and free library for designers and
         developers who want to use interactive maps in their own projects. It
         provides a core set of features in a tight, clean package with plenty of
         hooks for additional functionality
      -  BSD
      -  ?
      -  JavaScript_

   *  -  OpenLayers_
      -  2.13.1 (2013-07-09) **Active** 
         3.0.0alpha (2013-07-12) **Active**
      -  OpenLayers makes it easy to put a dynamic map in any web page. It can
         display map tiles and markers loaded from any source. OpenLayers has
         been developed to further the use of geographic information of all
         kinds.
      -  BSD-2-Clause 
      -  ArcGIS Server, GML, Google Maps, KML, MapGuide, MapServer, TMS, Bing Maps, WFS, WMS, etc.
      -  JavaScript_

   *  -  OpenScales_ 
      -  2.2 (2012-07-11) **Active**
      -  OpenScales is an open source (LGPL) mapping framework written in
         ActionScript 3 and Flex that enables developers to build Rich Internet
         Mapping Applications.
      -  Lesser GPL
      -  GML, KML, OSM, TMS, WFS, WMS and others.
      -  ActionScript, Flex, AIR

   *  -  p.mapper_ 
      -  4.3.1 (2013-04-04) **Active**
      -  The p.mapper framework is intended to offer broad functionality and
         multiple configurations in order to facilitate the setup of a MapServer
         application based on PHP/MapScript.
      -  GPLv2+
      -  MapServer
      -  JavaScript_, PHP_

   *  -  Polymaps_
      -  2.5.1 (2011-06-14) **Inactive**
      -  Polymaps is a free JavaScript library for making dynamic, interactive
         maps in modern web browsers. It provides speedy display of multi-zoom
         datasets over maps, and supports a variety of visual presentations for
         tiled vector data, in addition to the usual cartography from
         OpenStreetMap, CloudMade, Bing, and other providers of image-based web
         maps.
      -  BSD 3-clause
      -  Bing Maps, Cloudmade, OSM
      -  JavaScript_

   *  -  `ReadyMap Web SDK`_
      -  ?
      -  ReadyMap SDK is a free JavaScript library for embedding 3D maps in a web page. 
         Build 3D maps using ReadyMap's API, 
         or turn your OpenLayers or Leaflet maps into 3D globes.
      -  GPLv3
      -  See Openlayers_
      -  JavaScript_ (osgjs, jQuery_)
      
   *  -  TileCache_
      -  2.11 (2010-10-15) **Inactive**
      -  TileCache provides a Python-based WMS-C_ 
         server, with pluggable caching mechanisms and rendering backends. In the
         simplest use case, TileCache requires only write access to a disk, the
         ability to run Python CGI scripts, and a WMS you want to be cached.
      -  BSD-3-Clause
      -  Mapnik, MapServer, WMS
      -  Python_

   *  -  TileMill_ 
      -  0.10.1 (2012-10-10) **Active**
      -  TileMill is an application for making beautiful maps. Whether you're a
         journalist, web designer, researcher, or seasoned cartographer, TileMill
         is the design studio you need to create compelling, interactive maps.
      -  BSD
      -  Mapnik
      -  CSS-like map styling language

   *  -  `Thematic Mapping Engine`_
      -  2009 **Inactive**
      -  TME enables you to visualise global statistics on Google Earth. The
         engine returns a KMZ file that you can open in Google Earth or download
         to your computer.
      -  GPLv3
      -  KML
      -  JavaScript_, PHP_

      
.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt

