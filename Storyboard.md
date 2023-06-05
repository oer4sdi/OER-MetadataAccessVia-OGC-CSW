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
2. Background  
  2.1 The role of Metadata in SDIs  
  2.2 ISO metadata standards and how are they used in the context of INSPIRE  
  2.3 OGC catalog services (CSW)  
3. Use case: Finding data on protected sites in the context of windfarm planning   
4. Practical examples for accessing and using ISO metadata   
  4.1 Accessing metadata via geoportals  
  4.2 Accessing metadata via QGIS Metasearch  
    4.2.1 Installation Guide
    4.2.2 QGIS MetaSearch
  4.3 Accessing metadata via Python from a Jupyter Notebook  
    4.3.1 Installation Guide
    4.3.2 Jupyter Notebook
5. Summary and Notes on Related Topics  

The tutorial takes about 30 Minutes for reading and viewing the provided materials, downloading the software and for conducting the hands-on exercises and tasks.

This OER is primarily designed to be used by students in Geoinformatics, Geomatics and similar study programs. It is also useful for students of other study programs and for practitioners who want to enhance their understanding of SDI concepts and technologies. Some basic knowledge of web technologies such as HTTP and Web Services is required. However, you will be able to follow and find links to further resources if needed. Your computer should have #.# GB of usable RAM and #.# MB of usable disk space to download and use the software for this tutorial.
This Tutorial has been developed at the Institute for Geoinformatics, University of Münster. Authors are Tobias Krumrein and Albert Remke.

You are free to use, alter and reproduce the tutorial (H5P content, Storyboard) under the terms of the CC-BY-SA 4.0 license. Any code provided with the tutorial can be used under the terms of the MIT license. Please see the full license terms (tbd).

The OER4SDI project has been recommended by the Digital University NRW and is funded by the Ministry of Culture and Science NRW.       


# 2. Background

Before we can dive into the excercises we must clarify some terms and explain a bit about the background of metadata. Note that in a 30 minutes tutorial we can't go into every detail and must limit ourselves to specific approaches because the topic Accessing Metadata. Therefore, we concentrate on using ISO Metadata and OGC Catalog Services to find data on Protected Sites specifically in Germany. There are several more approaches, on which we cannot elaborate furhter in the following sections.
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/BackgroundGraphic.png" width="1000" alt="graphic background">      
*In Work: Fig.1: Background Graphic*     

## 2.1 The role of Metadata in SDIs

Metadata plays a critical role in Spatial Data Infrastructures (SDIs), which are complex distributed systems designed to facilitate the discovery, access, and use of spatial data.        
<img alt="SDI Grafik">    
*In Work: Fig.2: Graphic aout Spatial Data Infrastructures*      
Metadata provides essential information about spatial data resources, including their content, quality, and spatial extent, enabling users to find and evaluate data that meets their specific needs. It's like a detailed map that helps users navigate through the vast landscape of spatial data, ensuring they can locate and access the right information for their specific needs with confidence and ease. It forms the basis of an SDI architecture.       
In this context you maybe already heart of the Publish-Find-Bind paradigm in the lecture, where metadata is also crucial component.        

<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/Publish-Find-Bind.png" width="1000">       
*Fig.3: Publish-Find-Bind Paradigm*      

This paradigm consists of three components:     
1. The service provider created a new dataset or service and publishes metadata about it to a catalogue service (the service broker), 
2. then consumers can find the service by searching through the catalogue. Here it's important to know that different search engines and catalogues may have different capabilities and search algorithms. That can impact the effectiveness and efficiency of data discovery. So therefore, it is important to consider the characteristics and capabilities of search engines and catalogues, when working with them. Later on in the practical excercises we will look more into that.     
3. After finding the wanted dataset the consumer than can bind the service based on the infromation from the service description     

Overall, metadata is a critical element of SDI architecture, enabling efficient and effective data discovery, sharing, and use across distributed systems.

## 2.2 ISO metadata standards and how are they used in the context of INSPIRE

So in order to ensure effective sharing and also utilization of spatial data it's crucial to standardise data models for metadata. Therefor, there were many standards created like the Dublin Core, the ISO 19115 or DCAT for metadata.       
For our purpose today we will take a look at the ISO metadata standards. The International Organization for Standardization (ISO) has developed a series of metadata standards, including ISO 19115, which defines a conceptual data model for describing spatial data and associated metadata. This model provides a standardised framework for describing the content, quality, and spatial extent of spatial data, as well as information on ownership, access, and usage restrictions.     
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/OverviewISOMetadata.png" width="1000" title="Jean Brodeur et al (2019): Geographic Information Metadata—An Outlook from the International Standardization Perspective. International Journal of Geo-Information." src="https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=18&ved=2ahUKEwib0Yrtk6zmAhXkQ0EAHYbrBjYQFjARegQIAxAC&url=https%3A%2F%2Fwww.mdpi.com%2F2220-9964%2F8%2F6%2F280%2Fpdf&usg=AOvVaw3waCjPazkz9jy-2AKFLy8a">     
*In Work: Fig.4: Overview about ISO 19115 metadata standard*          
To facilitate the implementation of ISO metadata standards, ISO has also developed encoding standards, such as ISO 19139, which provide a standardised syntax and structure for encoding metadata in different formats.   
The ISO standards playing an important role in Europe because of INSPIRE. The European Union's INSPIRE Directive mandates the use of ISO metadata standards in the context of spatial data infrastructure development, implementation, and maintenance. INSPIRE requires Member States to establish national metadata catalogues that conform to ISO metadata standards and to provide interoperable access to spatial data resources. By standardising metadata, INSPIRE aims to promote the sharing and reuse of spatial data across Europe, thereby facilitating cross-border and cross-sector data interoperability. This makes the INSPIRE Catalogue Service and their GeoPortal a large gathering of all the catalogues of the member states.      

In summary, ISO metadata standards play a crucial role in standardising the conceptual data model and encoding standards for metadata, facilitating data interoperability and data sharing. The INSPIRE Directive ensures that these standards are used, making it easier to share and use spatial data across Europe.      

## 2.3 OGC catalog services (CSW)

If you want to know how to access metadata catalogues the Open Geospatial Consortium (OGC) Catalog Services (CSW) comes in. It's a standard that provides a standardised interface for accessing metadata catalogues in SDIs.      
The OGC is an organization that creates and maintains standards for geospatial technologies. They want to make it easier for different systems and organizations to share and use geospatial data. The CSW standard defines a set of operations for working with metadata catalogues. These operations include searching for metadata, retrieving metadata records, and managing them. Different catalogues can also interact with each other. As an example you can see in Fig.5 the structure of catalogues in Germany. To make this possible standards need to be defined so datasets from the "Geodatenkatalog" can also be found in the INSPIRE catalogue.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/SDICatalogues.png" width="1000">     
*Fig.5: Structure INSPIRE Catalogues*      
The CSW standard enables users to search for metadata using keywords, geographic extent, or other search criteria, and to retrieve metadata records in different formats, such as XML or JSON. But there is a difference between searching in search engines such as Google, Bing or Yahoo and catalogue services. Search engines are designed to crawl and index web pages, enabling users to search for information across the internet. On the other hand, catalogues, specifically metadata catalogues, are dedicated systems for managing and providing access to metadata. These catalogues services are designed to collect, organize, store, and retrieve metadata records which in turn describe various types of resources, such as datasets, services or other digital assets.           
The CSW standard has been implemented in a range of tools and instances, such as QGIS MetaSearch or ESRI Geoportal Server. These tools provide software solutions for managing and accessing metadata catalogues. But we'll take a closer look at how some of them work in Chapter 4.    

Overall, the OGC CSW standard plays a critical role in enabling efficient and effective access to metadata catalogues in spatial data infrastructures, promoting data interoperability and facilitating the sharing and use of spatial data.       

# 3. Use case: Finding data on protected sites in the context of windfarm planning  

Before we start with the practical excercises here's a real worl use case scenario to get a better understanding.      
Let's say a local authority in Lower Saxony has hired you to cooperate with a private investor to identify several potential sites in the state for enlarging and repowering existing wind farms with high-efficiency wind turbines. The selected site must meet several characteristics:    

* Located in the state of Lower Saxony in the distric Emsland by Lorup 
* Within 4 km of existing wind farms containing turbines  
* Within at least 800 m of neighbouring houses   
* Does not intersect with any protected site     
     
<img src="" width="1000">    
*In Work Fig.6: Use case scenario*     
      
The spatial data analysis plays a really important role for windfarm planning, to locate viable areas for new planning zones. The datasets should be up-to-date to get the most accurate data. To meet these criteria, you need to explore and find the data for example for the topic protected sites. Now you’re searching for datasets on the web for the protected sites by Lorup. But which one fits best for you?      
For such purposes SDIs have Catalog Services which are filled with Metadata describing their available datasets. You can access these Catalogue Services via geoportals, like geodatenkatalog.de, and search there for your wanted data. To find your data it’s necessary that the available datasets are described with quality metadata. By filtering through the metadata you can browse the geoportal to get the wanted dataset. To accurately describe data with metadata there are standards that have been developed like the ISO metadata standards.   
After browsing through the geoportals and finding your wanted datasets you can then download it and load it into a QGIS project to visualise and analyse it. Now let's dive deeper into Metadata and Catalogue Services.       

# 4.	Practical examples for accessing and using ISO metadata

After all the reading we can now put our new knowledge into action. Therefor you're getting some practical examples for accessing Catalogue Services through different approaches. As an example catalouge service we will use the "Geodatenkatalog" and search in it for a dataset for our use case. For the searching in the catalogue service we will use three different representation of the catalogue. First we will use the geoportal in the browser of the "geodatenkatalog". The second one wil be the plugin MetaSearch in QGIS which was specifically developed for catalogues. In the final excercise we will access the catalogue through the python library OWSLib in an jupyter notebook.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GrafikEnvironment.png" width="1000">       
*Fig.7: Envirnoment used for the upcoming excercises*     

For the excercises you will need docker for jupyter notebooks and QGIS. If you haven't downloaded them already no worries there will be an installatin guide for everything before every excercise.            


## 4.1 Accessing metadata via geoportals  
But before we look into accessing metadata via notebooks, let’s start with accessing metadata with the most common approach. We will look at how to access metadata via geoportals. Specifically, we will take up the use case of searching for and finding data on protected sites using a geoportal. Geoportals are online platforms that provide access to spatial data and related services. They typically offer users a variety of search and discovery tools to help them find the data they need.    
To begin, we will use a geoportal to search for data on protected sites in Lower Saxony. For our purposes, we will use the "Geodatenkatalog", which is the metadatainformationsystem from the "Geodateninfrastruktur Deutschland" (GDI-DE). After navigating to the portal's homepage (https://gdk.gdi-de.org/gdi-de/srv/ger/catalog.search#/home), we have several opportunities to find datasets related to protected sites. We can first start with filtering for one of the topics. Our wanted dataset for protected sites will probably be in the topic "Umwelt" which means "envirnoment"       
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIStart.png" width="1000">   
*Fig.8: Geodatenkatalog home*     

Now we have over 5000 datasets but that's to many so we need to filter more. For example we can use the map on the right side by zooming into our wanted area and after that draw a rectangle with the drawing tool. We can also use the Filter bar on the left site or searchbar to filter for specific keywords.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIUmwelt.png" width="1000">    
*Fig.9: Geodatenkatalog Umwelt*     

So our wanted region Lorup is between Papenburg and Cloppenburg in the district of Emsland. Let's try filtering them with the map first.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIKarte.png" width="1000">    
*Fig.10: Geodatenkatalog mapping tool*     

There are still to much datasets. You can try to find your wanted dataset by using the other filters too.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIFilter.png" width="1000">    
*Fig.11: Geodatenkatalog filters*     

With the filter "Naturschutzgebiete" in the search bar I now can have a look at the results and analyse them.     
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDINSGTitel.png" width="1000">    
*Fig.12: Geodatenkatalog with filter "Naturschutzgebiete"*     

The dataset "Naturschutzgebiete (NSG)", seems to fit quite good for our purpose. There are several positive aspects about searching metadata through geoportals. Once we find a dataset of interest, we can click on its title to view its metadata if you scroll down a bit. The HTML user interface of the geoportal provides a user-friendly layout of the metadata, allowing us to easily understand the dataset's attributes, such as its name, date of creation, and format.   
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDINSGMetadaten.png" width="1000">    
*Fig.13: Geodatenkatalog HTML interface metadata*     

Now you know how to search through a geoportal for metadata. Can you find the dataset with other filters too?   

At the bottom we can additionally view the metadata set in plain XML ("Metadaten herunterladen"), which is useful for machine-to-machine communication. This opens up the large .xml file with all the stored metadata for the dataset.
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDINSGMetadatenXML.png" width="1000">      

```xml
<gmd:MD_Metadata xmlns:gmd="http://www.isotc211.org/2005/gmd" xmlns:gco="http://www.isotc211.org/2005/gco" xmlns:srv="http://www.isotc211.org/2005/srv" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:gfm="http://www.isotc211.org/2005/gfm" xmlns:base="http://www.disy.de/preludio2/base" xsi:schemaLocation="http://www.isotc211.org/2005/gmd http://schemas.opengis.net/iso/19139/20060504/gmd/gmd.xsd" uuid="EE85FE8F-BD05-4A6D-813B-6ABC4514B18B">
  <link type="text/css" rel="stylesheet" id="dark-mode-custom-link"/>
  <link type="text/css" rel="stylesheet" id="dark-mode-general-link"/>
  <style lang="en" type="text/css" id="dark-mode-custom-style"/>
  <style lang="en" type="text/css" id="dark-mode-native-style"/>
  <style lang="en" type="text/css" id="dark-mode-native-sheet"/>
  ...
  <gmd:identificationInfo>
    <gmd:MD_DataIdentification uuid="093121e3-f872-4aa2-b9db-40ee82cc1a18">
      <gmd:citation>
        <gmd:CI_Citation uuid="60e4561f-7aea-49f3-93cb-1c66ba52f406">
          <gmd:title>
            <gco:CharacterString>Naturschutzgebiete (NSG)</gco:CharacterString>
          </gmd:title>
          <gmd:alternateTitle>
            <gco:CharacterString>Naturschutzgebiete_DTK25</gco:CharacterString>
          </gmd:alternateTitle>
          <gmd:date>
            ...
          </gmd:date>
          <gmd:date>
            ...
          </gmd:date>
          <gmd:identifier>
            <gmd:MD_Identifier uuid="cb1b4ff1-bf68-4e5a-aa84-73043f65501f">
              <gmd:code>
                <gco:CharacterString>https://registry.gdi-de.org/id/de.ni.mu.nlwkn.csw/EE85FE8F-BD05-4A6D-813B-6ABC4514B18B</gco:CharacterString>
              </gmd:code>
            </gmd:MD_Identifier>
          </gmd:identifier>
          <gmd:citedResponsibleParty>
            ...
          </gmd:citedResponsibleParty>
          <gmd:presentationForm>
            ...
          </gmd:presentationForm>
        </gmd:CI_Citation>
      </gmd:citation>
      <gmd:abstract>
        <gco:CharacterString>Digitale landesweite Übersichtskarte: Geometrien aller niedersächsischen Naturschutzgebiete (NSG) mit Angaben u. a. zu Name, Kennzeichen, VO-Datum und Datum des Inkrafttretens.Naturschutzgebiete werden gemäß § 16 NAGBNatSchG durch Verordnung ausgewiesen.Diese Daten sind auch im INSPIRE Datenmodell „Annex 1: Schutzgebiete“ erhältlich. Die Bereitstellung erfolgt per Darstellungs- und Downloaddienst, deren URLs in den Transferoptionen angegeben sind.</gco:CharacterString>
      </gmd:abstract>
````
*In work: Fig.14: Geodatenkatalog raw XML metadata*     

While XML can be difficult for humans to read, it is still a valuable tool for encoding data. We can learn how to read the content of the XML file, including the meaning of attributes, by referring to name spaces and sources of documentation. We should keep in mind that XML is mainly intended for machine-to-machine communication, such as with QGIS, Python, or other catalogues.  
Geoportals often rely on Catalog Services, which are dedicated meta-database queries that support the federation of catalogues. Catalog Services allow users to access metadata stored in different catalogues, making it easier to find the data they need. In the context of a geoportal, Catalog Services play a critical role in providing access to spatial data and related services.  
After accessing and going through the metadata, we can download the dataset, if it looks suitable. Now the dataset could be loaded into a QGIS project for visualisation and analysis. Through our findings, we can see that today's portals have just basic metadata retrieval functionality, and the capabilities of the existing search engines go far beyond. Nonetheless, accessing metadata via geoportals is an essential first step in finding the data needed for spatial analysis and decision-making.  
But you could access the metadata from catalogue services also through other approaches. Another one would be via python, to make the xml metadata more readable.  


## 4.2 Accessing metadata via QGIS MetaSearch

### 4.2.1 Installation Guide
If you already have QGIS 2.0 or higher installed you can skip this part and go directly to 4.2.2, because the plugin MetaSearch, which you're using later, is included by default.  
For downloading QGIS please follow the next steps:
1. Go to the QGIS Website https://www.qgis.org/en/site/forusers/download.html  
2. Choose your operating system from the options that are listed  
3. Than download QGIS (this step may take some time, in this time we can already continue with the next part(s) and come back later for the last to steps)  
4. After downloading run the installer and follow the prompts to install QGIS on your computer    

### 4.2.2 QGIS MetaSearch
The next example approach for accessing metadata through catalogue services, is through QGIS MetaSearch. Please open QGIS and start a new project.   

In the menu bar there is one feature called "Web" click on that and navigate to MetaSearch.   
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISMenuBar.png" width="1000">     
*Fig.15: QGIS Menubar*     

It should open a new window with the MetaSearch tool. you can navigate to "Dienste" and create a new connection if you click on the button "Neu..."
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISMetaSearchNew.png" width="1000">     
*Fig.16: QGIS MetaSearch*     

There you can type a name for your new connection and the URL of the catalogue service and click "Ok". We want to use the "geodatenkatalog" again so the URL would be https://gdk.gdi-de.org/gdi-de/srv/ger/csw.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISMSNewConnection.png" width="1000">     
*Fig.17: New MetaSearch connection*     

Now we can test the connection when we click "Dienstinfo". That corresponds to the GetCapabilites request. From the response there will be shown some selected metadata about the catalogue service.          
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKDienstinfo.png" width="1000">    
*Fig.18: MetaSearch test if new connection is active*     

If you get the Service Metadata too, you're connected to the geodatenkatalog and are ready to start with searching for datasets in "Suche". If you click on the button "Suche", the getRecords request with the arguements you give will be executed in the background of the search window. And afterwards it will be shown on the lower half in the results section ("Ergebnise").    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKSuche.png" width="1000">    
*Fig.19: Searching in MetaSearch*     

In the search section you have two options to filter in the datasets. You can search for for keywords and also can add a BBox as a filter. Let's start filtering through keywords. You can also type in more than one keyword. Can you find the dataset which we found in the last excercise?
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKNaturschutzgebieteNS.png" width="1000">    
*Fig.20: MetaSearch searching for Naturschutzgebiete (NSG)*     

Have you found the dataset? One Way to find out if it's the identical dataset is to look at the Identifier or at the abstract. Now you can click on it and a new window should open in which you can see the metadata about the dataset. There you can control if it's the right dataset.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKDataset.png" width="1000">     
*Fig.21: MetaSearch Naturschutzgebiete (NSG)*     

You also have the option to view the XML file about the metadata in your browser again. There you can see better what the links on the bottom can do. There is also one link to downlaod the dataset you want. As you can see the XML file looks a bit different than the one from the geoportal. That's because it's not the original metadata xml file from the dataset but the xml response from the request.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKDatasetXML.png" width="1000">   
*In Work: Fig.22: MetaSearch XML Naturschutzgebiete (NSG)*     



## 4.3 Accessing metadata via Python from a Jupyter Notebook

### 4.3.1 Installation Guide

The second software environment that we need is Docker. Therefore please follow the next steps.    
1. Install Docker: Go to the official web site https://docs.docker.com/get-docker/ and follow the guidance which is provided there to install docker on your computer (8GB RAM recommended).  
2. Download this Repository and unzip it in your wanted working directory   
3. Make sure Docker is up and running  
4. open a terminal and guide to your working directory  
5. use "docker-compose up" to start up the docker containers  
6. After building and the running is completed your output should look similar to that:  
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/DockerJupyterAccess.png" width="1000">       
*Fig.23: Example of a correct response in the terminal after the docker container is running*

Now go to your browser and access the URL from your command output that starts with http://127.0.0.1:8888/?token=.  
You will see the UI of the Jupyter Notebook server that is running and can access the notebook here.     

### 4.3.2 Jupyter Notebook

After the installation please start the notebook Accessing_Metadata_with-jupyter.ipynb and work yourself through the notebook. It will show you another approach to accessing metadata. Therefore you will work with the python package OWSLib. It is developed for client programming with OGC web services like CSW, WMS or WFS.  


When you have finished this exercise you can shut down and clean up your working environment.    
Therefore you need to type "docker-compose down" in your terminal in which you build the docker image to shut down the docker container.   
If you want to delete the image aswell type "docker image rm oer_jupyter".   



You have seen three different approaches to access metadata through a catalogue service but there are many more. Now you have a better understanding what catalogue services are good for and why a good metadata description is necessary to find the best suiting dataset for your specific purpose in the masses of available data. Which approach do you find best?    


# 5.	Summary and Notes on Related Topics

In this concluding section, we will summarize the activities covered in the tutorial. We will also provide an overview of other approaches and technologies used for organizing metadata in SDIs, including RDF/DCAT and enabling search engines to gather data on existing resources.       

So now you have got a good overview other the topic "Using ISO Metadata and OGC Catalog Services to find data on Protected Sites in Germany" and accessing metadata through through different approaches. As you have probably noticed they are a bit different but the main operations are the same whe searching through a catalogue. But searching a catalogue through a geoportal is probably the best option because it's easy to use and the XML metadata file is nice edited in an HTML interface for human reading. Due to that another big advantage the geoportal have, is that the links where the dataset is stored is also easy to find. That's a bit tricky by the two other approaches.         
If you have a bit programming experience and want to find a fitting dataset you could also do the searching with the python library OWSLib. They have similar useful operations, but if you then want to download the dataset it will be tricky to get to the download link.     
The same problem has the third approach through QGIS MetaSearch. There you also better look into the XML file to find the dowload link because in the MetaSearch layout the available links aren't nametagged. In addition the search options from MetasSearch are very limited. Although you can write more then one keyword in the search bar but you can only search through the whole dataset and cannot search more specifically like only the title or the description.      
Another big disadvantage of the MetaSearch and the OWSLib is the searching for the right link to get access to the catalogue service and using the right parts. There searching for the name of the service with CSW is probably the best option because you get very often the GetCapabilites request in one of the first results. From that you can use the first part of the link until the "?".      


But there are several more ways to organise metadata in SDIs and also store metadata for spatial data.     
Another standard data model for metadata to the ISO 19115 are RDF/DCAT. They work in a different way. Resource Description Framework (RDF) consists of of triples to describe resources:  < subject > < predicate > < object >      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GraphicRDF.png">    
*Fig.24: RDF Scheme*
On this RDF-Schemes you can create vocabularies like the Data Catalog Vocabulary (DCAT) from W3C. In the future there could be a change from CSW to DCAT or other RDF Schemes.       


# Wrap Up
That's it. You completed the tutorial on "Using ISO Metadata and OGC Catalog Services to find data on Protected Sites in Germany".       
You've learned about the big role that metadata have in SDIs and why standards are crucial for organising metadata in SDIs. In this context you got to know ISO and INSPIRE. You also worked with a catalogue service and accessed it over several ways and have found your wanted dataset. There you could compare the different approaches and get to know the pros and cons. In the end you also get to know some other approaches on the topic organising metadata.

Now you should be able to answer the following questions:      
* How can we use metadata for discovering datasets and services in an SDI?        
* What is the role of the ISO and INSPIRE metadata standards?       
* What is the role of OGC catalog services (CSW)?     
* How can I access OGC catalog services with QGIS and/or Python Code?     
* What other approaches are being used to support the discoverability of datasets and services?      

Thank you for your time!       

If you want to dive deeper into the topic of organising metadata in SDIs and using ISO metadata and OGC Catalogue Services to find data on protected site in Germany feel free to take a look in the created Google Doc to the topic. There are some useful links to the specific subtopics.     

# Refrences

[Jean Brodeur et al (2019): Geographic Information Metadata—An Outlook from the International Standardization Perspective. International Journal of Geo-Information](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=18&ved=2ahUKEwib0Yrtk6zmAhXkQ0EAHYbrBjYQFjARegQIAxAC&url=https%3A%2F%2Fwww.mdpi.com%2F2220-9964%2F8%2F6%2F280%2Fpdf&usg=AOvVaw3waCjPazkz9jy-2AKFLy8a)
