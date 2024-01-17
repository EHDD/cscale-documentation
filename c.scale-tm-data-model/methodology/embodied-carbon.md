# Embodied Carbon

The overview of how EPIC calculated embodied carbon is detailed on the [model structure](model-structure.md) page. Below, we give additional detail about how EPIC calculates emissions from all the assemblies and processes counted as part of a project's embodied carbon.

Every attempt has been made to ensure that EPIC's results describe a typical building (i.e. a building similar to those in our database) whose characteristics match those you enter in the tool. However, unreported characteristics may make a particular building atypical in ways that it is beyond the scope of EPIC to describe. For instance, the use of particularly high-carbon and high-cost finish materials (e.g., a building where all the millwork is in gold leaf) is not covered by EPIC. It is impossible to preemptively describe all cases where EPIC might deviate from a particular building (the possibilities are literally endless) but, as your project progresses, we recommend that your project team remains aware of how any deviation from "typical" design will affect the project's climate goals.

### Embodied Carbon in Building Structure

Embodied carbon in building structure is calculated in two stages: a bill of structural materials is estimated and carbon intensities are applied to those materials.

EPIC's estimation of embodied carbon in a building's structure is modeled based on statistical analysis of completed buildings. This approach is preferable to a first-principles approach—i.e. assuming an optimized structural grid for a given geometry—because it greatly reduces truncation error and better describes the variation present in real buildings.

<table><thead><tr><th width="233">Structural System</th><th>Description</th></tr></thead><tbody><tr><td><strong>Wood Frame</strong></td><td>A structural system comprised of dimensional lumber, plywood sheathing, and reinforced concrete cores.</td></tr><tr><td><strong>Steel Frame</strong></td><td>A structural system comprised of columns, beams, girders, and decking constructed from steel structural members connected with rigid or pin joints.</td></tr><tr><td><strong>Reinforced Concrete</strong></td><td>A structural system comprised of columns, beams, and slabs of concrete reinforced with steel that provides tensile strength.</td></tr><tr><td><strong>Mass Timber</strong></td><td>A structural system comprised of massive beams, panels, and columns, often assembled by aggregating many smaller timber elements.</td></tr><tr><td><strong>Hybrid Steel-Timber</strong></td><td>A mass timber structure with a large proportion of structural steel. These structures are common when the aesthetics and performance of a mass timber structure are pursued but the structural grid or building form isn't rigorously optimized for an all-timber design.</td></tr><tr><td><strong>Hybrid Concrete-Steel (High-Rise)</strong></td><td>A structural system that combines rigid steel frames with concrete columns, beams, and slabs. These hybrid structures are more materially intensive and may be used when there are significant seismic loads, in high-rise buildings, or for programs with very high live or environmental loads.</td></tr><tr><td><strong>Wood Frame over Concrete Podium</strong></td><td>A wood frame building with one or more of the lower floors in reinforced concrete. Typically, a five-story podium building has one floor in concrete and six- or seven-story buildings have two.</td></tr></tbody></table>

#### Calculating a Bill of Materials

EPIC uses a suite of machine learning models to estimate quantities of major structural materials in typical buildings. These models were trained from an EHDD database of structural quantities in completed buildings (n > 1000) assembled from both internal and public sources. The models are updated regularly as new data becomes available.&#x20;

These weighted data is used to train a statistical model for each structural material in each structural system. These models are trained on five predictors:

* Use category (one-hot encoded)
* Primary structural material
* Total GFA
* Number of floors
* GFA/floor

These methods for calculating a structural bill of materials have been reviewed by colleagues at [MKA](https://www.mka.com/), [Carbon Leadership Forum](https://carbonleadershipforum.org/), and confidential collaborators (to be announced in 2024) with additional comment from colleagues at [Arup](https://www.arup.com/). If you are a structural engineer or data scientist interested in providing further review of our modeling pipeline, [please reach out](mailto:epic@ehdd.com?subject=Review).

> We anticipate journal publication of our modeling pipeline in 2024. In the meantime, please direct questions regarding modeling methodology to Jack at j.rusk@ehdd.com

#### Carbon Intensities of Structural Materials

**Carbon intensity is the amount of CO2-equivalent emissions per unit of material**. For structural materials, carbon intensity information is drawn from a variety of sources. In all cases, EPIC uses GWP-100 characterization factors. These sources are documented in the [Reference Data Sources](broken-reference/) section of this guide.

The three specifications available in EPIC—low carbon, best practices, and conservative—correspond to the 20th, 50th, and 80th percentile of emissions for that material. These estimates _do not_ correspond to a specific EPD, as there are many options for achieving a certain level of performance. Most carbon intensities for structural materials in EPIC are national averages, as material supply chains for major structural materials are typically national (or global) in coverage.

Concrete emissions, on the other hand, as assessed at the zip code level. Concrete is a regional material, rarely traveling more than 25 miles between production and use. Additionally, the relatively large number of concrete EPDs available in the United States ([80,000+](https://buildingtransparency.org/ec3) at time of writing) supports a regional approach to measuring concrete emissions.

Where concrete EPDs are not available, the specification levels in EPIC are set using NRMCA published minimum, average, and maximum values in line with the method outlined in the CLF's [2021 Material Baseline Report](https://carbonleadershipforum.org/2021-material-baseline-report/), included the use of the uncertainty method put forward by Building Transparency. _<mark style="color:green;">(Coming soon: background concrete data alignment with CLF's 2023 Material Baseline Report)</mark>_

In locations where concrete EPDs are available, EPIC sets the specification levels for concrete by sampling the distribution of GWP values from available concrete EPDs at the 20th, 50th, and 80th percentile. Location specific data on concrete are collected via the [OpenEPD API](https://openepd.buildingtransparency.org/) and compiled in a GIS platform. High-strength concrete (7-10 kSI) carbon intensities correspond to Building Transparency's [OpenImpact](https://www.buildingtransparency.org/programs/openimpact/) data on 55.2 MPa concrete.

{% tabs %}
{% tab title="United States" %}
<table><thead><tr><th width="199">Structural Material</th><th>Low Carbon</th><th width="174">Best Practices</th><th>Conservative</th></tr></thead><tbody><tr><td><strong>Concrete, 3-4 kSI</strong></td><td><em>Location-specific</em></td><td><em>Location-specific</em></td><td><em>Location-specific</em></td></tr><tr><td><strong>Concrete, 5-6 kSI</strong></td><td><em>Location-specific</em></td><td><em>Location-specific</em></td><td><em>Location-specific</em></td></tr><tr><td><strong>Concrete, 7-10 kSI</strong></td><td>0.16 kgCO2e/kg</td><td>0.18 kgCO2e/kg</td><td>0.19 kgCO2e/kg</td></tr><tr><td><strong>Reinforcing Steel</strong></td><td>0.9 kgCO2e/kg</td><td>1.1 kgCO2e/kg</td><td>1.16 kgCO2e/kg</td></tr><tr><td><strong>Structural Steel</strong></td><td>0.9 kgCO2e/kg</td><td>1.1 kgCO2e/kg</td><td>1.2 kgCO2e/kg</td></tr><tr><td><strong>Steel Deck</strong></td><td>1.7 kgCO2e/kg</td><td>2.2 kgCO2e/kg</td><td>2.4 kgCO2e/kg</td></tr><tr><td><strong>Lumber</strong></td><td>0.09 kgCO2e/kg</td><td>0.16 kgCO2e/kg</td><td>0.21 kgCO2e/kg</td></tr><tr><td><strong>Plywood/OSB</strong></td><td>0.36 kgCO2e/kg</td><td>0.51 kgCO2e/kg</td><td>0.73 kgCO2e/kg</td></tr><tr><td><strong>Engineered Wood</strong></td><td>0.19 kgCO2e/kg</td><td>0.25 kgCO2e/kg</td><td>0.36 kgCO2e/kg</td></tr></tbody></table>

<figure><img src="../../.gitbook/assets/concrete regionalization-01.png" alt=""><figcaption><p>EPD regionalization. Note that EPDs are typically concentrated in metro areas, and the background NRMCA data for that region may have either a higher or a lower carbon intensity.</p></figcaption></figure>
{% endtab %}

{% tab title="Canada" %}
_coming soon_
{% endtab %}
{% endtabs %}

For access to EPIC's location-specific data or BoM datasets, [please reach out](mailto:epic@ehdd.com?subject=Review).

### Embodied Carbon in Building Assembles

Building assemblies in EPIC are evaluated on a per-area basis.

#### Embodied Carbon in the Building Envelope

The building envelope in divided into three components: opaque cladding, glazing, and roofing. The area of each is calculated based on user inputs for building floor area, number of floors, floor-to-floor height window-to-wall ratio (WWR), and building perimeter. EPIC makes a preliminary estimate of floor-to-floor height, WWR, and building perimeter (assuming a square building) which the user can refine in the "overrides" panel in the base case tab.

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

Additional data on envelope assemblies are accessible via EPIC's [API](../access-epic-via-api.md). For access to these data, [please reach out](mailto:epic@ehdd.com?subject=API).

#### Embodied Carbon in Interior Fit Out

Interior fit out is calculated on a per area basis for a proportion of the building's total area. Note that the dataset used to generate the quantities used in EPIC is not sensitive to use type and is biased toward commercial interiors. These data include internal EHDD data and data from the CLF study on tenant fit outs in commercial office buildings.

| Assembly           | Low Carbon    | Best Practices | Conservative   |
| ------------------ | ------------- | -------------- | -------------- |
| **Tenant Fit Out** | 4.0 kgCO2e/sf | 7.6 kgCO2e/sf  | 13.3 kgCO2e/sf |

This parameter can be customized for a scenario in the scenario customization screen.

#### Embodied Carbon in MEP

Embodied carbon in mechanical systems in evaluated at two specification levels—standard performance and high performance—and is dependent of the total square footage of the building. This approach, and the data used in EPIC, follow from the CLF study on building mechanical systems.

| Building Area       | Standard Performance | High Performance |
| ------------------- | -------------------- | ---------------- |
| < 25,000 sf         | 4.11 kgCO2e/sf       | 6.17 kgCO2e/sf   |
| 25,000 - 79,999 sf  | 4.58 kgCO2e/sf       | 5.76 kgCO2e/sf   |
| 80,000 - 300,000 sf | 5.93 kgCO2e/sf       | 6.02 kgCO2e/sf   |
| > 300,000 sf        | 4.83 kgCO2e/sf       | 6.79 kgCO2e/sf   |

Base case buildings in EPIC are always assumed to have a standard performance system. <mark style="background-color:yellow;">Scenarios that achieve an EUI reduction of more than 50% the benchmark are assumed to have a high performance system.</mark> The EUI reduction threshold is not directly editable in the public-facing web app, but can be redefined in the API.

This parameter can be customized for a scenario in the scenario customization screen.

#### Embodied Carbon in Solar Photovoltaic Arrays

Embodied carbon in solar photovoltaics arrays is calculated using values from the peer-reviewed literature. A citation to the current data source is available in in the [Reference Data Sources](broken-reference/) section of this guide.

#### Embodied Carbon in Hardscape

All site area not designated as planted is assumed to be hardscaped. Hardscape emissions were calculated by EHDD using a parameterized streamlined LCA model of built from standard hardscape details. The 20th, 50th, and 80th percentile of the resulting distribution was sampled and used to define the specification levels in EPIC.

| Assembly      | Low Carbon    | Best Practices | Conservative  |
| ------------- | ------------- | -------------- | ------------- |
| **Hardscape** | 4.4 kgCO2e/sf | 5.9 kgCO2e/sf  | 7.2 kgCO2e/sf |

#### Emissions from Landscape Maintenance

Emissions from landscape maintenance is calculated per planted area using values from the literature. A citation to the current data source is available in in the [Reference Data Sources](broken-reference/) section of this guide.

### Construction Emissions

Emissions from the construction of the building are estimated as a proportion of A1-A3 emissions. Our expert review process established below ground construction as the major driver of A4-A5 emission. EPIC estimates A4-A5 emissions as 10% of A1-A3 emissions when there is no below ground construction, and conservatively estimates the same at 18% when there is below ground construction.

This parameter can be customized for a scenario in the scenario customization screen.

### Emissions from Greenfield Development

When a user enters a site area, they have the option to select whether or not the site has been previously developed. If the site has been previously developed, EPIC treats it as a "brownfield" site with no carbon sequestered in its soil and existing landscape. If the site has _not_ been previously developed, EPIC treats it as a "greenfield" site with preexisting vegetation.

Developing a greenfield site releases carbon emissions from two sources: carbon stored in soil and carbon stored in biomass. EPIC assumes that 100% of the carbon stored in topsoil is emitted as carbon dioxide. Data on carbon storage in soil is highly regional, and EPIC uses FAO's Global Soil Organic Carbon data product for this calculation, taking the mean value at the zip code level.

To calculate emissions from the removal of above ground biomass, EPIC treats the site as vegetated with regionally-specific "low carbon storage" plants at 50% of the site's carrying capacity. More information on how carbon storage in living biomass is calculated in EPIC is available in the [Stored and Avoided Carbon](stored-avoided-carbon.md#carbon-storage-in-landscapes-and-green-roofs) section of the methodology.
