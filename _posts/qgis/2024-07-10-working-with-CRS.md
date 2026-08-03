---
layout: article
title: Working with CRS
modified: 2024-08-10
categories: qgis
image:
  teaser: CRS_teaser.png
---

Coordinate Reference System (CRS) often cause a lot of frustration when working with GIS data. But a proper understanding of the concepts and access to the right tools will make it much easier to deal with projections. Coordinate Reference Systems, also referred to as Spatial Reference Systems, include two common types:
+ Geographic Coordinate Systems (GCS)
+ Projected Coordinate Systems (PCS)

It is important to recognise them and the differences between them. The projected coordinate systems always include information about the projection. It is important to make an appropriate choice of CRS for projects. Choosing an inappropriate CRS can cause your maps to look distorted, and poorly reflect the real-world relative sizes and positions of features but it can also cause wrong spatial analysis results (wrong area or distance estimations). Usually, while working in smaller geographic areas, there will be a number of standard CRSs used within a particular country or administrative area. It’s important to research which CRSs are appropriate or standard choices for the area you are mapping, and ensure that your QGIS project follows these standards. You can read more about Coordinate Reference Systems from [<span style="color:#0564A0">QGIS Documentation</span>](https://docs.qgis.org/3.28/en/docs/gentle_gis_introduction/coordinate_reference_systems.html#coordinate-reference-systems)

In this tutorial, we will explore how CRSs work in QGIS and learn about the tools available for vector and raster data layers.
The tutorial is mainly based on Ujaval Gandhi's [QGIS Tutorials and Tips](https://www.qgistutorials.com/en/docs/introduction.html).
#### The tutorial consists of the following steps:

- [1. Download data](#1-download-data)
- [2. Steps to work with CRS](#2-steps-to-work-with-crs)
  * [2.1. Change project CRS](#21-change-project-crs)
  * [2.2 Change vector layer CRS](#22-change-vector-layer-crs)
  * [2.3 Change raster layer CRS](#23-change-raster-layer-crs)

### 1. Download data

Natural Earth has an [<span style="color:#0564A0">Admin 0 - Countries</span>](http://www.naturalearthdata.com/downloads/10m-cultural-vectors/) dataset. Download the [<span style="color:#0564A0">countries</span>](https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_0_countries.zip) and extract them to your working folder.

>:scroll:**Note**
>
*By default Natural Earth shows de facto boundaries (according to who controls the territory) versus de jure. Optional point-of-view (POV) variants are available for several dozen countries in [<span style="color:#0564A0">Natural Earth</span>]( https://naturalearthdata.com/downloads/10m-cultural-vectors/) under Admin 0 – Countries point-of-views. For example, Ukraine can be found [<span style="color:#0564A0">here</span>](https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_0_countries_ukr.zip).*

[<span style="color:#0564A0">Estonian Land Board</span>](https://geoportaal.maaamet.ee/eng/Spatial-Data-p58.html) provides open data about Estonia for download. However, it is very high resolution (1 to 5m) and would be too big for this exercise. Therefore we will use the version, which is resampled to 100m: [<span style="color:#0564A0">100m resolution DTM</span>](../../datasets/est_dtm100.zip).

For convenience, you may directly download the files required for this tutorial from the link below:
[<span style="color:#0564A0">data_projections.zip</span>](../../datasets/data_projections.zip)

**Data Sources:** [<span style="color:#0564A0">Natural Earth</span>](https://www.naturalearthdata.com/) and [<span style="color:#0564A0">Estonian Land Board</span>](https://maaamet.ee/en)

### 2. Steps to work with CRS
#### 2.1. Change project CRS
1. Open QGIS. Locate your working folder in the Browser panel and drag/drop the <span style="font-family:Consolas; color:#AF1B03">ne_10m_admin_0_countries.shp</span> file to your QGIS Map view or alternatively click on Open Data Source Manager button ![image of icon data manager](../../images/icon_data source manager.png), click on the Vector tab and add the file from there. Save your project with a suitable name to your working folder.
![image of add vector](../../images/3_add vector file.png)
2. At the bottom of QGIS window, you will notice the label Coordinate. As you move your cursor over the map, it will show you the X and Y coordinates at that location. Currently it is presenting geographic coordinates because the data layer CRS is geographic, more precisely WGS84 (EPSG:4326), which you can see at the bottom-right corner. This is also the current Project CRS because QGIS assigns an empty project the CRS of the first layer you add to the project.
![image of CRS info](../../images/3_coord and CRS info.png)
3. To determine a layer’s projection, we can look into the metadata. Right click on <span style="font-family:Consolas; color:#AF1B03">ne_10m_admin_0_countries.shp</span> layer and select `Properties`. From there switch to the `Information` tab in the Layer Properties dialog. Under coordinate reference system you will find CRS. As you can see, there is also a lot of other information under metadata, such as extent of the layer, units etc.
![image of CRS info](../../images/3_layer crs information.png)
4. Lets first change the Project CRS. Click on EPSG:4326 in the status bar's lower right corner. Type "winkel" to the filter. This should bring up several Winkel CRS-s. Click on World_Winkel_Tripel_NGS (ESRI:54042)[^1] and then OK. Winkel-Tripel is minimal-error projection and it a standard projection for world maps made by the National Geographic Society (Wiki). As a result, the map should change in your map view since the Project CRS was changed.
![image of change project CRS](../../images/3_change project crs.png)
5. Please re-check the layer's CRS by right clicking on <span style="font-family:Consolas; color:#AF1B03">ne_10m_admin_0_countries.shp</span> layer and select `Properties`. From there switch to the `Information` tab in the Layer Properties dialog and check the CRS information. This should still be the same as before: WGS84 (EPSG: 4326). You only changed the project CRS but the layer's CRS did not change and in the map view the map was automatically and only virtually projected to the project CRS. This is because QGIS supports On-The-Fly (OTF) CRS transformation for both raster and vector data. Which means that whenever a layer’s CRS doesn’t match the Project CRS, it will automatically be transformed to the Project CRS so it can be displayed correctly. This means that regardless of the underlying CRS of particular map layers in your project, they will always be automatically transformed into the common CRS defined for your project. Behind the scenes, QGIS transparently reprojects all layers contained within your project into the project’s CRS, so that they will all be rendered in the correct position with respect to each other.

#### 2.2 Change vector layer CRS
6. Now let’s change the layer’s CRS. This operation is called Reprojection. It is possible to reproject the whole layer but rather than reprojecting the entire layer, we can also select a subset of features and reproject them to a new layer. Use the Select Features by Area or Single Click tool ![icon of select](../../images/icon_select.png) and click on Estonia to select it.
![image of select estonia](../../images/3_select estonia.png)
7. If you don't have Processing Toolbox open on the right side, switch it on by clicking `View ► Panels`. If you have Processing Toolbox available then you can skip this step.
![image of processing toolbox](../../images/3_processing toolbox.png)
8. From the Processing Toolbox search for Reproject layer.
![image of processing toolbox](../../images/3_find reproject.png)
9. Select <span style="font-family:Consolas; color:#AF1B03">ne_10m_admin_0_countries.shp</span> as the Input layer, check Selected features only then click on the Select CRS icon ![icon of select](../../images/icon_CRS2.png) next to Target CRS, search and select EPSG:3301 - Estonian Coordinate System of 1997. In Reprojected, choose the ... and click Save to a file. Now choose the directory and enter the name as <span style="font-family:Consolas; color:#AF1B03">estonia.gpkg</span> and click Run.
![image of processing toolbox](../../images/3_reproject.png)
10. The new layer <span style="font-family:Consolas; color:#AF1B03">estonia.gpkg</span> will appear in the Layer Panel. As you can see, both of the layers still line up exactly with each other - even though they are in different CRSs. This is thanks to the On-The-Fly CRS transformation. To check if the layer <span style="font-family:Consolas; color:#AF1B03">estonia</span> CRS has really been changed, right-click on the layer <span style="font-family:Consolas; color:#AF1B03">estonia</span> and click on `Properties`. In the Layer Properties, switch to `Information` where you can see that the CRS is EPSG:3301. This confirms that the layer’s CRS has been changed.
11. Now let’s set the Project CRS to match the newly created <span style="font-family:Consolas; color:#AF1B03">estonia</span>  layer’s CRS. Remove the layer <span style="font-family:Consolas; color:#AF1B03">ne_10m_admin_0_countries</span> and right click on the <span style="font-family:Consolas; color:#AF1B03">estonia</span> layer and choose `Layer CRS ► Set Project CRS from Layer`.
You will see that the Project CRS is now updated to EPSG: 3301 (Estonian Coordinate System 1997).


#### 2.3 Change raster layer CRS
12. Now let’s add a Raster layer. Go to `Layer ► Add Layer ► Add Raster Layer…` or alternatively click on Open Data Source Manager button ![image of icon data manager](../../images/icon_data source manager.png), click on the Raster tab and add the <span style="font-family:Consolas; color:#AF1B03">est_dtm100.tif</span> file from there. The new raster layer was added to the map view, but the layers are not perfectly overlaping each other because of the different level of detail. The raster map has a higher level of detail and the coastline is more precise. Also, the lakes have been removed from the elevation model.
![image of raster layer](../../images/icon_data source manager.png)
13. Check the CRS of the raster layer by right-clicking on the <span style="font-family:Consolas; color:#AF1B03">est_dtm100</span> layer and click on `Properties`. In the Layer Properties, switch to `Information` where you can see that the CRS is WGS84 (EPSG:4326).
14. To make both layers visible switch the order of the layers by dragging the <span style="font-family:Consolas; color:#AF1B03">est_dtm100</span> layer to the bottom in the Layers panel. In order to see the raster layer underneath the vector layer we need to change the symbology. Make a right click on the layer <span style="font-family:Consolas; color:#AF1B03">estonia</span> in the layer panel and choose `Properties`
![image of layer properties](../../images/3_raster lakes.png)
Under the Properties switch to `Symbology` tab and click on Simple Fill. Change Fill Style to No Brush and change the Stroke color into red and Stroke width to 0.3, and click OK.
![image of change symbology](../../images/3_symbology.png)
15. To change the raster layer's CRS into L-EST97 (EPSG: 3301) we need to use different tool compared to vector layers. Type "reproject" into the Processing Toolbox search which will bring up Warp (reproject) under GDAL[^2]. Choose the layer <span style="font-family:Consolas; color:#AF1B03">EST_dtm100</span> as Input, define WGS84 as Source input and choose L-EST97 (EPSG 3301) as Target CRS. Leave other parameters as default and scroll down to Advanced Parameters where you can change whether you want your new reprojected raster layer to be Saved to temporary file or Save to file. You may leave this temporary which means that after you close the QGIS project the file will be deleted. This is often an useful option when you have a lot of intermediate results that you know, you won't need later. Click Run to start reprojecting. A new file called <span style="font-family:Consolas; color:#AF1B03">Reprojected</span> should appear in the Layer panel. The new layer should align with the original file because of On-The-Fly CRS transformation but it's layer CRS should now be WGS84. Check the layer CRS under it's propeties to make sure it is so.
![image of warp](../../images/3_warp.png)


[^1]: As you might notice there is ESRI code instead of EPSG. This is because not all CRS have EPSG code and the specific Winkel Tripel (NGS) has been implemente in ESRI softwares under this specific code.
[^2]: [<span style="color:#0564A0">GDAL</span>](https://gdal.org/) is a open source translator library for raster and vector geospatial data formats
