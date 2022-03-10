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

## Major tasks and workflow
There are 10 major task involved in this guide. Some of them are independent and some others are interdependent. Figure 2 represents the most efficient interaction between them. In the graph, the task are organized so that it could produce an outcome as fast as possible. Use this workflow schema to take advantage of the independency among task and stay ahead in the project’s development. However, organizational or environmental factors might affect the flow of information. Use alternatives responding to the project’s environment.

## Spatial scope definition
Defining the spatial scope means to decide the extension of the urban area that will be covered. This location, from now on called area of interest, should be easily identifiable. Use land administration information or toponym to identify the spatial shape of this place. A simple query (Figure 3) on any map online service like Google Maps , Bing  or Open Street Maps  will provide a quick idea of it.

Identify socio spatial divisions inside the area of interest. That is non visible borders based on social features like economic status, familiarity, foundation or any other singularity. Make sure you have this data since it will be needed to address the allocation of some services. If this information is not easily available through any geospatial database (public or from any government agency) it must be consulted on field surveys.

## Terrain data acquisition
Acquire a digital elevation model for the area of interest. This might be acquired from the USGS Earth Explorer  platform. Find the mission SRTM  dataset, and find the most recent capture of the area of interest. Another characteristic to consider is resolution; a recommended one is 1 arc-second or 30m. Other sources of information might be the Copernicus Open Access Hub.

The DEM will be the main source of information to derive morphological and hydrological analysis. As the DEM provided by any platform would cover a bigger size area than the area of interest, it is required to clip it to a more practical size (Figure 4) in order to make processing faster. Use the ‘Clip raster by extend’ algorithm from the GDAL  modules; find this and any other algorithm on the Processing Toolbox.

## Hydrological analysis
The hydrological analysis is composed by two calculus derived from the DEM. The Terrain Wetness Index and the Stream Power Index. 
The Terrain Wetness Index (TWI) provides a relative score showing the areas where the terrain is most probable to accumulate water. It’s defined as: 
(pending figure)

In the QGIS environment, apply the next sequence of algorithms to calculate it: Use the ‘Flow Accumulation’ algorithm from the SAGA  modules; apply it to the DEM clip. The result is the local upslope catchment area (UCA). The local slope is calculated with the native ‘Slope’ algorithm; it should be transformed into radians. But first, the 0 values corrected since it would induce error when calculating natural logarithm; add 0.001 to the slope values.

Then, multiply the modified slope value 0.01745 times. In order to do this, use the ‘Raster Calculator’ algorithm; use it for any raster algebra operation. Finally, calculate the log normal function. The UCA must be multiplied by the X and Y values of raster pixel dimensions. 
