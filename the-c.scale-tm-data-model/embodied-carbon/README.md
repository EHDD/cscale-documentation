# Whole Life Carbon Assessment

C.Scale generates detailed time series estimates of a building's embodied carbon emissions and organizes those emissions into the appropriate life cycle stages.&#x20;

## A1-3: Upstream Product Emissions

A1-A3 emissions are calculated from a bill of materials (e.g., life cycle inventory) inferred from the user's description of a building. The exact method for generating that bill of materials and performing calculation of A1-A3 emissions vary by building assembly.&#x20;

For each contributor $$i$$, embodied emissions in life cycle stages A1-A3 are assessed with the following expression:

$$
{Assessed\ emissions}_i=\ A\ast x_i\ast c_i
$$

Where A is the total building area, $$x_i$$ is the quantity of the contributor $$i$$ per building area, and $$c_i$$ is the carbon intensity per unit of the contributor $$i$$.

For example, a 10,000 square foot building may use 4 pounds of reinforcing steel per square foot of floor area, and the reinforcing steel may have a carbon intensity of 500 grams (0.5 kilograms) of carbon dioxide-equivalent emissions per pound of steel (values for illustrative purposes only). Taking the product of these three hypothetical quantities yields the contribution of reinforcing steel to that building’s embodied carbon emission:

$$
10,000\ sf\ast4\ \frac{lbs\ rebar}{sf}\ast0.5\ \frac{kg\ CO_2e}{lb\ rebar}=20,000\ kg\ CO_2e
$$

Other pages in this section detail the calculation of A1-A3 emissions from [structure](structure.md), [envelope](envelope.md), and [other building assemblies](other-building-assemblies.md).&#x20;

## A4-5: Construction Emissions

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

To calculate emissions from the removal of above ground biomass, C.Scale treats the site as vegetated with regionally-specific "low carbon storage" plants at 50% of the site's carrying capacity. More information on how carbon storage in living biomass is calculated in C.Scale is available in the [Stored and Avoided Carbon](stored-avoided-carbon.md#carbon-storage-in-landscapes-and-green-roofs) section of the methodology.

### A5.3: Jobsite Waste

For each material and building assembly, C.Scale assumes a percentage of the installed total is wasted during construction. For all waste incurred during A5.3, we calculate A1-A4 and C2-C4 emissions for the wasted material and assign it to A5.3 emission for that material's category. C.Scale's default (conservative!) waste rates are included in the table below.&#x20;

<table><thead><tr><th width="355">Building Material/Assembly</th><th>Waste Rate</th></tr></thead><tbody><tr><td>Concrete (all types)</td><td>5%</td></tr><tr><td>Reinforcing Steel</td><td>3%</td></tr><tr><td>Hot-Rolled Steel</td><td>10%</td></tr><tr><td>Cold-Formed Steel</td><td>10%</td></tr><tr><td>Dimensional Lumber</td><td>10%</td></tr><tr><td>Ply and OSB Products</td><td>15%</td></tr><tr><td>Engineered Timber</td><td>10%</td></tr><tr><td>CMU Block</td><td>5%</td></tr><tr><td>CMU Mortar</td><td>15%</td></tr></tbody></table>

## B Phase: Use Stage

The use stage includes all emissions from the operation of the building from the completion of construction until the end of the reference service period.&#x20;

### B1: In-Use Emissions

Fugitive emissions from annual refrigerant leakage, as well as refrigerant leakage for equipment replaced during the operating life of the building,  are counted in life cycle stage B1. This is treated in detail in the documentation section on [Refrigerant Emissions](refrigerant-emissions.md).

Annual carbon storage in landscape is also included in this phase.

### B2-B5: Replacement and Refurbishment

C.Scale uses a simplified model of replacement and refurbishment. For all materials in the C.Scale model, the emissions associated with these replacement and refurbishment—including manufacturing, transportation, and installation of the new materials, as well as end-of-life emissions for any removed materials—are assigned to the year(s) determined by the user-selected refurbishment period.&#x20;

### B6: Operational Energy use

Life cycle stage B6 includes operational emissions from energy use. This is treated in detail in the documentation section on [Operational Carbon](operational-carbon.md).&#x20;

## C Phase: End of Life

Data from life cycle stages C1-C4 cover the process from building demolition to final disposition of materials, as input to recycling, waste recovery processes, or to a landfill.&#x20;

### C1: Demolition

C.Scale assumes that business-as-usual demolition practices will 30% of the emissions used to construct the same asset. This value can be overridden with a project-specific value. C1 also includes emissions from refrigerant leakage of all removed equipment.

### C2: Transportation to End of Life Processing

By default, C.Scale assumes that all waste travels 50 miles (80 km) to the nearest waste processing facility by truck with a 50% load. This distance can be overridden by user inputs.&#x20;

### C3: Waste Processing for Recycling, Reuse, and Recovery

Data for life cycle stages C3 are collected from regionally-appropriate industry-average EPDs.

### C4: Landfill Disposal Emissions

Data for life cycle stages C3 are collected from regionally-appropriate industry-average EPDs. Where data is not available in the US, EPA Warm is used a reference data source.&#x20;

## D Phase: Benefits Beyond the System Boundary

The D phase of a whole life carbon assessment includes environmental benefits and burdens beyond the system boundary. D phase emissions are typically reported separately from life cycle impacts.

### D1: Potential Benefits from Recycling, Recovery, and Reuse

Data for life cycle stages D1 are collected from regionally-appropriate industry-average EPDs. Where this data was not available, we assume D1 to be zero.&#x20;

### D2: Benefits from Exported Energy

Once production from an onsite solar array has exceeded annual electricity use, C.Scale assumes all additional energy generated by the array displaces generation of electricity by the electrical grid. The avoided emissions from surplus onsite energy generation are calculated as the emissions that this displaced energy would have incurred.

This method assumes that there is no curtailment of PV production, and that the carbon emissions of grid electricity when solar energy is produced is substantially similar to the annual average emissions. In locations with a high proportion of solar on the grid, _these assumptions will not hold_ and skepticism of C.Scale's calculation of avoided emissions is warranted. Read more about curtailment in [this publication ](https://www.nrel.gov/docs/fy14osti/60983.pdf)(pdf) from there National Renewable Energy Laboratory.

The assumption of displacement generation will not hold true in all locations, and some skepticism of this estimate is encouraged. Two interrelated situations where C.Scale's assumptions of displaced generation will not hold are when:

* Daytime (i.e., when solar is available) emissions from the electrical grid are significantly lower than the national average.
* Surplus energy generation is expected to be curtailed by the utility. For an overview of curtailment in the United States, we recommend [this report from NREL](https://www.nrel.gov/docs/fy14osti/60983.pdf) (pdf).

The generation of excess energy by an onsite solar photovoltaic array displaces the generation an equivalent amount of electricity from the utility grid. This is calculated as follows:

$$
Avoided\ carbon\ emissions=\ \sum_{t=1}^{m}\ e_{t}\ast c_{t}
$$

Where $$e_{t}$$ is the excess energy in kWh generated in year $$t$$ and $$c_{t}$$ is the carbon intensity of the electrical grid per unit demand in year $$t$$. This method assumes that there is no curtailment of PV production, and that the carbon emissions of grid electricity when solar energy is produced is substantially similar to the annual average emissions. In locations with a high proportion of solar on the grid, curtailment is likely and skepticism of C.Scale's calculation of avoided emissions is warranted.

If you are interested in further analysis of hourly emissions, [please reach out](mailto:epic@ehddd.com).
