Mapping in R
================

> ## Learning Objectives
>
> * Learn about types of spatial data
> * Load and plot spatial data into R
> * Customize maps with basic functions

Firs things first, let's load the packages we will need for this workshop.

All the maps will be plotted based on `ggplot` framework, so we need that one.
Spatial objects will be loaded into R in the SF format, so it helps us to have
the `sf` package loaded, to give us some functions to work with them.

``` {r}
library("ggplot2")
library("sf")
```

## Goals

For this workshop, our goal will be to build three maps:
1) a simple map of contiguous United States, showing the states boundaries;
2) a close-up map of the New York City area, showing the subway stops
3) an elevation map of Manhattan

## Map 1: contiguous United States

Some of the data we will be using today is from a collection called [Natural Earth](https://www.naturalearthdata.com/).

Reading states data:

```{r}
states <- read_sf('data/us_state_boundaries/ne_110m_admin_1_states_provinces.shp')
```

Plotting states:

```{r}
ggplot()+geom_sf(data = states)
ggplot()+geom_sf(data = states)+theme_minimal()
```

Reading and plotting countries with states:

```{r}
countries <- read_sf('data/world_countries/ne_110m_admin_0_countries.shp')
ggplot()+geom_sf(data = countries)+geom_sf(data = states)

```

Reducing the extent to continental US only:

```{r}
ggplot()+geom_sf(data = countries)+geom_sf(data = states)+
  coord_sf(xlim = c(-130.327727,-50.774995), ylim = c(24.321161,52.537236), expand = FALSE)
```

Saving the map:

```{r}
ggsave('us_states.tif', width = 7, height = 9)
```

## Map 2: New York City with subway stops

Steps:
1. Load the boroughs shapefile
2. Load the subway stations shapefile
3. Plot both shapefiles together using ggplot and geom_sf

Try and do this map on your own first before seeing the code below.

Reading boroughs and subway points data:

```{r}
boroughs <- read_sf('data/nyc_boroughs/nyc_boroughs.shp')
subway <- read_sf('data/nyc_subway_stations/nyc_subway_stations.shp')
```

Plotting:

```{r}
ggplot()+geom_sf(data=boroughs)+geom_sf(data=subway)
```

Saving the map:

```{r}
ggsave('nyc_subway_stops', width = 7, height = 9)
```

## Map 3: Manhattan Elevation Map

Loading raster library:

```{r}
library(raster)
```

Reading raster:

```{r}
```

Transforming raster in dataframe:

```{r}
```

Plotting raster:

```{r}
```

## Customizing our maps

```{r}
library('ggspatial')
```

Customizing background color:

```{r}
```

Customizing subway stops color:

```{r}
```

Customizing axis labels and title

```{r}
```

Setting themes

```{r}
```

Adding scale and north arrows

```{r}
```
