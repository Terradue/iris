# IRIS - Intelligence foR Image Segmentation<sup>1</sup>
<sup>1</sup>Yes, it is a <a href="https://en.wikipedia.org/wiki/Backronym">backronym</a>.
**Work in progress.**

<img src="preview/1.png" />

Tool for manual image segmentation and classification of satellite imagery (or images in general).
This application is a flask app which can be run locally. 

<hr />

## Installation
Since IRIS is written in python, you will need a python 3.7 environment to use this app.
Go to your preferenced installation folder via your console and clone this repository by running:

`git clone https://github.com/ESA-PhiLab/iris.git`.

Enter the iris directory with

`cd iris`

and install the app with pip

`pip install .`

This should install all necessary python packages automatically.

## Usage
You will need a configuration file to run IRIS. There is one example in the examples folder you can use. 

You can start IRIS in two different modes:
1) **label:** This will open a local browser application which helps you to perform manual segmentation of the images in your project. Start IRIS in the label mode like this: `iris label PROJECT_FILE`. Then open this address with your browser (chrome or firefox): `http://localhost:5000`

2) **conclude:** (NOT YET IMPLEMENTED) After labelling is done (by using the *label* mode), you can use this mode to bundle the output masks and get some statistics.

## Documentation

### Label interface

### Project file
Before you can use IRIS, you have to provide a configurations file for your project (must be in yaml or json format). See [here](examples/example-config.json) for an example.

The table below shows different options for the configurations:

Field | Description | JSON Example
--- | --- | ---
**label-mode** | IRIS is going to provide different label modes: *segmentation* or *classification* (the latter is not yet implemented) | `"label-mode": segmentation`
**in_path** | The input directory for your project. This directory should contain subfolders (which names present the tile ids) with the images that you want to label. | `"in_path": "/home/user/projects/sentinel-labeling/examples"`
**image_filename** | The filename of the images inside the tile folders. IRIS can load standard image formats (like *png* or *tif*) and numpy files (*npy*). The arrays inside the numpy arrays should have the shape HxWxC | `"image_filename": "image.npy"` 
**out_path** | The output directory for your project. This directory will contain the mask files (from the segmentation) and user configurations | `"out_path": "/home/user/projects/sentinel-labeling/results"` 
**classes** | This is a list of classes that you want to allow the user to label. Each class is represented as a dictionary with the following keys:<ul><li>*name:* Name of the class</li><li>*description:* Further description which explains the user more about the class (e.g. why is it different from another class, etc.)</li><li>*colour:* Colour for this class. Must be a list of 4 integers (RGBA) from 0 to 255.</li><li>*user_colour (optional)*: Colour for this class when user mask is activated in the interface. Useful for background classes which are normally transparent.</li></ul> | "classes": [<br>&nbsp;{<br>&nbsp;&nbsp;"name": "Clear",<br>&nbsp;&nbsp;"description": "All clear pixels.",<br>&nbsp;&nbsp;"colour": [255,255,255,0],<br>&nbsp;&nbsp;"user_colour": [0,255,255,70]<br>},<br>{<br>&nbsp;&nbsp;"name": "Cloud",<br>&nbsp;&nbsp;"description": "All cloudy pixels.",<br>&nbsp;&nbsp;"colour": [255,255,0,70]<br>}]<br>
**image_shape** | The dimensions of the images you want to label (WxH). | `"image_shape": [1280, 1280]` 
**mask_area** | In case you don't want to allow the user to label the complete image, you can limit the segmentation area. | `"mask_area": [128, 128, 1152, 1152]`

### Project structure


Coming soon.
