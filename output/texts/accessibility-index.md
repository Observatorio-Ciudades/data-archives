Last-update: 11/08/21

# Accessibility index

## Accessibility
In order to analyze accesibility in a context of COVID-19 we've created and index based on the distance to different commodities and basic services. As we explored this concept during a pandemic, we searched for the distance to pharmacies, supermarkets and hospital, which our team identified as vital spaces for groceries, access to medication and medical attention. To calculate this distances we used the urban morphology seen through the nodes and edges of the city roads which were downloaded using [OSMnx](https://osmnx.readthedocs.io/en/stable/). Each stablishment was analyzed indepently with specific distance parameters:
+ Pharmacies: up to 300m is considered a proper service area and beyond 1000m inadequate.
+ Supermarkets: up to 300m is considered a proper service area and beyond 1000m inadequate.
+ Hospitals: up to 1000m is considered a proper service area and beyond 5000m inadequate.

## Creating an index
Taking into account the distance parameters we applied a function that changed each distance to a value between 0 and 1. Given the characteristics of the data we opted to use a sigmoidal function adapted for each ammenity.
[Sigmoidal-function](output/figures/accessibility_index/img/plot.png)

## Accessibility index: Population vs territory
The calculated index is divided in two: territory and population. Both are based on the distance to ammenities and the sigmoidal function described previously and presented using [H3](https://h3geo.org/) hexagons. The territorial index takes into account the nodes within each hexagon. Giving a higher weight to those hexagons with more nodes.
[Nodes-edges-within-hexagons](output/figures/accessibility_index/img/territory.png)

On the other hand, the population index only takes into account those hexagons that contain population data. This lets us analyze the whole territory and the areas were the population live.
[Comparison-territory-vs-population](output/figures/accessibility_index/img/index_city.png)

### Querétaro
We can see the accessibility index for Querétaro in the following image. In it the holes without hexagons represent urban areas without nodes. This means that no distance can be calculated within that area. Now, analyzing the results we can see the distribution of the urban area, and, whithin it, the zones that are more consolidated, which tend to be around the historical center of the city. While new developments tend to have a lower accessibility index. We can see that there are a lot of hexagons with accessibility indexes near to 0, this is because it is calculated for the whole municipality.

[index-queretaro](output/figures/accessibility_index/img/index_qto.png)

### Ciudad de México
A different dynamic can be found in Mexico City. Its urban development and location within the Metropolitan Area of the Valley of Mexico results in a different distribution for the index, compared to Querétaro or even other mexican cities. With highly consolidated areas towards the center and north of the municipalities and lower index values in the south.

[index-cdmx](output/figures/accessibility_index/img/index_cdmx.png)
