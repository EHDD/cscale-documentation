# Embodied Carbon

The overview of how C.Scale calculated embodied carbon is detailed on the [model structure](../model-structure.md) page. Below, we give additional detail about how C.Scale calculates emissions from all the assemblies and processes counted as part of a project's embodied carbon.

Every attempt has been made to ensure that C.Scale's results describe a typical building (i.e. a building similar to those in our database) whose characteristics match those you enter in the tool. However, unreported characteristics may make a particular building atypical in ways that it is beyond the scope of C.Scale to describe. For instance, the use of particularly high-carbon and high-cost finish materials (e.g., a building where all the millwork is in gold leaf) is not well-described by C.Scale. It is impossible to preemptively describe all cases where C.Scale might deviate from a particular building (the possibilities are literally endless) but, as your project progresses, we recommend that your project team remains aware of how any deviation from "typical" design will affect the project's climate goals.

### Embodied Carbon in Building Assembles

Building assemblies in C.Scale are evaluated on a per-area basis.

#### Embodied Carbon in the Building Envelope

The building envelope in divided into three components: opaque cladding, glazing, and roofing. The area of each is calculated based on user inputs for building floor area, number of floors, floor-to-floor height window-to-wall ratio (WWR), and building perimeter. C.Scale makes a preliminary estimate of floor-to-floor height, WWR, and building perimeter (assuming a square building) which the user can refine in the "overrides" panel in the base case tab.

$$
Envelope \ area = Perimeter \ * \ Floor \ Height \ * \ Number \ of \ floors
$$

$$
Glazing \ area = WWR \ * \ Perimeter \ * \ Floor \ Height \ * \ Number \ of \ floors
$$

$$
Cladding \ area = (1-WWR) \ * \ Perimeter \ * \ Floor \ Height \ * \ Number \ of \ floors
$$

$$
Roof \ area = Above \ Ground \ Floor \ Area
$$

For each of the three envelope categories, the carbon intensity is determined by sampling the distribution of GWP values from typical assemblies at the 20th, 50th, and 80th percentile. These data are summarized in the table below.

| Assembly     | Low Carbon     | Best Practices | Conservative   |
| ------------ | -------------- | -------------- | -------------- |
| **Cladding** | 3.0 kgCO2e/sf  | 8.8 kgCO2e/sf  | 14.3 kgCO2e/sf |
| **Glazing**  | 11.4 kgCO2e/sf | 13.6 kgCO2e/sf | 19.0 kgCO2e/sf |
| **Roofing**  | 5.3 kgCO2e/sf  | 7.7 kgCO2e/sf  | 14.0 kgCO2e/sf |

All three parameters can be customized for a scenario in the scenario customization screen.

Additional data on envelope assemblies are accessible via C.Scale's [API](broken-reference). For access to these data, [please reach out](mailto:epic@ehdd.com?subject=API).

#### Embodied Carbon in Interior Fit Out

Interior fit out is calculated on a per area basis for a proportion of the building's total area. Note that the dataset used to generate the quantities used in C.Scale is not sensitive to use type and is biased toward commercial interiors. These data include internal EHDD data and data from the CLF study on tenant fit outs in commercial office buildings.

| Assembly           | Low Carbon    | Best Practices | Conservative   |
| ------------------ | ------------- | -------------- | -------------- |
| **Tenant Fit Out** | 4.0 kgCO2e/sf | 7.6 kgCO2e/sf  | 13.3 kgCO2e/sf |

This parameter can be customized for a scenario in the scenario customization screen.

#### Embodied Carbon in MEP

Embodied carbon in mechanical systems in evaluated at two specification levels—standard performance and high performance—and is dependent of the total square footage of the building. This approach, and the data used in C.Scale, follow from the CLF study on building mechanical systems.

| Building Area       | Standard Performance | High Performance |
| ------------------- | -------------------- | ---------------- |
| < 25,000 sf         | 4.11 kgCO2e/sf       | 6.17 kgCO2e/sf   |
| 25,000 - 79,999 sf  | 4.58 kgCO2e/sf       | 5.76 kgCO2e/sf   |
| 80,000 - 300,000 sf | 5.93 kgCO2e/sf       | 6.02 kgCO2e/sf   |
| > 300,000 sf        | 4.83 kgCO2e/sf       | 6.79 kgCO2e/sf   |

Base case buildings in C.Scale are always assumed to have a standard performance system. <mark style="background-color:yellow;">Scenarios that achieve an EUI reduction of more than 50% the benchmark are assumed to have a high performance system.</mark> The EUI reduction threshold is not directly editable in the public-facing web app, but can be redefined in the API.

This parameter can be customized for a scenario in the scenario customization screen.

#### Embodied Carbon in Solar Photovoltaic Arrays

Embodied carbon in solar photovoltaics arrays is calculated using values from the peer-reviewed literature. A citation to the current data source is available in in the [Reference Data Sources](../../c.scale-tm-data-model/methodology/broken-reference/) section of this guide.

#### Embodied Carbon in Hardscape

All site area not designated as planted is assumed to be hardscaped. Hardscape emissions were calculated by EHDD using a parameterized streamlined LCA model of built from standard hardscape details. The 20th, 50th, and 80th percentile of the resulting distribution was sampled and used to define the specification levels in C.Scale.

| Assembly      | Low Carbon    | Best Practices | Conservative  |
| ------------- | ------------- | -------------- | ------------- |
| **Hardscape** | 4.4 kgCO2e/sf | 5.9 kgCO2e/sf  | 7.2 kgCO2e/sf |

#### Emissions from Landscape Maintenance

Emissions from landscape maintenance is calculated per planted area using values from the literature. A citation to the current data source is available in in the [Reference Data Sources](../../c.scale-tm-data-model/methodology/broken-reference/) section of this guide.

### Construction Emissions

Emissions from the construction of the building are estimated as a proportion of A1-A3 emissions. Our expert review process established below ground construction as the major driver of A4-A5 emission. C.Scale estimates A4-A5 emissions as 10% of A1-A3 emissions when there is no below ground construction, and conservatively estimates the same at 18% when there is below ground construction.

This parameter can be customized for a scenario in the scenario customization screen.

### Emissions from Greenfield Development

When a user enters a site area, they have the option to select whether or not the site has been previously developed. If the site has been previously developed, C.Scale treats it as a "brownfield" site with no carbon sequestered in its soil and existing landscape. If the site has _not_ been previously developed, C.Scale treats it as a "greenfield" site with preexisting vegetation.

Developing a greenfield site releases carbon emissions from two sources: carbon stored in soil and carbon stored in biomass. C.Scale assumes that 100% of the carbon stored in topsoil is emitted as carbon dioxide. Data on carbon storage in soil is highly regional, and C.Scale uses FAO's Global Soil Organic Carbon data product for this calculation, taking the mean value at the zip code level.

To calculate emissions from the removal of above ground biomass, C.Scale treats the site as vegetated with regionally-specific "low carbon storage" plants at 50% of the site's carrying capacity. More information on how carbon storage in living biomass is calculated in C.Scale is available in the [Stored and Avoided Carbon](../stored-avoided-carbon.md#carbon-storage-in-landscapes-and-green-roofs) section of the methodology.
