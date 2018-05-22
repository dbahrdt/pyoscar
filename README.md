# Setup
## Cloning
```Bash
git clone --recursive https://github.com/dbahrdt/pyoscar
´´´

## Updating
```Bash
git --rebase pull && git submodule update && git submodule foreach --recursive git submodule update
´´´

## Pre-requisites
 - Python 3
 - Boost-Python
 - zlib-dev
 - CGAL
 - cryptopp
 - icu


## building
```Bash
mkdir build
cd build
cmake ../
make
´´´

# Sample data

Sample data files can be found here:

http://data.oscar-web.de/

For the germany data set, download all files from:
http://data.oscar-web.de/archive/de/

place them in a single folder:

export OSCAR_DATA_PATH=your_path

cd ${OSCAR_DATA_PATH}
wget http://data.oscar-web.de/archive/de/index
wget http://data.oscar-web.de/archive/de/kvstore
wget http://data.oscar-web.de/archive/de/textsearch

# Using pyoscar
## Load the package:
```python
import pyoscar
´´´

## Load the data
```
import pyoscar
import os

cmp = pyoscar.OsmCompleter()
cmp.setAllFilesFromPrefix(os.environ['OSCAR_DATA_PATH'])
cmp.energize()
´´´

## Issuing a query
```
result = cmp.query("@highway in Stuttgart")
´´´

## Getting all cells
```
cells = result.cells()
´´´

## Getting all item ids
```
items = result.items()
´´´

## Get the real item
```
store = cmp.store()
for itemid in items:
	item = store.at(itemid)
	#do something?
´´´