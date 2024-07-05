# 🪵 Version Log

_This is a log of all updates which either affect the use of the API or are otherwise important to communicate to our users (e.g. bug fixes or performance updates requested by users). This is not an exhaustive list of updates, and many internal updates are not listed below. For a complete list of updates in a specific version, please reach out._&#x20;

<mark style="background-color:green;">Check out our feature roadmap and subscribe to our feature updates via RSS on o</mark>[<mark style="background-color:green;">ur canny.io site</mark>](https://cscale.canny.io/changelog)<mark style="background-color:green;">.</mark>

### 2.33.00

This update moves C.Scale's calculations in line with emerging whole life carbon standards, with a particular focus on how we handle replacements, refrigerants, and landscape carbon storage by phase.

**Updated B2-5 Calculation**

When accounting for the regular replacement and refurbishment of materials over time in modules B2-B5 (maintenance, repair, replacement, refurbishment), C.Scale now accounts for:

* Emissions from the transportation of those materials to the site (following the assumptions used in module A4),
* Emissions from the installation of that material and associated waste (following the assumptions in modules A5.2 and A5.3)
* End-of-life emissions of all removed materials (following the same assumptions in modules C2-C4).

All of these emissions are 'rolled into' the B2-5 estimate, better describing the total impact of those replacements.

**Improved Refrigerant Model**

Emissions from refrigerant leakage are now more richly described by life cycle module:

* Emissions from installation of MEP equipment are counted in A5.2 (jobsite emissions).
* Emissions from annual leakage are counted in B1 (in-use emissions).
* Emissions from end-of-life leakage from the replacement of MEP equipment over the project's life cycle are counted in B1 (in-use emissions).
* Emissions from the removal of MEP systems at end-of-life are counted in phase C1 (demolition emissions).

We're in the process of scoping a wider update to our refrigerant model to better predict the mass of refrigerants installed, potentially with some additional (systems-specific) refrigerant data.

**Improved Site and Landscape Model**

As with the refrigerants model described above, we've worked to better organize and describe landscape emissions by life cycle module:

* Land use change emissions from greenfield development are counted in A5.2 (jobsite emissions).
* Carbon storage in the landscape plantings is counted in B1 (in-use emissions).
* Recurring emissions from landscape maintenance are counted in B2-B5 (maintenance, repair, replacement, refurbishment).

### 2.32.00

No new data model capabilities this update, but a number of changes to make the API more robust, stable, and useful. Enjoy :)

**Bulk Calculation Endpoints**

In this release are two new "bulk calculation" endpoints, which accept a list of requests and return a list of responses. This endpoint is available for the [simple building form](http://api.cscale.io/api/cscale-swagger-docs#/Whole%20Life%20Carbon/calculate\_bulk\_emissions\_simple\_api\_calculate\_simple\_form\_bulk\_post) and for the [stacked building form](http://api.cscale.io/api/cscale-swagger-docs#/Whole%20Life%20Carbon/calculate\_bulk\_emissions\_stacked\_api\_calculate\_stacked\_form\_bulk\_post). The maximum number of calculations you can currently pass via this endpoint is **50**.

In addition to better supporting the use of the API for masterplanning and larger-scale projects, we hope this update also gives our users a method for reducing the need to send large sets of concurrent requests.

**Incident Reporting**

Up until now, the best way to report a potential issue with the API was to email (or sometimes text) Jack. Now, we have an new incident reporting endpoint available at `/api/report/incident`. This endpoint logs the incident via Better Stack and then Better Stack emails, texts, Slacks (and, if it's severe, calls) the dev-on-duty to troubleshoot the incident ASAP.

We hope that this will give a stronger line of communication between our users and our team, as well as ensuring that we can meet our user's highest expectations for support and incident response times.

**Additional Testing**

In this update, we added additional tests to support the B2-5 bugfix we made earlier today, as well as adding an additional schema-driven testing suite that ensures that the API can handle any request within the schema's validation parameters.

### 2.31.00

**Updates to C and D Phase Emissions**

This release represents a significant improvement of how C.Scale calculates C Phase emissions. Where previously these were ambiguously grouped into a C1-C4 object, data is now available for each C phase separately. To ensure that this update is applied evenly throughout the model, we also divided the D phase into D1 and D2. With the addition of more detail, the overall phases are also still available, and the C1-C4 and D objects in the category\_by\_stages object are retained.A few non-breaking API changes related to this update:

* Alias'ed `D` to `benefits` in `lifecycle_stages` request object. This parameter now affects more phases than D. I.e., carbon storage in landscape is in B1, upstream carbon storage in timber supply chains is included in A1.
* D Phase is divided into D1 (potential recycling, reuse, and recovery benefits) and D2 (exported energy).
* A5.3 estimates will change slightly, since they now include end-of-life (C Phase) emissions for all wasted materials

**New Endpoints!**

We restructured the endpoints to better support the stacked building form. The current `/api/calculate` endpoint will continue to be supported, but is considered a legacy endpoint since it's (purposefully) schema-agnostic. Moving forward, URLs for calculate endpoints will be structured around the schema they accept. We are also deprecating the `/api/summary` and `/api/timeseries` endpoints. They're a little silly, since they just return a subset of the results for the/api/calculate. This alone is not sufficient reason for us to maintain a separate endpoint. Here's the non-breaking changes you can expect from the endpoint update:

* `/api/timeseries` is marked as deprecated. It will be removed from the model in Q4 2024.
* `/api/summary` is marked as deprecated. It will be removed from the model in Q4 2024.
* `/api/calculate` is marked as legacy. We will continue to support this model, even as it grows stranger from accepting too many schemas all at once.

Two new shiny endpoints for calculating whole life carbon:

* `/calculate/simple-form` accepts a request in a nested schema with a simple `building_form` request.
* /`calculate/stacked-form` accepts a request in a nested schema with a stacked `building_form` request.

You can see an example of these request objects (and more) in our [current API notebook](https://drive.google.com/drive/u/0/folders/1Q\_\_pMVDnPgzv01aWb-cfakifKtuqyH4K).

**ZeroTool Update**

Previously, C.Scale used the public ZeroTool API provided by Architecture 2030 for EUI baselines for Canada and North America. This API is awesome, and made earlier versions of our C.Scale possible. As we scale up, though, it didn't feel right that our model depended on their server resources. From this version of C.Scale and moving forward, we're hosting our own instance of ZeroTool. In addition to lessening the load on ZeroTool, this also allows us to add more resources to the ZeroTool, helping get around a performance bottleneck. Beside this, no changes to the C.Scale side.

**Uptime Monitoring**

* The [api.cscale.io](http://api.cscale.io) page now includes an uptime monitor widget, connected to the live status page available at [api-uptime.cscale.io](http://api-uptime.cscale.io). This will help determine is perceived downtime is on the C.Scale side.

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
