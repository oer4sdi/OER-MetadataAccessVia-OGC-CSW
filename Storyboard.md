# Using ISO Metadata and OGC Catalog Services to find data on Protected Sites in Germany

## 1. Overview

This learning material is a technical tutorial on how to access and use metadata in an SDI to find data on Protected Sites that is needed for windfarm planning in Germany.

After using this tutorial, you will be able to answer the following questions: 
*	How are metadata used to support the discoverability of datasets and services in an SDI? 
*	What is the role of the ISO and INSPIRE metadata standards in this context? 
*	What is the role of OGC catalog services (CSW) in this context?
*	How can I access OGC catalog services with QGIS?
*	How to write Python code that interacts with OGC Catalog services (CSW)?
*	What are the current trends in SDI development that will change the way we’re working with metadata?

The tutorial is structured as follows: 
1. Overview
2. Use case: Finding data on protected sites in the context of windfarm planning
3. Background
    * The role of Metadata in SDIs
    *	ISO metadata standards and how are they used in the context of INSPIRE
    *	OGC catalog services (CSW)
4.	Practical examples for accessing and using ISO metadata
    *	Accessing metadata via a geoportal 
    *	Accessing metadata via QGIS Metasearch
    *	Accessing metadata via Python from a Jupyter Notebook
5.	Summary and Notes on Related Topics

The tutorial takes about 30 Minutes for reading and viewing the provided materials, downloading the software and for conducting the hands-on exercises and tasks.  

This OER is primarily designed to be used by students in Geoinformatics, Geomatics and similar study programs. It is also useful for students of other study programs and for practitioners who want to enhance their understanding of SDI concepts and technologies. 
Some basic knowledge of web technologies such as HTTP and Web Services is required. However, you will be able to follow and find links to further resources if needed. 
Your computer should have #.# GB of usable RAM and #.# MB of usable disk space to download and use the software for this tutorial.

This Tutorial has been developed at the Institute for Geoinformatics, University of Münster. Authors are Tobias Krumrein and Albert Remke.

You are free to use, alter and reproduce the tutorial (H5P content, Storyboard) under the terms of the CC-BY-SA 4.0 license. Any code provided with the tutorial can be used under the terms of the MIT license. Please see the full license terms (tbd).

The OER4SDI project has been recommended by the Digital University NRW and is funded by the Ministry of Culture and Science NRW.

  
## Chapter 2: What is OGC CSW
__max. 5min__
  * what is OGC CSW
  * CSW methods and structures
## Chapter 3: Searching for Catalog Services on Web
__min. 10min__
  * Searching for example CSW with INSPIRE dataset in area of lower saxony on protected sites
    * GetCapabilities 
    * GetRecords
  * look into XML Response
    * understand the key features
  * Metadataprovider: Why it's good to look for INSPIRE
  * what are more readable ways for the user (HTML)
## Chapter 4: Accessing OGC CSW on QGIS and Python  
__around 15min__
  ### QGIS  
  * QGIS MetaSearch  
    * Open example CSW in QGIS 
    * Search with QGIS MetaSearch  
    * Open dataset in QGIS  
  ### Python
  * Jupyter Notebook 
