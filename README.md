Converting latitude/longitude for point / polygon co-ordinates to Landsat WRS-2 paths/rows

# Credit http://blog.rtwilson.com/converting-latitudelongitude-co-ordinates-to-landsat-wrs-2-pathsrows/
# NOTE: you can jump to my contribution below as here you already has shapefile and only need to install GDAL/ORG and Shapely for python.

This code finds the Landsat WRS-2 path/row which contains a given latitude/longitude co-ordinate.

# Dependencies #
* [GDAL/ORG](https://pypi.python.org/pypi/GDAL/)
* [Shapely](https://pypi.python.org/pypi/Shapely)
* Landsat WRS-2 Path/Row Shapefiles - download from [USGS site](http://landsat.usgs.gov/tools_wrs-2_shapefile.php), you want `wrs2_descending.zip`

# How to use #
	>>> import get_wrs
	>>> conv = ConvertToWRS()
	>>> conv.get_wrs(50.14, -1.7)
	[{'path': 202, 'row': 25}]
	>>> conv.get_wrs(50.14, -1.43)
	[{'path': 201, 'row': 25}, {'path': 202, 'row': 25}]

More details are available in the docstrings (try `ConvertToWRS?` or `conv.get_wrs?` in IPython) and in my original [blog post](#).

# License #
This code is released under the 3-clause BSD license (see the LICENSE file for more information).


# Here is my contribution (Bang Pham Huu - b.phamhuu@jacobs-university.de)
# I've added a function named getWrsByPolygon and you can add a pairs of array (longitude, latitude) as in EarthExplorer http://earthexplorer.usgs.gov/ can get all the WRS paths which intersect with your polygon.
# Example: 

conv = ConvertToWRS();
pairs = [(10.3052, 47.1449),(14.6558, 46.8752),(11.9531, 44.8081), (7.7783, 44.9181)];
conv.getWrsByPolygon(pairs);

# which returns a list of WRS path which interects your polyline of your polygon
{'path': 194, 'row': 27},
{'path': 194, 'row': 28},
{'path': 194, 'row': 29},
{'path': 192, 'row': 27},
{'path': 192, 'row': 28},
{'path': 192, 'row': 29},
{'path': 190, 'row': 27},
{'path': 190, 'row': 28},
{'path': 195, 'row': 28},
{'path': 195, 'row': 29},
{'path': 193, 'row': 27},
{'path': 193, 'row': 28},
{'path': 193, 'row': 29},
{'path': 191, 'row': 27},
{'path': 191, 'row': 28},
{'path': 191, 'row': 29}
