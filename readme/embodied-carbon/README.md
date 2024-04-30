# Embodied Carbon

The overview of how C.Scale calculated embodied carbon is detailed on the [model structure](../model-structure.md) page. Below, we give additional detail about how C.Scale calculates emissions from all the assemblies and processes counted as part of a project's embodied carbon.

Every attempt has been made to ensure that C.Scale's results describe a typical building (i.e. a building similar to those in our database) whose characteristics match those you enter in the tool. However, unreported characteristics may make a particular building atypical in ways that it is beyond the scope of C.Scale to describe. For instance, the use of particularly high-carbon and high-cost finish materials (e.g., a building where all the millwork is in gold leaf) is not well-described by C.Scale. It is impossible to preemptively describe all cases where C.Scale might deviate from a particular building (the possibilities are literally endless) but, as your project progresses, we recommend that your project team remains aware of how any deviation from "typical" design will affect the project's climate goals.

### Embodied Carbon in Building Assembles

Building assemblies in C.Scale are evaluated on a per-area basis.

#### Emissions from Landscape Maintenance

Emissions from landscape maintenance is calculated per planted area using values from the literature. A citation to the current data source is available in in the [Reference Data Sources](../../c.scale-tm-data-model/methodology/broken-reference/) section of this guide.

### Construction Emissions

Emissions from the construction of the building are estimated as a proportion of A1-A3 emissions. Our expert review process established below ground construction as the major driver of A4-A5 emission. C.Scale estimates A4-A5 emissions as 10% of A1-A3 emissions when there is no below ground construction, and conservatively estimates the same at 18% when there is below ground construction.

This parameter can be customized for a scenario in the scenario customization screen.

### Emissions from Greenfield Development

When a user enters a site area, they have the option to select whether or not the site has been previously developed. If the site has been previously developed, C.Scale treats it as a "brownfield" site with no carbon sequestered in its soil and existing landscape. If the site has _not_ been previously developed, C.Scale treats it as a "greenfield" site with preexisting vegetation.

Developing a greenfield site releases carbon emissions from two sources: carbon stored in soil and carbon stored in biomass. C.Scale assumes that 100% of the carbon stored in topsoil is emitted as carbon dioxide. Data on carbon storage in soil is highly regional, and C.Scale uses FAO's Global Soil Organic Carbon data product for this calculation, taking the mean value at the zip code level.

To calculate emissions from the removal of above ground biomass, C.Scale treats the site as vegetated with regionally-specific "low carbon storage" plants at 50% of the site's carrying capacity. More information on how carbon storage in living biomass is calculated in C.Scale is available in the [Stored and Avoided Carbon](../stored-avoided-carbon.md#carbon-storage-in-landscapes-and-green-roofs) section of the methodology.
