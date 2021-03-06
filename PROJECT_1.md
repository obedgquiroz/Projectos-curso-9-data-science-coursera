---
title: ""
output: 
  html_document: 
    keep_md: yes
---
<div style="text-align: center">
# The five most popular Colombian tourist cities among travelers
#### Made by: Obed Garcia Quiroz
#### Date: 18/7/2020
<div/>

<div style="text-align: left">
This is the solution to the first project of the Developing Data Products course of the data science specialization offered by Johns Hopkins University in coursera. For this project, using the leaflet library in RStudio, locate on a map the five most popular Colombian cities among travelers, according to the  [viala](https://viajala.com.co/blog/los-10-destinos-mas-buscados-en-colombia) web page, on the map, you can see the names of the cities ordered in ascending order, as they are located in the ranking mentioned above and you can also see the location of each city, so that when you click In the city location, the name of the city will appear, and if you click on this name, you will be able to access a web page that presents a tourist guide to the city.

<div/>

<!--html_preserve--><div id="htmlwidget-308179c671ed95cc35bd" style="width:912px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-308179c671ed95cc35bd">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[4.598326,10.423561,6.252239,11.228152,3.454998],[-74.075209,-75.539,-75.56825,-74.177355,-76.534631],null,null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["<a href='https://mapaturistico.net/colombia/bogota/'>Bogotá<\/a>","<a href='https://colombia.travel/es/cartagena-de-indias'>Cartagena<\/a>","<a href='https://colombia.travel/es/medellin'>Medellín<\/a>","<a href='https://visitsantamarta.com/?gclid=EAIaIQobChMI6Zfo6drX6gIVNfC1Ch2m4QqqEAAYASAAEgK7DfD_BwE'>Santa Marta<\/a>","<a href='https://mapaturistico.net/colombia/cali/'>Cali<\/a>"],null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addCircleMarkers","args":[[4.598326,10.423561,6.252239,11.228152,3.454998],[-74.075209,-75.539,-75.56825,-74.177355,-76.534631],10,null,null,{"interactive":true,"className":"","stroke":true,"color":["blue","green","orange","red","black"],"weight":5,"opacity":0.5,"fill":true,"fillColor":["blue","green","orange","red","black"],"fillOpacity":0.2},null,null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addLegend","args":[{"colors":["blue","green","orange","red","black"],"labels":["Position 1: Bogotá","Position 2: Cartagena","Position 3: Medellín","Position 4: Santa Marta","Position 5: Cali"],"na_color":null,"na_label":"NA","opacity":0.5,"position":"bottomright","type":"unknown","title":null,"extra":null,"layerId":null,"className":"info legend","group":null}]}],"limits":{"lat":[3.454998,11.228152],"lng":[-76.534631,-74.075209]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

<div style="text-align: center"> 
Below you can see the code with which the map was created

<div/>
<div style="text-align: left">

```r
library(leaflet)
lat <- c(4.598326,10.423561,6.252239,11.228152,3.454998)
lng <- c(-74.075209,-75.539000,-75.568250,-74.177355,-76.534631)
place_name <- c("Position 1: Bogotá","Position 2: Cartagena","Position 3: Medellín","Position 4: Santa Marta","Position 5: Cali")
colors <- c("blue","green","orange","red","black")
links_sites <- c("<a href='https://mapaturistico.net/colombia/bogota/'>Bogotá</a>",
                 "<a href='https://colombia.travel/es/cartagena-de-indias'>Cartagena</a>",
                 "<a href='https://colombia.travel/es/medellin'>Medellín</a>",
                 "<a href='https://visitsantamarta.com/?gclid=EAIaIQobChMI6Zfo6drX6gIVNfC1Ch2m4QqqEAAYASAAEgK7DfD_BwE'>Santa Marta</a>",
                 "<a href='https://mapaturistico.net/colombia/cali/'>Cali</a>")
my_map <- data.frame(lat,lng,place_name,colors,links_sites)
top5 <- my_map %>% leaflet() %>% 
        addTiles() %>%
        addMarkers(lng = lng, lat =lat,popup = my_map$links_sites)%>%
        addCircleMarkers(color = my_map$colors)%>%
        addLegend("bottomright",colors = my_map$colors, labels = place_name)
top5
```
<div/>

### References
<div style="text-align: left">
1- https://viajala.com.co/blog/los-10-destinos-mas-buscados-en-colombia

2- https://mapaturistico.net/colombia/bogota

3- https://colombia.travel/es/cartagena-de-indias

4- https://colombia.travel/es/medellin

5- https://visitsantamarta.com/?gclid=EAIaIQobChMI6Zfo6drX6gIVNfC1Ch2m4QqqEAAYASAAEgK7DfD_BwE

6- https://mapaturistico.net/colombia/cali/")
<div/>
