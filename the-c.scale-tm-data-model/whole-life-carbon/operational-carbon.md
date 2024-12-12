# Operational Carbon

The overview of how C.Scale calculated operational carbon is detailed on the [model structure](<../../README (2).md>) page. Below, we give additional detail about how C.Scale calculates emissions from all the sources contributing to a project's operational carbon.

## Overview of Operational Carbon Calculation

The operational emissions of the project are assessed annually and summed across all years before the target date. The equation is similar to the equation for embodied emissions, with two key differences: first, the quantity x is substituted for the energy use intensity (EUI) e; second, the equation is a double summation, once across all the fuel types in the building and again across all years between the building’s completion and the target year. The total operational emissions assessed by C.Scale are represented by this expression:

$$
Operational\ carbon\ emissions=\ \sum_{t=1}^{m}\ \sum_{j=1}^{o}\ A\ast e_{tj}\ast c_j
$$

For m total years between the building’s completion and the target year and across o fuel types, where A is the total building area, $$e_{tj}$$ is the energy use per building area (EUI) in year $$t$$ of fuel $$j$$, and $$c_{tj}$$ is the carbon intensity per energy unit in year $$t$$ of fuel $$j$$.

Carbon emissions associated with electricity are derived from NREL's Cambium model. Onsite fossil fuel use is assumed to be natural gas. The carbon emissions of natural gas are assessed with a 2.4% leakage rate. Fuel oil emissions account for N20 and CH4 emissions. Characterization of non-CO2 emissions is determined with the GWP100 factors published in IPCC AR6.

## Energy Use

C.Scale uses energy use intensity (EUI) in units of kBtu/sf/yr (or kWh/m2/yr) as its metric for energy use in buildings. C.Scale is designed to give accurate feedback on the carbon emissions associated with a declared energy use, but is not an energy modeling tool for determining how a declared energy use can be achieved.

Baseline EUIs are set in c.scale using a direct API connection with Architecture 2030's [Zero Tool](https://zerotool.org/zerotool/), with a failover to a subset of cached Zero Tool results. Zero Tool estimates are used to set baselines for AIA 2030 reporting, but should not be construed as representing "code minimum" design. To set a code minimum EUI, enter your desired value as the `benchmark_EUI` in the request object.

### Fuel Mix

Benchmark buildings are assumed to be "mixed fuel," using energy from both electricity and onsite combustion. All onsite combustion is assumed to be natural gas. The fuel mix of buildings is calculated to align with assumptions in Architecture 2030's [Zero Tool](https://zerotool.org/zerotool/). Zero Tool estimates are used to set baselines for AIA 2030 reporting, but should not be construed as representing "code minimum" design.&#x20;

C.Scale assumes a 2.4% upstream leakage rate for all fossil fuel combusted in a building. The carbon intensity of this leakage is calculated with characterization factors from the IPCC's AR6.

#### Fuel Mix in Canadian Buildings

Fossil fuel usage at the building level is reported by [Energy Star](https://portfoliomanager.energystar.gov/pdf/reference/FuelMixandCost.pdf). This data represents the average fuel mix used across all existing building stock within each province. Building use category is not factored into this data.

In order to fill in the data gap for the Northwest Territories, Nunavut, and Yukon, the data representing the prairies region (Alberta, Manitoba, and Saskatchewan) was used. The assumption is that the territories are likely to be more reliant on fossil fuels given that they have less developed infrastructure for the transmission of electricity due to how remote they are.

### Carbon Intensity of Electricity

C.Scale includes estimates of carbon emissions from demand for electricity from now until 2110. These estimates are based on NREL's Cambium capacity expansion model. If you are curious about the underlying data, you can explore Cambium data in NREL's [online scenario viewer](https://scenarioviewer.nrel.gov/). Cambium data is not available annually, but annual data is necessary in C.Scale. To annualize Cambium data, we use the following method:

* **Fill temporal gaps in Cambium data from 2024-2050** with geometric interpolation for all years between two years reported in Cambium.
  * I.e. for 2025 between the reported values in 2024 and 2026, or for 2041-2044 between the reported values in 2040 and 2045.
* **Extend data to 2110** assuming the electricity grid continue to decarbonize at the same average rate that it decarbonized from 2024-2050. Note that the end date of 2110 has no basis in the data; 2110 is only chosen so that C.Scale can model a 60 year reference period for buildings completed up to the year 2050.
* **Fill geographic gaps** to give wall-to-wall coverage of United States.
  * C.Scale assumes the average emission rate in Washington, DC, is the same as in Virginia (highly interconnected grids, both PJM).
  * For Alaska and Hawaii, we assume exponential reductions that allow them to meet their climate goals (in the mid-case scenario) or get to 95% decarb by 2045. We don’t make an assumption to approximate a scenario like High Cost of Renewable Energy for either of these two states.

#### Electrical grid emission metrics

C.Scale includes two metrics for grid emissions.

* **Average Emission Rate (AER)**. By default, C.Scale measures annual emission factors by summing the total generation of all resources in a given year and putting them on a MWh basis. This average emission rate also includes 'precombustion emissions from the leakage of fossil gas in the energy supply chain. This metric is described in NREL's Cambium model as "AER Load: Combustion + Precombustion."
* **Long-Run Marginal Emission Rates (LRMER)**. LRMER emissions are described by NREL as emission rates for “of the next unit of electricity considering the grid’s structure as variable.” This emission metric is preferable to a simple average emission rate because buildings are long-lived assets whose demand for energy has a marginal influence on the evolution of the energy grid. This metric is described in NREL's Cambium model as "LRMER: Combustion + Precombustion."

#### Electrical grid projections

The future of the electrical grid is uncertain. To account for this uncertainty, C.Scale includes three future grid scenarios in each region.

{% tabs %}
{% tab title="North America" %}
#### United States

C.Scale includes three NREL Cambium scenarios for the future evolution of the electrical grid. Portions of the text below are quoted from the description of these scenarios and their derivation published by NREL [here](https://www.nrel.gov/docs/fy23osti/84916.pdf) (pdf).

* **Expected Decarbonization**. Average estimates for inputs such as technology costs, fuel prices, and demand growth. No inclusion of nascent technologies. Electric sector policies as they existed in September 2022, with the assumption that the Inflation Reduction Act’s Production and Investment Tax Credits do not phase out. This metric is described in NREL's Cambium model as "Midcase."
* **Slow Decarbonization**. Average estimates as in the mid-case scenario, but with an assumption that battery and renewable energy costs are high. This scenario assumes that the thresholds set by the Inflation Reduction Act’s Production and Investment Tax Credits are not met and, as such, they do not phase out. This metric is described in NREL's Cambium model as "High Cost of Renewable Energy."
* **Rapid Decarbonization**. Average estimates for inputs such as technology costs, fuel prices, and demand growth. Nascent technologies are included. Electric sector policies as they existed in September 2022, with the assumption that the Inflation Reduction Act’s Production and Investment Tax Credits do not phase out. High-level assumption that the national electricity grid's carbon emissions in 2050 are 5% of their 2005 level. This metric is described in NREL's Cambium model as "95% decarbonization by 2050."

#### Canada

In order to ensure accurate operational emissions estimations for the lifecycle of a building in C.Scale, a similar method to incorporating U.S. Grid Data was employed. Using [measured Grid Data](https://data-donnees.ec.gc.ca/data/substances/monitor/canada-s-official-greenhouse-gas-inventory/C-Tables-Electricity-Canada-Provinces-Territories/?lang=en) and [future projection data](https://open.canada.ca/data/en/dataset/5a6abd9d-d343-41ef-a525-7a1efb686300), yearly Canadian Grid emissions are estimated through 2110 with three different decarbonization scenarios so that operational emissions of any C.Scale project started before 2050 can be effectively estimated over a 60 year lifetime. Given the uncertainty of future grid emissions, the three decarbonization forecasts included represent the following scenarios:

* **Expected Decarbonization:** Current policies are maintained, including an assumption that non-emitting materials comprise 80% of electricity generation by 2030, and comprise 89% of generation by 2050. Where electricity generation comes from emitting technologies, carbon capture and storage units are to be built. Electricity Storage becomes possible, as well as inter-provincial transmission, allowing excess generation to be shared among provinces. This is referred to as “Net Zero Electricity (NZE) Baseline” in Canadian Energy Regulator Energy Future 2021.
* **Slower Decarbonization:** Same as NZE Baseline scenario, except there is no inter-provincial transmission of electricity due to high cost of expansion and subsequently, investment is uncertain. Without inter-provincial transmission, provinces with less ability to decarbonize still need to use emitting technologies. This is referred to as “Limited Transmission” Canadian Energy Regulator Energy Future 2021.
* **Rapid Decarbonization:** Same as NZE Baseline scenario, but carbon pricing reaches the point that investment in renewables is more financially sensible than emitting carbon. The high cost of carbon will see non-emitting technology grow more rapidly than in the NZE baseline scenario. This is referred to as “High Carbon Price” in Canadian Energy Regulator Energy Future 2021.



To fill in geographic gaps in future grid emissions for Northwest Territories, Nunavut, and Yukon, national grid projections for each scenario were used to forecast decarbonization in these three provinces.
{% endtab %}

{% tab title="EU + UK" %}
#### United Kingdom

C.Scale has three scenarios describing the future decarbonization of the electrical grid in the United Kingdom, based on the National Grid ESO's [Future Energy Scenarios](https://www.nationalgrideso.com/future-energy/future-energy-scenarios-fes/fes-documents) (FES).&#x20;

* **Expected Decarbonization**. Based on the System Transformation scenario from FES, where the UK meets its net zero target in 2050.
* **Slow Decarbonization**. Based on the Falling Short scenario from FES, where the UK does not meet its target of net zero by 2050. This scenario still shows some progress on decarbonization, but much lower than other scenarios.&#x20;
* **Rapid Decarbonization**. Based on the Leading the Way scenario from FES, where the UK meets its net zero target in 2046.&#x20;

#### EU Countries

For locations across the EU, we reference [data from the European Environment Agency](https://www.eea.europa.eu/en/analysis/indicators/greenhouse-gas-emission-intensity-of-1) for present-day emissions for each country. For future emissions, we consider three scenarios:

* **Expected Decarbonization**. The country achieves an 80% reduction relative their present-day emissions by 2050, in alignment with the trajectory of a bloc-wide goal of a 90% reduction by 2040 relative to emissions in 1990.&#x20;
* **Slow Decarbonization**.  The country falls short, achieving only a 20% reduction by 2050 relative their present-day emissions.&#x20;
* **Rapid Decarbonization**. The country achieves a 99% decarbonization by 2050 relative their present-day emissions.C
{% endtab %}

{% tab title="ANZ" %}
#### Australia

Present-day electrical grid emissions in Australia are cited from data provided by the Australian Energy Market Operator. As of 2024, Australia is developing a [2050 Net Zero Plan](https://www.dcceew.gov.au/climate-change/emissions-reduction/net-zero/electricity-and-energy-sector-plan), but it is not yet published.&#x20;

* **Expected Decarbonization**. Australia achieves an 80% reduction relative their present-day emissions by 2050.
* **Slow Decarbonization**.  Australia alls short, achieving only a 20% reduction by 2050 relative their present-day emissions.&#x20;
* **Rapid Decarbonization**. Australia achieves a 99% decarbonization by 2050 relative their present-day emissions.
{% endtab %}

{% tab title="Gulf Countries" %}
#### Saudi Arabia

Present-day electricity-related emissions in Saudi Arabia are from [EMBER](https://ember-energy.org/about/). Saudi Arabia has a [goal of a net zero economy by 2060](https://www.kapsarc.org/wp-content/uploads/2023/12/KS-2023-DP31-Saudi-Arabia-Net-Zero-GHG-Emissions-by-2060-Transformation-of-the-Electricity-Sector.pdf), but data is not published on emissions rates on a kWh-basis.&#x20;

* **Expected Decarbonization**. Saudi Arabia achieves an 90% reduction relative their present-day emissions by 2060.
* **Slow Decarbonization**.  Saudi Arabia falls short, achieving only a 20% reduction by 2060 relative their present-day emissions.&#x20;
* **Rapid Decarbonization**. Saudi Arabia achieves a 99% decarbonization by 2060 relative their present-day emissions.

#### United Arab Emirates

The UAE has a plan to achieve a electricity grid carbon intensity of 0.27 kgCO2e/kWh by the year 2030, and net zero by 2050. However, these plans indicate a percentage of gas and coal remaining on the grid in 2050, suggesting that the actual incurred emissions will not be zero.&#x20;

* **Expected Decarbonization**. The Emirates achieve an 80% reduction relative their present-day emissions by 2050, and are on track to achieving their stated 2060 goal.
* **Slow Decarbonization**.  The Emirates  falls short, achieving only a 20% reduction by 2050 relative their present-day emissions.&#x20;
* **Rapid Decarbonization**. The Emirates achieves a 99% decarbonization by 2050 relative their present-day emissions.
{% endtab %}

{% tab title="Southeast Asia" %}
#### Singapore

Present-say emission factors are from [EMA](https://www.ema.gov.sg/resources/singapore-energy-statistics/chapter2). Singapore has a goal of a net zero electricity sector by 2045.&#x20;

* **Expected Decarbonization**. Singapore achieves an 90% reduction relative their present-day emissions by 2045.
* **Slow Decarbonization**.  Singapore falls short, achieving only a 20% reduction by 2045 relative their present-day emissions.&#x20;
* **Rapid Decarbonization**. Singapore achieves a 99% decarbonization by 2045 relative their present-day emissions.
{% endtab %}
{% endtabs %}

C.Scale evaluates energy use on an annual basis. The carbon emissions from electricity, however, vary hour by hour. Depending on the use type and location, this can lead to a difference of as much as +/- 20% between annual (modeled) and hourly (measured) estimates of operational emissions.

## Energy Generation from Onsite Renewables

C.Scale calculates energy generation from onsite solar photovoltaic arrays using an API connection to Version 8 of NREL's [PVWatts](https://pvwatts.nrel.gov/) tool. This energy is assumed to displace an equivalent amount of energy demand from the electrical grid and, by doing so, displace a corresponding quantity of emissions (calculated using the Cambium data detailed above).

The array area returned by the c.scale is the total area of the array (i.e., inclusive of the space between the panels). The ratio of solar panels to total array area is the Ground Coverage Ratio (GCR).

PVWatts is limited to latitudes from -60 to +60 degrees. For latitudes outside this range, we calculate solar potential at the limit (either -60 or +60). If you're using C.Scale to model a PV array at extreme latitudes, use caution.
