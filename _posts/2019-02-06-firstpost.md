---
layout: post
title: Making the blog in NYC
author: michelle
coordinates: -73.985234,40.691411
place: Brooklyn, NY
img: assets/images/nyc.jpg
category: "done"
---


![NYC Skyline at night]({{site.url}}/{{page.img}})


Right now, we're packing up the Brooklyn apartment and saying see-ya-later to a lot of good friends in NYC. Lots of people ask us where the road-trip is taking us, so I thought it would be good to make a map. I also thought it would be good to make a blog with the map to keep people posted about our journey.

I have never really wrote, let alone made, a blog before. A while ago, I kept a [Wordpress blog](https://michellegetsoutside.wordpress.com/) about getting outdoors while living in NYC. I also wrote a couple [Medium posts](https://medium.com/@michellemho) about some bits of code that helped me. Occasionally, I contributed to my [company's blog](https://carto.com/blog/predicting-nyc-collisions/). But that was about it.

I started with jotting and drawing some ideas down on paper. I wanted the map of our road-trip to be the focus of the blog. And the posts themselves would appear as pop-ups on top of the map. I didn't want to put a lot of effort into maintaining it while on the road. The goal was to write a new post in markdown, tag it with a longitude-latitude coordinate, and the map-blog could auto-update accordingly.

I chose [Jekyll](https://jekyllrb.com/) because I have noticed other people make blogs with Jekyll and it seemed simple but able to do what I needed. Jekyll helps you transform plain text into static websites and blogs.

Jekyll processes files with something called "front matter"-- which is a snippet of YAML at the top of the file. The variables defined in front matter can be accessed using Liquid, a templating language, which Jekyll understands as anything between curly brackets like: `{% raw %}{{ location }}{% endraw %}`, and even logic/control flow between curly brackets with percent signs like: `{% raw %}{% for post in posts %}{% endraw %}`. I had a hunch that I could add the longitude-latitude coordiates in the "front matter" and figure out some way to access them elsewhere using Jekyll for the map.

Like so:	

```
---
title: Making the blog in NYC
coordinates: -73.985234,40.691411
---
```

After I had the bare-bones of a Jekyll blog up and running, I started searching for methods to process a GeoJSON with Jekyll. I was really stoked to see that [Katy Decorah](https://katydecorah.com) had already come up with a method for using [Jekyll to cook up a geojson file](https://katydecorah.com/code/jekyll-geojson/). This was exactly what I needed.

GeoJSON is a format standard for encoding a variety of geographic data structures. There's a blog post written by Tom MacWright entitled ["More than you ever wanted to know about GeoJSON"](https://macwright.org/2015/03/23/geojson-second-bite.html), in case you want to read more about it. Basically, GeoJSON boils down to coordinates-- longitude-latitude pairs that, when weaved together correctly, can create wonderful things like `Point`, `LineString`, `Polygon`, `MultiPoint`, `MultiLineString`, and `MultiPolygon`.

With a little help from Katy and the power of Liquid for loops, I eventually had the GeoJSON file I needed based on some pre-created posts. What next? I opted to use [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/api/), which is a JavaScript library that uses WebGL to render interactive maps with vector tiles client-side. I also used [CARTO VL](https://carto.com/developers/carto-vl/), another JavaScript library that sits well with Mapbox GL, for styling.

Then I brought it to my fellow Recursers for feedback. Thanks to so many friends with excellent eyes for detail and design, I got more ideas of how to make the mapblog better: add a suggestion box, add a legend (duh), add instructions or a summary, add a line between points to show the route, add more color, change the navigation bar, add 3D elevation, etc. etc. I'm still working on tweaking the blog as we go, but I think we're ready to hit the road now.

Thanks for reading! See you on the road.