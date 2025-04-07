# Site and Landscape

C.Scale allows users to approximate the carbon emissions and sequestration associated with site and landscape features. All site area not occupied by the building footprint is assumed to be a combination of hardscape (sidewalks, site walls, paving, parking) and planted areas.

## Construction Emissions and Land Use Change

Developing a "greenfield" site (one that has not been previously developed) will release carbon dioxide into the atmosphere through the disturbance of carbon stocks in soils and vegetation. Emissions from site disturbance and land use change are reported in life cycle stage A5.2 - Jobsite Activities.

When a user enters a site area, they have the option to select whether or not the site has been previously developed. If the site has been previously developed, C.Scale treats it as a "brownfield" site with no carbon sequestered in its soil and existing landscape. If the site has not been previously developed, C.Scale treats it as a "greenfield" site with preexisting vegetation.

Developing a greenfield site releases carbon emissions from two sources: carbon stored in soil and carbon stored in biomass. C.Scale assumes that 100% of the carbon stored in topsoil is emitted as carbon dioxide. Data on carbon storage in soil is highly regional, and C.Scale uses FAO's Global Soil Organic Carbon data product for this calculation, taking the mean value at the zip code level.

To calculate emissions from the removal of above-ground biomass, C.Scale treats the site as vegetated with regionally-specific "low carbon storage" plants at 50% of the site's carrying capacity.&#x20;

More information on how carbon storage in living biomass is calculated in C.Scale is available in the[ Stored Carbon](https://docs.cscale.io/the-c.scale-tm-data-model/whole-life-carbon/stored-avoided-carbon#carbon-storage-in-landscapes-and-green-roofs) section of the methodology.

## Embodied Carbon in Paving Assemblies

All site area not designated as planted is assumed to be hardscaped. Hardscape emissions were calculated by C.Scale using a parameterized streamlined LCA model built from standard hardscape details. The 20th, 50th, and 80th percentile of the resulting distribution was sampled and used to define emission ranges in C.Scale.

A custom carbon intensity of paving assemblies or other landscape features can be entered by passing a kgCO2e per area (sf or m2, depending on the unit system) value directly to the API. The hardscape area is assumed to be the total site area, less the building footprint and plantings.&#x20;

## Emissions from Landscape Maintenance

Emissions from landscape maintenance are calculated per planted area using values from the literature. Maintenance emissions are reported annually in the life cycle stage B2-5. A citation to the current data source is available in the [Reference Data Sources](../reference-data.md) section of this guide.



## Landscape Stored Carbon

For details on quantifying biogenic carbon storage in landscape areas, see [Stored Carbon](stored-avoided-carbon.md).&#x20;

\
