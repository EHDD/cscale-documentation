# Structure

### Embodied Carbon in Building Structure

Embodied carbon in building structure is calculated in two stages: a bill of structural materials is estimated and carbon intensities are applied to those materials.

C.Scale's estimation of embodied carbon in a building's structure is modeled based on machine learning models built from over bills of material from real buildings. This approach is preferable to a first-principles approach—i.e. assuming an optimized structural grid for a given geometry—because it greatly reduces truncation error and better describes the variation present in real buildings.

<table><thead><tr><th width="233">Structural System</th><th>Description</th></tr></thead><tbody><tr><td><strong>Wood Frame</strong></td><td>A structural system comprised of dimensional lumber, plywood sheathing, and reinforced concrete cores.</td></tr><tr><td><strong>Steel Frame</strong></td><td>A structural system comprised of columns, beams, girders, and decking constructed from steel structural members connected with rigid or pin joints.</td></tr><tr><td><strong>Reinforced Concrete</strong></td><td>A structural system comprised of columns, beams, and slabs of concrete reinforced with steel that provides tensile strength.</td></tr><tr><td><strong>Mass Timber</strong></td><td>A structural system comprised of massive beams, panels, and columns, often assembled by aggregating many smaller timber elements.</td></tr><tr><td><strong>Hybrid Concrete-Steel (High-Rise)</strong></td><td>A structural system that combines rigid steel frames with concrete columns, beams, and slabs. These hybrid structures are more materially intensive and may be used when there are significant seismic loads, in high-rise buildings, or for programs with very high live or environmental loads.</td></tr></tbody></table>

### Calculating a Bill of Materials

C.Scale uses a suite of machine learning models to estimate quantities of major structural materials in typical buildings. These models were trained from an C.Scale database of structural quantities in completed buildings (n > 1200) assembled from both internal and public sources. The models are updated regularly as new data becomes available.

These weighted data is used to train a statistical model for each structural material in each structural system. These models are trained on a small set of predictors from the underlying data set.&#x20;

Training data is divided into 80% training data and 20% data. Each bill of materials is weighted relative the data provenance. LCI data from a detailed wbLCA is given the highest weight, with data from journal articles, white papers, partial data, and modeled data given progressively lower weights.&#x20;

There are five ML models in our model pipeline. The least accurate model in our pipeline has a Mean Absolute Percentage Error of 16.7% and an r2 value of 0.74. The four other models each have an r2 value over 0.95. K-folds cross-validation (n=5) is used to confirm that each models can consistently predict unseen data.&#x20;

C.Scale uses an instance of this modeling pipeline served in the cloud to generate a bill of materials 'live' as a user requests data from our API.&#x20;

These methods for calculating a structural bill of materials have been reviewed by colleagues at [MKA](https://www.mka.com/), [Carbon Leadership Forum](https://carbonleadershipforum.org/), and Autodesk with additional comment from colleagues at [Arup](https://www.arup.com/). If you are a structural engineer or data scientist interested in providing further review of our modeling pipeline, [please reach out](mailto:epic@ehdd.com?subject=Review).

Known issues with the structural bill or materials generation models are an overprediction of material quantities for small industrial warehouses and rare combinations of use category and primary structural material (e.g. light wood frame hospitals).&#x20;

### Carbon Intensities of Structural Materials

**Carbon intensity is the amount of CO2-equivalent emissions per unit of material**. For structural materials, carbon intensity information is drawn from a variety of sources. In all cases, C.Scale uses GWP-100 characterization factors. These sources are documented in the [Reference Data Sources ](../reference-data.md)section of this guide.

The three specifications available in C.Scale—**low carbon, average, and high carbon**—correspond to the 20th, 50th, and 80th percentile of emissions for that material. These estimates _do not_ correspond to a specific EPD, as there are many options for achieving a certain level of performance. Most carbon intensities for structural materials in C.Scale are national averages, as material supply chains for major structural materials are typically national (or global) in coverage.

Concrete emissions, on the other hand, as assessed regionally. Concrete is a local material, rarely traveling more than 25 miles between production and use. Additionally, the relatively large number of concrete EPDs available in the United States ([80,000+](https://buildingtransparency.org/ec3)) supports a regional approach to measuring concrete emissions.

When specific data is not known, the API includes three choices carbon intensities, defined by the range of products or assemblies available in a particular location:

* **High Carbon** represents the 80th percentile of carbon intensities for regionally-available material or assemblies.
* **Average** represents the 50th percentile of carbon intensities for regionally-available material or assemblies.
* **Low Carbon** represents the 20th percentile of carbon intensities for regionally-available material or assemblies.

#### Regionalization of Carbon Intensity Data

Wherever feasible, carbon intensity data is regionalized to the appropriate level of resolution. Our regionalization methodology aims to reflect the products and assemblies available in a region (the "market mix"), which is often distinct from those manufactured in that region (the "production mix").

Our API includes country-level data for the following countries: United States of America, Canada, United Kingdom, Denmark, France, Germany, Italy, Norway, Saudi Arabia, United Arab Emirates, Singapore, and Sweden. Where regional data is not available, we use background data specific to the region. Currently, we maintain background datasets for North America, the EU, and "rest of world" (RoW). &#x20;
