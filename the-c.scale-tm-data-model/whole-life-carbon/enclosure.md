# Enclosure

### Enclosure Quantity Takeoffs

The building enclosure in divided into three components: solid exterior wall, transparent exterior wall, and roofing. The area of each is calculated based on user inputs for building floor area, number of floors, floor-to-floor height window-to-wall ratio (WWR), and building perimeter. C.Scale makes a preliminary estimate of floor-to-floor height, WWR, and building perimeter (assuming a square building) which the user can refine in the "overrides" panel in the base case tab.

$$
Enclosure \ area = Perimeter \ * \ F2F \ Height \ * \ Number \ of \ floors
$$

$$
Transparent \ Exterior \ Wall \ area = WWR \ * \ Perimeter \ * \ F2F \ Height \ * \ Number \ of \ floors
$$

$$
Solid \ Exterior \ Wall \ area = (1-WWR) \ * \ Perimeter \ * \ F2F \ Height \ * \ Number \ of \ floors
$$

$$
Roof \ area = Building \ Footprint
$$

#### Floor-to-Floor Height

Floor to floor (F2F) height can be set in the app for each floor individually (if using the stacked `BuildingForm` object) or for all floors together (in the simple `BuildingForm` object). Default values for floor-to-floor height are set by use type, as described in the table below.

| Use Categories                                                                                                                 | Default F2F Height (ft) | Default F2F Height (m) |
| ------------------------------------------------------------------------------------------------------------------------------ | ----------------------- | ---------------------- |
| Dormitory, Hotel, Multifamily Housing, Senior Care Facility, Single Family Home                                                | 11.5 feet               | 3.5 meters             |
| Fitness Center, K-12 School, Medical Clinic, Office, Pre-school / Day Care, Restaurant, Retail Store, University/College       | 13 feet                 | 4.0 meters             |
| Aquarium, Hospital, Laboratory, Library, Museum, Performing Arts, Post Office, Stadium, Transit Station, Worship Facility, Zoo | 15 feet                 | 4.6 meters             |
| Convention Center                                                                                                              | 18 feet                 | 5.5 meters             |
| Distribution Center, Warehouse                                                                                                 | 20 feet                 | 6.1 meters             |

### Parametric Enclosure Model

C.Scale includes a dynamic enclosure model which allows users to input very general data (when very little is known) or very specific data (during later stages of design).&#x20;

When specific data is not known, the app includes C.Scale's pre-defined carbon intensities, defined by the levels of ambition:

* **High Carbon** represents the 80th percentile of material or assembly carbon intensities.
* **Average** represents the 50th percentile of material or assembly carbon intensities.
* **Low Carbon** represents the 20th percentile of material or assembly carbon intensities.

When more data is available, C.Scale allows you to define specific cladding assemblies, exterior insulation types, and wall framing assemblies. Using the `description` parameter in the `enclosure.cladding`  or `enclosure.glazing` section of the request, you can pass in a more precise definition of the solid exterior wall. Where one or more layers of the assembly is unknown (or up for discussion, pass a `None` parameter).&#x20;

C.Scale will use your description of the enclosure (i.e., any declarations of specific materials) to subset our library of enclosure assemblies (\~1200) to only those meeting your criteria. The app will use the relevant `specification` parameter to choose the 20th, 50th, or 80th percentile of that subset. This allows the user to know the range of potential carbon intensities available both within and between their declared design.

* If all parameters are `None` (no design criteria entered), then we evaluate the percentile from the full set of enclosures in our database (\~1200 modeled enclosure assemblies).&#x20;
* With the user selects their design criteria, we subset the data used to generate these percentiles. For instance, if a user selects a Timber Rainscreen cladding, we will return the 20th, 50th, of 80th percentile of all enclosure assemblies in our database with a Timber Rainscreen (\~100 modeled enclosure assemblies).

Multiple enclosures can be described for a building by passing a list of descriptions. The relative proportion of each enclosure is described with the `proportion` field with each `description`. The app will normalize all proportion entries to the total solid exterior wall. This means that a use can pass in proportions of 20000, 25000, and 5000 (representing m2 of enclosure area) or of 0.4, 0.5, and 0.1 (representing the same assemblies as proportions of the total).

In all cases, user-declared carbon intensity data can be entered on a kgCO2e/m2 (of kgCO2e/sf) basis for each component of the enclosure.&#x20;

### Solid Exterior Wall

{% tabs %}
{% tab title="Cladding Assemblies" %}
**Cladding assemblies available via app:**

* Thin Brick
* EIFS
* Fiber Cement
* Wood Siding
* Profiled Metal Panel
* Composite Metal Panel
* Glass Fiber Reinforced Concrete&#x20;
* Stone Veneer
* Terracotta
{% endtab %}

{% tab title="Exterior Insulation" %}
**Exterior insulation types types available via app:**

* Mineral Wool
* PolyIso
* XPS
* EPS
{% endtab %}

{% tab title="Wall Framing" %}
**Wall framing types available via app:**

* 6in (152mm) CMU
* 6in (152mm) Metal Stud
* 6in (152mm) Metal Stud
{% endtab %}
{% endtabs %}

Data in the C.Scale enclosure model makes use of Payette Kaleidoscope data for some assemblies by permission. Find the full citation for these data in the [Reference Data](../reference-data.md) section of the methodology.

**Default R-Values**

The declared R-value of the assembly is used to calculate the amount of exterior insulation needed. R-values for framing assemblies are de-rated using the nominal R-values in ASHRAE 90.1-2019 Appendix A. If an R-value is not declared by the user, the default is set by climate zone.&#x20;

<table data-full-width="false"><thead><tr><th width="297">ASHRAE Climate Zone</th><th>C.Scale Default R-Value</th></tr></thead><tbody><tr><td>Climate Zone 0</td><td>18</td></tr><tr><td>Climate Zone 1</td><td>18</td></tr><tr><td>Climate Zone 2</td><td>18</td></tr><tr><td>Climate Zone 3</td><td>20</td></tr><tr><td>Climate Zone 4</td><td>21</td></tr><tr><td>Climate Zone 5</td><td>2</td></tr><tr><td>Climate Zone 6</td><td>26</td></tr><tr><td>Climate Zone 7</td><td>26</td></tr><tr><td>Climate Zone 8</td><td>29</td></tr></tbody></table>

### Transparent Exterior Wall

{% tabs %}
{% tab title="Mullion/Frame Material" %}
**Mullion/frame types available via app:**

* Aluminum
* Timber/Aluminum
{% endtab %}

{% tab title="Insulated Glazing Unit (IGU)" %}
**IGU types available via app:**

* Double-glazed IGU
* Triple-glazed IGU
* Closed Cavity Facade
{% endtab %}
{% endtabs %}

### Roofing

_Parametric roofing model coming soon!_
