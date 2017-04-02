The power of GIS lies in it's ability to be used by anyone for 
virtually anything - its ability to truly _empower_ users at all 
levels. The ArcGIS Platform excels in this arena, providing the 
software, tools, and templates to allow organizations to 
produce applications to empower their end users. One such 
organization is the St. Johns County, Florida Water 
Utility, a provider of water, sanitary sewer and reuse water 
services to 42,000 accounts and 100,000 residents in coastal 
northeast Florida Tibbitts, 2016). The Utilities' service area is experiencing 
new development and high growth, and as a result, in 2013 the St. Johns 
County Utility Department (SJCUD) initiated the 
development of an Integrated Water Resources Plan (IWRP) to 
implement water resources solutions through 2040. The IWRP 
indicates that by 2040, the SJCUD customer base will grow by 
88,000 people under medium-growth scenarios (St. Johns County 
Utility Department, 2015). Current growth combined with this 
anticipated future growth is and will continue to bring challenges 
of expanded capacity, replacing infrastructure, and meeting new 
regulations for water reuse and availablity requirements 
(Tibbitts, 2016). For years the Utility has embraced the capabilities of 
its GIS, but in order to meet the needs of such high growth 
and expansion, they realized a variety of solutions would needed 
to be put in place to empower both their workforce and 
customers. These solutions begin at the data level and expand 
out to web and mobile applications for data entry, service outages, 
water quality, service availability, and capital funds expenditures.

# Data

## Publication geodatabases

To meet security requirements, geodatabases were stood up with both 
read/write feature access and read-only access. Read/write data is housed 
in a enterprise geodatabase separate from main production. For read-only data, a 
custom Python script utilizing the arcpy module extracts data nightly 
from the main Utility production enterprise geodatabase, replicates it to a file 
geodatabase on the web server, and rebuilds the water distribution 
geometric network, providing data to power applications for both 
in-house and external customer use. 

## Geocoder

Keeping up with utility infrastructure in such a fast-growing area is 
difficult, _locating_ it can sometimes be just as hard. With so many 
newcomers to the area, residential street construction also continues 
to rise, resulting in the need for a custom in-house local geolocator/geocoding 
service built on the latest and greatest street data based on local 
knowledge and sources. Geolocators for address points and streets are 
updated frequently and combined into a composite locator which is then 
published to ArcGIS Server and consumed in a multitude of web applications, 
ensuring that staff and end users can find even the newest of addresses 
with the service area.

# Applications

## Internal

Water availability and water quality are paramount for the Utility. To 
aid Utility staff with these directives, the Utility Isolation Trace  
from Esri (http://solutions.arcgis.com/utilities/water/help/web-isolation-trace/) 
was implemented within two Web AppBuilder (WAB) Developer Edition applications - 
one for field crews to use in the field for running isolation traces and 
another to be used by managers for further analyzing and disseminating the 
isolation trace results.

The field application, referred to internally as "Water Isolation Trace", 
consists of a WAB Developer Edition application with the Utility Isolation Trace 
widget configured against the Utility's water distribution network housed in 
the publication file geodatabase and ArcGIS Server feature services housed 
in the read/write enterprise geodatabase. Utility field personnel access 
Water Isolation Trace over the internet from their Toughbook laptops, allowing 
them to conduct isolation traces while out in the field assessing current 
conditions. Isolation trace results can be saved to the enterprise 
geodatabase, enabling other applications to consume the data.

The managerial application, Advisory Manager, is a clone of the Water 
Isolation Trace application, with the addition of the Esri WAB Edit widget and two 
custom (todo are they really custom?) widgets to work with the Utility's 
existing Code Red system (https://ecnetwork.com/community-notification/). 
Code Red is used to notify customers of outages and other potential water supply 
and quality issues. The Create Code Red tool (Figure X) takes a outage area 
polygon from an isolation trace run, intersects it with parcel polygons to 
prepare a notification area. The Extract Code Red Tool is a WAB widget created 
from a geoprocessing script based off the TODO geoprocessing tool. This 
tool enables the Utility to export a Code Red notification area from 
Advisory Manager as a shapefile for import into the Code Red system. Code Red 
accepts the shapefile as input and gathers all registered users in that 
area and sends out notifications.

## Public

To notify customers of water quantity and/or quality issues, the Esri 
Drinking Water Advisory template 
(http://solutions.arcgis.com/utilities/water/help/drinking-water-advisory/) 
was deployed (https://goo.gl/q5GEDn). Boil water notices, boil water notice 
retractions, water outages, and low water pressure notices can be created 
and edited in Advisory Manager (is this the workflow?) in a ArcGIS Server 
feature service and then show up in Water Advisories.

To inform customers of services available in their area, the Esri Information 
Lookup template was implemented as the Customer Services Summary application 
(Figure X). Users can click on the map or search by address (using the custom 
in-house geocoding service) to get a list of services, contacts, and other 
information for that location (Figure X) such as water quality reports, 
irrigation regulations, and utility rates.


# References Cited

St. Johns County Utility Department, 2015. SJCUD Integrated 
Water Resources Plan Technical Report. 
http://www.sjcfl.us/Utilities/media/IWRP/201511SJCIWRPFinal.pdf

Tibbitts, T., 2016. Technology Transforms St. Johns County Water 
Utilities, Esri News for Water and Wastewater, Summer 2016. 
http://www.esri.com/library/newsletters/water/summer-2016.pdf
