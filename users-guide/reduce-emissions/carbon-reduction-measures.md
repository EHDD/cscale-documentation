# Carbon Reduction Measures

To determine a decarbonization target for the project, carbon reduction measures can be applied to scenarios. C.Scale highlights salient carbon reduction measures that can be consistently modeled with available data. The set of carbon reduction measures included in C.Scale do not represent an exhaustive list of possible emission reduction strategies.

## Reuse

### Building Reuse

The percentage of existing building materials to remain on-site and be used in the project, reducing the demand for new materials.

<details>

<summary>Building Reuse Parameters</summary>

_Note that these measures only affect upfront emissions; refurbishments are counted normally._&#x20;

**Structure Reuse**

The reuse of a pre-existing structural system for a given percentage of the building's floor area.

**Solid Exterior Wall Reuse**

The reuse of solid exterior wall for a given percentage of the building’s total enclosure. Note that this measure only affects upfront emissions; refurbishments are counted normally.&#x20;

**Transparent Exterior Wall Reuse**

The reuse of transparent exterior wall for a given percentage of the building’s total enclosure. Note that this measure only affects upfront emissions; refurbishments are counted normally.&#x20;

**Roofing Reuse**

The reuse of the roofing assembly for a given percentage of the building’s total roof area.&#x20;

**Interior Reuse**

The reuse of interior fitout materials as a percentage of the total fitout.

**Services Reuse**

The reuse of MEP systems as a percentage of the total system.

</details>

## Form and Massing

### **Building Perimeter**

The user-declared perimeter of the building. In the absence of a user input, C.Scale assumes the building is an extruded square.

### **Floor-to-Floor Height**

The vertical distance between building floors in feet. The default value is 13’.

### Window-to-Wall Ratio (WWR)

The ratio of windows to total wall area. The default value is .45.

## Energy Use

### All Electric Building

The elimination of all onsite combustion and provision of 100% of the project’s energy use from electric sources.

### EUI Target

The reduction of the building’s EUI by any of a number of strategies. If the you have not entered a custom EUI, the EUI is estimated via [ZeroTool](https://zerotool.org/).&#x20;

### Clean Power Purchase

The purchase of clean power through Direct Ownership, Green Retail Tariffs, Power Purchase Agreements (PPAs), Community Renewables or Utility Renewable Contracts (the five categories of renewables for which credit can be claimed in AIA 2030 commitment reporting) equivalent to the selected percentage of total energy use. _The purchase of unbundled RECs should not be counted as a clean power purchase in_ C.Scal&#x65;_._

### Solar Photovoltaic (PV) Array System Design

The addition of a solar PV array on the project site. The size of this array can be input in three forms:

* **Percentage of Load.** The solar PV area size is calculated to account for the input percentage of building energy load.
* **Nameplate Capacity.** The solar PV area size is input by its nameplate capacity in kW.
* **Area.** The solar PV area size is input by its total area in square feet.

#### Solar PV orientation

The ability of solar PV arrays to produce electricity is related to their geometry and siting. Not all projects sites, such as partially shaded sites, will have an optimal solar orientation. This toggle has two options:

* **Optimal.** There is no impediment on the site to maximum solar exposure.
* **Suboptimal.** There is solar potential on the site, but it is partly compromised. A 20% penalty on solar energy production will be assessed.

## Structure

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

### Responsibly-Sourced Timber

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

## Enclosure&#x20;

### Solid Exterior Wall Specification

The specification of the solid exterior wall assemblies. These specification levels do not describe specific assemblies. When specific data is not known, the C.Scale app includes pre-defined carbon intensities, defined by the levels of ambition. When more data is available, C.Scale allows you to define specific cladding assemblies, exterior insulation types, and wall framing assemblies. C.Scale will use your description of the solid exterior wall (i.e., any declarations of specific materials) to subset our library of solid exterior wall assemblies (\~1200) to only those meeting your criteria. This allows the user to know the range of potential carbon intensities available both within and between their declared design.

<details>

<summary>Solid Exterior Wall Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for solid exterior wall assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for solid exterior wall assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for solid exterior wall assemblies.&#x20;

</details>

#### Solid Exterior Wall Service Life

The length of time over which a majority of the solid exterior wall will be replaced.

#### Solid Exterior Wall Assemblies Configurator

The Solid Exterior Wall Assemblies Configurator is designed to support the input of more detailed, project-specific data.

To begin using this feature, turn on **Use Assemblies** within the Solid Exterior Wall accordion.

<div align="left"><figure><img src="../../.gitbook/assets/image (7).png" alt="" width="350"><figcaption><p>Turn on the Use Assemblies within accordion.</p></figcaption></figure></div>

Once turned on, click the **Configure Assemblies** to start editing Solid Exterior Wall Assemblies.

<div align="left"><figure><img src="../../.gitbook/assets/image (8).png" alt="" width="350"><figcaption><p>Click on Configure Assemblies.</p></figcaption></figure></div>

This opens up a **pop-out** for Solid Exterior Wall Assembly Configurator. This automatically generates an R-Value, Service Life, and Carbon Intensity, which can be changed as needed.&#x20;

<div align="left"><figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Customize Solid Exterior Wall Assembly options in pop-out.</p></figcaption></figure></div>

You can choose the assembly options as you see fit to tailor them to your requirements. These options will continue to evolve based on ongoing feedback.

{% tabs %}
{% tab title="Solid Exterior Wall Cladding Assembly Choices" %}
* Thin Brick
* EIFS
* Fiber Cement
* Wood Siding
* Profiled Metal Panel
* Composite Metal Panel
* Glass Fiber Reinforced Concrete
* Stone Veneer
* Terracotta
{% endtab %}

{% tab title="External Insulation Choices" %}
* Mineral Wool
* Polylso
* XPS
* EPS
{% endtab %}

{% tab title="Framing Choices" %}
* 6 in. CMU
* 6 in. Metal Stud
* 2x6 Wood Stud
{% endtab %}
{% endtabs %}

To add and edit additional Solid Exterior Wall Assemblies, simply click on the 3-dot menu on the right side and choose **Duplicate**.

<div align="left"><figure><img src="../../.gitbook/assets/image (10).png" alt="" width="151"><figcaption><p>Duplicate to create a new Assembly.</p></figcaption></figure></div>

Customize as needed and ensure the **Area(%)** adds up to a 100%, validating the area.&#x20;

<div align="left"><figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Customize all solid wall assemblies and validate. </p></figcaption></figure></div>

Click Update to see changes to the carbon emissions values in the **Enclosure accordion**.

<div align="left"><figure><img src="../../.gitbook/assets/image (14).png" alt="" width="351"><figcaption><p>Updated carbon emissions values in Enclosure accordion.</p></figcaption></figure></div>

### Transparent Exterior Wall Specification

The specification of the transparent exterior wall assemblies. These specification levels do not describe specific assemblies. When specific data is not known, the C.Scale app includes pre-defined carbon intensities, defined by the levels of ambition. When more data is available, C.Scale allows you to define specific glazing units, mullions, and insulation. C.Scale will use your description of the transparent exterior wall (i.e., any declarations of specific materials) to subset our library of transparent exterior wall assemblies (\~1200) to only those meeting your criteria. This allows the user to know the range of potential carbon intensities available both within and between their declared design.

<details>

<summary>Transparent Exterior Wall Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for transparent exterior wall assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for transparent exterior wall assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for transparent exterior wall assemblies.&#x20;

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (2).png" alt="" width="350"><figcaption><p>Choose from pre-defined transparent exterior wall carbon intensities.</p></figcaption></figure></div>

#### Transparent Exterior Wall Service Life

The length of time over which a majority of the transparent enclosure will be replaced.

### Roofing Specification

The specification of the roofing assemblies. These specification levels do not describe specific assemblies. Instead, they approximate the 80th, 50th, and 20th percentile of the distribution of all roofing options.&#x20;

<details>

<summary>Roofing Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for roofing assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for roofing assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for roofing assemblies.&#x20;

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (3).png" alt="" width="350"><figcaption><p>Choose from pre-defined roofing carbon intensities.</p></figcaption></figure></div>

#### Roofing Service Life

The length of time over which a majority of the roofing will be replaced.

## Interiors

### Floor Area w/ Fit-Out

The percentage of floor space that will be fitted out for occupation by building tenants. The default value is 70%. If tenant fit-out is outside the project scope, this field can be set to 0%.

### Interior Fit Out Specification

The specification of the fittings, furniture, and fixtures required for the use of the building by its tenants. These specification levels do not describe specific fit-outs or materials. Instead, they approximate the 80th, 50th, and 20th percentile of the distribution of all available data on tenant fit-outs.&#x20;

<details>

<summary>Interior Fit Out Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for interior fitouts.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for interior fitouts.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for interior fitouts.&#x20;

- **Custom**. Enter a custom carbon intensity.

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (31).png" alt="" width="339"><figcaption><p>Choose from pre-defined interior carbon intensities, or input a custom value.</p></figcaption></figure></div>

#### Interiors Service Life

The length of time over which a majority of the interior fit out will be replaced.

## Services

### Conditioned Area

The percentage of total floor area that is heated or cooled.&#x20;

### MEP Specification

Embodied carbon in mechanical systems in evaluated at two specification levels—standard performance and high performance—and is dependent of the total square footage of the building. This approach, and the data used in C.Scale, follow from the CLF study on building mechanical systems.&#x20;

Baseline buildings in C.Scale are always assumed to have a standard performance system. Scenarios that achieve an EUI reduction of more than 50% below the baseline are assumed to have a high performance system.&#x20;

_Embodied carbon in MEP is a data-scarce category, and we cannot confidently describe the potential to reduce embodied carbon in MEP systems through specification._&#x20;

<details>

<summary>MEP Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for MEP systems.

- **Average (50th percentile).** 50th percentile of GWP for MEP systems.

* **High Carbon (80th percentile).** 80th percentile of GWP for MEP systems.

- **Custom**. Enter a custom carbon intensity.

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (32).png" alt="" width="333"><figcaption><p>Choose from pre-defined MEP carbon intensities, or input a custom value.</p></figcaption></figure></div>

#### MEP Service Life

The length of time over which a majority of the MEP systems will be replaced.

### PV Specification

Embodied carbon in solar photovoltaics arrays is calculated using values from the peer-reviewed literature. A citation to the current data source is available in in the [Reference Data Sources](https://docs.cscale.io/the-c.scale-tm-data-model/reference-data) section of this guide.

<details>

<summary>PV Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for PV systems.

- **Average (50th percentile).** 50th percentile of GWP for PV systems.

* **High Carbon (80th percentile).** 80th percentile of GWP for PV systems.

- **Custom**. Enter a custom carbon intensity.

</details>

#### PV Refresh Rate

The length of time over which a majority of the PV systems will be replaced.

#### Solar ground coverage ratio

For any solar array entered as a decarbonization measure, this ratio describes the ratio of active solar cells to total array area. C.Scale's assumption is 0.7, representing an efficient solar layout.&#x20;

## Refrigerants

### Total Refrigerant Charge

The reduction of the total quantity of refrigerants used in the buildings HVAC+R system.&#x20;

<details>

<summary>Refrigerant Charge Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of the total quantity of refrigerants used in the buildings HVAC+R system.

- **Average (50th percentile).** 50th percentile of the total quantity of refrigerants used in the buildings HVAC+R system.

* **High Carbon (80th percentile).** 80th percentile of the total quantity of refrigerants used in the buildings HVAC+R system.

- **Custom**. Enter a custom carbon intensity.

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (33).png" alt="" width="340"><figcaption><p>Choose from pre-defined refrigerant charges, or input a custom value.</p></figcaption></figure></div>

### Refrigerant GWP

The  average global warming potential (GWP) of refrigerants used in the buildings HVAC+R system. Throughout C.Scale, three options are given for specification-related options: High Carbon, Average, and Low Carbon. Typically, these refer to the 80th, 50th, and 20th percentile of GWP values for available materials. We were unable to replicate this methodology for refrigerants, though, as the overall distribution of refrigerants skews very high–and this highly skewed distribution doesn’t represent the choices designers are making on their projects. In the refrigerant model, these three choices are keyed to specific refrigerants as follows:

<details>

<summary>Refrigerant GWP Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** Next-Gen Natural Refrigerant (e.g., CO2). GWP Value = 5.

- **Average (50th percentile).** Low-GWP Refrigerant (e.g., R-513). GWP Value = 700.

* H**igh Carbon (80th percentile).** HFC Refrigerant (e.g., 60% R-410a; 40% R-134). GWP Value = 2000.

- **Custom**. Enter a custom carbon intensity.

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (34).png" alt="" width="337"><figcaption><p>Choose from pre-defined refrigerant GWPs, or input a custom value.</p></figcaption></figure></div>

## Sitework

When a user enters a site area, they have the option to select whether or not the site has been previously developed. If the site has been previously developed, C.Scale treats it as a "brownfield" site with no carbon sequestered in its soil and existing landscape. If the site has not been previously developed, C.Scale treats it as a "greenfield" site with preexisting vegetation.

### Planted Area

Set the percentage of site area, minus the building footprint, which is planted. To calculate emissions from the removal of above-ground biomass, C.Scale treats the site as vegetated with regionally-specific "low carbon storage" plants (such as no-mow turfgrass or other herbaceous perennials) at 50% of the site's carrying capacity. All unplanted area is assumed to be hardscape.&#x20;

#### High Carbon Storage Planted Area

Set the percentage of the planted site area comprised of a high carbon storage landscape, such as dense broadleaf shrubs and trees in a matrix of no-mow turfgrass or herbaceous perennials.

### Hardscape specification

All site area not designated as planted is assumed to be hardscaped. The specification of the pervious and impervious surfaces on the building site (outside the building enclosure. These specification levels do not describe specific materials or assemblies. Instead, they approximate the 80th, 50th, and 20th percentile of the distribution of all hardscape assemblies based on a set of standard details.&#x20;

<details>

<summary>Hardscape Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for hardscape assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for hardscape assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for hardscape assemblies.&#x20;

- **Custom**. Enter a custom carbon intensity.

</details>

<div align="left"><figure><img src="../../.gitbook/assets/image (35).png" alt="" width="332"><figcaption><p>Choose from pre-defined hardscape carbon intensities, or input a custom value.</p></figcaption></figure></div>

#### Hardscape Service Life

The length of time over which a majority of the site's hardscape will be replaced.

## Jobsite

### A5.2 Jobsite Emissions

Enter a custom carbon intensity (kgCO₂e/sf) for jobsite emissions related to construction activities and land use. The default value assumes 40 kgCO₂e/m² for construction emissions, which includes fuel, tools, and energy used on-site. This default is adjustable based on project-specific data. For greenfield sites, emissions from soil and vegetation are also calculated, using regional data to estimate carbon release from land development.

### Demolished Area

Pre-construction demolition emissions are calculated per floor area of the demolished building, using a default factor of 35 kgCO2e/m2. This is a data-scarce category. Where project-specific data is available, this default can be overridden by the user.
