# Operational Carbon

The overview of how c.scale calculated operational carbon is detailed on the [model structure](model-structure.md#calculating-operational-carbon) page. Below, we give additional detail about how c.scale calculates emissions from all the sources contributing to a project's operational carbon.

## Energy Use

EPIC uses energy use intensity (EUI) in kBtu/sf/yr as its metric for energy use in buildings. EPIC is designed to give accurate feedback on the carbon emissions associated with a declared energy use, but is not an energy modeling tool for determining how a declared energy use can be achieved.

Baseline EUIs are set in c.scale using a direct API connection with Architecture 2030's [Zero Tool](https://zerotool.org/zerotool/), with a failover to a subset of cached Zero Tool results. Zero Tool estimates are used to set baselines for AIA 2030 reporting, but should not be construed as representing "code minimum" design. To set a code minimum EUI, enter a custom value in the "Benchmark EUI" [override](../../epic-web-application/base-case/overrides.md) in EPIC's Base Case tab.

### Fuel Mix

Benchmark buildings are assumed to be "mixed fuel," using energy from both electricity and onsite combustion. All onsite combustion is assumed to be natural gas. The fuel mix of buildings is calculated to align with assumptions in Architecture 2030's [Zero Tool](https://zerotool.org/zerotool/). Zero Tool estimates are used to set baselines for AIA 2030 reporting, but should not be construed as representing "code minimum" design. To set a code minimum fossil fuel use, enter a custom value in the "% Onsite Fossil Fuel Combustion" [override](../../epic-web-application/base-case/overrides.md) in EPIC's Base Case tab.

c.scale assumes a 2.4% upstream leakage rate for all fossil fuel combusted in a building. The carbon intensity of this leakage is calculated with characterization factors from the IPCC's AR6.

#### Fuel Mix in Canadian Buildings

Fossil fuel usage at the building level is reported by [Energy Star](https://portfoliomanager.energystar.gov/pdf/reference/FuelMixandCost.pdf). This data represents the average fuel mix used across all existing building stock within each province. Building use category is not factored into this data.

In order to fill in the data gap for the Northwest Territories, Nunavut, and Yukon, the data representing the prairies region (Alberta, Manitoba, and Saskatchewan) was used. The assumption is that the territories are likely to be more reliant on fossil fuels given that they have less developed infrastructure for the transmission of electricity due to how remote they are.

### Carbon Intensity of Electricity

c.scale includes estimates of carbon emissions from demand for electricity from now until 2110. These estimates are based on NREL's Cambium capacity expansion model. If you are curious about the underlying data, you can explore Cambium data in NREL's [online scenario viewer](https://scenarioviewer.nrel.gov/). Cambium data is not available annually, but annual data is necessary in c.scale. To annualize Cambium data, we use the following method:

* **Fill temporal gaps in Cambium data from 2024-2050** with geometric interpolation for all years between two years reported in Cambium.
  * I.e. for 2025 between the reported values in 2024 and 2026, or for 2041-2044 between the reported values in 2040 and 2045.
* **Extend data to 2110** assuming the electricity grid continue to decarbonize at the same average rate that it decarbonized from 2024-2050. Note that the end date of 2110 has no basis in the data; 2110 is only chosen so that c.scale can model a 60 year reference period for buildings completed up to the year 2050.
* **Fill geographic gaps** to give wall-to-wall coverage of United States.
  * c.scale assumes the average emission rate in Washington, DC, is the same as in Virginia (highly interconnected grids, both PJM).
  * For Alaska and Hawaii, we assume exponential reductions that allow them to meet their climate goals (in the mid-case scenario) or get to 95% decarb by 2045. We don’t make an assumption to approximate a scenario like High Cost of Renewable Energy for either of these two states.

#### Electrical grid emission metrics

c.scale includes two metrics for grid emissions.

* **Average Emission Rate (AER)**. By default, c.scale measures annual emission factors by summing the total generation of all resources in a given year and putting them on a MWh basis. This average emission rate also includes 'precombustion emissions from the leakage of fossil gas in the energy supply chain. This metric is described in NREL's Cambium model as "AER Load: Combustion + Precombustion."
* **Long-Run Marginal Emission Rates (LRMER)**. LRMER emissions are described by NREL as emission rates for “of the next unit of electricity considering the grid’s structure as variable.” This emission metric is preferable to a simple average emission rate because buildings are long-lived assets whose demand for energy has a marginal influence on the evolution of the energy grid. This metric is described in NREL's Cambium model as "LRMER: Combustion + Precombustion."

#### Electrical grid projections

The future of the electrical grid is uncertain. To account for this uncertainty, c.scale includes three future grid scenarios in each region.&#x20;

{% tabs %}
{% tab title="United States" %}
The future of the electrical grid is uncertain. To account for this uncertainty, c.scale includes three NREL Cambium scenarios for the future evolution of the electrical grid. Portions of the text below are quoted from the description of these scenarios and their derivation published by NREL [here](https://www.nrel.gov/docs/fy23osti/84916.pdf) (pdf).

* **Expected decarbonization**. Average estimates for inputs such as technology costs, fuel prices, and demand growth. No inclusion of nascent technologies. Electric sector policies as they existed in September 2022, with the assumption that the Inflation Reduction Act’s Production and Investment Tax Credits do not phase out. This metric is described in NREL's Cambium model as "Midcase."
* **Slow Decarbonization**. Average estimates as in the mid-case scenario, but with an assumption that battery and renewable energy costs are high. This scenario assumes that the thresholds set by the Inflation Reduction Act’s Production and Investment Tax Credits are not met and, as such, they do not phase out. This metric is described in NREL's Cambium model as "High Cost of Renewable Energy."
* **Rapid Decarbonization**. Average estimates for inputs such as technology costs, fuel prices, and demand growth. Nascent technologies are included. Electric sector policies as they existed in September 2022, with the assumption that the Inflation Reduction Act’s Production and Investment Tax Credits do not phase out. High-level assumption that the national electricity grid's carbon emissions in 2050 are 5% of their 2005 level. This metric is described in NREL's Cambium model as "95% decarbonization by 2050."



<figure><img src="../../.gitbook/assets/EPIC - LRMER and AER.png" alt=""><figcaption><p>Carbon emissions from electricity demand from 2023-2110 for two metrics and three scenarios.</p></figcaption></figure>
{% endtab %}

{% tab title="Canada" %}
In order to ensure accurate operational emissions estimations for the lifecycle of a building in EPIC, a similar method to incorporating U.S. Grid Data was employed. Using [measured Grid Data](https://data-donnees.ec.gc.ca/data/substances/monitor/canada-s-official-greenhouse-gas-inventory/C-Tables-Electricity-Canada-Provinces-Territories/?lang=en) and [future projection data](https://open.canada.ca/data/en/dataset/5a6abd9d-d343-41ef-a525-7a1efb686300), yearly Canadian Grid emissions are estimated through 2110 with three different decarbonization scenarios so that operational emissions of any EPIC project started before 2050 can be effectively estimated over a 60 year lifetime. Given the uncertainty of future grid emissions, the three decarbonization forecasts included represent the following scenarios:

* **Expected Decarbonization:** Current policies are maintained, including an assumption that non-emitting materials comprise 80% of electricity generation by 2030, and comprise 89% of generation by 2050. Where electricity generation comes from emitting technologies, carbon capture and storage units are to be built. Electricity Storage becomes possible, as well as inter-provincial transmission, allowing excess generation to be shared among provinces. This is referred to as “Net Zero Electricity (NZE) Baseline” in Canadian Energy Regulator Energy Future 2021.
* **Slower Decarbonization:** Same as NZE Baseline scenario, except there is no inter-provincial transmission of electricity due to high cost of expansion and subsequently, investment is uncertain. Without inter-provincial transmission, provinces with less ability to decarbonize still need to use emitting technologies. This is referred to as “Limited Transmission” Canadian Energy Regulator Energy Future 2021.
* **Rapid Decarbonization:** Same as NZE Baseline scenario, but carbon pricing reaches the point that investment in renewables is more financially sensible than emitting carbon. The high cost of carbon will see non-emitting technology grow more rapidly than in the NZE baseline scenario. This is referred to as “High Carbon Price” in Canadian Energy Regulator Energy Future 2021.

To fill in geographic gaps in future grid emissions for Northwest Territories, Nunavut, and Yukon, national grid projections for each scenario were used to forecast decarbonization in these three provinces.
{% endtab %}
{% endtabs %}

c.scale evaluates energy use on an annual basis. The carbon emissions from electricity, however, vary hour by hour. Depending on the use type and location, this can lead to a difference of as much as +/- 20% between annual (modeled) and hourly (measured) estimates of operational emissions.

## Energy Generation from Onsite Renewables

c.scale calculates energy generation from onsite solar photovoltaic arrays using an API connection to Version 8 of NREL's [PVWatts](https://pvwatts.nrel.gov/) tool. This energy is assumed to displace an equivalent amount of energy demand from the electrical grid and, by doing so, displace a corresponding quantity of emissions (calculated using the Cambium data detailed above).

The array area returned by the c.scale is the total area of the array (i.e., inclusive of the space between the panels). The ratio of solar panels to total array area is the Ground Coverage Ratio (GCR). This ratio can be adjusted in the [Overrides](../../epic-web-application/base-case/overrides.md#solar-ground-coverage-ratio) panel of the Base Case tab.

PVWatts is limited to latitudes from -90 to +90 degrees. For latitudes outside this range, we calculate solar potential at the limit (either -90 or +90). If you're using EPIC to model a PV arrray at extreme latitudes, use caution.&#x20;

## Refrigerant Emissions

In c.scale, fugitive emissions from refrigerant leakage are categorized as operational emissions. They are counted in life cycle stage B1.

For each year of operation, emissions from refrigerant leakage are calculated as:

$$Emissions_{\text{annual}} = (\text{ref charge}) \cdot (\text{ref leakage rate}_{\text{annual}}) \cdot (\text{ref GWP})$$

For each year where MEP systems are replaced/refurbished (denoted in EPIC as the “refurbishment period”), emissions from refrigerant leakage are calculated as:

$$Emissions_{\text{EoL}} = (\text{ref charge}) \cdot (\text{ref leakage rate}_{\text{EoL}} + \text{leakage rate}_{\text{annual}}) \cdot (\text{ref GWP})$$

### Estimating Total Refrigerant Charge

Estimates of total building refrigerant charge are based on data in Barbara Rodriguez’s dissertation entitled "Embodied Carbon of Heating, Ventilation, Air Conditioning and Refrigerants (HVAC+R) Systems." These data are collected from a sample of 20 LEED-certified buildings in the Pacific Northwest region of the United States.

### Refrigerant Leakage Rates

Annual and end-of-life refrigerant leakage rates are typically a model assumption, not a carbon reduction measures. In c.scale, there are two options for leakage assumptions.

| Reporting Scheme    | Annual Leakage | End-of-Life Leakage |
| ------------------- | -------------- | ------------------- |
| LEED                | 2%             | 10%                 |
| CIBSE TM65 (Type 2) | 4%             | 2%                  |

### Refrigerant GWP

Throughout c.scale, three options are given for specification-related options: Conservative, Best Practices, and Low Carbon. Typically, these refer to the 20th, 50th, and 80th percentile of GWP values for available materials. We were unable to replicate this methodology for refrigerants, though, as the overall distribution of refrigerants skews very high–and this highly skewed distribution doesn’t represent the choices designers are making on their projects. In the refrigerant model, these three choices are keyed to specific refrigerants as follows:

| Specification Level | Reference Refrigerant(s) | GWP Value |
| ------------------- | ------------------------ | --------- |
| Standard            | 60% R-410a; 40% R-134    | **1675**  |
| Lower Carbon        | R-513                    | **573**   |
| Lowest Carbon       | R-123                    | **79**    |
