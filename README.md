<!--
 * @Author: wanhaoming wanhaoming@outlook.com
 * @Date: 2024-06-24 23:58:49
 * @LastEditors: wanhaoming wanhaoming@outlook.com
 * @LastEditTime: 2024-06-25 23:05:48
 * @FilePath: \Curve-Matching\README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# Curve-Matching
The implemention of paper：["Tree Species Classification of Forest Stands Using Multisource Remote Sensing Data"](https://www.mdpi.com/2072-4292/13/1/144)  

# Purpose of this method
    Fusion different structure data base on mechine learning
![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/frame.png)
# Data
    1.1 Multi-spectral image(Sentinel-2)
    2.2 LiDAR data
    3.3 Hyper-spectral image

# Brifly steps of the fusion method  
## 1. Generating Objects  
Traditional OBIA (Object-Based Image Analysis) methods were adopted to cluster the same pixel. (This is just a clustering method; you can choose any method you prefer, such as super-pixel segmentation or k-means based on features extracted by a deep learning model.)  

![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/Segmentation.png)

## 2. Extracting Features  
The key point of this method is how to express different structure data as curves.

### 2.1. For High-Resolution RGB imagery (Sentinel-2)

Drawing the histogram on each band.  

![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/RGB.jpg)  

### 2.1. For Multi-spectral Images (Sentinel-2)

Each pixel location involves 12 bands; therefore, simply calculate the mean value based on the object.
![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/Multispectral.jpg)

### 2.2. For LiDAR Data

Before we start extracting features, let's assume that the same tree has the same structure, such as height and the shape of the canopy.
Based on this assumption, the curve that reflects the tree's geo-structure can be generated by counting the lighting numbers in the vertical direction.
![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/GEOStructure-2.png)  
![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/GEOStructure-1.png)  
![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/LIDAR.jpg)  

## How to Classify?

Now, all different structure data has been described as curves. You can use any ML algorithm you like to classify them. However, according to our experiment, curve matching might be better, as it can achieve higher accuracy performance with fewer samples.  

![img](https://github.com/XavierMFC/Curve-Matching/blob/main/data/example_data/CurveMatch.jpg)
