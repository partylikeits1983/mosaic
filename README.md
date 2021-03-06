# mosaic

This utility can be used to generate [photo-mosaic](http://en.wikipedia.org/wiki/Photographic_mosaic) images. 

There is **no cheating** with semi-transparent overlays, tile tinting, or repeating images (by default).

This script is focused on **maximum accuracy** (using scikit's Mean Squared Error). This is a pixel-by-pixel comparison to produce the best match. Other libraries simplify this by only comparing against a limited (averaged, antialiased) number of pixels from the original sector, or just compare against the histograms. Producing large, highly detailed mosaics takes a lot of time! 

To make a mosaic of a film, specify the path to the file. Using the jupyter notebook you can specify the film you would like to extract images from and use those images to generate the photo-mosaic. 

This repository is an updated version of [dvdtho/python-photo-mosaic](https://github.com/dvdtho/python-photo-mosaic) and was created since the previous version no longer works with the current version of scikit-image. 


**Prerequisites**
<pre>pip install scikit-image numpy pillow</pre>

**Usage**
```python
create_mosaic(
    source_path="/path/to/source/image", 
    target="/path/to/output/image", 
    tile_paths=tile_paths,
    tile_ratio=800/800, # Crop tiles to be height/width ratio
    tile_width=300, # Tile will be scaled
    enlargement=5, # Mosiac will be this times larger than original
    reuse=False, # Should tiles be used multiple times?
    color_mode='RGB',  # RGB (color) L (greyscale)
) 
```

### Sample: 2001: A Space Odyssey
A still every second yields about 9,000 images. ~5,000 unique stills are matched and used below. This mosaic took over 4 hours to render on an intel i7 CPU.

------------

![Sample](doc/2001e.jpeg)

Feel free to contact me if you would like the highest resolution version.


------------
Changed from original project (https://github.com/codebox/mosaic):  
*   ability to not reuse tiles 
*   increased quality of match by comparing against whole tile images 
*   increased quality of mosaic by starting with the center instead of top left
*   ability to input color mode

Tested with:
*   Python 3.8.10
*   numpy==1.19.5
*   Pillow==9.0.0
*   scikit-image==0.19.1
