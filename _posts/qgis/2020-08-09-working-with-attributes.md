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
1. Locate the span <style="font-family:Consolas; color:#AF1B03"ne_10m_populated_places_simple.shp</span> file in the QGIS Browser drag it to the map view. Save your project with a suitable name to your working folder.
>**Tip** :smirk:
>
*You can add files also directly from zip-file without extracting them if you expant the zip file in the Browser and drag shp-file to the map view*

2. A new <span style="color:#AF1B03">ne_10m_populated_places_simple</span> will now be loaded in QGIS and you will see many points representing the populated places of the world. The default view in the QGIS canvas shows the geometry of the GIS layer. Each point also has associated attributes. Let’s view them. Locate the Attributes Toolbar. This toolbar contains many useful tools to inspect, view, select, and modify attributes of a layer. If you do not see the toolbar, you can enable it from `View ► Toolbars ► Attributes Toolbar`.
![image of attribute toolbar](../../images/4_attribute toolbar.png)
3. Click the Identify button ![icon of identify](../../images/icon_identify.png) on the Attributes Toolbar. Once the tool is selected, click on any point on the canvas. The associated attributes of that point will be displayed in a new Identify Results panel. Once you are done exploring attributes of different points, you can click the Close button.
![image of identify](../../images/4_identify.png)
4. You can also view all of the attributes together as a table. Click the Open Attribute Table button ![icon of attr table](../../images/icon_attribute table.png) on the Attributes Toolbar. You can also right-click the <span style="color:#AF1B03">ne_10m_populated_places_simple</span> and select Open Attribute Table.
>**Tip** :smirk:
>
*You open also the attribute table with F6 from the keyboard. However, the layer of which attribute table you wish to open must be selected from the Layer panel*

5. In the attribute table, scroll horizontally and locate the **pop_max** column. This field contains the population of the associated place. You can click twice on the field header to sort the column in descending order.
![image of identify](../../images/4_sort attributes.png)
