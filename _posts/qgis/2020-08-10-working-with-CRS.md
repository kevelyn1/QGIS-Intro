---
layout: article
title: Working with CRS
modified: 2020-08-10
categories: qgis
image:
  teaser: CRS_teaser.png
---

Coordinate Reference System (CRS) often cause a lot of frustration when working with GIS data. But a proper understanding of the concepts and access to the right tools will make it much easier to deal with projections. Coordinate Reference Systems, also referred to as Spatial Reference Systems, include two common types:
+ Geographic Coordinate Systems (GCS)
+ Projected Coordinate Systems (PCS)

It is important to recognise and make the difference between them. The projected coordinate systems always include also information about the projection.

In this tutorial, we will explore how CRSs work in QGIS and learn about tools available for vector and raster data layers.

#### The tutorial consists of the following steps:

- [1. Download data](#1-download-data)
- [2. Steps to make a map](#2-steps-to-make-a-map)

### 1. Download data

Natural Earth has [<span style="color:#0564A0">Admin 0 - Countries</span>](http://www.naturalearthdata.com/downloads/10m-cultural-vectors/) dataset. Download the [<span style="color:#0564A0">countries</span>](https://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_0_countries.zip).

UK’s Ordnance Survey provides open data for download. Download the MiniScale raster product for Great Britain and extract it to a folder on your computer.

For convenience, you may directly download a copy of the dataset from the link below:

ne_10m_admin_0_countries.zip

minisc_gb.zip (Contains only the files required for this tutorial)

Data Sources: [NATURALEARTH] [OSOPENDATA]

### 2. Steps to make a map
#### 2.1. Creating the main map
1. Download
