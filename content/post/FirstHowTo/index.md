---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Hemorrhage Treatment HowTo"
subtitle: "Create a program that monitors patient vitals during hemorrhage"
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
projects: ["BioGears"]
---
Leveraging BioGears libraries to write your own HowTo
==================

We have BioGears built and ready to go but the question is, now what? What can we do with BioGears, how powerful is it and what type of applications can be build with it? These are some of the questions we will address in this tutorial on developing your own application leveraging BioGears API tools in C++. 

Running a HowTo file
-------------------
To start lets first just verify that we can, in fact, run one of the many HowTo files provided by BioGears when we clone the repository. If you followed, the first post on this site you should have built BioGears as well as all the HowTos. If you didn't complete that please refer back this that [post](https://austinbaird.dev/post/buildingbiogears/). To run a HowTo file simply execute the binaries in the proper directory.

Once you have a directory and the package manager set up, navigate to that newly created directory through the command line and copy the clone [link](https://github.com/BioGearsEngine/core.git) on github. From this directory we will install all the dependencies needed to begin running and using BioGears. To proceed copy and past the following code (to install requirements)

```
brew install wget
brew install git
brew install ninja
brew  install g++
brew  install gcc
brew  install eigen
brew  install log4cpp
brew  install xerces-c
brew install xsd
``` 

Navigate the core folder (for me, `~/Development/BioGears/Core/core`) and create a build directory `mkdir build`. Next, navigate to that build folder. We will now go through a series a cmake commands to set up the build configuration. We will make a few assumptions; first, we will assume that our install directory will be `opt/biogears/usr`. We will then link a prefix path. Now from the build folder we can type:

```
cmake -G "Ninja" -DCMAKE_INSTALL_PREFIX=/opt/biogears/usr \
                 -DCMAKE_PREFIX_PATH='/usr/local/opt \
                 -DBiogears_BUILD_JAVATOOLS=OFF \ 
                 ..
```

Debugging 
-----------

If it isn't present you might have forgotten the '..' at the end of the command chain above. 
To fix this issue back out to the top directory, for me this will be Core. From Core use the rm command to remove the cloned directory`--- BioGears/Core » rm -rf core`  then re-clone BioGears: `--- BioGears/Core » git clone https://github.com/BioGearsEngine/core.git core` then create the build folder, navigate to the build folder and re-run the cmake command above. `--- BioGears/Core/core/build » cmake -G "Ninja" -DCMAKE_INSTALL_PREFIX=/opt/biogears/usr -DCMAKE_PREFIX_PATH='/usr/local/opt' -DBiogears_BUILD_JAVATOOLS=OFF ..`

Hopefully this will create the required file.

Building and Testing Scenario Driver
--------------------------------------

Now from the build folder, we can build the scenario driver executable. This program creates a serializes in a scenario file, creates a BioGears engine and then pushes actions and data calls to the engine. Its a great place to start understanding how to use BioGears and what the engine is capable of. 

To build the scenario driver, simply type (from the build folder) `--- BioGears/Core/core/build » ninja scenario_driver`, now lets run the scenario driver to test that it's working correctly. First navigate to the runtime directory (if there isn't a generated runtime directory type `cmake STAGE` from the build directory). From the runtime directory type `../outputs/Release/bin/scenario_driver ./Scenarios/Patient/BasicStandard.xml`

To confirm that this file ran, navigate to the ./Scenarios/Patient folder and confirm that there is a BasicStandard.log and BasicStandardResults.csv file. Feel free to look at the log and associated xml, log, and csv files to figure out the structure of a scenario run and how the outputs reflect what you input into the .xml.

Configuring Xcode Build
--------------------------------------

To configure a build that generates an Xcode project, make a new build folder in core, called `core/buildXcode`, then in the cmake GUI set up the configuration step as shown in the image: 

![png](./cmake1.png)

After you configure the where the source code is and where the build files will be generated (top two lines) as seen in the image. Click the configure button and select Xcode from the generators list that will pop up. There should be no errors, if there are you might need to re-install some of the binaries. Next, click generate, there will be some red text but this step should still finish. Next, click open project and the project should be launched in Xcode. In the next image you can see the folder structure and the Cardiovascular.cpp file which houses all models associated with BioGears cardiovascular system.

![png](./xcodeProj.png)

If you have other issues while building, feel free to post a comment on the community pages ([link](https://github.com/BioGearsEngine/core/issues))!
