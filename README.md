# 3D-printable Fagaras mountains
These are notes on how this data was obtained and processed.

## Concepts and terms
The whole process, with acronyms, is described at https://edutechwiki.unige.ch/en/3D_printing_of_digital_elevation_models.\
Concepts:
- DEM = Digital Elevation Model, either DTM or DSM
- DTM = Digital Terrain Model, includes just terrain
- DSM = Digital Surface Model, includes terrain but also buildings/etc.
- Raster = height map stored as equal rectangular blocks, an "image" (e.g. formats: GeoTIFF, HGT) -> most widely accessible (but buildings less likely)
- Vector = data stored as point-clouds / meshes / (contour) lines -> could contain buildings


## 1. Download terrain models
Source 1: OpenTopography.org - abbrebiated "OT", resolution 30m
- https://opentopography.org/learn/3D_printing
- directly in TIFF file format

Source 2: ViewFinderPanoramas.org - abbereviated "VFP", resolution ???
- https://opentopography.org/learn/3D_printing
- used this data source, though is horizontally stretched (compressed horizontally to 66% ??)
- in HGT file format

## 2. Convert to Blender-openable heightmap
- open files relevant files: `N45E024.hgt` and `N45E025.hgt` in QGIS application (further named "layers")
- change the displayed altitude range to 600m-2500m (layer properties > Synology > Min / Max)
- export each layer (east+west) as TIFF: right-click > Export > Save As > Rendered image + GeoTIFF
- open east+west TIFFs in an image editor (e.g. GIMP) to merge them
    - delete unwanted black pixels (min-altitude)
    - (optional) crop any unwanted areas (e.g. neighbouring mountains & hills)
    - (optional) create a border around printed

## 3. convert to 3D object
- use the heightmaps in Blender using the Displace modifier
- filter out polygons that have 0-altitude
- create a base

## 4. 3D-print the 3D object