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

The spatial data analysis plays a really important role for windfarm planning, to locate viable areas for new planning zones. The datasets must be up-to-date to get the most accurate data. To meet these criteria, you need to explore and find the data for example for the topic protected sites. Now you’re searching for datasets on the web for the protected sites in lower saxony. But which one fits best for you?    
For such purposes SDIs have Catalog Services which are filled with Metadata describing their available datasets. You can access these Catalogue Services via geoportals, like geodatenkatalog.de, and search there for your wanted data. To find your data it’s necessary that the available datasets are described with quality metadata. By filtering through the metadata you can browse the geoportal to get the wanted dataset. To accurately describe data with metadata there are standards that have been developed like the ISO metadata standards.   
After browsing through the geoportals and finding your wanted datasets you can then download it and load it into a QGIS project to visualise and analyse it. Now let's dive deeper into Metadata and Catalogue Services.

# 3. Background

Before we can dive into the excercises we must clarify some terms and explain a bit about the background of metadata. Note that in a 30 minutes tutorial we can't go into every detail and must limit ourselves to specific approaches because the topic Accessing Metadata. Therefore, we concentrate on using ISO Metadata and OGC Catalog Services to find data on Protected Sites specifically in Germany. There are several more approaches, on which we cannot elaborate furhter in the following sections.
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/BackgroundGraphic.png" width="1000" alt="graphic background"> 

## 3.1 The role of Metadata in SDIs

Metadata plays a critical role in Spatial Data Infrastructures (SDIs), which are complex distributed systems designed to facilitate the discovery, access, and use of spatial data.        
<img alt="SDI Grafik">        
Metadata provides essential information about spatial data resources, including their content, quality, and spatial extent, enabling users to find and evaluate data that meets their specific needs. It's like a detailed map that helps users navigate through the vast landscape of spatial data, ensuring they can locate and access the right information for their specific needs with confidence and ease. It forms the basis of an SDI architecture.      
In this context you maybe already heart of the Publish-Find-Bind paradigm in the lecture, where metadata is also crucial component.        

<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/Publish-Find-Bind.png" width="1000">       

This paradigm consists of three components:     
1. The service provider created a new dataset or service and publishes metadata about it to a catalogue service (the service broker), 
2. then consumers can find the service by searching through the catalogue. Here it's important to know that different search engines and catalogues may have different capabilities and search algorithms. That can impact the effectiveness and efficiency of data discovery. So therefore, it is important to consider the characteristics and capabilities of search engines and catalogues, when working with them. Later on in the practical excercises we will look more into that.     
3. After finding the wanted dataset the consumer than can bind the service based on the infromation from the service description     

Overall, metadata is a critical element of SDI architecture, enabling efficient and effective data discovery, sharing, and use across distributed systems.

## 3.2 ISO metadata standards and how are they used in the context of INSPIRE

So in order to ensure effective sharing and also utilization of spatial data it's crucial to standardise data models for metadata. Therefor, there were many stadards created like the Dublin Core, the ISO 19115 or DCAT.       
For our purpose today we will take a look at the ISO metadata standards. The International Organization for Standardization (ISO) has developed a series of metadata standards, including ISO 19115, which defines a conceptual data model for describing spatial data and associated metadata. This model provides a standardised framework for describing the content, quality, and spatial extent of spatial data, as well as information on ownership, access, and usage restrictions.     
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/OverviewISOMetadata.png" width="1000" title="Jean Brodeur et al (2019): Geographic Information Metadata—An Outlook from the International Standardization Perspective. International Journal of Geo-Information." src="https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=18&ved=2ahUKEwib0Yrtk6zmAhXkQ0EAHYbrBjYQFjARegQIAxAC&url=https%3A%2F%2Fwww.mdpi.com%2F2220-9964%2F8%2F6%2F280%2Fpdf&usg=AOvVaw3waCjPazkz9jy-2AKFLy8a">      
To facilitate the implementation of ISO metadata standards, ISO has also developed encoding standards, such as ISO 19139, which provide a standardised syntax and structure for encoding metadata in different formats.   

The ISO standards playing an important role in Europe because of INSPIRE. The European Union's INSPIRE Directive mandates the use of ISO metadata standards in the context of spatial data infrastructure development, implementation, and maintenance. INSPIRE requires Member States to establish national metadata catalogues that conform to ISO metadata standards and to provide interoperable access to spatial data resources. By standardising metadata, INSPIRE aims to promote the sharing and reuse of spatial data across Europe, thereby facilitating cross-border and cross-sector data interoperability. This makes the INSPIRE Catalogue Service and their GeoPortal a large gathering of all the catalogues of the member states.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/SDICatalogues.png" width="1000">     

In summary, ISO metadata standards play a crucial role in standardising the conceptual data model and encoding standards for metadata, facilitating data interoperability and data sharing. The INSPIRE Directive ensures that these standards are used, making it easier to share and use spatial data across Europe.      

## 3.3 OGC catalog services (CSW)

If you want to know how to access metadata catalogues the Open Geospatial Consortium (OGC) Catalog Services (CSW) comes in. It's a standard that provides a standardised interface for accessing metadata catalogues in SDIs.      
The OGC is an organization that creates and maintains standards for geospatial technologies. They want to make it easier for different systems and organizations to share and use geospatial data. The CSW standard defines a set of operations for working with metadata catalogues. These operations include searching for metadata, retrieving metadata records, and managing them.      
The CSW standard enables users to search for metadata using keywords, geographic extent, or other search criteria, and to retrieve metadata records in different formats, such as XML or JSON. The CSW standard has been implemented in a range of tools and instances, such as QGIS MetaSearch or ESRI Geoportal Server. These tools provide software solutions for managing and accessing metadata catalogues. But we'll take a closer look at how some of them work in Chapter 4.     

Overall, the OGC CSW standard plays a critical role in enabling efficient and effective access to metadata catalogues in spatial data infrastructures, promoting data interoperability and facilitating the sharing and use of spatial data.   

# 4.	Practical examples for accessing and using ISO metadata

Now you're getting some practical examples for accessing Catalogue Services through different approaches.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GrafikEnvironment.png" width="1000">     
But before you can start with them, you need to install Docker to work with Jupyter Notebooks and QGIS if you don't have it already.    

## 4.1 Downloading and installing the software for the hands-on exercises
### 4.1.1 QGIS  
If you already have QGIS 2.0 or higher installed you can skip this part and go directly to the next part, because the plugin MetaSearch, which you're using later, is included by default.  
For downloading QGIS please follow the next steps:
1. Go to the QGIS Website https://www.qgis.org/en/site/forusers/download.html  
2. Choose your operating system from the options that are listed  
3. Than download QGIS (this step may take some time, in this time we can already continue with the next part(s) and come back later for the last to steps)  
4. After downloading run the installer and follow the prompts to install QGIS on your computer  
  
### 4.1.2 Docker  
The second software environment that we need is Docker. Therefore please follow the next steps.    
1. Install Docker: Go to the official web site https://docs.docker.com/get-docker/ and follow the guidance which is provided there to install docker on your computer (8GB RAM recommended).  
2. Download this Repository and unzip it in your wanted working directory   
3. Make sure Docker is up and running  
4. open a terminal and guide to your working directory  
5. use "docker-compose up" to start up the docker containers  
6. After building and the running is completed your output should look similar to that:  
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/DockerJupyterAccess.png" width="1000">       

Now go to your browser and access the URL from your command output that starts with http://127.0.0.1:8888/?token=.  
You will see the UI of the Jupyter Notebook server that is running and can access the notebook later there.     


## 4.2 Accessing metadata via geoportals  
But before we look into accessing metadata via notebooks, let’s start with accessing metadata with the most common approach. We will look at how to access metadata via geoportals. Specifically, we will take up the use case of searching for and finding data on protected sites using a geoportal. Geoportals are online platforms that provide access to spatial data and related services. They typically offer users a variety of search and discovery tools to help them find the data they need.    
To begin, we will use a geoportal to search for data on protected sites in Lower Saxony. For our purposes, we will use the "Geodatenkatalog", which is the metadatainformationsystem from the "Geodateninfrastruktur Deutschland" (GDI-DE). After navigating to the portal's homepage (https://gdk.gdi-de.org/gdi-de/srv/ger/catalog.search#/home), we have several opportunities to find datasets related to protected sites. We can first start with filtering for one of the topics. Our wanted dataset for protected sites will probably be in the topic "Umwelt"       
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIStart.png" width="1000">   
Now we have over 5000 datasets but that's to many so we need to filter more. For example we can use the map on the right side by zooming into our wanted area and than drawing a a rectangle with the drawing tool. We can also use the Filter bar on the left site or searchbar to filter for specific keywords.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIUmwelt.png" width="1000">    
So our wanted region Lorup is between Papenburg and Cloppenburg in the district of Emsland. Let's try filtering them with the map first.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIKarte.png" width="1000">    
There are still to much datasets. You can try to find your wanted dataset by using the other filters too.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDIFilter.png" width="1000">    
With the filter "Naturschutzgebiete" in the search bar I now can have a look at the results and analyse them.     
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDINSGTitel.png" width="1000">    
The dataset "Naturschutzgebiete (NSG)", seems to fit quite good for our purpose. There are several positive aspects about searching metadata through geoportals. Once we find a dataset of interest, we can click on its title to view its metadata if you scroll down a bit. The HTML user interface of the geoportal provides a user-friendly layout of the metadata, allowing us to easily understand the dataset's attributes, such as its name, date of creation, and format.   
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDINSGMetadaten.png" width="1000">    
Now you know how to search through a geoportal for metadata. Can you find the dataset with other filters too?   

At the bottom we can additionally view the metadata set in plain XML ("Metadaten herunterladen"), which is useful for machine-to-machine communication. This opens up the large .xml file with all the stored metadata for the dataset.
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/GDINSGMetadatenXML.png" width="1000">      
While XML can be difficult for humans to read, it is still a valuable tool for encoding data. We can learn how to read the content of the XML file, including the meaning of attributes, by referring to name spaces and sources of documentation. We should keep in mind that XML is mainly intended for machine-to-machine communication, such as with QGIS, Python, or other catalogues.  
Geoportals often rely on Catalog Services, which are dedicated meta-database queries that support the federation of catalogues. Catalog Services allow users to access metadata stored in different catalogues, making it easier to find the data they need. In the context of a geoportal, Catalog Services play a critical role in providing access to spatial data and related services.  
After accessing and going through the metadata, we can download the dataset, if it looks suitable. Now the dataset could be loaded into a QGIS project for visualisation and analysis. Through our findings, we can see that today's portals have just basic metadata retrieval functionality, and the capabilities of the existing search engines go far beyond. Nonetheless, accessing metadata via geoportals is an essential first step in finding the data needed for spatial analysis and decision-making.  
But you could access the metadata from catalogue services also through other approaches. Another one would be via python, to make the xml metadata more readable.  

## 4.3 Accessing metadata via Python from a Jupyter Notebook
Now you can go back to the Jupyter Notebook server, that you started earlier, in your browser again. Start the notebook Accessing_Metadata_with-jupyter.ipynb and work yourself through the notebook. It will show you another approach to accessing metadata. Therefore you will work with the python package OWSLib. It is developed for client programming with OGC web services like CSW, WMS or WFS.  


When you have finished this exercise you can shut down and clean up your working environment.    
Therefore you need to type "docker-compose down" in your terminal in which you build the docker image to shut down the docker container.   
If you want to delete the image aswell type "docker image rm oer_jupyter".   

## 4.4 Accessing metadata via QGIS MetaSearch
The last example approach for accessing metadata through catalogue services, is through QGIS MetaSearch. Now you're downlaod should be complete and you can start with the last steps:
* run the installer and follow the prompts to install QGIS on your computer
  
Now you're ready to go. Open QGIS and start a new project.    
In the menu bar there is one feature called "Web" click on that and navigate to MetaSearch.   
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISMenuBar.png" width="1000">      
It should open a new window with the MetaSearch tool. you can navigate to "Dienste" and create a new connection if you click on the button "Neu..."
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISMetaSearchNew.png" width="1000">     
There you can type a name for your new connection and the URL of the catalogue service and click "Ok". We want to use the "geodatenkatalog" again so the URL would be https://gdk.gdi-de.org/gdi-de/srv/ger/csw.    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISMSNewConnection.png" width="1000">     
Now we can test the connection when we click "Dinestinfo".     
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKDienstinfo.png" width="1000">    
If you get the Service Metadata too, you're connected to the geodatenkatalog and are ready to start with searching for datasets in "Suche".    
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKSuche.png" width="1000">    
In the search section you have two options to filter in the datasets. You can search for for keywords and also can add a BBox as a filter. Let's start filtering through keywords. You can also type in more than one keyword. Can you find the dataset which we found in the last excerciese?
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKNaturschutzgebieteNS.png" width="1000">    
Have you found the dataset? Now you can click on it and a new window should open in which you can see the metadata about the dataset.   
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKDataset.png" width="1000">     
You also have the option to view the XML file about the metadata in your browser again. There you can see better what the links on the bottom can do. There is also one link to downlaod the dataset you want.      
<img src="https://github.com/oer4sdi/OER-MetadataAccessVia-OGC-CSW/blob/main/img/QGISGKDatasetXML.png" width="1000">    

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
On this RDF-Schemas you can create vocabularies like the Data Catalog Vocabulary (DCAT) from W3C. It's designed to facilitate interoperability between data catalogues published on the Web. Therefor, the DCAT re-uses terms from existing voabularies such as Dublin Core, which is another standard similar to the ISO 19115.     
The European Commission developed a DCAT profile the DCAT-AP, which is a application profile for data portals in europe. To close the gap to the ISO 19115 the European Commission also have developed the GeoDCAT-AP, which is a geospatial extension to theDCAT-AP. the intention behind that is to support the data exchang between INSPIRE metadata catalogues in Europe. 


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
