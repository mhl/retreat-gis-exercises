# Introduction

- Why should you care about GIS?
     - Comes up in a lot of our work - e.g. you might need to prepare data
       for a new MapIt instance, reverse geocoding (what MapIt does: point
       to enclosing regions / names) is important for lots of our services.
     - The basic GIS model of the world:
           - Tables + geometric features

- What do we mean by shapefiles?
     - Strictly speaking, ESRI Shapefiles - made up of multiple files
     - Colloquially people use sometimes use "shapefile" to include
       KML files, GeoJSON, etc.

- By default QGIS does On-The-Fly transformations - see the button in
  the bottom right to change that. But each layer still has its own CRS
  (coordinate reference system). If you're saving to a Shapefile, you
  can choose what CRS it will use.

- Terminology:
     - Features - typically a polygon, multipolygon or a line
     - Layers - made up of multiple features, usually of the same type
       (e.g. representing the same administrative level)
     - Shapefiles - usually have a single layer (but can have
       multiple layers)

- Warning: in some of these exercises you'll need to toggle a layer
  into editing mode. If you save those changes (e.g. by saying "yes,
  save" when you toggle out of editing mode again) your changes are
  actually written to the shapefile the area is based on. This might
  be a suprise. For other warnings, see 'Random Things To Mention'
  below.

# Exercises

- Open and inspect shapefiles
     - Find the "Add Vector Layer" button
     - Try opening the Argentinian departments

- Displaying OpenStreetMap tiles as a background
     - Under Tile Server (XYZ)
     - https://www.qgis.org/en/site/forusers/visualchangelog218/index.html#feature-native-support-of-xyz-tile-layers

- Make them transparent
     - Layers Panel - right click, Properties -> Style

- Overlay multiple shapefiles
     - Open another one - the Argentinian provinces
     - Try moving them up and down in the Layers panel
     - Set transparency again

- Turn on and off visibility of layers
     - Checkbox in the Layers panel

- Use identify to click on an area and see its metadata
     - Pointer to a blue 'i' in a circle in the toolbar

- Find an area by its name
     - Open the attribute table for the layer

- Find an area by its ID
     - Similarly, use the attribute table

- Add a new metadata field called 'binky', which can hold strings of 10 characters
     - Layers Panel - right click, Properties -> Fields
     - n.b. this is the first point at which you'll need to toggle on
       editing of the area - may need to for most of the other exercises

- Populate the new metadata field based on an existing one
     - Open the attribute table, go to "field calculator"
     - Take an existing field's value, add a prefix and set binky to that

- Add a new field called area with the areas of each feature
      - What units is it in?

- Try creating a new polygon out of a hole in an existing one:
      - A suggested method:
           - Create a new Shapfile Layer (you have to specify an on-disk file)
           - Freehand draw a new polygon over the hole
           - Use "difference" to create the holes
           - Tidy up any stray bits with the help of the attribute table
           - Create a new layer make up of merging your new layer and the one with the hole
      - Two (or arguably one) other method here: https://www.youtube.com/watch?v=B1zdMPQUaNQ

## Optional exercise:

Recreate the "France is Bacon" image france-is-bacon.jpg

(This meme refers to: https://www.reddit.com/r/AskReddit/comments/dxosj/what_word_or_phrase_did_you_totally_misunderstand/c13pbyc/ )

# Random other things to mention:

- The QGIS "dissolve" function under Vector -> Geoprocessing tools is
  super slow. GRASS's v.dissolve, which you can find in the Processing
  Toolbox in QGIS is much faster.

- You might have to turn off the OpenStreetMap tile layer if it's
  slowing everything down - if the tile server is slow, or internet is
  laggy, it's frustrating waiting for those remote tiles to load.

- If something not working as you expect, then it's worth checking if
  the geometry of your polygons if valid (Vector -> Geometry Tools ->
  Check validity) and if not, fixing them with v.clean (Processing ->
  Toolbox -> v.clean). If you try again after fixing any errors,
  sometimes operations that appeared to do nothing before will
  suddenly work.

- Mark made four screencase with commonn GIS tasks we've had to do for
  the political data projects recently, which might be useful:
  https://www.youtube.com/channel/UCYKxTdhMrahBjua3q7Vul_A
