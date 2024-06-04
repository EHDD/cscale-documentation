# 🪵 Version Log

_This is a log of all updates which either affect the use of the API or are otherwise important to communicate to our users (e.g. bug fixes or performance updates requested by users). This is not an exhaustive list of updates, and many internal updates are not listed below. For a complete list of updates in a specific version, please reach out._&#x20;

### 2.29.00

* `StackedBuildingForm` object is live and available to all users
* Update material carbon intensity data in France, Italy, and Sweden

2.28.03

* Fix bug in display (not calculation) of carbon intensities for `CMUMortar` and `CMUBlock`

2.28.01

* Minor request refactoring
* `interior.percent_floor_area` can now equal 0

### **2.28.00**

* Major middleware and DevOps update
* Performance updates to Geodatabase

2.27.08

* Fixed a bug where `mep.specification`, `solar_pv.specification`, and `refrigerants.GWP_specification` were not being properly converted when `SI` was used

2.27.07

* Refactored POST `/carbon-intensities` endpoint to remove hyphens from `structure` response object
* Separated routers for `/carbon-intensities` and `/location-data`

2.27.05

* added `ASHRAE_CZ` and `KG_CZ` to `regional_data` response object + added descriptions

2.27.04

* Fixed bug with `GetCarbonIntensities` endpoint where response data was not being parsed correctly.

2.27.03

* Fix responsibly sourced timber bug in some geo's

2.27.02

* Added POST endpoints for `/tokens/token-data` and `/carbon-intensities`

2.27.01

* bugfix for 500 internal server error in `/api/tokens/token-data endpoint`

### **2.27.00**

* Updated the following datasets:&#x20;
  * Denmark, Germany: grid, fuel mix baselines, material carbon intensity
  * Sweden, UK, Italy, France: grid, fuel mix baselines
* Added the following regions: Australia, Spain, Belgium, EU, Finland
* Added `/location-data` endpoint
* Added request and response schema for `/location-data` endpoint

2.26.03

* Hotfix for 100% reuse on all reuse parameters
* `{category.reuse}` now being applied to `A4`, `A5p3` calculations for `structure`, `cladding`, `glazing`, `roofing`,`mep`, `interiors`

2.26.01

* Bug fixes for`category_by_stages` response object
* Added `demolition` as a stage in response schema

### **2.26.00**

* New A4-A5 modules in `LifeCycleStages.py` to reflect ASHRAE/ICC 240P
  * A4\_Emissions: Transportation emissions&#x20;
    * A5\_Emissions: Demolition (A5.1), construction activity (A5.2), and jobsite waste (A5.3)
* Added a new `A4_5Options` class, which allows users to input A4 transportation emission factors, `demolished_area`, and A5.1 and/or A5.2 emission factors
* Added total\_pv\_panel\_area to response\_areas response object
* Added total\_pv\_panel\_area to response\_pv\_data response object
* Refactored `structure.custom_carbon_intensities` and `structure.custom_bom` for better visibility in schema and to happily accept incomplete inputs.
* Requests can now have `none` declared anywhere

2.25.01

* Hotfixes related to schema for Cambium 2023.&#x20;
* Deprecate size/performance MEP data in `/carbon-intensities` endpoint.

### **2.25.00**

* Migrated from Cambium 2022 to Cambium 2023 electricity emissions data for the contiguous US
  * NREL deprecated state-level data, so our analysis increased resolution to the ReEDS Balancing Authority level.
* Interim A4-A5 refactor in preparation for alignment with ASHRAE/ICC 240P.
* Update `/carbon-intensities` endpoint to give better visibility into EC ranges possible for specific cladding types.
* Added `description` to glazing data to increase resolution.
  * Multiple glazing types
  * Multiple mullion/CW materials
* Fix refrigerant GWP bug (in flat schema only).

2.24.01

* Implemented standard 20/50/80 specification levels for MEP systems (in nested schema only)
* Added example request/response to `tokens/token_data` endpoint
* Pointed links in docs to [cscale.io](https://cscale.io)

**2.24.00**

* Implemented rate limiting of some tokens
* Authentication refactor to allow for more fine-grained backend permissioning
* Rewrite deployment routine

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

2.23.03

* Added working request example to swagger doc
* Fixed serializer warning with `request_LatLong`
* Fixed validation edge case for `location`: validator first checks `region` type and parses to correct `location` validator based on input

2.23.02

* Refactor schemas
* Refactored endpoints so that invalid nested schemas could properly return validation errors

2.23.01

* Replaced `"` with `in` in `cladding_description`/`envelope.description` parameter
* Added mm equivalent to `cladding_description`/`envelope.description` parameter

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

2.22.02

* Fixed bug where SMQi was not responding to metric units.
* Add all CIBSE TM65 options to refrigerant leakage model.&#x20;

2.22.01

* Added support for `metric`and `SI` in both the `/calculate` and `/carbon-intensities` endpoints.

**2.22.00**

* Internationalization!
  * `country` is now aliased to `region` and `postalcode` is now aliased to `location`.
  * Expanded list of regions to 8+ countries and RoW.&#x20;
  * C.Scale now supports latitude and longitude lookups.
    * Added a new `global` option for `region`. User must input a dict object into `location` to use this feature.
  * Include global GeoDB.
* A new response object called `regional_data` has been added. This includes the request's `HDD`, `CDD`, and `country`.

**2.21.01**

* Added a new response object called `category_by_stages` which includes stages for `structure`, `interior_fitout`, `mep`, `cladding`, `glazing`, `roofing`, `site`, `ref`, `operational_energy`
* Fixed bug where EoL was being calculated even when some material categories were out of scope.

**2.21.00**

* BREAKING CHANGES: Some response parameters have been updated:
  * `api-messages` → `api_messages`
  * `kgCO2e/sf` → `kgCO2e_sf`
* New response objects `areas`, `structural_carbon_intensities`, `emission_totals`, `carbon_intensities`, `structural_quantities`, `energy_data`, `pv_data`, `ref_data`.
* Updated C.Scale's swagger docs to reflect new response schemas.
* The `verbose` toggle has now been removed. The new response object will always include all parameters.

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

**2.20.01**

* Fix PVWatts error for very northern locations (>60N)
* Updated refrigerant methodology
* `include_ref` defaults to `True`

**2.20.00**&#x20;

* Migrate to FastAPI
* BREAKING CHANGES: Some grid scenario names are updated as follows:
  * `HighRE` → `SlowDecarb`
  * `Decarb` → `RapidDecarb`
* `mod_seq_planting_percentage` is deprecated and will be removed in a future version.
* `clean_power_purchase_amount` now accepts values from 0-100
* First implementation of refrigerants model
  * In 2.20.00, `include_ref` defaults to `False`. In future versions, it will default to `True`.

2.14.10&#x20;

* Update emissions leakage per peer review;&#x20;
* Fix `include_site` toggle bug

**2.14.00**&#x20;

* Add failover to address ZeroTool errors.&#x20;
* Remove extraneous dependencies.&#x20;
* Move in-memory storage to .parquet

**2.13.00**&#x20;

* Additional reuse parameters&#x20;
* Named assemblies
* Fixed reuse bug
* Metric ingress function

_Changelogs for versions prior to 2.13.00 available upon request_
