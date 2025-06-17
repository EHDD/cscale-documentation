# Services

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

<div align="left"><figure><img src="../../../.gitbook/assets/image (32).png" alt="" width="333"><figcaption><p>Choose from pre-defined MEP carbon intensities, or input a custom value.</p></figcaption></figure></div>

**Services Reuse**

The reuse of MEP systems as a percentage of the total system. _Note that these measures only affect upfront emissions; refurbishments are counted normally._

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

#### PV Service Life

The length of time over which a majority of the PV systems will be replaced.

#### Solar ground coverage ratio

For any solar array entered as a decarbonization measure, this ratio describes the ratio of active solar cells to total array area. C.Scale's assumption is 0.7, representing an efficient solar layout.&#x20;
