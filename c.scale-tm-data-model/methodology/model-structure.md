# Model Structure

## c.scale calculates whole life carbon emissions

c.scale integrates embodied, operational, and landscape carbon emission assessment into a single model. By taking a 'whole carbon' view, c.scale prevents burden shifting and ensures that a project has the information necessary to target the most impactful carbon reductions.

c.scale uses GWP-100 characterization factors.

### Calculating Embodied Carbon [↗](model-structure.md#calculating-embodied-carbon)

For each contributor $$i$$, embodied emissions are assessed with the following expression:

$$
{Assessed\ emissions}_i=\ A\ast x_i\ast c_i
$$

Where A is the total building area, $$x_i$$ is the quantity of the contributor $$i$$ per building area, and $$c_i$$ is the carbon intensity per unit of the contributor $$i$$.

For example, a 10,000 square foot building may use 4 pounds of reinforcing steel per square foot of floor area, and the reinforcing steel may have a carbon intensity of 500 grams (0.5 kilograms) of carbon dioxide-equivalent emissions per pound of steel (values for illustrative purposes only). Taking the product of these three hypothetical quantities yields the contribution of reinforcing steel to that building’s embodied carbon emission:

$$
10,000\ sf\ast4\ \frac{lbs\ rebar}{sf}\ast0.5\ \frac{kg\ CO_2e}{lb\ rebar}=20,000\ kg\ CO_2e
$$

In each section of its model, c.scale sums the assessed emission of many individual contributors. While simple summation is acceptable in some cases, some materials will be replaced before the target date. For these materials, the emissions are assigned to the year(s) in which they’re replaced, and a multiplier is added to the total summation. The total embodied emissions assessed by c.scale are represented by this expression:

$$
Total\ embodied\ carbon\ emissions=\ \sum_{i=1}^{n}\ A\ast x_i\ast c_i\ast(1+r_i)\
$$

For n number of contributors to the embodied emissions, where A is the total building area, $$x_i$$ is the quantity of the contributor $$i$$ per building area, $$c_i$$ is the carbon intensity per unit of the contributor $$i$$, and $$r_i$$ is the number of replacements of the contributor $$i$$ before the target date.

### Calculating Operational Carbon [↗](model-structure.md#calculating-operational-carbon)

The operational emissions of the project are assessed annually and summed across all years before the target date. The equation is similar to the equation for embodied emissions, with two key differences: first, the quantity x is substituted for the energy use intensity (EUI) e; second, the equation is a double summation, once across all the fuel types in the building and again across all years between the building’s completion and the target year. The total operational emissions assessed by c.scale are represented by this expression:

$$
Operational\ carbon\ emissions=\ \sum_{t=1}^{m}\ \sum_{j=1}^{o}\ A\ast e_{tj}\ast c_j
$$

For m total years between the building’s completion and the target year and across o fuel types, where A is the total building area, $$e_{tj}$$ is the energy use per building area (EUI) in year $$t$$ of fuel $$j$$, and $$c_{tj}$$ is the carbon intensity per energy unit in year $$t$$ of fuel $$j$$.

Carbon emissions associated with electricity are derived from NREL's Cambium model. Onsite fossil fuel use is assumed to be natural gas. The carbon emissions of natural gas are assessed with a 2.4% leakage rate. Fuel oil emissions account for N20 and CH4 emissions. Characterization of non-CO2 emissions is determined with the GWP100 factors published in IPCC AR6.

#### Refrigerant Emissions

In c.scale, fugitive emissions from refrigerant leakage are categorized as operational emissions. They are counted in life cycle stage B1.

### Calculating Stored and Avoided Carbon [↗](model-structure.md#calculating-stored-and-avoided-carbon)

In c.scale, landscaping and the use of structural timber contribute to biogenic carbon storage. Carbon storage in structural materials is assessed once in the first year of the project, and landscape sequestration is assessed each year. Biogenic carbon sequestration is evaluated with the following expression:

$$
Carbon\ Storage=x_i\ast C_i+\ \sum_{t=1}^{m}\ A_k\ast C_k
$$

Where $$x_i$$ is the amount of carbon-sequestering timber structural material $$i$$, $$C_i$$ is the carbon sequestration per unit $$i$$,$$A_k$$ is the area A of carbon-sequestering planting type k, and $$C_k$$ is the carbon sequestration in year $$t$$ per area of planting $$k$$.

The generation of excess energy by an onsite solar photovoltaic array displaces the generation an equivalent amount of electricity from the utility grid. This is calculated as follows:

$$
Avoided\ carbon\ emissions=\ \sum_{t=1}^{m}\ e_{t}\ast c_{t}
$$

Where $$e_{t}$$ is the excess energy in kWh generated in year $$t$$ and $$c_{t}$$ is the carbon intensity of the electrical grid per unit demand in year $$t$$. This method assumes that there is no curtailment of PV production, and that the carbon emissions of grid electricity when solar energy is produced is substantially similar to the annual average emissions. In locations with a high proportion of solar on the grid, curtailment is likely and skepticism of c.scale's calculation of avoided emissions is warranted.

## c.scale is a time series model

In the built environment, it is essential to understand the [time value of carbon](https://carbonleadershipforum.org/the-time-value-of-carbon/). To this end, c.scale uses time series data to analyze carbon emissions across a building's life. For each year in the analysis period (defined by the project's [time horizon](./#time-horizon)), c.scale estimates all emissions occurring in that year.

**In the first year**, the following emissions are always calculated:

* Embodied emissions in construction materials (life cycle stages A1-A3)
* Construction site emissions (life cycle stages A4-A5)
* Storage of biogenic carbon in timber structural components (life cycle stage D)

**In each year**, the following emissions are always calculated:

* Operational carbon emissions from onsite fossil fuel use (life cycle stage B6)
* Operational carbon emissions from onsite electricity use (life cycle stage B6)
* Emissions from landscape maintenance, when applicable (life cycle stage B2)

**In only some years,** the following emissions are always calculated:

* Replacement and refurbishment of hardscape (life cycle stages B3-B5)
* Replacement and refurbishment of the building envelope (life cycle stages B3-B5)
* Replacement and refurbishment of interior fit-out (life cycle stages B3-B5)
* Replacement and refurbishment of MEP and PV systems (life cycle stages B3-B5)

## Units in EPIC

Units describe data. When we compare 2 kilograms to 2 square feet, the units help us to understand which is a measure of mass and which of area. In EPIC, where data are used both to calculate and present the result of carbon reduction measures, the interpretation of units is essential to the evaluation and comparison of carbon reduction strategies. EPIC uses a set of units specific to the tool's objectives. The units included in EPIC, and the consequences of their inclusion, are described below.

#### Area Units

* **Square feet.** As the geographic scope of c.scale is currently limited to the United States, area is described in square feet and emissions evaluated on a per square foot basis. In much of the literature on carbon emissions from buildings, however, emissions are compared on a per square meter basis. To compare results from c.scale to results on a per square meter basis, unit conversion is necessary.

#### Time Units

* **Years.** EPIC evaluates emissions on an annual basis. The choice of an annual basis means that EPIC cannot describe intra-annual variations in carbon emissions from electricity, such as seasonal or daily variations. This approach is standard practice, but precludes inclusion of important carbon reduction measures such as demand response or battery storage in EPIC.

**Energy and Power Units**

* **kBtu/sf/yr.** This unit describes Energy Use Intensity (EUI), the quantity of energy required by a building per square foot per year. 1 kBtu is equivalent to 1,000 British thermal units and 293 Watt-hours. In EPIC, energy use is measured at the project site (site EUI) and not at the generation source.
* **kW.** The nameplate capacity of a solar array is described in kilowatts (kW), a unit of power.

#### Carbon Emissions Units

* **Metric tons of CO2-equivalent** (tCO2e)**.** Following conventions across the literature, carbon emissions are described in metric units. One metric ton is equal to 1000 kilograms and 2,204 pounds. EPIC measures emissions of "carbon dioxide equivalents," using emission factors published by the IPCC to include emissions of extremely potent greenhouse gases (such as methane and nitrous oxide) based on their comparability to carbon dioxide emissions.

## EPIC and c.scale are customizable and extensible

c.scale is built as a series of modules, each connected to the others and tasked with a specific set of calculations. These modules are added or expanded in response to the requests of users.

Many parts of the EPIC model (in v2.0.0 and beyond) can be customized or overriden by the user. This allows for the addition of project-specific data where it is available while maintaining the EPIC model for calculating all other parts of the project's carbon footprint. The customizations available in the open access web app are described [here](../../epic-web-application/carbon-reduction-measures/customize-scenario.md). To request additional features, [contact us](mailto:epic@ehdd.com).
