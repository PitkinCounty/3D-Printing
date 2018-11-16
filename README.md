# 3D Printing Scripts

This repository holds scripts used to prepare data from ArcGIS for 3D printing.

## Inventory
* phstl.py ([copied from another repo](https://github.com/anoved/phstl))
  * convert a **.TIF** file into a 3D surface **.STL**
* blender.py
  * convert a 3D surface **.STL** (no thickness) to a solid body **-3D.STL**

## Workflow
* Export GeoTiff Height File (*.tif) from ArcGIS
  * File size should not exceed 10 MB
	* breaks in the model should have their value set to 4000 ft
* run *.tif through phstl.py to generate *.stl surface

        python phstl.py -m 5000 example.tif example.stl
	* Ideal file size < 100 MB
* run *.stl through blender.py to generate *-3D.stl solid model

        blender untitled.blend --background --python printv4.py C:\OSGeo4W64\example.stl
	* Ideal file size < 100 MB
	* should modify to name the file '3D-*.stl'?
* import *-3D.stl into slicing software to generate *.gcode for 3D printer
  * We use ideaMaker

## Acknowledgements
* [anoved/phstl](https://github.com/anoved/phstl)
