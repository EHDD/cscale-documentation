# Refrigerant Emissions

In C.Scale, fugitive emissions from refrigerant leakage are categorized as operational emissions. They are counted in life cycle stage B1.

For each year of operation, emissions from refrigerant leakage are calculated as:

$$
Emissions_{\text{annual}} = (\text{ref charge}) \cdot (\text{ref leakage rate}_{\text{annual}}) \cdot (\text{ref GWP})
$$

For each year where MEP systems are replaced/refurbished (denoted in C.Scale as the “refurbishment period”), emissions from refrigerant leakage are calculated as:

$$
Emissions_{\text{EoL}} = (\text{ref charge}) \cdot (\text{ref leakage rate}_{\text{EoL}} + \text{leakage rate}_{\text{annual}}) \cdot (\text{ref GWP})
$$

### Estimating Total Refrigerant Charge

Estimates of total building refrigerant charge are based on data in Barbara Rodriguez’s dissertation entitled "Embodied Carbon of Heating, Ventilation, Air Conditioning and Refrigerants (HVAC+R) Systems." These data are collected from a sample of 20 LEED-certified buildings in the Pacific Northwest region of the United States.

### Refrigerant Leakage Rates

Annual and end-of-life refrigerant leakage rates are typically a model assumption, not a carbon reduction measures. In C.Scale, there are two options for leakage assumptions.

| Reporting Scheme    | Annual Leakage | End-of-Life Leakage |
| ------------------- | -------------- | ------------------- |
| LEED                | 2%             | 10%                 |
| CIBSE TM65 (Type 2) | 4%             | 2%                  |

### Refrigerant GWP

Throughout C.Scale, three options are given for specification-related options: Conservative, Best Practices, and Low Carbon. Typically, these refer to the 20th, 50th, and 80th percentile of GWP values for available materials. We were unable to replicate this methodology for refrigerants, though, as the overall distribution of refrigerants skews very high–and this highly skewed distribution doesn’t represent the choices designers are making on their projects. In the refrigerant model, these three choices are keyed to specific refrigerants as follows:

<table><thead><tr><th width="202">Specification Level</th><th width="406.3333333333333">Reference Refrigerant(s)</th><th>GWP Value</th></tr></thead><tbody><tr><td>Conservative</td><td>HFC Refrigerant (e.g., 60% R-410a; 40% R-134)</td><td>2000</td></tr><tr><td>Best Practices</td><td>Low-GWP Refrigerant (e.g., R-513)</td><td>700</td></tr><tr><td>Low Carbon</td><td>Next-Gen Natural Refrigerant (e.g., CO2)</td><td>5</td></tr></tbody></table>
