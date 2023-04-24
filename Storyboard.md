# OER Module: Using ISO Metadata and OGC Catalog Services to find data on Protected Sites in Germany
## 1. Overview

This learning material is a technical tutorial on how to access and use metadata in an SDI to find data on Protected Sites that is needed for windfarm planning in Germany.
After using this tutorial, you will be able to answer the following questions:
* How can we use metadata for discovering datasets and services in an SDI?
* What is the role of the ISO and INSPIRE metadata standards?
* What is the role of OGC catalog services (CSW)?
* How can I access OGC catalog services with QGIS and/or Python Code?
* What other approaches are being used to support the discoverability of datasets and services?  

The tutorial is structured as follows:  
1. Overview  
2. Use case: Finding data on protected sites in the context of windfarm planning
3. Background  
  3.1 The role of Metadata in SDIs  
  3.2 ISO metadata standards and how are they used in the context of INSPIRE  
  3.3 OGC catalog services (CSW)  
4. Practical examples for accessing and using ISO metadata  
  4.1 Downloading and installing the software for the hands-on exercises
  4.2 Accessing metadata via geoportals  
  4.3 Accessing metadata via Python from a Jupyter Notebook  
  4.4 Accessing metadata via QGIS Metasearch  
5. Summary and Notes on Related Topics  

The tutorial takes about 30 Minutes for reading and viewing the provided materials, downloading the software and for conducting the hands-on exercises and tasks.

This OER is primarily designed to be used by students in Geoinformatics, Geomatics and similar study programs. It is also useful for students of other study programs and for practitioners who want to enhance their understanding of SDI concepts and technologies. Some basic knowledge of web technologies such as HTTP and Web Services is required. However, you will be able to follow and find links to further resources if needed. Your computer should have #.# GB of usable RAM and #.# MB of usable disk space to download and use the software for this tutorial.
This Tutorial has been developed at the Institute for Geoinformatics, University of Münster. Authors are Tobias Krumrein and Albert Remke.

You are free to use, alter and reproduce the tutorial (H5P content, Storyboard) under the terms of the CC-BY-SA 4.0 license. Any code provided with the tutorial can be used under the terms of the MIT license. Please see the full license terms (tbd).

The OER4SDI project has been recommended by the Digital University NRW and is funded by the Ministry of Culture and Science NRW.

# 2. Use case: Finding data on protected sites in the context of windfarm planning  

A local authority in Lower Saxony has hired you to cooperate with a private investor to identify several potential sites in the state for enlarging and repowering existing wind farms with high-efficiency wind turbines. The selected site must meet several characteristics:  
* Located in the state of Lower Saxony  
* Within 4 km of existing wind farms containing turbines  
* Within at least 800 m of neighbouring houses   
* Does not intersect with any protected site   

The spatial data analysis plays a really important role for windfarm planning, to locate viable areas for new planning zones. The datasets must be up-to-date to get the most accurate data. To meet these criteria, you need to explore and find the data for example for the topic protected sites. Now you’re searching for datasets on the web for the protected sites in lower saxony. But which one fits best for you? For such purposes SDIs have Catalog Services which are filled with Metadata describing their available datasets. You can access these Catalogue Services via geoportals, like geodatenkatalog.de, and search there for your wanted data. To find your data it’s necessary that the available datasets are described with quality metadata. By filtering through the metadata you can browse the geoportal to get the wanted dataset. To accurately describe data with metadata there are standards that have been developed like the ISO metadata standards.   
After browsing through the geoportals and finding your wanted datasets you can then download it and load it into a QGIS project to visualise and analyse it. Now let's dive deeper into Metadata and Catalogue Services.

# 3. Background

## 3.1 The role of Metadata in SDIs

Metadata plays a critical role in Spatial Data Infrastructures (SDIs), which are complex distributed systems designed to facilitate the discovery, access, and use of spatial data. Metadata provides essential information about spatial data resources, including their content, quality, and spatial extent, enabling users to find and evaluate data that meets their specific needs. Metadata is a crucial component of the Publish-Find-Bind model, which forms the basis of SDI architecture. In this model, metadata is published to a catalogue, which users can search to find data resources that match their criteria. Different search engines and catalogues may have different capabilities and search algorithms, which can impact the effectiveness and efficiency of data discovery. Therefore, it is important to consider the characteristics and capabilities of search engines and catalogues when designing and implementing SDIs. Overall, metadata is a critical element of SDI architecture, enabling efficient and effective data discovery, sharing, and use across distributed systems.

## 3.2 ISO metadata standards and how are they used in the context of INSPIRE

Standardising data models for metadata is essential to ensure that spatial data can be effectively shared and used across different systems and organisations. The International Organization for Standardization (ISO) has developed a series of metadata standards, including ISO 19115, which defines a conceptual data model for describing spatial data and associated metadata. This model provides a standardised framework for describing the content, quality, and spatial extent of spatial data, as well as information on ownership, access, and usage restrictions. To facilitate the implementation of ISO metadata standards, ISO has also developed encoding standards, such as ISO 19139, which provide a standardised syntax and structure for encoding metadata in different formats.   

The European Union's INSPIRE Directive mandates the use of ISO metadata standards in the context of spatial data infrastructure development, implementation, and maintenance. INSPIRE requires Member States to establish national metadata catalogues that conform to ISO metadata standards and to provide interoperable access to spatial data resources. By standardising metadata, INSPIRE aims to promote the sharing and reuse of spatial data across Europe, thereby facilitating cross-border and cross-sector data interoperability.  

In summary, ISO metadata standards play a crucial role in standardising the conceptual data model and encoding standards for metadata, facilitating data interoperability and data sharing. The INSPIRE Directive mandates the use of ISO metadata standards to promote the sharing and reuse of spatial data across Europe, contributing to the development of an efficient and effective European Spatial Data Infrastructure.  

## 3.3 OGC catalog services (CSW)

The Open Geospatial Consortium (OGC) Catalog Services (CSW) is a standard that provides a standardised interface for accessing metadata catalogues in spatial data infrastructures. The OGC develops and maintains standards for geospatial technologies to promote interoperability and facilitate the sharing and use of geospatial data across different systems and organisations. The CSW standard defines a set of operations for querying metadata catalogues, including search, retrieval, and management of metadata records. The CSW standard enables users to search for metadata using keywords, geographic extent, or other search criteria, and to retrieve metadata records in different formats, such as XML or JSON. The CSW standard has been implemented in a range of tools and instances, such as QGIS MetaSearch or ESRI Geoportal Server, which provide software solutions for managing and accessing metadata catalogues. Overall, the OGC CSW standard plays a critical role in enabling efficient and effective access to metadata catalogues in spatial data infrastructures, promoting data interoperability and facilitating the sharing and use of spatial data.   

# 4.	Practical examples for accessing and using ISO metadata

Now you're getting some practical examples for accessing Catalogue Services through different approaches. But before you can start with them, you need to install QGIS [and also will need to download the Jupyter Notebooks]. 

## 4.1 Downloading and installing the software for the hands-on exercises
If you already have QGIS 2.0 or higher installed you can skip this part and go directly to the next part, because the plugin MetaSearch, which you're using later, is included by default.  
For downloading QGIS please follow the next steps:
1. Go to the QGIS Website https://www.qgis.org/en/site/forusers/download.html  
2. Choose your operating system from the options that are listed  
3. Than download QGIS (this step may take some time, in this time we can already continue with the next part(s) and come back later for the last to steps)  
4. After downloading run the installer and follow the prompts to install QGIS on your computer

## 4.2 Accessing metadata via geoportals 



## 4.3 Accessing metadata via Python from a Jupyter Notebook



## 4.4 Accessing metadata via QGIS MetaSearch
The last example approach for accessing metadata through catalogue services, is through QGIS MetaSearch. Now you're downlaod should be complete and you can start with the last steps:
* run the installer and follow the prompts to install QGIS on your computer
  
Now you're ready to go.



# 5.	Summary and Notes on Related Topics

