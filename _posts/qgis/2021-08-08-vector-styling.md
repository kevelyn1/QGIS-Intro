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

### 1. Download data
In this tutorial we will use [<span style="color:#0564A0">UNESCO World Heritage Sites</span>](http://whc.unesco.org/en/syndication). Scroll down and find World Heritage List in XLS format. Download the file and open in Excel. Save the file as csv-file `File ► Save As` and name it <span style="font-family:Consolas; color:#AF1B03">whc_sites_2021.csv</span> and choose file type as CSV (Comma delimited).

For convenience, you may directly download a copy of dataset from the link below:
[<span style="color:#0564A0">vector_styling.zip</span>](../../datasets/whc_sites_2021.csv)

Data Sources:
World Heritage List from [<span style="color:#0564A0">World Heritage List</span>](http://whc.unesco.org/en/syndication) and base maps from [<span style="color:#0564A0">Klas Karlsson</span>](https://github.com/klakar)

### 2. Procedure
#### 2.1. Add csv file to QGIS
1. Open QGIS and in the QGIS Browser Panel, locate the directory where you added the data. The World Heritage Sites (WHS) database is a CSV file, so we will need to import it. CSV-files are simple text files but if they have coordinates in them then they can be easily imported as spatial data. Click the Open Data Source Manager button ![image](../../images/icon_data source manager.png) on the toolbar. You can also use `Ctrl + L` keyboard shortcut.
