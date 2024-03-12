# Building Assemblies

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

For each assembly, the carbon intensity is determined by sampling the distribution of GWP values from typical assemblies at the 20th, 50th, and 80th percentile. These data are summarized in the table below.

<table><thead><tr><th width="243">Assembly</th><th>Low Carbon</th><th width="172">Best Practices</th><th>Conservative</th></tr></thead><tbody><tr><td><strong>Cladding</strong></td><td>3.0 kgCO2e/sf</td><td>8.8 kgCO2e/sf</td><td>14.3 kgCO2e/sf</td></tr><tr><td><strong>Glazing</strong></td><td>11.4 kgCO2e/sf</td><td>13.6 kgCO2e/sf</td><td>19.0 kgCO2e/sf</td></tr><tr><td><strong>Roofing</strong></td><td>5.3 kgCO2e/sf</td><td>7.7 kgCO2e/sf</td><td>14.0 kgCO2e/sf</td></tr><tr><td><strong>Tenant Fit Out</strong></td><td>4.0 kgCO2e/sf</td><td>7.6 kgCO2e/sf</td><td>13.3 kgCO2e/sf</td></tr><tr><td><strong>Hardscape</strong></td><td>4.4 kgCO2e/sf</td><td>5.9 kgCO2e/sf</td><td>7.2 kgCO2e/sf</td></tr></tbody></table>

#### Embodied Carbon in Interior Fit Out

Interior fit out is calculated on a per area basis for a proportion of the building's total area. Note that the dataset used to generate the quantities used in C.Scale is not sensitive to use type and is biased toward commercial interiors. These data include internal EHDD data and data from the CLF study on tenant fit outs in commercial office buildings.

#### Embodied Carbon in MEP

Embodied carbon in mechanical systems in evaluated at two specification levels—standard performance and high performance—and is dependent of the total square footage of the building. This approach, and the data used in C.Scale, follow from the CLF study on building mechanical systems.

#### Embodied Carbon in Solar Photovoltaic Arrays

Embodied carbon in solar photovoltaics arrays is calculated using values from the peer-reviewed literature. A citation to the current data source is available in in the [Reference Data Sources](../c.scale-tm-data-model/methodology/broken-reference/) section of this guide.

#### Embodied Carbon in Hardscape

All site area not designated as planted is assumed to be hardscaped. Hardscape emissions were calculated by EHDD using a parameterized streamlined LCA model of built from standard hardscape details. The 20th, 50th, and 80th percentile of the resulting distribution was sampled and used to define the specification levels in C.Scale.

#### Emissions from Landscape Maintenance

Emissions from landscape maintenance is calculated per planted area using values from the literature. A citation to the current data source is available in in the [Reference Data Sources](../c.scale-tm-data-model/methodology/broken-reference/) section of this guide.

### Example Data

For reference, below is a tabular summary of some of the data used in the US. Additional data (across all supported regions) is [available via API](../reference-data.md#reference-data-via-api).&#x20;

<table><thead><tr><th width="243">Assembly</th><th>Low Carbon</th><th width="172">Best Practices</th><th>Conservative</th></tr></thead><tbody><tr><td><strong>Cladding</strong></td><td>3.0 kgCO2e/sf</td><td>8.8 kgCO2e/sf</td><td>14.3 kgCO2e/sf</td></tr><tr><td><strong>Glazing</strong></td><td>11.4 kgCO2e/sf</td><td>13.6 kgCO2e/sf</td><td>19.0 kgCO2e/sf</td></tr><tr><td><strong>Roofing</strong></td><td>5.3 kgCO2e/sf</td><td>7.7 kgCO2e/sf</td><td>14.0 kgCO2e/sf</td></tr><tr><td><strong>Tenant Fit Out</strong></td><td>4.0 kgCO2e/sf</td><td>7.6 kgCO2e/sf</td><td>13.3 kgCO2e/sf</td></tr><tr><td><strong>Hardscape</strong></td><td>4.4 kgCO2e/sf</td><td>5.9 kgCO2e/sf</td><td>7.2 kgCO2e/sf</td></tr></tbody></table>

###

