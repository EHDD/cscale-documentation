# Embodied Carbon

The overview of how C.Scale calculated embodied carbon is detailed on the [model structure](../model-structure.md) page. Below, we give additional detail about how C.Scale calculates emissions from all the assemblies and processes counted as part of a project's embodied carbon.

Every attempt has been made to ensure that C.Scale's results describe a typical building (i.e. a building similar to those in our database) whose characteristics match those you enter in the tool. However, unreported characteristics may make a particular building atypical in ways that it is beyond the scope of C.Scale to describe. For instance, the use of particularly high-carbon and high-cost finish materials (e.g., a building where all the millwork is in gold leaf) is not well-described by C.Scale. It is impossible to preemptively describe all cases where C.Scale might deviate from a particular building (the possibilities are literally endless) but, as your project progresses, we recommend that your project team remains aware of how any deviation from "typical" design will affect the project's climate goals.

## A1-3: Upstream Product Emissions

A1-A3 emissions are calculated from a bill of materials (e.g., life cycle inventory) inferred from the user's description of a building. The exact method for generating that bill of materials and performing calculation of A1-A3 emissions vary by building assembly.&#x20;

Other pages in this section detail the calculation of A1-A3 emissions from [structure](structure.md), [envelope](envelope.md), and [other building assemblies](other-building-assemblies.md).&#x20;

## A4-5: Construction Emissions

Emissions from the construction of the building are estimated as a proportion of A1-A3 emissions. Our expert review process established below ground construction as the major driver of A4-A5 emission. C.Scale estimates A4-A5 emissions as 10% of A1-A3 emissions when there is no below ground construction, and conservatively estimates the same at 18% when there is below ground construction.

This parameter can be customized for a scenario in the scenario customization screen.

### A4: Transportation of Materials to Site

All materials accounted for in A1-A3 must be transported to site. C.Scale defaults to emission factors from the ASHRAE 240P draft guidance in table 6.5.2.1. These are conservative estimates of emissions per quantity material. These data include a 0.5 return trip factor.&#x20;

### A5.1: Pre-Construction Demolition

Pre-construction demolition emissions are calculated per floor area of the demolished building, using a default factor of 35 kgCO2e/m2. This is a data-scarce category. Where project-specific data is available, this default can be overridden by the user.

### A5.2: Jobsite Activities

Emissions from construction activities and land use change are included in A5.2.&#x20;

#### Construction Activities&#x20;

Construction activities include the use of tools, fuel, equipment, and energy on the building site. This includes site preparation, installation of materials, and other jobsite activities. As a default value, C.Scale assumes the carbon intensity of construction activities to be 40 kgCO2e/m2 of project floor area. Where project-specific data is available, this default can be overridden by the user.

Emissions from construction activities are proportioned out to categories by the proportion of their A1-A3 emissions. For example, if a building's envelope accounts for 25% of its total A1-A3 emissions, C.Scale assumes the A5.2 construction activities associated with enveloped are 10 kgCO2e/m2, 25% of the default value of 40kgCO2e/m2. Or, if the user has entered a custom carbon intensity for A5.2, the model will calculate 25% of that value instead.

#### Emissions from Greenfield Development

Land use change emissions from greenfield development are counted in A5.2. When a user enters a site area, they have the option to select whether or not the site has been previously developed. If the site has been previously developed, C.Scale treats it as a "brownfield" site with no carbon sequestered in its soil and existing landscape. If the site has _not_ been previously developed, C.Scale treats it as a "greenfield" site with preexisting vegetation.

Developing a greenfield site releases carbon emissions from two sources: carbon stored in soil and carbon stored in biomass. C.Scale assumes that 100% of the carbon stored in topsoil is emitted as carbon dioxide. Data on carbon storage in soil is highly regional, and C.Scale uses FAO's Global Soil Organic Carbon data product for this calculation, taking the mean value at the zip code level.

To calculate emissions from the removal of above ground biomass, C.Scale treats the site as vegetated with regionally-specific "low carbon storage" plants at 50% of the site's carrying capacity. More information on how carbon storage in living biomass is calculated in C.Scale is available in the [Stored and Avoided Carbon](../stored-avoided-carbon.md#carbon-storage-in-landscapes-and-green-roofs) section of the methodology.

### A5.3: Jobsite Waste

For each material and building assembly, C.Scale assumes a percentage of the installed total is wasted during construction. For all waste incurred during A5.3, we calculate A1-A4 and C2-C4 emissions for the wasted material and assign it to A5.3 emission for that material's category. C.Scale's default (conservative!) waste rates are included in the table below.&#x20;

<table><thead><tr><th width="355">Building Material/Assembly</th><th>Waste Rate</th></tr></thead><tbody><tr><td>Concrete (all types)</td><td>5%</td></tr><tr><td>Reinforcing Steel</td><td>3%</td></tr><tr><td>Hot-Rolled Steel</td><td>10%</td></tr><tr><td>Cold-Formed Steel</td><td>10%</td></tr><tr><td>Dimensional Lumber</td><td>10%</td></tr><tr><td>Ply and OSB Products</td><td>15%</td></tr><tr><td>Engineered Timber</td><td>10%</td></tr><tr><td>CMU Block</td><td>5%</td></tr><tr><td>CMU Mortar</td><td>15%</td></tr></tbody></table>

&#x20;
