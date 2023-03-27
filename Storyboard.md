# OER Module: Metadata Access via OGC CSW  
## Chapter 1: About this Module  
If you're working with spatial data and were recently looking online for an specific dataset you're probably were stumbling over the term OGC CSW or something like this:  
__Screenshot__  
That looks very deterrent at first sight. But if you look a little more closely into OGC CSW, a lot of things will become more clear and you see that this huge xml text makes a lot of sense. This OER module should help you to understand how to work with OGC Catalogue Services. It will give you some background on how to access INSPIRE Metadata via OGC Catalogue Services. And once you have completed this tutorial, you will be able to answer the following questions:  
* Why use INSPIRE metadata?  
* How to read XML-Metadata?  
* What's OGC CSW? How to organise Metadata in a Catalog Service?  
* How to access INSPIRE Metadata via classic OGC CSW?  
* How to access OGC CSW in QGIS and Python?  

So let’s start with the module it is structured as follows:  
__Chapter 1:__ About this module  
__Chapter 2:__ OGC CSW  
__Chapter 3:__ Other ways to access CSW Metadata  
__Chapter 4:__ Wrap Up

## Chapter 2: OGC CSW  
Catalogue Service Web (CSW) from the Open Geospatial Consortium (OGC), is a standard for exposing catalogues of geospatial records on the Internet. These catalogues are online databases of many geospatial data, which can be filtered through Post-Requests with operations. But in these databases there is only the Metadata about the specific geodata and not the geodata itself. According to the standard the responses are the records in XML.  
Many spatial data infrastructures (SDI) have a CSW where their metadata for all their geodata is stored and can be browsed through. Therefore CSW is a powerful tool to use when you're searching for geodata on the web. Germany's GDI-DE for example has a big CSW which can be accessed via https://gdk.gdi-de.org/gdi-de/srv/ger/csw?service=CSW&version=2.0.2&request=GetCapabilities.  
Now let's take a closer look at this CSW. You can also open the link on the side in your browser but that's not needed. The parameters that a CSW request must include are:
* The service which you want to use : service=CSW,  
* The version of the CSW, which is version=2.0.2 in most of the services,  
* You also need to specify which operation you want to use  
All of them should be added with a ‘&’ into the URL. If you want to access a CSW your first request should be the GetCapabilities-request. There you can see the Metadata about the service, like the ServiceIdentification, the ServiceProvider and the very important OperationsMetadata and Filter_Capabilities. 
__Screenshot__   
At OperationsMetadata you get information about all the operations you can use within the CSW.
__Screenshot__   
If you want to search for geodata you should look for the GetRecords Operation. Now we just open a new tab and exchange request to GetRecords
https://gdk.gdi-de.org/gdi-de/srv/ger/csw?service=CSW&version=2.0.2&request=GetRecords

Something went wrong we got an exception.   
__Screenshot__   
It says that we’re missing a parameter named typeNames. Let’s look into our GetCapabilities request again and search for typeNames in GetRecords Operation.   
__Screenshot__   
We need to set a value for typeNames, let’s try the first one csw:Record. Add it to our GetRecords Request.   

* Filter by attributes on bbox and theme  
* Look at found Dataset 
  * Show INSPIRE ISO Standard
    * Discuss why so important
* Refer to geodatenkatlog.de  
  * Better readable because CSW in HTML  

## Chapter 3: Other Ways to access CSW Metadata   
* Open QGIS   
  * Use Metasearch to access CSW   
  * Filter CSW to get same dataset   
* Use jupyter notebooks   
  * Accessing CSW via request   
  * Browse through it with request   
* Pros/Cons of accessing CSW via QGIS and Python   

## Chapter 4: Wrap Up  
* summarising the different accessing methods  

