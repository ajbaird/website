---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Using Python to Create Plotting Animations"
subtitle: ""
summary: ""
authors: [Austin Baird]
tags: []
categories: []
date: 2020-04-26T20:00:32-04:00
lastmod: 2020-04-26T20:00:32-04:00
featured: true
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: ["TBI"]
---
Using Matplotlib animation functionality to create videos
==================

As a little bit of an aside, I thought that I would detail a python script I wrote that takes in comma separated data (.csv files) to ouputs an mp4 movie of the data. This is useful if you'd like to create an animated plot of your temporal data to highlight the progression or evolution of the plot over time. I find that this type of data presentation can, sometimes, be more compelling than just introducing a line plot. It is especially compelling when placed side-by-side with three dimensional data. I wrote this script to plot bifurcation data over sime while a three dimensional .vtk plot runs next to it. In this blog you will (hopefully):

- Create a function that takes in command line arguments for your script
- Use pythons OS library to check paths given by the user and generate output folders 
- Format graphs using matplotlib to create publication worthy output
- Use the animation library to generate videos of your data

Command Line Arguments
-------------------


![png](./runHem.png)


Check Paths and Verify Data
-------------------


Formatting Graphs Using Matplotlib
------------------------------------

Animating the Data
------------------------------------

If it is running correctly your console screen should look the like this 

![png](./consol.png)


To see the full set of code developed for this tutorial, please see the [github page](https://github.com/ajbaird/TBISimulator/blob/master/animateData.py)


If you have other issues feel free to post a comment on the community pages ([link](https://github.com/BioGearsEngine/core/issues))!
