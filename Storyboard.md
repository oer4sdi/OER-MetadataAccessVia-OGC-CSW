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
