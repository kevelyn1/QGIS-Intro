---
layout: article
title: Basic raster analysis
modified: 2024-08-07
categories: qgis
image:
  teaser: vector_analysis_teaser.png
---

Raster analysis can enable very powerful and large scale analysis. It is especially useful in different environmental applications to detect land use change, mapping and modelling species distribution, mapping suitable locations for either different spieces or solar power parks. 

In this task, you will analyse forest loss in Estonia and whether protected species habitats are affected by forest loss or not.


#### The tutorial consists of the following steps:

### 1. Download data
- [1. Download data](#1-download-data)
Please download the forest loss data: [<span style="color:#0564A0">Hansen_GFC_2023_lossyear_60N_020E.tif</span>](../../datasets/Hansen_GFC_2023_lossyear_60N_020E.tif) and Estonian borders [<span style="color:#0564A0">estonia.gpkg</span>](../../datasets/estonia.gpkg)

>:scroll:**Note**
>
*Global Forest Change is based on time-series analysis of Landsat images characterizing forest extent and change globally.
Trees are defined as vegetation taller than 5m in height. ‘Forest Cover Loss’ is defined as a stand-replacement disturbance, or a change from a forest to non-forest state, during the period 2000–2023.  ‘Forest Loss Year’ is a disaggregation of total ‘Forest Loss’ to annual time scales and the raster value from 1 to 23 indicates loss year from 2001 to 2023 respectively*

**Data Sources:**  [<span style="color:#0564A0">"Global Forest Change by Hansen et al 2011"</span>](https://glad.earthengine.app/view/global-forest-change) and Estonian Land Board