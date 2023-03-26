# Using ISO Metadata and OGC Catalog Services to find data on Protected Sites in Germany

## 1. Overview

This learning material is a technical tutorial on how to access and use metadata in an SDI to find data on Protected Sites that is needed for windfarm planning in Germany.

After using this tutorial, you will be able to answer the following questions: 
*	How can we use metadata for discovering datasets and services in an SDI? 
*	What is the role of the ISO and INSPIRE metadata standards? 
*	What is the role of OGC catalog services (CSW)?
*	How can I access OGC catalog services with QGIS and/or Python Code?
*	What other approaches are being used to support the discoverability of datasets and services?

The tutorial is structured as follows: 
1. Overview
2. Use case: Finding data on protected sites in the context of windfarm planning
3. Background
    * The role of Metadata in SDIs
    *	ISO metadata standards and how are they used in the context of INSPIRE
    *	OGC catalog services (CSW)
4.	Practical examples for accessing and using ISO metadata
    * Downloading and installing the software for the hands-on exercises
    * Accessing metadata via a geoportal 
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

# 2. Use case: Finding data on protected sites in the context of windfarm planning
[start form the real-world use case "windfarm planning" with its need for spatial data analysis and certain datasets to identify the viable area for the extension of new planning zones (-> we need the most up-to-date datasets on proteted sites and their footprint since these are exclusion areas for wind farms; **briefly** summarize the workflow with just a few screenztprints ->  use a geoportal to search for, find and download a dataset, load it into a QGIS project and show the exclusion areas; rshow that the same dataset is available in many portals (lower saxony, national portal);  point to the open questions -> what happened under the hood? How is the metadata organized? what technologies are involved?]

# 3. Background

## 3.1 The role of Metadata in SDIs

[general overview on the role of metadata in SDIs -> architecture of a distributed System; resources & metadata; publish find bind; comparing search engines and catalogs; ..]

## 3.2 ISO metadata standards and how are they used in the context of INSPIRE

[why standardizing data models for metadata makes sense; conceptual data model / encoding metadata; role of ISO, ISO metadata Standards,INSPIRE]

## 3.3 OGC catalog services (CSW)

[idea of standardized interfaces; role of OGC; overview on the CSW standard (Operations); implementations (tools, instances) ]

# 4.	Practical examples for accessing and using ISO metadata

## 4.1 Downloading and installing the software for the hands-on exercises
[overview on the technical setup as needed for the practical exercises; guidance on doanloading and installing the software -> QGIS, Jupyter, Pythoin Notebook(s)]


## 4.2 Accessing metadata via geoportals 

[introduction: what are we trying to showcase in this practical example; <br>
taking up the use case; use a geoportal to search for and find data on protected sites; use the HTML user interface of the geoportal to view the metadata in a nice layout; view the metadata set in plain XML (-> refers to what we've learned in section 3.2); provide some help to read the content of the XML file (nasty, but doable; as for the meaning of the attributes point to the name spaces and sources of documentation);clarify that XML ist to a certain extent human readable (less than HTML), but the main purpose is to encode data for machine-to-machine communication (-> QGIS, Python; other catalogs; clarify the role of a catalog service in the ocntext of the portal (-> dedicated meta-database queries; supporting the federation of catalogs); discussing some findings: todays portals have just some basic metadata retrieval functionality, the capabilities of the existing search engines go far beyond ]

## 4.3 Accessing metadata via QGIS Metasearch

[introduction: what is the context and what are we trying to showcase in this practical example(-> direct machine-to-machine interaction with a CSW); <br>
introducing QGIS Metasearch; accessing the CSW of the portal that we used for downloading metadata through the portal's user interface; show that we can find the same dataset via metasearch; (if possible: download and view the metadata; download the data and use it in QGIS). Discuss some findings: limited capabilities of QGIS Metasearch; but shows that ist works..]


## 4.4 Accessing metadata via Python from a Jupyter Notebook

[introduction: what are we trying to showcase in this practical example; -> low level client-server interaction; how to form requests (e.g.:<br>
- searching for the dataset on protected sites; display the dataset; <br>
- all metadata that has been updated since ##.##.#### ; using a paging mechanism; show a list of metadatasets with ids, title and last_update timestamp); <br>


# 5.	Summary and Notes on Related Topics

[acknowledge the user's engagement; summarize the activties; provide an overview on other approaches and technologies that are used for organizing metadata in SDIs, particularly a) RDF/DCAT (without going into the very details) b) enabling search engines to gather data on existing respources]


[Clean Up: provide information on how to de-install the software and the data; ..]



***[Open issues:***
* ***how can we make sure that the on-line catalogs we're using will be up-and-running; we dont want to run into dead links; what does it take to set up our own metadata server - e.g. via GeoNetwork, PyCSW or GeoServer? Can we find and re-use a small existing metadata set?***
* ***Format of the presentations: text+screenshots or video]***
* ***how to support active Learning: which tasks could be given? -> these could be defined in the Python notebook***
