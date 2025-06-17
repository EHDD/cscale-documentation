# Structure

### **Structure Reuse**

The reuse of a pre-existing structural system for a given percentage of the building's floor area. _Note that these measures only affect upfront emissions; refurbishments are counted normally._&#x20;

### Primary Structural System

Specification of a structural system other than the system modeled in the baseline. Note that this is not strictly a carbon _reduction_ measure, as the substitution of some structural systems with some others can lead to an increase in embodied emissions.&#x20;

<details>

<summary>Structural System Choices</summary>

* **Reinforced Concrete**. A structural system comprised of columns, beams, and slabs of concrete reinforced with steel that provides tensile strength.

- **Mass Timber**. A structural system comprised of massive beams, panels, and columns, often assembled by aggregating many smaller timber elements. This approach assumes that timber elements are aggressively substituted for other structural materials.

* **Wood Frame**. A structural system comprised of dimensional lumber, plywood sheathing, and reinforced concrete cores and podiums.

- **Steel Frame**. A structural system comprised of steel columns, beams, and girders connected with rigid or pin joints. Floors are steel decking with a concrete topping slab.&#x20;

* **Hybrid Concrete-Steel**. A structural system that combines rigid steel frames with concrete columns, beams, and slabs. These hybrid structures are more materially intensive and may be used when there are significant seismic loads, in high-rise buildings, or for programs with very high live or environmental loads.

</details>

### Secondary Structural System

Specification of a secondary structural system, and its associated percentage of the overall building structure.&#x20;

### Structural Material Intensity

Specification of the the structural material intensity based on the chosen material. The selections made in this field sample the distribution of bills of materials _(not carbon intensities)_. Choices are described in narrative form below, and the underlying data is listed in [C.Scale's whole life carbon methodology](https://docs.cscale.io/the-c.scale-tm-data-model/embodied-carbon).&#x20;

<details>

<summary>Structural Material Intensity Choices</summary>

* **Low Carbon (20th percentile).** Represents the 20th percentile of structural material intensity.&#x20;

- **Average (50th percentile).** Represents the 50th percentile of structural material intensity.&#x20;

* **High Carbon (80th percentile).** Represents the 80th percentile of structural material intensity.&#x20;

</details>

### Concrete Specification

The specification of concrete for a given strength class. These estimates do not correspond to a specific EPD, as there are many options for achieving a certain level of performance. Concrete emissions are assessed regionally. It is a local material, rarely traveling more than 25 miles between production and use. Additionally, the relatively large number of concrete EPDs available in the United States ([80,000+](https://buildingtransparency.org/ec3)) supports a regional approach to measuring concrete emissions.

<details>

<summary>Concrete Carbon Intensity Choices</summary>

* **Low Carbon (20th percentile).** GWP in the 20th percentile of locally available concrete for a given strength class.&#x20;

- **Average (50th percentile).** GWP in the 50th percentile of locally available concrete for a given strength class.&#x20;

* **High Carbon (80th percentile).** GWP in the 80th percentile of locally available concrete for a given strength class.&#x20;

</details>

### Steel Specification

The specification of hot-rolled structural steel, cold-formed steel (including steel deck), and reinforcing bar. These estimates _do not_ correspond to a specific EPD, as there are many options for achieving a certain level of performance. Most carbon intensities for structural materials in C.Scale are national averages, as material supply chains for major structural materials are typically national (or global) in coverage.

<details>

<summary>Steel Carbon Intensity Choices</summary>

* **Low Carbon (20th percentile)** GWP in the 20th percentile of available timber products in a category.&#x20;
* **Average (50th percentile).** GWP in the 50th percentile of available timber products in a category.&#x20;
* **High Carbon (80th percentile).** GWP in the 80th  percentile of available timber products in a category.&#x20;

</details>

### Timber Specification

The specification of lumber, plywood/OSB, and engineered timber elements. These estimates _do not_ correspond to a specific EPD, as there are many options for achieving a certain level of performance. Most carbon intensities for structural materials in C.Scale are national averages, as material supply chains for major structural materials are typically national (or global) in coverage.

<details>

<summary>Timber Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile)** GWP in the 20th percentile of available timber products in a category.

- **Average (50th percentile).** GWP in the 50th percentile of available timber products in a category. This is the default value.

* **High Carbon (80th percentile).** GWP in the 80th  percentile of available timber products in a category.

</details>

#### Responsibly-Sourced Timber

In accordance with ISO 21930, the carbon content of biogenic materials can only be counted as carbon-storing if the timber comes from a forest managed with sustainable practices. An example of this is timber from an FSC-certified forest. For more information, please refer to C.Scale methodology for [stored and avoided carbon emissions](https://docs.cscale.io/the-c.scale-tm-data-model/embodied-carbon/stored-avoided-carbon) or the procurement guidance from the [Climate Smart Wood Group](https://www.climatesmartwood.net/procurement/).

In C.Scale, we identify three criteria contributing to the claim that wood products are responsibly sourced. While C.Scale does not prevent the user from counting the carbon storage benefits on other terms (as the list is nonexhaustive), we recommend meeting at least two out of the three criteria below in order to claim climate benefits from carbon storage.

<details>

<summary>Criteria for "Responsibly-Sourced Timber"</summary>

* **Transparent & traceable supply chain (required)**. Claims can be made about the environmental attributes of timber are impossible to verify without transparency and traceability in the supply chain. This means that a project team should be able to identify:
  1. The source forest(s) or supply area(s)
     * _This is the area from which a primary manufacturer sources most or all of its logs, typically a circle drawn around the location of the site of the mill, with the size being dictated by the maximum hauling distance of the logs._
  2. The primary manufacturer mill(s)
     * _E.g., sawmill, veneer mill, chip mill, etc._
  3. The fabrication shop (for engineered timber).

- **Source forest has a growing carbon stock (optional)**. Carbon storage in wood products can only be claimed if the carbon stock of the source forest is maintained or increasing. This means that the forest area is managed and regenerates in a way that either preserves or increases the average level of carbon stored in vegetation and soils, or that high conservation value or high carbon stock forests are not replaced by less ecological valuable and carbon rich production forests.

* **Timber is certified, recycled, or reclaimed (optional)**. The use of recycled or reclaimed wood prolongs its storage of carbon and can displace the use of virgin timber. Certification by the Forest Stewardship Council (FSC) ensures that sound forestry, audit, and reporting practices are used.

</details>
