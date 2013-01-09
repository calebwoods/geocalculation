# Geo Calculations in Ruby

!SLIDE

# Geo Calculations in Ruby

## By Caleb Woods

!SLIDE

# Things to Consider

* Libraries
* Projections
* Data Transport and Storage

!SLIDE

# Open Source Libraries

#### [GEOS](http://trac.osgeo.org/geos/)

* Geometry Calculation Engine
* `brew install geos`

#### [Proj.4](https://trac.osgeo.org/proj/)

* Cartographic Projection
* `brew install proj`

!SLIDE

# Ruby Gems

#### [RGeo](https://github.com/dazuma/rgeo)

* Geo spatial data library
* Relies on GEOS and Proj.4
* `gem install rgeo`

#### [RGeo GeoJSON](https://github.com/dazuma/rgeo-geojson)

* Parse and Create GeoJSON objects
* Uses official [GeoJSON Spec](http://www.geojson.org/geojson-spec.html)
* `gem install rgeo-geojson`

!SLIDE

# Other Libraries

#### [PostGIS](http://postgis.refractions.net/)

* Adds support for geographic objects in PostgreSQL
* Geo Spatial queries

!SLIDE

# Projections

* The earth is 3D
* 2D plane for Geometry calculations
* Projection in the translation

!SLIDE

# Common Projections

#### [Mercator](https://en.wikipedia.org/wiki/Mercator_projection)

* Used by Google Map and Apple Map
* Maintains shape, but not distances and areas

#### [Albers](https://en.wikipedia.org/wiki/Albers_projection)

* Equal Area Projection
* Maintains distances and areas, not shape

#### [UTM](https://en.wikipedia.org/wiki/Universal_Transverse_Mercator_coordinate_system)

* Similar to Mercator
* Divides earth into 60 "zones"

!SLIDE

# Albers vs UTM

```ruby
# Albers Equal Area Projection
small_field = 35.85907491318873 acres
large_field = 222.1015016221715 acres

# UTM Zone 15
small_field = 35.87419394539743 acres
large_field = 222.1926541039243 acres

# Deltas
small_field = 0.01511903220870181 acres
large_field = 0.09115248175280044 acres
```

!SLIDE

# UTM Zones

A Polygon can span a UTM zone border

```ruby
# Example of Polygon that spans UTM zones 15 and 16

# Calculated with Zone 15
304.64208165875334 acres

# Calculated with Zone 16
304.64176688085104 acres

# Split on Zone line and combined
304.6407631743717 acres
```


For a ~300 acre field largest delta is 13 thousands of an acre

!SLIDE

# Common Formats

* WKT
* KML
* GeoJSON

!SLIDE

# WKT Example

```ruby
"MULTIPOLYGON (((-90.4738990305427 36.4133434167215, ... )))"

```

!SLIDE

# GeoJSON Example


```javascript
{
    "type": "Polygon",
    "coordinates": [
      [
        [-90.4738990305427,36.4133434167215],
        [-90.473979105792,36.4106894643104],
        [-90.4773486100253,36.4108323810396],
        [-90.4738853926222,36.4135819451996],
        [-90.4738990305427,36.4133434167215]
      ],
      [
        [-90.4748795899079,36.4122608328937],
        [-90.4751238366577,36.4120176306662],
        [-90.4750501289294,36.4117390431922],
        [-90.4746434744808,36.4118880581738],
        [-90.4746528723027,36.4123276807651],
        [-90.4748795899079,36.4122608328937]
      ]
    ]
  }
```

!SLIDE

# GeoJSON Example

<div id="map" style="width: 500px; height: 500px"></div>

!SLIDE

# Questions?

!SLIDE

# Further Reading

#### Daniel Azuma's Blog

* [http://blog.daniel-azuma.com/](http://blog.daniel-azuma.com/)
* Writer and Maintainer of RGeo and PostGIS

#### RailsConf 2012 Geospatial Anlysis in Rails

* [My Notes](https://github.com/calebwoods/railsconf2012/blob/master/2012-04-23-03-geo-spatial.md)
* [Slides](http://daniel-azuma.com/railsconf2012)
* [Video](http://www.youtube.com/watch?v=QI0e2jkUbkk&list=PLF16D2F3A8469021E&index=49)

!SLIDE

# Presentation Tools

#### Slides: [Keydown](https://github.com/infews/keydown)

* Ruby Gem
* Write Slides in Markdown
* Generates [Deck.js](https://github.com/imakewebthings/deck.js) presentation


#### Maps: [Gmaps.js](http://hpneo.github.com/gmaps/)

* Sane interface to Google Maps JS API

!SLIDE

#Get the Slides

## [http://geo-calculation.calebwoods.com](http://geo-calculation.calebwoods.com)

