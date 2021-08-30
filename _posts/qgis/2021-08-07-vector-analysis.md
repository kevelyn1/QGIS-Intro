---
layout: article
title: Simple vector analysis
modified: 2021-08-07
categories: qgis
image:
  teaser: vector_analysis_teaser.png
---

Spatial queries and spatial joins are one of the basic analysis forms in GIS. In this tutorial, we will find how many UNSESCO WHC sites are every country. In some areas there are a lot of WHC sites and this makes their visualization complicated because points tend to overlap. To overcome this, we will analyze points in a grid or generate a heatmap.

#### The tutorial consists of the following steps:

### 1. Download data
This tutorial is a continuation to [<span style="color:#0564A0">"Basic vector syling"</span>](https://kevelyn1.github.io/QGIS-Intro/qgis/vector-styling/). And we will use the same WHC sites data from [<span style="color:#0564A0">UNESCO World Heritage Sites</span>](http://whc.unesco.org/en/syndication) saved as gpkg ([<span style="color:#0564A0">"Basic vector syling"</span>](https://kevelyn1.github.io/QGIS-Intro/qgis/vector-styling/) sections 1. and 2.1).

We will also need country borders. Download the [<span style="color:#0564A0">countries</span>](https://http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_0_countries.zip) and extract to your working folder.

Data Source:
World Heritage List from [<span style="color:#0564A0">World Heritage List</span>](http://whc.unesco.org/en/syndication) and country borders from [<span style="color:#0564A0">Natural Earth</span>](https://www.naturalearthdata.com/)

### 2. Procedure
#### 2.1. Spatial join
1. Open QGIS and in the QGIS Browser Panel, locate the directory where you added the data and add files <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.gpkg</span> and the <span style="font-family:Consolas; color:#AF1B03">ne_10m_admin_0_countries.shp</span> to QGIS.
2. Change the CRS of the project to Winkel Tripel (ESRI:54042) and save your project.

#### 2.2 Spatial query
3. Let's find out which countries have the highest numbers of world heritage sites. We will use spatial join.

#### 2.2. Heatmap
