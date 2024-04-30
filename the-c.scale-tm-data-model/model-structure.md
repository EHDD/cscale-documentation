# Model Structure

## C.Scale calculates whole life carbon emissions

C.Scale integrates embodied, operational, and landscape carbon emission assessment into a single model. By taking a 'whole carbon' view, C.Scale prevents burden shifting and ensures that a project team has the information necessary to target the most impactful carbon reductions.

C.Scale uses GWP-100 characterization factors.

## C.Scale describes typical buildings

Every attempt has been made to ensure that C.Scale's results describe a typical building (i.e. a building similar to those in our database) whose characteristics match those you enter in the tool. However, unreported characteristics may make a particular building atypical in ways that it is beyond the scope of C.Scale to describe.&#x20;

For instance, the use of particularly high-carbon and high-cost finish materials (e.g., a building where all the millwork is in gold leaf) is not well-described by C.Scale. It is impossible to preemptively describe all cases where C.Scale might deviate from a particular building (the possibilities are literally endless) but, as your project progresses, we recommend that your project team remains aware of how any deviation from "typical" design will affect the project's climate goals.

### Embodied Carbon [↗](model-structure.md#calculating-embodied-carbon)

A1-A3 emissions are calculated from a bill of materials (e.g., life cycle inventory) inferred from the user's description of a building. The exact method for generating that bill of materials and performing calculation of A1-A3 emissions vary by building assembly.&#x20;

### Operational Carbon [↗](operational-carbon.md)

The operational emissions of the project are assessed annually and summed across all years before the target date. The equation is similar to the equation for embodied emissions, with two key differences: first, the quantity x is substituted for the energy use intensity (EUI) e; second, the equation is a double summation, once across all the fuel types in the building and again across all years between the building’s completion and the target year. The total operational emissions assessed by C.Scale are represented by this expression:

$$
Operational\ carbon\ emissions=\ \sum_{t=1}^{m}\ \sum_{j=1}^{o}\ A\ast e_{tj}\ast c_j
$$

For m total years between the building’s completion and the target year and across o fuel types, where A is the total building area, $$e_{tj}$$ is the energy use per building area (EUI) in year $$t$$ of fuel $$j$$, and $$c_{tj}$$ is the carbon intensity per energy unit in year $$t$$ of fuel $$j$$.

Carbon emissions associated with electricity are derived from NREL's Cambium model. Onsite fossil fuel use is assumed to be natural gas. The carbon emissions of natural gas are assessed with a 2.4% leakage rate. Fuel oil emissions account for N20 and CH4 emissions. Characterization of non-CO2 emissions is determined with the GWP100 factors published in IPCC AR6.

#### Refrigerant Emissions

In C.Scale, fugitive emissions from refrigerant leakage are categorized as operational emissions and counted in life cycle stage B1.

### Stored and Avoided Carbon [↗](stored-avoided-carbon.md)

In C.Scale, landscaping and the use of structural timber contribute to biogenic carbon storage. Carbon storage in structural materials is assessed once in the first year of the project, and landscape sequestration is assessed each year. Biogenic carbon sequestration is evaluated with the following expression:

$$
Carbon\ Storage=x_i\ast C_i+\ \sum_{t=1}^{m}\ A_k\ast C_k
$$

Where $$x_i$$ is the amount of carbon-sequestering timber structural material $$i$$, $$C_i$$ is the carbon sequestration per unit $$i$$,$$A_k$$ is the area A of carbon-sequestering planting type k, and $$C_k$$ is the carbon sequestration in year $$t$$ per area of planting $$k$$.

The generation of excess energy by an onsite solar photovoltaic array displaces the generation an equivalent amount of electricity from the utility grid. This is calculated as follows:

$$
Avoided\ carbon\ emissions=\ \sum_{t=1}^{m}\ e_{t}\ast c_{t}
$$

Where $$e_{t}$$ is the excess energy in kWh generated in year $$t$$ and $$c_{t}$$ is the carbon intensity of the electrical grid per unit demand in year $$t$$. This method assumes that there is no curtailment of PV production, and that the carbon emissions of grid electricity when solar energy is produced is substantially similar to the annual average emissions. In locations with a high proportion of solar on the grid, curtailment is likely and skepticism of C.Scale's calculation of avoided emissions is warranted.

## C.Scale is a Time Series model

In the built environment, it is essential to understand the [time value of carbon](https://carbonleadershipforum.org/the-time-value-of-carbon/). To this end, C.Scale uses time series data to analyze carbon emissions across a building's life. For each year in the analysis period (defined by the project's [time horizon](../#time-horizon)), C.Scale estimates all emissions occurring in that year.

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

## Building Geometry in C.Scale

C.Scale's calculations are based on area and material takeoffs from simple building geometry. A diagram of this building geometry is provided below.

<figure><img src="../.gitbook/assets/Diagrams.png" alt=""><figcaption></figcaption></figure>

## C.Scale customizable and extensible

C.Scale is built as a series of modules, each connected to the others and tasked with a specific set of calculations. These modules are added or expanded in response to the requests of users.

The C.scale model's assumptions and background data can be overriden or refined through additional inputs. This allows for the addition of project-specific data where it is available while maintaining the C.Scale model for calculating all other parts of the project's carbon footprint. For more information on how this works, check out our Swagger docs or reach out for a conversation.
