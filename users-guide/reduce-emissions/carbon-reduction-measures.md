# Carbon Reduction Measures

Embodied carbon in solar photovoltaics arrays is calculated using values from the peer-reviewed literature. A citation to the current data source is available in in the [Reference Data Sources](https://docs.cscale.io/the-c.scale-tm-data-model/reference-data) section of this guide.

<details>

<summary>PV Specification Choices (Carbon Intensity)</summary>

* **Low (20th percentile).** 20th percentile of GWP for PV systems.

<!---->

* **Medium (50th percentile).** 50th percentile of GWP for PV systems.

<!---->

* **High (80th percentile).** 80th percentile of GWP for PV systems.

<!---->

* **Custom**. Enter a custom carbon intensity.

</details>

#### PV Refresh Rate

The length of time over which a majority of the PV systems will be replaced.

#### Solar ground coverage ratio

For any solar array entered as a decarbonization measure, this ratio describes the ratio of active solar cells to total array area. EPIC's assumption is 0.7, representing an efficient solar layout.&#x20;

## Refrigerants

### Total Refrigerant Charge

The reduction of the total quantity of refrigerants used in the buildings HVAC+R system.&#x20;

<table><thead><tr><th width="469">Specification Level</th><th>kg refrigerants per 1000 sf</th></tr></thead><tbody><tr><td>Low (20th percentile)</td><td>1.86</td></tr><tr><td>Medium (50th percentile)</td><td>4.66</td></tr><tr><td>High (80th percentile)</td><td>8.36</td></tr><tr><td>Custom</td><td>Custom</td></tr></tbody></table>

### Refrigerant GWP

The  average global warming potential (GWP) of refrigerants used in the buildings HVAC+R system.

| Specification Level | Reference Refrigerant(s) | GWP Value |
| ------------------- | ------------------------ | --------- |
| Low                 | R-123                    | **79**    |
| Medium              | R-513                    | **573**   |
| High                | 60% R-410a; 40% R-134    | **1675**  |
| Custom              | Custom                   | Custom    |

## Sitework

### Planted Area

Set the percentage of site area, minus the building footprint, which is planted. This planted area is assumed to be a **low carbon storage landscape**, such as no-mow turfgrass or other herbaceous perennials. All unplanted area is assumed to be hardscape.&#x20;

#### High Carbon Storage Planted Area

Set the percentage of the planted site area comprised of a high carbon storage landscape, such as dense broadleaf shrubs and trees in a matrix of no-mow turfgrass or herbaceous perennials.

### Hardscape specification

The specification of the pervious and impervious surfaces on the building site (outside the building envelope. These specification levels do not describe specific materials or assemblies. Instead, they approximate the 80th, 50th, and 20th percentile of the distribution of all hardscape assemblies based on a set of standard details.&#x20;

<details>

<summary>Hardscape Specification Choices (Carbon Intensity)</summary>

* **Low (20th percentile).** 20th percentile of GWP for hardscape assemblies.&#x20;

<!---->

* **Medium (50th percentile).** 50th percentile of GWP for hardscape assemblies.&#x20;

<!---->

* **High (80th percentile).** 80th percentile of GWP for hardscape assemblies.&#x20;

<!---->

* **Custom**. Enter a custom carbon intensity.

</details>

| Assembly      | Low Carbon    | Best Practices | Conservative  |
| ------------- | ------------- | -------------- | ------------- |
| **Hardscape** | 4.4 kgCO2e/sf | 5.9 kgCO2e/sf  | 7.2 kgCO2e/sf |

#### Hardscape Refresh Rate

The length of time over which a majority of the site's hardscape will be replaced.

## Jobsite

### A5.2 Jobsite Emissions

Enter a custom carbon intensity (kgCO₂e/sf) for jobsite emissions related to construction activities and land use. The default value assumes 40 kgCO₂e/m² for construction emissions, which includes fuel, tools, and energy used on-site. This default is adjustable based on project-specific data. For greenfield sites, emissions from soil and vegetation are also calculated, using regional data to estimate carbon release from land development.

### Demolished Area

Pre-construction demolition emissions are calculated per floor area of the demolished building, using a default factor of 35 kgCO2e/m2. This is a data-scarce category. Where project-specific data is available, this default can be overridden by the user.
