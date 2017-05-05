# Equipping workers and empowering citizens with the Esri platform at St. Johns County Utilities

Chad Cooper, Solutions Engineer, Geographic Information Services, Inc. (GISinc)

The power of GIS lies within its ability to be used by anyone for 
virtually anything - its ability to truly _empower_ users at all 
levels. The ArcGIS Platform excels in this area, providing the 
software, tools, and templates to allow organizations to 
produce applications that empower their end users. One such 
organization is St. Johns County Water 
Utility, a provider of water, sanitary sewer and reuse water 
services to 42,000 accounts and 100,000 residents in coastal 
northeast Florida (Tibbitts, 2016). The Utilities' service area is experiencing 
new development and high growth, and as a result, in 2013 the St. Johns 
County Utility Department (SJCUD) initiated the 
development of an Integrated Water Resources Plan (IWRP) to 
implement water resources solutions through 2040. The IWRP 
indicates that by 2040, the SJCUD customer base will grow by 
88,000 people under medium-growth scenarios (St. Johns County 
Utility Department, 2015). Current growth combined with this 
anticipated future growth will continue to bring challenges 
of expanded capacity, replacing infrastructure, and meeting new 
regulations for water reuse and availability requirements 
(Tibbitts, 2016). For years the Utility has embraced the capabilities of 
its GIS, but in order to meet the needs of such high growth 
and expansion, they realized a variety of solutions would be needed 
to be put in place to empower both their workforce and its
customers. These solutions begin at the data level and expand 
out to web and mobile applications for data entry and analysis, service outages, 
water quality, service availability, and capital funds expenditures.

## Data

### Publication Geodatabases

Quality data is the lifeblood of any great application. To meet security 
requirements, geodatabases were stood up with both read/write 
feature access and read-only access. Read/write feature service data is housed 
in an enterprise geodatabase separate from main production. For read-only data, a 
custom Python script utilizing the arcpy module extracts data nightly 
from the main Utility production enterprise geodatabase. To provide data to power applications for both in-house and external customer use, the script replicates it to a publication 
file geodatabase on the application server, and rebuilds the water distribution 
geometric network. 

### Geocoder

Keeping up with new and expanding utility infrastructure in a fast-growing area is 
difficult, _locating_ a particular piece of infrastructure can sometimes be just 
as hard. With so many 
newcomers to the area, residential street construction continues 
to rise. This results in the need for a custom in-house geolocator/geocoding 
service built on the latest and greatest street data based on local 
knowledge and sources. Geolocators for address points and streets are 
frequently updated and combined into a composite locator which is then 
published to ArcGIS Server and consumed in a multitude of web applications; 
ensuring that staff and end users can find even the newest of addresses 
within the service area.

## Applications

### Field

Water availability and quality are paramount for the Utility. To 
aid Utility staff with these directives, the Utility Isolation Trace tool 
from Esri (http://solutions.arcgis.com/utilities/water/help/web-isolation-trace/) 
was implemented within two Web AppBuilder (WAB) Developer Edition applications - 
one for field crews to run isolation traces during water main breaks and 
another to be used by managers for further analyzing, maintaining, and 
disseminating isolation trace results as outage information to the public.

The field application, referred to internally as "Water Isolation Trace", 
consists of a WAB Developer Edition application with the Utility Isolation Trace 
widget. It is configured against the Utility's water distribution network housed in 
the publication file geodatabase and ArcGIS Server feature services housed 
in the read/write enterprise geodatabase (Figure 1). Repair crews in the field 
access Water Isolation Trace over the internet from their laptops and tablets, 
allowing them to conduct isolation traces while onsite assessing current 
conditions, such as a main break. Isolation trace results can be saved to the 
enterprise geodatabase, saving significant amounts of time by reducing the 
necessity of coordinating with staff back at the office. Other applications, 
such as Advisory Manager, can then consume the isolation trace data and results.

Powering applications such as these requires accurate and trustworthy 
data. To help insure data quality, the Utility created a Collector application 
that is a hybrid of the Map Notes and Map Change Request Collector apps. 
Named "Field Observer" (Figure 2), this app is a one-stop shop for Utility staffers to 
enter not only utility infrastructure issues from the field, but also address data concerns 
that arise as part of ground-truthing while in the field. Conditions such as a paved-over 
valve, vegetation issue, or evidence of a leak can be captured as well as sewer, 
water, and reuse map data change requests. Field Observer allows Utility 
personnel to quickly and easily identify both infrastructure and data issues by getting them logged and into the system of record where further corrective 
actions can be taken.

Field Observer has been used recently to increase the accuracy of GIS data and 
streamline communication between field crews and the GIS team. Field crews 
verified the location of valves and used Field Observer to note changes to 
valve locations. In the past, changes such as these were communicated using 
screenshots and an email for each valve. Now, the information is added to the 
map, which is instantly visible to GIS staff; resulting in a reduced volume 
of emails and an increased flow of information.

### Office

The managerial application, Advisory Manager (Figure 3), is a clone of the Water 
Isolation Trace application, with the addition of the Esri WAB Edit widget and two 
custom widgets to work with the Utility's 
existing Code Red system (https://ecnetwork.com/community-notification/). 
Code Red is used to notify customers of outages and other potential water supply 
and quality issues. The Create Code Red tool (Figure 4) takes an outage area 
polygon from an isolation trace run and intersects it with parcel polygons to 
prepare a notification area. The Extract Code Red Tool is a custom WAB widget powered 
by a slightly modified version of the Esri Extract Data script tool from the Server 
Tools Toolbox. This tool allows a user to select a Code Red polygon to export from 
Advisory Manager as a shapefile for import into the Code Red system (Figure 5). Code Red 
accepts the shapefile as an input, gathers all registered users in that 
area, and sends out notifications regarding the issue; helping the Utility to 
streamline their customer notification processes.

Advisory Manager is also used to manage the status of drinking water advisories. 
Following a recent water main break, SJCUD's Environmental Manager quickly 
created a Boil Water Notice for the impacted customers and pushed that information 
out to the public. Once the lab tests determined that the water was safe for 
consumption it was just as easy to issue a retraction; so easy in fact that the 
retraction was issued using Advisory Manager on a mobile phone from a tennis court.
This anytime/anywhere application makes the flow of information from the Utility to 
their customers smooth and virtually instantaneous. 

### Community

To notify customers of water quantity and/or quality issues, the Esri 
Drinking Water Advisory template 
(http://solutions.arcgis.com/utilities/water/help/drinking-water-advisory/) 
was deployed (https://goo.gl/q5GEDn). Boil water notices, boil water notice 
retractions, water outages, and low water pressure notices created through the 
Create Code Red tool are displayed here as Drinking Water Alerts and Advisories 
(Figure 6). The Alerts and Advisories layer is updated from within the Advisory 
Manager application.

To inform customers of services available in their area, the Esri Information 
Lookup template (http://solutions.arcgis.com/shared/help/information-lookup/) 
was implemented as the Customer Services Summary application 
(https://goo.gl/VZ7Zw9). Users can click on the map or search by address (using the custom 
in-house geocoding service) to get a list of services, contacts, and other 
information for that location (Figure 7) such as water quality reports, 
irrigation regulations, and utility rates.

Keeping their customer base up to date on future projects and expenditures 
is important to any utility. To help with this a public-facing Capital 
Improvement Projects (CIP) site (https://maps.sjcutility.us/cip/) was 
created using the Esri Story Map Tour template customized with a tabbed 
layout for viewing reuse, water, and sewer capital improvement projects by category (Figure 8). 
The Utility had powered Story Maps in the traditional methods in the past (CSV file and hosted 
feature services), but wanted to be able to drive this CIP Story Map dynamically 
from a enterprise geodatabase backed feature service. With this setup, Utility 
GIS staff can add content to the Story Map simply by adding new CIP features 
and/or changing a status in the data with no need to touch the application or 
any items in its ArcGIS Online (AGO) backend. With this application, the 
public can learn where capital investments are being made in the county and 
what the investment can do for them.

An internal-only AGO web application was also put in place to keep Utility staff 
informed of current and future CIPs. Although simply a viewer, this internal 
app shows all CIPs and provides full access to data attributes and full-resolution 
photographs (Figure 9).

After Hurricane Matthew hit the area in early October 2016, the Utility was 
able to quickly deploy applications to aid in response and recovery. A Damage 
Assessment tool was used to quickly assess damage to approximately 360 
liftstations. Teams equipped with tablets began assessments, completing the 
project within a matter of days and ahead of schedule. Liftstation conditions 
were quickly recorded, including photographs of any damage. Information 
gathered with this tool was used for documentation for insurance evaluation 
and for FEMA reimbursement. Public Water Advisories were posted to the 100,000 
customers without water. Sanitary Sewer Overflows were located, noticed to the 
public, and inspected for water quality compliance. The hurricane response 
and recovery tasks were tracked and reported using Cityworks and ArcGIS Server. 
To demonstrate the sheer volume of work completed during and after the 
hurricane, a time line application (https://goo.gl/Wa54uK) 
was built and has been used in various presentations to demonstrate the speed 
at which issues were addressed and resolved.

## Conclusion

St. Johns County Utilities is using the Esri Platform to enable their workforce and 
empower their customers. By putting the right tools, maps, and applications into 
the hands of their field workforce, they can provide 
quality data, up-to-date information, and timely and accurate 
notifications to their customers. With the help of a healthy GIS, 
the Utility will be able to keep up with rapid growth in a fast-changing 
world. In the aftermath of a natural disaster, GIS applications helped power and 
aid the recovery effort. Even though the Utility is a mature GIS shop, they 
continue discovering new ways to utilize GIS and the Esri Platform to help them 
gain efficiencies and save themselves and their customers money.

For more information, please contact Chad Cooper at chad.cooper@gisinc.com.

## Acknowledgements

The author would like to thank Tom Tibbitts, Karri Thomas, and Bryan Bommersbach at 
St. Johns County Water Utilities for partnering with GISinc and 
help with this article. Michael Parma and Chris Blinn of GISinc were 
both instrumental in workflows and applications implemented for 
the Utility by GISinc.

## References Cited

St. Johns County Utility Department, 2015. SJCUD Integrated 
Water Resources Plan Technical Report. 
http://www.sjcfl.us/Utilities/media/IWRP/201511SJCIWRPFinal.pdf

Tibbitts, T., 2016. Technology Transforms St. Johns County Water 
Utilities, Esri News for Water and Wastewater, Summer 2016. 
http://www.esri.com/library/newsletters/water/summer-2016.pdf

## About the author

Chad Cooper has worked in the geospatial industry, over the last 15 years, in positions of technician, analyst, 
and developer, as it pertains to state and local governments, oil and 
gas, and academia. For the last three years, Chad has worked as a Solutions 
Engineer consulting on the State and Local 
Government team with Geographic Information Services, Inc. (GISinc, 
http://www.gisinc.com). At work, he couldn't be happier spending the 
day writing Python and helping clients such as St. Johns County Utilities get the most 
out of their data through the use of the Esri Platform. At home, he 
enjoys hanging out with his gorgeous wife of 12 years and their three 
wonderful children. They enjoy hiking, fishing, and doing nothing on a 
nice beach.
