# Envelope

### Envelope Quantity Takeoffs

The building envelope in divided into three components: opaque cladding, glazing, and roofing. The area of each is calculated based on user inputs for building floor area, number of floors, floor-to-floor height window-to-wall ratio (WWR), and building perimeter. C.Scale makes a preliminary estimate of floor-to-floor height, WWR, and building perimeter (assuming a square building) which the user can refine in the "overrides" panel in the base case tab.

$$
Envelope \ area = Perimeter \ * \ Floor \ Height \ * \ Number \ of \ floors
$$

$$
Glazing \ area = WWR \ * \ Perimeter \ * \ Floor \ Height \ * \ Number \ of \ floors
$$

$$
Cladding \ area = (1-WWR) \ * \ Perimeter \ * \ Floor \ Height \ * \ Number \ of \ floors
$$

$$
Roof \ area = Above \ Ground \ Floor \ Area
$$

### Custom Data

In all cases, custom data can be entered on a kgCO2e/m2 (of kgCO2e/sf) basis for each component of the envelope.&#x20;

### Parametric Envelope Model

C.Scale includes a dynamic envelope model which allows users to input very general data (when very little is known) or very specific data (during later stages of design).&#x20;

When specific data is not known, the API includes EPIC's pre-defined carbon intensities, defined by the levels of ambition:

* **Conservative** represents the 80th percentile of material or assembly carbon intensities.
* **Best Practices** represents the 50th percentile of material or assembly carbon intensities.
* **Low Carbon** represents the 20th percentile of material or assembly carbon intensities.

When more data is available, C.Scale allows you to define specific cladding assemblies, exterior insulation types, and wall framing assemblies. Using the `description` parameter in the `envelope.cladding`  or `envelope.glazing` section of the request, you can pass in a more precise definition of the opaque building envelope. Where one or more layers of the assembly is unknown (or up for discussion, pass a `None` parameter.&#x20;

C.Scale will use your description of the envelope (i.e., any declarations of specific materials) to subset our library of envelope assemblies (\~1200) to only those meeting your criteria. The API will use the relevant `specification` parameter to choose the 20th, 50th, or 80th percentile of that subset. This allows the user to know the range of potential carbon intensities available both within and between their declared design.

* If all parameters are `None` (no design criteria entered), then we evaluate the percentile from the full set of envelopes in our database (\~1200 modeled envelope assemblies).&#x20;
* With the user selects their design criteria, we subset the data used to generate these percentiles. For instance, if a user selects a Timber Rainscreen cladding, we will return the 20th, 50th, of 80th percentile of all envelope assemblies in our database with a Timber Rainscreen (\~100 modeled envelope assemblies).

Multiple envelopes can be described for a building by passing a list of descriptions. The relative proportion of each envelope is described with the `proportion` field with each `description`. The API will normalize all proportion entries to the total opaque envelope area. This means that a use can pass in proportions of 20000, 25000, and 5000 (representing m2 of envelope area) or of 0.4, 0.5, and 0.1 (representing the same assemblies as proportions of the total).

### Opaque Envelope

{% tabs %}
{% tab title="Cladding Assemblies" %}
**Cladding assemblies available via API:**

* Granite Veneer
* Limestone Veneer
* Brick Veneer
* EIFS
* Glass Fiber Reinforced Concrete Rainscreen
* Aluminum Composite Panel Rainscreen
* Terracotta Rainscreen
* Fiber Cement Rainscreen
* Formed Zinc Panel Rainscreen
* Thin Brick Rainscreen
* Formed Steel Panel Rainscreen
* Hardwood Rainscreen
{% endtab %}

{% tab title="Exterior Insulation" %}
**Exterior insulation types types available via API:**

* Mineral Wool
* PolyIso
* XPS
* EPS
{% endtab %}

{% tab title="Wall Framing" %}
**Wall framing types available via API:**

* 6in (152mm) CMU
* 3.625in (92mm) Metal Stud | 16in (400mm) Spacing
* 3.625in (92mm) Metal Stud | 24in (600mm) Spacing
* 2x4 (50x100mm) Wood Stud | 24in (600mm) Spacing
* 2x4 (50x100mm) Wood Stud | 16in (400mm) Spacing
* 6in (152mm) Metal Stud | 16in (400mm) Spacing
* 6in (152mm) Metal Stud | 24in (600mm) Spacing
* 2x6 (50x150mm) Wood Stud | 24in (600mm) Spacing
* 2x6 (50x150mm) Wood Stud | 16in (400mm) Spacing
{% endtab %}
{% endtabs %}

### Transparent Envelope

{% tabs %}
{% tab title="Mullion/Frame Material" %}
**Mullion/frame types available via API:**

* Steel
* Timber/Aluminum
* Aluminum
* Timber
{% endtab %}

{% tab title="Insulated Glazing Unit (IGU)" %}
**IGU types available via API:**

* Double-glazed IGU
* Triple-glazed IGU
{% endtab %}
{% endtabs %}

### Calculating Opaque Assembly R-Value

The declared R-value of the assembly is used to calculate the amount of exterior insulation needed. R-values for framing assemblies are de-rated using the nominal R-values in ASHRAE 90.1-2019 Appendix A.&#x20;

### Roofing

_Parametric roofing model coming soon!_
