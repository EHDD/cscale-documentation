# Energy Use

## Energy

### All Electric Building

The elimination of all onsite combustion and provision of 100% of the project’s energy use from electric sources.

### EUI Target

The reduction of the building’s EUI by any of a number of strategies. If the you have not entered a custom EUI, the EUI is estimated via [ZeroTool](https://zerotool.org/).&#x20;

### Clean Power Purchase

The purchase of clean power through Direct Ownership, Green Retail Tariffs, Power Purchase Agreements (PPAs), Community Renewables or Utility Renewable Contracts (the five categories of renewables for which credit can be claimed in AIA 2030 commitment reporting) equivalent to the selected percentage of total energy use. _The purchase of unbundled RECs should not be counted as a clean power purchase in_ C.Scal&#x65;_._

## Solar Photovoltaic (PV) Array System Design

The addition of a solar PV array on the project site. The size of this array can be input in three forms:

* **Percentage of Load.** The solar PV array is calculated where production is a percentage of the building's electrical demand.
* **Nameplate Capacity.** The solar PV array' nameplate capacity in kW.
* **Area.** The solar PV area size is input by its total area in square feet.

#### Detailed Design

* **Tilt (deg).** The tilt angle is the angle from horizontal of the photovoltaic modules in the array. For a fixed array, the tilt angle is the angle from horizontal of the array where 0° = horizontal, and 90° = vertical. For more information, please refer to C.Scale methodology for [Operational carbon](../../../the-c.scale-tm-data-model/whole-life-carbon/operational-carbon.md) and documentation from [PVWatts<sup>®</sup> Calculator](https://pvwatts.nrel.gov/). &#x20;
* **Azimuth (deg).** For a fixed array, the azimuth angle is the angle clockwise from true north describing the direction that the array faces. For an array with one-axis tracking, the azimuth angle is the angle clockwise from true north of the axis of rotation. The azimuth angle does not apply to arrays with two-axis tracking. The default value is an azimuth angle of 180° (south-facing) for locations in the northern hemisphere and 0° (north-facing) for locations in the southern hemisphere. For more information, please refer to C.Scale methodology for [Operational carbon](../../../the-c.scale-tm-data-model/whole-life-carbon/operational-carbon.md) and documentation from [PVWatts<sup>®</sup> Calculator](https://pvwatts.nrel.gov/).&#x20;
* **Losses.** The system losses account for performance losses you would expect in a real system that are not explicitly calculated by the PVWatts<sup>®</sup> model equations. The default value for the system losses of 14% is based on the categories:

| Category                  | Default Value (%) |
| ------------------------- | ----------------- |
| Soiling                   | 2                 |
| Shading                   | 3                 |
| Snow                      | 0                 |
| Mismatch                  | 2                 |
| Wiring                    | 2                 |
| Connections               | 0.5               |
| Light-Induced Degradation | 1.5               |
| Nameplate Rating          | 1                 |
| Age                       | 0                 |
| Availability              | 3                 |

For more information, please refer to C.Scale methodology for [Operational carbon](../../../the-c.scale-tm-data-model/whole-life-carbon/operational-carbon.md) and documentation from [PVWatts<sup>®</sup> Calculator](https://pvwatts.nrel.gov/).&#x20;
