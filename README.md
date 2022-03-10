# A technical guide on tier-one urban network for emergency response
The objective of this guide is to identify the most useful road network in a specific loca-tion to get to the main services around in case of emergency. This guide could be used in slums or other areas, regardless of size. However, areas at the scale of cities or even wards requires heavier computational analysis and a more complex process of decision making that is not covered in this guide.

This guide is based in the work of the department of Urbanization and Sustainable Cities  of GRADE and the lessons learned from the project Capacity Building for Smart Data and Inclusive Cities in India. 
## General and Software Requirements
This technical guide requires use of spatial information. So it needs software to process this kind of information. It’s highly recommendable to use QGIS . Download and install the latest LTR version. The algorithms referred on this guide come from QGIS. However, they have equivalents on similar software like ARCGIS since the processing tasks are public domain. 

Depending on the data availability it might be needed a location device like a smartphone. It’s highly recommendable to use a standalone device for more accuracy. The average accuracy of a smartphone range from 3 – 50 meters, depending on the location of the area of interest and the device’s technology. A dedicated device has a location accuracy of 0.5 – 1 meters. Using this kind of device will increase the precision of the location register and reduce the post processing time.

It’s is required to have access to the area of interest. A dedicated team to recognize the fieldwork and engage the local population will provide information that otherwise cannot be acquired. This team will be responsible to gather on the field spatial information and communicate it with the team in charge of spatial analysis. 

Most of the communication should be based on thematic maps (Figure 1). These maps are based on specific data regarding open spaces, markets, roads, physical risks, community services. Reports should gather imagery, location and commentaries. Is highly recommended to compose maps with applications like My Maps . Such applications allow you to easily build thematic maps based on the gathered information on the ground. It also makes it easier to share the information via link. 

Make sure that any photograph taken on field has also location data. It reduces human error at reporting location of any event. Consider the use of a single My Maps composition to stock each field work report organized into different layers.

Interoperability between this platform and qgis is reliable. To import/export the reports data just find the ‘Export to KML/KMZ’ action and select the necessary information; a vector layer will be created. On the qgis environment, open the data. Although it will not present the same icons, color or style the data would be just the same. It will be organized by vector type; that is points, lines or polygons.


