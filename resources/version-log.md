# Version Log

_Changelogs for versions prior to 2.13.00 available upon request_

**2.13.00**&#x20;

* Additional reuse parameters&#x20;
* Named assemblies
* Fixed reuse bug
* Metric ingress function

**2.14.00**&#x20;

* Add failover to address ZeroTool errors.&#x20;
* Remove extraneous dependencies.&#x20;
* Move in-memory storage to .parquet

2.14.10&#x20;

* Update emissions leakage per peer review;&#x20;
* Fix `include_site` toggle bug

**2.20.00**&#x20;

* Migrate to FastAPI
* BREAKING CHANGES: Some grid scenario names are updated as follows:
  * `HighRE` → `SlowDecarb`
  * `Decarb` → `RapidDecarb`
* `mod_seq_planting_percentage` is deprecated and will be removed in a future version.
* `clean_power_purchase_amount` now accepts values from 0-100
* First implementation of refrigerants model
  * In 2.20.00, `include_ref` defaults to `False`. In future versions, it will default to `True`.

**2.20.01**

* Fix PVWatts error for very northern locations (>60N)
* Updated refrigerant methodology
* `include_ref` defaults to `True`

**2.20.02**

* Add parameters to describe buildings with multiple structural systems:
  * `secondary_structural_system` accepts the same inputs as `primary_structural_system`
  * `primary_structural_percentage` accepts values (1,100] with a default value of **100**
  * `secondary_structural_percentage` accepts values (0,99] with a default value of **0**
* `primary_percentage` renamed `primary_use_percentage` to disambiguate with `primary_structural_percentage`
  * `primary_percentage` still accepted as an alias for `primary_use_percentage`
* `secondary_percentage` renamed `secondary_use_percentage` to disambiguate with `secondary_structural_percentage`
  * `secondary_percentage` still accepted as an alias for `secondary_use_percentage`
* Expose parameters to model custom grid with an annual grid decarbonization factor

**2.21.00**

* BREAKING CHANGES: Some response parameters have been updated:
  * `api-messages` → `api_messages`
  * `kgCO2e/sf` → `kgCO2e_sf`
* New response objects `areas`, `structural_carbon_intensities`, `emission_totals`, `carbon_intensities`, `structural_quantities`, `energy_data`, `pv_data`, `ref_data`.
* Updated C.Scale's swagger docs to reflect new response schemas.
* The `verbose` toggle has now been removed. The new response object will always include all parameters.

**2.21.01**

* Added a new response object called `category_by_stages` which includes stages for `structure`, `interior_fitout`, `mep`, `cladding`, `glazing`, `roofing`, `site`, `ref`, `operational_energy`
* Fixed bug where EoL was being calculated even when some material categories were out of scope.

**2.22.00**

* Internationalization!
  * `country` is now aliased to `region` and `postalcode` is now aliased to `location`.
  * Expanded list of regions to 8+ countries and RoW.&#x20;
  * C.Scale now supports latitude and longitude lookups.
    * Added a new `global` option for `region`. User must input a dict object into `location` to use this feature.
  * Include global GeoDB.
* A new response object called `regional_data` has been added. This includes the request's `HDD`, `CDD`, and `country`.

2.22.01

* Added support for `metric`and `SI` in both the `/calculate` and `/carbon-intensities` endpoints.

2.22.02

* Fixed bug where SMQi was not responding to metric units.
* Add all CIBSE TM65 options to refrigerant leakage model.&#x20;

**2.23.00**&#x20;

* Exposed nested c.scale request schema and perform associated refactoring to support discoverability and extensibility of the API.
  * Requests made with the legacy flat schema will be parsed to the nested schema
  * Passing the `/api/payload` endpoint a 'flat' request will return a nested one
  * Generally, there is more resolution within the nested schema. More specific data will always overrride more general data; any variables declared in a nested part of the schema will take precedence over top-level defintiions
* Add configurable envelope data to the calculation, based on new dataset. This is reflected in both the flat and nested schema.
* Rename minor schemas to better organize the Swagger doc
* Finally rewrite a few recalcitrant functions to `async`
* Add link to swagger to the API landing page.
* `mod_seq_planting_percentage` has been removed from the response object

2.23.01

* Replaced `"` with `in` in `cladding_description`/`envelope.description` parameter
* Added mm equivalent to `cladding_description`/`envelope.description` parameter

2.23.02

* Refactor schemas
* Refactored endpoints so that invalid nested schemas could properly return validation errors

2.23.03

* Added working request example to swagger doc
* Fixed serializer warning with `request_LatLong`
* Fixed validation edge case for `location`: validator first checks `region` type and parses to correct `location` validator based on input

2.23.04

* added `primary_structure` and `secondary_structure` as aliases to `primary_structural_system` and `secondary_structural_system` respectively
* `custom_structure` refactor
* Added `custom_structure` alias to `custom_carbon_intensities`
* `benchmark_EUI` is now defaulted to `None`
* `site_area` is now defaulted to `None`
* Added subassembly refurbishment periods to `EmbodiedCarbonEmissions` calculations
* Aliased `custom_struct_bom` to `custom_bom`
* Rewrote `CustomGrid` class and its respective validations
* Added happy helpful `custom_grid` validation error messages
* Fixed `custom_grid` param to correctly display in Swagger

**2.24.00**

* Implemented rate limiting of some tokens
* Auth refactor
* Rewrite deployment routine
