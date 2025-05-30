---
description: '[Organization feature]'
---

# All Portfolio Settings

The following settings are applied at the portfolio level, meaning they affect the target scenario for each project. This ensures that all projects within the portfolio share the same underlying assumptions, making them comparable.&#x20;

To refine the portfolio, click on **All Portfolio Settings** in the left-hand panel.

<div align="left"><figure><img src="../../.gitbook/assets/image (2) (2).png" alt="" width="246"><figcaption><p>All Portfolio Settings button found in the left-hand panel.</p></figcaption></figure></div>

## Scope

<div align="left"><figure><img src="../../.gitbook/assets/image (3) (2).png" alt="" width="375"><figcaption><p>Scope settings.</p></figcaption></figure></div>

C.Scale allows project teams to refine the scope of analysis at the portfolio-level by including or excluding LCA stages or parts of the building to meet reporting goals or to facilitate comparison within the portfolio.&#x20;

Any decarbonization measures in excluded parts of the portfolio scope are still saved with the portfolio, but will become temporarily unavailable as long as they are out of scope. When their scope is restored, the values will reappear as last entered.&#x20;

### Analysis Period

Select an analysis period to determine over how many years the analysis takes place.&#x20;

### Life Cycle Stages

**A4-A5 (Construction Process)**\
Turning off this toggle will remove construction process emissions—counted in the A4 and A5 life cycle stages—from the C.Scale model.&#x20;

**D, Biogenic Carbon Storage, and Avoided Emissions**\
Turning off this toggle will remove biogenic carbon stored in timber structural elements, carbon sequestered in landscape, and emissions avoided by excess energy production from on-site renewable from the C.Scale model.

### Scope Categories

**Structure**\
Structure and Foundations are always included. &#x20;

**Enclosure**\
Turning off this toggle will remove the embodied carbon associated with cladding, glazing, and roofing from the C.Scale model.&#x20;

**Interior**\
Turning off this toggle will remove the embodied carbon associated with interior fitouts from the C.Scale model.&#x20;

**Services**\
Turning off this toggle will remove the embodied carbon associated with MEP and PV Arrays (the energy generated by PV panels will still be included).&#x20;

**Refrigerants**\
Turning off this toggle will remove the emissions associated with refrigerant use in the building.&#x20;

**Sitework**\
Turning off this toggle will remove all site and landscaping from the C.Scale model.&#x20;

## General

<div align="left"><figure><img src="../../.gitbook/assets/image (4) (2).png" alt="" width="375"><figcaption><p>General settings.</p></figcaption></figure></div>

### Unit System

Modify the unit system for the portfolio's calculations.&#x20;

## Electricity Grid

<div align="left"><figure><img src="../../.gitbook/assets/image (5) (2).png" alt="" width="375"><figcaption></figcaption></figure></div>

### Future Scenario

The future of the electric grid is uncertain. C.Scale gives the user the choice between three future scenarios, each derived from NREL's [CAMBIUM model](https://www.nrel.gov/analysis/cambium.html).&#x20;

* **Expected decarbonization**. Average estimates for inputs such as technology costs, fuel prices, and demand growth. No inclusion of nascent technologies. Electric sector policies as they existed in September 2022, with the assumption that the Inflation Reduction Act’s Production and Investment Tax Credits do not phase out. This metric is described in NREL's Cambium model as "Midcase."
* **Slow Decarbonization**. Average estimates as in the mid-case scenario, but with an assumption that battery and renewable energy costs are high. This scenario assumes that the thresholds set by the Inflation Reduction Act’s Production and Investment Tax Credits are not met and, as such, they do not phase out. This metric is described in NREL's Cambium model as "High Cost of Renewable Energy."
* **Rapid Decarbonization**. Average estimates for inputs such as technology costs, fuel prices, and demand growth. Nascent technologies are included. Electric sector policies as they existed in September 2022, with the assumption that the Inflation Reduction Act’s Production and Investment Tax Credits do not phase out. High-level assumption that the national electricity grid's carbon emissions in 2050 are 5% of their 2005 level. This metric is described in NREL's Cambium model as "95% decarbonization by 2050."

### Emission Metric

For a given scenario, there are multiple methods to account for the emissions associated with a building. Two metrics are provided in C.Scale, both derived from NREL's [CAMBIUM model](https://www.nrel.gov/analysis/cambium.html). Both metrics use GWP-100 characterization factors.&#x20;

* **Average Emission Rate (AER)**. By default, C.Scale measures annual emission factors by summing the total generation of all resources in a given year and putting them on a MWh basis. This average emission rate also includes 'precombustion emissions from the leakage of fossil gas in the energy supply chain. This metric is described in NREL's Cambium model as "AER Load: Combustion + Precombustion."&#x20;
* **Long-Run Marginal Emission Rates (LRMER)**. LRMER emissions are described by NREL as emission rates for “of the next unit of electricity considering the grid’s structure as variable.” This emission metric is preferable to a simple average emission rate because buildings are long-lived assets whose demand for energy has a marginal influence on the evolution of the energy grid. This metric is described in NREL's Cambium model as "LRMER: Combustion + Precombustion."&#x20;
