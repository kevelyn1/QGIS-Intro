---
layout: article
title: Simple vector analysis
modified: 2021-08-07
categories: qgis
image:
  teaser: vector_analysis_teaser.png
---


#### The tutorial consists of the following steps:

### 1. Download data
In this tutorial we will use [<span style="color:#0564A0">UNESCO World Heritage Sites</span>](http://whc.unesco.org/en/syndication). Scroll down and find World Heritage List in XLS format. Download the file and open in Excel. Save the file as csv-file `File ► Save As` and name it <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.csv</span> and choose file type as CSV (Comma delimited).
We will also need country borders. Download the [<span style="color:#0564A0">countries</span>](https://http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_0_countries.zip) and extract to your working folder.

Data Source:
World Heritage List from [<span style="color:#0564A0">World Heritage List</span>](http://whc.unesco.org/en/syndication) and country borders from [<span style="color:#0564A0">Natural Earth</span>](https://www.naturalearthdata.com/)

### 2. Procedure
#### 2.1. Add csv file to QGIS
1. Open QGIS and in the QGIS Browser Panel, locate the directory where you added the data. Expand the ne_10m_land folder and select the ne_10m_land.shp layer. Drag the layer to the canvas.
