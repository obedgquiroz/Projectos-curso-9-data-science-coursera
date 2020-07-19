---
title: ""
output: 
  html_document: 
    keep_md: yes
---
<div style="text-align: center">
# Top five tourist sites in Colombia
#### Made by: Obed Garcia Quiroz
#### Date: 18/7/2020
<div/>

<div style="text-align: left">
Below  are the five most popular Colombian cities among travelers, according to the [viala](https://viajala.com.co/blog/los-10-destinos-mas-buscados-en-colombia) web page, on the map, you can see the names of the cities ordered in ascending order, according to whether they are located in the aforementioned ranking and you can also see the location of each city, so that when you click on the location of the city, the name of the city will appear, and if you click on this name, you will be able to access a web page that presents a tourist guide to the city.
<div/>


```
## Assuming "lng" and "lat" are longitude and latitude, respectively
```

<!--html_preserve--><div id="htmlwidget-1aeb576531e43fcf7048" style="width:912px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-1aeb576531e43fcf7048">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[4.598326,10.423561,6.252239,11.228152,3.454998],[-74.075209,-75.539,-75.56825,-74.177355,-76.534631],null,null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["<a href='https://mapaturistico.net/colombia/bogota/'>Bogotá<\/a>","<a href='https://www.kayak.com.co/Cartagena.26923.guide'>Cartagena<\/a>","<a href='https://www.medellincuenta.com/irj/go/km/docs/pccdesign/informativo/DesarrolloEconomico/Shared%20Content/Documentos/2018/Gui%CC%81a%20Turi%CC%81stica.compressed.pdf'>Medellín<\/a>","<a href='https://visitsantamarta.com/?gclid=EAIaIQobChMI6Zfo6drX6gIVNfC1Ch2m4QqqEAAYASAAEgK7DfD_BwE'>Santa Marta<\/a>","<a href='https://mapaturistico.net/colombia/cali/'>Cali<\/a>"],null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addCircleMarkers","args":[[4.598326,10.423561,6.252239,11.228152,3.454998],[-74.075209,-75.539,-75.56825,-74.177355,-76.534631],10,null,null,{"interactive":true,"className":"","stroke":true,"color":["blue","green","orange","red","black"],"weight":5,"opacity":0.5,"fill":true,"fillColor":["blue","green","orange","red","black"],"fillOpacity":0.2},null,null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addLegend","args":[{"colors":["blue","green","orange","red","black"],"labels":["Position 1: Bogotá","Position 2: Cartagena","Position 3: Medellín","Position 4: Santa Marta","Position 5: Cali"],"na_color":null,"na_label":"NA","opacity":0.5,"position":"bottomright","type":"unknown","title":null,"extra":null,"layerId":null,"className":"info legend","group":null}]}],"limits":{"lat":[3.454998,11.228152],"lng":[-76.534631,-74.075209]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

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
                 "<a href='https://www.kayak.com.co/Cartagena.26923.guide'>Cartagena</a>",
                 "<a href='https://www.medellincuenta.com/irj/go/km/docs/pccdesign/informativo/DesarrolloEconomico/Shared%20Content/Documentos/2018/Gui%CC%81a%20Turi%CC%81stica.compressed.pdf'>Medellín</a>",
                 "<a href='https://visitsantamarta.com/?gclid=EAIaIQobChMI6Zfo6drX6gIVNfC1Ch2m4QqqEAAYASAAEgK7DfD_BwE'>Santa Marta</a>",
                 "<a href='https://mapaturistico.net/colombia/cali/'>Cali</a>")
my_map <- data.frame(lat,lng,place_name,colors,links_sites)
top5 <- my_map %>% leaflet() %>% 
        addTiles() %>%
        addMarkers(lng = lng, lat =lat,popup = my_map$links_sites)%>%
        addCircleMarkers(color = my_map$colors)%>%
        addLegend("bottomright",colors = my_map$colors, labels = place_name)
```

```
## Assuming "lng" and "lat" are longitude and latitude, respectively
```

```r
top5
```
<div/>
