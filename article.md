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

## Publication geodatabase

To meet security requirements, geodatabases were stood up with both 
read/write feature access and read-only access. For read-only data, a 
custom Python script utilizing the arcpy module extracts data nightly 
from the production enterprise geodatabase, replicates it to a file 
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








# References Cited

St. Johns County Utility Department, 2015. SJCUD Integrated 
Water Resources Plan Technical Report. 
http://www.sjcfl.us/Utilities/media/IWRP/201511SJCIWRPFinal.pdf

Tibbitts, T., 2016. Technology Transforms St. Johns County Water 
Utilities, Esri News for Water and Wastewater, Summer 2016. 
http://www.esri.com/library/newsletters/water/summer-2016.pdf