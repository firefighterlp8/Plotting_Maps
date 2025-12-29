# README
In this project, I show how to create nice maps form [OpenStreetMap](https://www.openstreetmap.org/) data.

![image](results\helsinki.png)

## Dependencies
This Project requires [Osmium](https://osmcode.org/osmium-tool/) for cropping the OSM .pbf files:

```
conda install conda-forge::osmium-tool
```

and a few Python Packages:

```
pip install pyrosm
pip install shapely
pip install pandas
pip isntall numpy
pip install matplotlib
```

## Download the OSM Data
The data can be downloaded from [Geofabrik](https://download.geofabrik.de/) in the .pbf format.  
To crop the .pbf file, use Osmium (This step is optional, but recomended, in order to reduce runtime while plotting maps). This is the example to extract a map of Helsinki.
```
osmium extract -b 24.44,60.07,25.40,60.41 finland-251214.osm.pbf -o helsinki.osm.pbf
```

## Downloading polygons of the Ocean/Sea
Within the OSM-data, polygons of the ocean/sea are not included (only the coastlines are included). If the ocean should be incuded in the map, this data has to be downloaded separately from [this page](https://osmdata.openstreetmap.de/data/water-polygons.html). Download the eater polygons in the WGS84 Projection and un-zip them.

## Plotting Maps
To plot the map, run the Notebook ```map.ipynb```. An example for plotting the map of Helsinki and Karlsruhe is given in ```map.ipynb``` notebook.  
There are a couple of options when plotting a map: 
* Choosing the Coordinates of the bottom left corner of the map
* Adjusting the scale  
    -> set the ```height``` parameter. This parameter sets the extent in latitudal direction. The unit of this parameter is degree (latitude). The extent in longitudal direction is calculated automatically according to the dimension of the map (default DIN A3 - horizontal).
* Including different types oft water/wetland/...  
    -> read the corresponding attributes and pass them as a argument to the ```plot_map()``` function
* Including buildings
    -> set the corresponding parameter
* Adding points/markers to the map
    -> pass the coordinates of the point to be plotted
* Editing the title
    -> set the city/country name as title/subtitle. If the style of the title should be updated, edit the corresponding line in the ```plot_map()``` function.
* Adjusting the format of the map (default is DIN A3 - horizontal as .pdf and .png file)  
    -> edit the corresponding line in the ```plot_map()``` function.
* Excluding Rails  
    -> edit the corresponding line in the ```plot_map()``` function.
* And more (be creative!)