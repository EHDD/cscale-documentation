# 📡 Access c.scale via API

## Why use our API?

In addition to the open access version of EPIC, an expanded version of the data model behind EPIC is accessible by API. By directly integrating EPIC into their own platforms and workflows, our API has allowed our partners to:

* Perform higher-resolution analysis of specific buildings.
* Analyze "look-ahead" scenarios for the construction or acquisition of large portfolios of buildings.
* Perform sensitivity testing of carbon reduction measures.
* Stress-test planning and policy decisions at the municipal, regional, or national scale.

API integration has also allowed organizations to extend EPIC to meet their specific needs:

* Supplement c.scale with building-specific data or organization-specific carbon reduction measures.
* Integrate c.scale into their existing ESG and carbon accounting platforms.
* Deploy a custom versions of c.scale to an organization's internal servers.

API access can be tailored to meet your organization's specific needs. If you are interested in learning more, [please contact our team](mailto:epic@ehdd.com?API).  &#x20;

## Overview of c.scale API <a href="#overview" id="overview"></a>

c.scale is a stateless API for calculating whole carbon footprints from buildings. c.scale has the ability to calculate embodied, operational, and landscape emissions at various levels of resolution. A description of c.scale's methodology for calculating carbon emissions is available in our [public-facing documentation](https://epic-documentation.gitbook.io/epic/) and additional information about our methods is available [upon request](mailto:epic@ehdd.com?subject=Methods). EPIC's API is [RESTful](http://en.wikipedia.org/wiki/Representational\_State\_Transfer), accepts [JSON-encoded](http://www.json.org/) request bodies, returns [JSON-encoded](http://www.json.org/) responses, and uses standard HTTP response codes, authentication, and verbs.

### Data Dictionary <a href="#data-dictionary" id="data-dictionary"></a>

A full data dictionary for the 100+ parameters in our data model is available to our partners. To learn more or preview the data structure, [please reach out](mailto:epic@ehdd.com?subject=API).

### Simple API Calls <a href="#minimum-parameters" id="minimum-parameters"></a>

At each of its endpoints, EPIC can calculate the emissions from a building from a small set of parameters. The seven minimum parameters are:

* `project name` : The name of the project.
* `year_completion` : The year in which work on the project is completed.
* `zipcode` : The postal code for the building's location.
* `primary_structural_system` : The description of the building's structural system.
* `primary_use` : The use type of the building.
* `above_floor_sqf` : The average area per floor for all above ground floors.
* `above_floors` : The number of floors above ground.

{% swagger method="post" path="/summary" baseUrl="https://epic-model.ehdd.com" summary="Summary | Basic Parameters" %}
{% swagger-description %}
Returns a summary of model results.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="json" type="JSON" %}
{"project_name": "demo", "year_completion": 2025, "zipcode": "04019", "primary_structural_system": "Reinforced Concrete", "primary_use": "Office", "above_floor_sqf": 10000, "above_floors": 5 }
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-self-token" required="true" type="Token" %}
XXXX-XXXX-XXXX-XXXX
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Summary results as .json object" %}
```javascript
{'benchmark_EUI': 101.92127853699436,
 # some results omitted
 'onsite_ff_pc': 0.441,
 'total_area_sf': 50000,
 'kgCO2e/sf': 105.66523882591783,
 'em_env': 923602.5,
 'em_syst': 801500.0,
 'em_site': 0.0,
 'em_struct': 1657595.9728746423,
 'em_constr': 271313.46842124924,
 'em_tfo': 1629250.0,
 'op_total': 11566515.725664519,
 'em_total': 5283261.941295891,
 'net_total': 16849777.66696041,
 'av_total': 0.0,
 'total_planting_area': 0
 }
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Validation error returned." %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/timeseries" baseUrl="https://epic-model.ehdd.com" summary="Time Series | Basic Parameters" %}
{% swagger-description %}
Returns results as time series data. Set verbose to "True" for a full list of parameters.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="json" type="JSON" %}
{"project_name": "demo", "year_completion": 2025, "zipcode": "04019", "primary_structural_system": "Reinforced Concrete", "primary_use": "Office", "verbose":True, "above_floor_sqf": 10000, "above_floors": 5 }
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-self-token" required="true" type="Token" %}
XXXX-XXXX-XXXX-XXXX
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Summary results as .json object" %}
```javascript
{'timeseries': [
  {'year': 2025,
   'net_cumul': 3186955.817568227,
   'av_cumul': 0.0,
   'em_cumul': 2984448.1526337415,
   'op_cumul': 202507.66493448563,
   'em_struct': 1402899.6842124923,
   'em_clad': 204347.0,
   'em_glaz': 271128.0,
   'em_roof': 140260.0,
   'em_tfo': 465500.0,
   'em_mep': 229000.0,
   'em_pv': 0.0,
   'op_foss': 173118.96895680786,
   'op_elec': 29388.695977677762,
   'av_pv': 0,
   'em_constr': 271313.46842124924,
   'av_store': -0.0,
   'em_hardsc': 0.0,
   'em_green': 0,
   'em_maint': 0.0}, ### etc. for each year
]}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Validation error returned." %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### Expanded API Calls <a href="#expanded-api-calls" id="expanded-api-calls"></a>

While only seven parameters are necessary to calculate a preliminary estimate with c.scale, almost 100 additional parameters are available in the API to tune that estimate to better describe your specific case.

{% swagger method="post" path="/summary" baseUrl="https://epic-model.ehdd.com" summary="Summary | Custom EC data, custom scope" %}
{% swagger-description %}
Summary results with custom embodied carbon data entered for the building envelope.

Exclude interiors from the analysis.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="json" type="JSON" %}
{"project_name": "demo", "year_completion": 2025, "zipcode": "04019", "primary_structural_system": "Reinforced Concrete", "primary_use": "Office", "above_floor_sqf": 10000, "above_floors": 5, "include_interior_fitout":False, "custom_cladding": 0.4, "custom_glazing": 12.2,

\


"custom_roofing": 0.2,

\


"concrete_specification": "Low Carbon", "envelope_refurbishment": 50 }
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-self-token" required="true" type="Token" %}
XXXX-XXXX-XXXX-XXXX
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Summary results as .json object" %}
```javascript
 {'benchmark_EUI': 101.92127853699436,
 # some results omitted
 'onsite_ff_pc': 0.441,
 'total_area_sf': 50000,
 'kgCO2e/sf': 43.10412606301398,
 'em_env': 923602.5,
 'em_syst': 572500.0,
 'em_struct': 1042397.002864272,
 'em_constr': 152962.8002864272,
 'em_tfo': 0.0,
 'op_total': 5983066.696869811,
 'em_total': 2155206.303150699,
 'net_total': 8138273.00002051,
 'av_total': 0.0,
 'total_planting_area': 0
 }
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Validation error returned." %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/timeseries" baseUrl="https://epic-model.ehdd.com" summary="Time series | all-electric building, decarbonizing grid" %}
{% swagger-description %}
Using NREL's LRMER metrics for electricity-related emissions.

Return truncated time series data (i.e., Verbose is "False")
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="json" type="JSON" %}
{"project_name": "demo", "year_completion": 2025, "zipcode": "04019", "primary_structural_system": "Reinforced Concrete", "primary_use": "Office", "above_floor_sqf": 10000, "above_floors": 5, "gridOutlook": "Decarb", "emissionMetric":"LRMER", "verbose":False }
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-self-token" required="true" type="Token" %}
XXXX-XXXX-XXXX-XXXX
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Summary results as .json object" %}
```javascript
{'timeseries': [
 {'year': 2025,
  'net_cumul': 3319789.3837627876,
  'av_cumul': 0.0,
  'em_cumul': 2984448.1526337415,
  'op_cumul': 335341.2311290462},
 {'year': 2026,
  'net_cumul': 3646698.062920966,
  'av_cumul': 0.0,
  'em_cumul': 2984448.1526337415,
  'op_cumul': 662249.9102872245},
 {'year': 2027,
  'net_cumul': 3957242.5818188465,
  'av_cumul': 0.0,
  'em_cumul': 2984448.1526337415,
  'op_cumul': 972794.429185105}, ### etc. for each year 
 ]}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Validation error returned." %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
