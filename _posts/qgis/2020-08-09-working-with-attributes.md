---
layout: article
title: Working with attributes
modified: 2020-08-09
categories: qgis
image:
  teaser: attributes_teaser.png
---

GIS data has two parts - features and attributes. Attributes are structured data about each feature. This tutorial shows how to view the attributes of a GIS vector layer and do basic queries on them in QGIS.

#### The tutorial consists of the following steps:

### 1. Download data
Natural Earth provides a [<span style="color:#0564A0">Populated Places</span>](http://www.naturalearthdata.com/downloads/10m-cultural-vectors/10m-populated-places/) dataset. Download the [<span style="color:#0564A0">simple (less columns) dataset</span>](http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/cultural/ne_10m_populated_places_simple.zip). Extract the dataset to your working folder.

For convenience, you may directly download a copy of datasets from the link below:
[<span style="color:#0564A0">ne_10m_populated_places_simple.zip</span>](../../datasets/ne_10m_populated_places_simple.zip)

Data Source: [<span style="color:#0564A0">NaturalEarth</span>](https://www.naturalearthdata.com/)

### 2. Steps to work with attributes
1. Locate the span style="font-family:Consolas; color:#AF1B03"ne_10m_populated_places_simple.shp</span> file in the QGIS Browser drag it to the map view. Save your project with a suitable name to your working folder.
>**Tip** :smirk:
>
*You can add files also directly from zip-file without extracting them if you expant the zip file in the Browser and drag shp-file to the map view*

2. A new <span style="color:#AF1B03">ne_10m_populated_places_simple</span> will now be loaded in QGIS and you will see many points representing the populated places of the world. The default view in the QGIS canvas shows the geometry of the GIS layer. Each point also has associated attributes. Let’s view them. Locate the Attributes Toolbar. This toolbar contains many useful tools to inspect, view, select, and modify attributes of a layer. If you do not see the toolbar, you can enable it from `View ► Toolbars ► Attributes Toolbar`.
