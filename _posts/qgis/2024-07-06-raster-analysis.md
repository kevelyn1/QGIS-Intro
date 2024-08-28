---
layout: article
title: Basic raster analysis
modified: 2024-08-07
categories: qgis
image:
  teaser: raster_styling_teaser.png
---

Raster analysis can enable very powerful and large scale analysis. It is especially useful in different environmental applications to detect land use change, mapping and modelling species distribution, mapping suitable locations for either different spieces or solar power parks. 

In this task, you will analyse forest change in Estonia and whether protected species *Lanius collurio* habitats are affected by forest change or not.

#### The tutorial consists of the following steps:
- [1. Download data](#1-download-data)
- [2. Calculating raster area](#2-calculating-raster-area)
  * [2.1. Raster clipping](#21-raster-clipping)
  * [2.2. Reprojecting raster](#22-reprojecting-raster)
  * [2.3. Styling raster](#23-styling-raster)
  * [2.4. Calculating areas](#24-calculating-areas)
- [3. Sampling raster data to points](#3-sampling-raster-data-to-points)

### 1. Download data
- [1. Download data](#1-download-data)
Please download the forest loss data: [<span style="color:#0564A0">Hansen_GFC_2023_lossyear_60N_020E.tif</span>](../../datasets/Hansen_GFC_2023_lossyear_60N_020E.tif) and Estonian borders [<span style="color:#0564A0">estonia.gpkg</span>](../../datasets/estonia.gpkg). For the second part, download bird species *Lanius collurio* data  [<span style="color:#0564A0">lanius_collurio.gpkg</span>](../../datasets/lanius_collurio.gpkg) 

>:scroll:**Note**
>
*Global Forest Change is based on time-series analysis of Landsat images characterizing forest extent and change globally.
Trees are defined as vegetation taller than 5m in height. ‘Forest Cover Loss’ is defined as a stand-replacement disturbance, or a change from a forest to non-forest state, during the period 2000–2023.  ‘Forest Loss Year’ is a disaggregation of total ‘Forest Loss’ to annual time scales and the raster value from 1 to 23 indicates loss year from 2001 to 2023 respectively*

**Data Sources:**  [<span style="color:#0564A0">"Global Forest Change by Hansen et al 2011"</span>](https://glad.earthengine.app/view/global-forest-change) and Estonian Land Board and [<span style="color:#0564A0">Estonian Environmental Portal (Keskkonnaportaal)</span>](https://register.keskkonnaportaal.ee/register)

### 2. Calculating raster area
#### 2.1. Raster clipping
1. Open QGIS and in the QGIS Browser Panel, locate the directory where you added the data and add files <span style="font-family:Consolas; color:#AF1B03">estonia.gpkg</span> and <span style="font-family:Consolas; color:#AF1B03">Hansen_GFC_2023_lossyear_60N_020E.tif</span> to QGIS.
2. Save your project with an appropriate name, for example raster_analysis.
3. Now lets clip the raster layer with the Estonian vector boundary to obtain forest cahnge data only for Estonia. Find 'Clip raster by mask layer' in the Processing toolbox and open it. Choose <span style="font-family:Consolas; color:#AF1B03">Hansen_GFC_2023_lossyear_60N_020E</span> layer as the Input layer and <span style="font-family:Consolas; color:#AF1B03">estonia</span> layer as the Mask layer. Enter 0 as the NoData value. If NoData is determined in raster file then it will not be used in further calculations and will be shown as transparent. In most cases, it is useful to define NoData value.
![image](../../images/7_clip raster.png)
4. Raster files can get very big and therefore it is always recommended to use compression. You should always use lossless compression such as LZW. If you use lossy compression (JPEG). To apply compression, choose in the Advanced Parameters section Low compression. Double click on the value box and write LZW. Save the file as <span style="font-family:Consolas; color:#AF1B03">forest_est_wgs84.tif</span> and click `Run`. 
![image](../../images/7_clip raster2.png)
5. Right-click <span style="font-family:Consolas; color:#AF1B03">Hansen_GFC_2023_lossyear_60N_020E.tif</span> layer and select Remove Layer.

#### 2.2. Reprojecting raster
6. Next we need to reproject the raster layer to the Estonian coordinate system. In the Processing Toolbox search Warp and open it. Choose <span style="font-family:Consolas; color:#AF1B03">forest_est_wgs84</span> as the Input Layer and EPSG:3301 as the Target CRS. In the Advanced Parameters choose Low Compression and LZW like before. Save the file as <span style="font-family:Consolas; color:#AF1B03">forest_est_reprojected.tif</span> and click `Run`.
![image](../../images/7_warp.png)
7. Remove the <span style="font-family:Consolas; color:#AF1B03">forest_est_wgs84.tif</span> layer. Let's set the project layer to the Estonian coordinate system. Click on <span style="font-family:Consolas; color:#AF1B03">forest_est_reprojected.tif</span> layer and choose `Layer CRS ► Set Project CRS from Layer`.
![image](../../images/7_layer crs.png)

#### 2.3. Styling raster
8. Now let's change the symbology of the raster layer to a more suitable one. Double click on <span style="font-family:Consolas; color:#AF1B03">forest_est_reprojected</span> to open Symbology. Choose Singleband pseudocolor as the Render type, Equal Interval as the mode and 23 classes. Also choose a color ramp to your liking, for example Viridis. Then click `OK`.
![image](../../images/7_symbology.png)
9. For better visualization move the layer <span style="font-family:Consolas; color:#AF1B03">estonia</span> to the bottom and change it to black. 
![image](../../images/7_symbology2.png)
10. Next we'll add roads and settlements, which we'll get via WMS. Click `Layer ► Add Later ► Add WMS/WMTS Layer...`. In the new window click `New` and then write Maa-amet as the name and copy this link (https://kaart.maaamet.ee/wms/alus?) as the URL.
![image](../../images/7_wms.png)

>:scroll:**Note**
>
*WMS (Web Map Service) is a service based on OGC WMS (Open Geospatial Consortium Web Map Service) standard that enables to display spatially referenced data on the computer screen without downloading . Many governmental agencies provide their data using WMS service. Estonian Land Board provideas a lot of free spatial data via WMS: https://geoportaal.maaamet.ee/eng/services/public-wms-wfs-p346.html *

11. Now click `Connect` and choose the layers with ID numbers 138, 139 and 140. Make sure to check the option to Load as separate layers and then click `Add`.
![image](../../images/7_wms2.png)
![image](../../images/7_wms3.png)

#### 2.4. Calculating areas
12. Now let's calculate the area for each class. Search Raster layer unique values report in the Processing Toolbox and open it. Choose <span style="font-family:Consolas; color:#AF1B03">forest_est_reprojected</span> as the Input layer. Save the file as <span style="font-family:Consolas; color:#AF1B03">class_areas.gpkg</span> and click `Run`.
![image](../../images/7_unique values.png)
13. Right-click on the <span style="font-family:Consolas; color:#AF1B03">class_areas.gpkg</span> layer and open Attribute Table. The column m2 contains the area for each class in square meters. 
14. Let's convert the area to square kilometers. To do that, search Field calculator in the Processing Toolbox and open it. Select <span style="font-family:Consolas; color:#AF1B03">class_areas</span> as the Input layer. Enter the Field name as area_sqkm and for the result field type choose decimal (double). In the Expression window enter <span style="font-family:Consolas">round("m2" / 1000000, 2)</span>. This will convert the square meters to square kilometers. Save the file as <span style="font-family:Consolas; color:#AF1B03">class_area_sqkm.xlsx</span> and click `Run`.
![image](../../images/7_field calc.png)

### 3. Sampling raster data to points
15. Our goal is to see how many habitats of the red-backed shrike are affected by logging. First add the layer <span style="font-family:Consolas; color:#AF1B03">lanius_collurio.gpkg</span> to the map. 
16. Then search Sample raster values in the Processing Toolbox and open it. Add <span style="font-family:Consolas; color:#AF1B03">lanius_collurio</span> as the Input layer and <span style="font-family:Consolas; color:#AF1B03">forest_est_reprojected</span> as the Raster layer. For the output column prefix write forest_loss_. Then save the file as <span style="font-family:Consolas; color:#AF1B03">lanius_collurio_forest_loss.gpkg</span> and click `Run`.
![image](../../images/7_raster values.png)
17. Next open the attribute table of <span style="font-family:Consolas; color:#AF1B03">lanius_collurio_forest_loss</span>. As you can see there is a new column forest_loss_1. NULL means that there was no forest change and the number means that there was (the number shows which year the change took place).
![image](../../images/7_forest loss.png)
18. Now we'll count how many habitats had forest loss. Search Basic statistics for fields in the Processing Toolbox and open it. Choose <span style="font-family:Consolas; color:#AF1B03">lanius_collurio_forest_loss</span> as the Input layer and forest_loss_1 as the field to calculate statistics on. Double click on Statistics in the Results Viewer. 
![image](../../images/7_basic statistics.png)
19. Count shows how many rows had a value (aka how many points were affected by forest change) and NULL means there was no forest change.