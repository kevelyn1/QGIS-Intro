---
layout: article
title: Making a map
modified: 2020-08-11
categories: qgis
image:
  teaser: QGIS_intro_teaser.png
---
A map is the most common output of GIS. This tutorial shows how to create a map from vector and raster data with standard map elements like map inset, grids, north arrow, scale bar and labels.
Lets make a map from vector data.

### Download data

We will use the Natural Earth dataset - specifically the Natural Earth Quick Start Kit that comes with beautifully styled global layers that can be loaded directly to QGIS.

Download the [<span style="color:#0564A0">Natural Earth Quickstart Kit</span>](https://naciscdn.org/naturalearth/packages/Natural_Earth_quick_start.zip). If the download link doesn’t work, get it directly from Natural Earth Downloads page.

### Steps to make a map

1. Download and extract the Natural Earth Quick Start Kit data. Open QGIS. Locate the <span style="font-family:Consolas; color:#AF1B03">Natural_Earth_quick_start</span> folder in the Browser panel. Expand the folder to locate the <span style="font-family:Consolas; color:#AF1B03">Natural_Earth_quick_start_for_QGIS_v3</span> project. This is the project file that contains styled layers in QGIS Document format. Double-click the project to open it.
![image of browse data](../../images/2_browse_data.png)
2. The state of your QGIS session is called a project. QGIS works on one project at a time.  Please save your project `Project ► Save as` into your folder. The information saved in a project file includes add layers, layer properties and symbology, projection of the map view, print layouts etc. Read more about QGIS project from [<span style="color:#0564A0">QGIS Documentation</span>](https://docs.qgis.org/testing/en/docs/user_manual/introduction/project_files.html#).
3. You may notice that the map labels are in Greek. This project uses variables to set the language.  We can change the variables by going to `Project ► Properties`. Switch to the `Variables` tab in the `Project Properties` dialog. Locate the <span style="font-family:Consolas">project_language</span> variable and change the language to <span style="font-family:Consolas>name_en</span> and click OK. ![image of browse data](../../images/2_language-prop.png)

The attribute table of <span style="font-family:Consolas; color:#AF1B03">ne_10m_populated_places</span> contains place names in multiple languages and therefore you can use variables to create a map in several language. Open the attribute table of <span style="font-family:Consolas; color:#AF1B03">ne_10m_populated_places</span> by making a right click on the layer name choose `Open Attribute Table`. Find in the table variables (column names) <span style="font-family:Consolas>name_en</span> and <span style="font-family:Consolas>name_el</span>. Place names are generated automatically to the map based on these variables. 
