---
layout: article
title: Basic vector styling
modified: 2021-08-08
categories: qgis
image:
  teaser: vector_styling_teaser.png
---

To create a map, one has to style the GIS data and present it in a form that is visually informative and also pleasing. There are a large number of options available in QGIS to apply different types of symbology to the underlying data. In this tutorial, we will take a text file and apply different data visualization techniques to highlight spatial patterns in the data.

#### The tutorial consists of the following steps:
- [1. Download data](#1-download-data)
- [2. Procedure](#2-procedure)
  * [2.1. Add csv file to QGIS](#21-add-csv-file-to-qgis)
  * [2.2. Add base maps](#22-add-base-maps)
  * [2.3. Categorized symbology](#23-categorized-symbology)
  * [2.4. Graduated symbology](#24-graduated-symbology)

### 1. Download data
In this tutorial we will use [<span style="color:#0564A0">UNESCO World Heritage Sites</span>](http://whc.unesco.org/en/syndication). Scroll down and find World Heritage List in XLS format. Download the file and open in Excel. Save the file as csv-file `File ► Save As` and name it <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.csv</span> and choose file type as CSV UTF-8 (Comma delimited).

For convenience, you may directly download a copy of dataset from the link below:
[<span style="color:#0564A0">vector_styling.zip</span>](../../datasets/whc_sites_2021.csv)

Data Sources:
World Heritage List from [<span style="color:#0564A0">World Heritage List</span>](http://whc.unesco.org/en/syndication) and base maps from [<span style="color:#0564A0">Klas Karlsson</span>](https://github.com/klakar)

### 2. Procedure
#### 2.1. Add csv file to QGIS
1. Open QGIS and in the QGIS Browser Panel, locate the directory where you added the data. The World Heritage Sites (WHS) database is a CSV file, so we will need to import it. CSV-files are simple text files but if they have coordinates in them then they can be easily imported as spatial data. Click the Open Data Source Manager button ![image](../../images/icon_data source manager.png) on the toolbar. You can also use `Ctrl + L` keyboard shortcut.
In the Data Source Manager window, switch to the Delimited Text tab. Click the … button next to File name and browse to the directory where the <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.csv</span> file is and select it. QGIS will auto detect the delimiter if it is a comma. Expand the Geometry Definition. The X and Y have been recognised correctly by QGIS and also that the CRS is WGS84 (EPSG: 4326). Finally, click Add and close.
![image](../../images/5_add csv.png)
2. A new layer <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021</span> will be added to the Layers panel and you will see the points representing the World Heritage Sites. Make right click on the layer name and `Export ► Save Features As...` and save it as <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.gpkg</span>. You can remove the CSV layer <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.gpkg</span> by right clicking on it and `Remove Layer`.
![image](../../images/5_whs sites.png)
3. Change the CRS of the project to Winkel Tripel (ESRI:54042).

#### 2.2. Add base maps
3. Lets add some base maps to our map.  Sometimes it is practical to use ready made stylised base maps instead of styling the base map yourself. [<span style="color:#0564A0">Klas Karlsson</span>](https://github.com/klakar) has collated a nice collection of different basemaps which can be added by running a little Python script in QGIS. Open [<span style="color:#0564A0">qgis_basemaps.py</span>](https://github.com/klakar/QGIS_resources/blob/master/collections/Geosupportsystem/python/qgis_basemaps.py) from GitHub. Select the script starting from # Sources and copy it (`Crtl+C`).
![image](../../images/5_select script.png)
4. Go back to QGIS and open Python Console by clicking ![image](../../images/icon_python console.png) on the toolbar. Python Console opens under the Map view. Paste the script to the console and click Enter on the keyboard. After this you may close the Python Console.
![image](../../images/5_paste script.png)
5. On the Browser Panel under XYZ tiles, a lot of new layers have appeared. These are the added base maps. Let's try some of them. Double-click on CartoDb Dark Matter and the base map is added to the map view. It covers the WHS points but in the Layer panel drag <span style="font-family:Consolas; color:#AF1B03">CartoDb Dark Matter</span> under the <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021</span>. Try also for example Google Satellite base map or more fun Stamen Watercolor. Explore some more base maps if you like but finally leave Stamen Watercolor as the map base map.
![image](../../images/5_add base map layers.png)
6. You might notice that the there are two New Zealands on the map. This is because the specific projection should not show rectangular shaped map but the base map is rectangular and it stretches/duplicates some areas. We can mask these areas out by creating a grid. From the Processing Toolbox find Create grid tool. For the Grid type choose rectangle, Grid extent: -180,180,-90,90 (whole world), Grid CRS choose WGS84 (EPSG: 4326) and horizontal and vertical spacing 10 degrees. Save the grid into a file <span style="font-family:Consolas; color:#AF1B03">global_grid.gpkg</span> and click Run and Close.
![image](../../images/5_create grid.png)
7. You have now grid that is being projected into Winkel Tripel that is yoru project CRS. Let's make a mask from it by changing it's symbology. Double-click on <span style="font-family:Consolas; color:#AF1B03">global_grid</span> in the Layer panel to open it's properties. Switch to Symbology. Change the Single Symbol to Inverted Polygons. Click on Simple Fill and change the Fill color to white and Stroke style No Pen and click OK.
![image](../../images/5_inverted polys.png)
8. You should now have nicely masked world and only one NZ.
![image](../../images/5_masked world.png)

#### 2.3. Categorized symbology
6.

#### 2.4. Graduated symbology
