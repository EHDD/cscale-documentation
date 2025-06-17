# Enclosure

### Enclosure Specification

The specification of the enclosure assemblies. C.Scale includes a dynamic enclosure model which allows users to input very general data (when very little is known) or very specific data (during later stages of design). When specific data is not known, the app includes C.Scale's pre-defined carbon intensities, defined by the levels of ambition.

<details>

<summary>Enclosure Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for solid exterior wall, transparent exterior wall and roofing assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for for solid exterior wall, transparent exterior wall and roofing assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for solid exterior wall, transparent exterior wall and roofing assemblies.&#x20;

</details>

<div align="left"><figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="369"><figcaption><p>Choose from pre-defined enclosure carbon intensities.</p></figcaption></figure></div>

#### Enclosure Service Life

The length of time over which a majority of the enclosure will be replaced.

### Solid Exterior Wall Specification

The specification of the solid exterior wall assemblies. These specification levels do not describe specific assemblies. When specific data is not known, the C.Scale app includes pre-defined carbon intensities, defined by the levels of ambition. When more data is available, C.Scale allows you to define specific cladding assemblies, exterior insulation types, and wall framing assemblies. C.Scale will use your description of the solid exterior wall (i.e., any declarations of specific materials) to subset our library of solid exterior wall assemblies (\~1200) to only those meeting your criteria. This allows the user to know the range of potential carbon intensities available both within and between their declared design.

<details>

<summary>Solid Exterior Wall Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for solid exterior wall assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for solid exterior wall assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for solid exterior wall assemblies.&#x20;

</details>

**Solid Exterior Wall Reuse**

The reuse of solid exterior wall for a given percentage of the building’s total enclosure. _Note that these measures only affect upfront emissions; refurbishments are counted normally._

#### Solid Exterior Wall Service Life

The length of time over which a majority of the solid exterior wall will be replaced.

#### Solid Exterior Wall Assemblies Configurator

The Solid Exterior Wall Assemblies Configurator is designed to support the input of more detailed, project-specific data.

To begin using this feature, turn on **Use Assemblies** within the Enclosure accordion.

<div align="left"><figure><img src="../../../.gitbook/assets/image (7) (1).png" alt="" width="350"><figcaption><p>Turn on the Use Assemblies within accordion.</p></figcaption></figure></div>

Once turned on, click the **Configure Assemblies** to start editing Solid Exterior Wall Assemblies.

<div align="left"><figure><img src="../../../.gitbook/assets/image (8) (1).png" alt="" width="350"><figcaption><p>Click on Configure Assemblies.</p></figcaption></figure></div>

This opens up a **pop-out** for Enclosure Assembly Configurator. This automatically generates an R-Value, Service Life, and Carbon Intensity, which can be changed as needed.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Customize Solid Exterior Wall Assembly options in pop-out.</p></figcaption></figure>

You can choose the assembly options as you see fit to tailor them to your requirements. These options will continue to evolve based on ongoing feedback.

{% tabs %}
{% tab title="Solid Exterior Wall Cladding Assembly Choices" %}
* Thin Brick
* EIFS
* Fiber Cement
* Wood Siding
* Profiled Metal Panel
* Composite Metal Panel
* Glass Fiber Reinforced Concrete
* Stone Veneer
* Terracotta
{% endtab %}

{% tab title="External Insulation Choices" %}
* Mineral Wool
* Polylso
* XPS
* EPS
{% endtab %}

{% tab title="Framing Choices" %}
* 6 in. CMU
* 6 in. Metal Stud
* 2x6 Wood Stud
{% endtab %}
{% endtabs %}

To add more Solid Exterior Wall Assemblies, simply click on the **New Assembly** button.

<div align="left"><figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="153"><figcaption><p>Create a new Assembly.</p></figcaption></figure></div>

Customize as needed and ensure the **Area(%)** adds up to a 100%, validating the area.&#x20;

<div align="left"><figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Customize all solid wall assemblies and validate. </p></figcaption></figure></div>

When you click Update, depending on the choices made, the **Life Cycle Emissions chart** pertaining to the Enclosure assemblies will change.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Life Cycle Emissions chart before changes.</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Life Cycle Emissions chart after changes.</p></figcaption></figure>

Click out of the Enclosure Assembly Configurator to see changes to the carbon emissions values in the **Enclosure accordion**.

<div align="left"><figure><img src="../../../.gitbook/assets/image (14).png" alt="" width="351"><figcaption><p>Updated carbon emissions values in Enclosure accordion.</p></figcaption></figure></div>

### Transparent Exterior Wall Specification

The specification of the transparent exterior wall assemblies. These specification levels do not describe specific assemblies. When specific data is not known, the C.Scale app includes pre-defined carbon intensities, defined by the levels of ambition. When more data is available, C.Scale allows you to define specific glazing units, mullions, and insulation. C.Scale will use your description of the transparent exterior wall (i.e., any declarations of specific materials) to subset our library of transparent exterior wall assemblies (\~1200) to only those meeting your criteria. This allows the user to know the range of potential carbon intensities available both within and between their declared design.

<details>

<summary>Transparent Exterior Wall Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for transparent exterior wall assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for transparent exterior wall assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for transparent exterior wall assemblies.&#x20;

</details>

**Transparent Exterior Wall Reuse**

The reuse of transparent exterior wall for a given percentage of the building’s total enclosure. _Note that this measure only affects upfront emissions; refurbishments are counted normally._&#x20;

#### Transparent Exterior Wall Service Life

The length of time over which a majority of the transparent enclosure will be replaced.

#### Transparent Exterior Wall Assemblies Configurator

The Transparent Exterior Wall Assemblies Configurator is designed to support the input of more detailed, project-specific data.

To begin using this feature, turn on **Use Assemblies** within the Enclosure accordion.

<div align="left"><figure><img src="../../../.gitbook/assets/image (7) (1).png" alt="" width="350"><figcaption><p>Turn on the Use Assemblies within accordion.</p></figcaption></figure></div>

Once turned on, click the **Configure Assemblies** to start editing Transparent Exterior Wall Assemblies.

<div align="left"><figure><img src="../../../.gitbook/assets/image.png" alt="" width="345"><figcaption><p>Click on Configure Assemblies.</p></figcaption></figure></div>

This opens up a **pop-out** for Enclosure Assembly Configurator. This automatically generates a Service Life and Carbon Intensity, which can be changed as needed.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Customize Transparent Exterior Wall Assembly options in pop-out.</p></figcaption></figure>

You can choose the assembly options as you see fit to tailor them to your requirements. These options will continue to evolve based on ongoing feedback.

{% tabs %}
{% tab title="Transparent Exterior Wall Glazing Type Choices" %}
* Curtain Wall
{% endtab %}

{% tab title="Glazing Unit Choices" %}
* Double-Glazed IGU
* Triple-Glazed IGU
* Closed Cavity Facade
{% endtab %}

{% tab title="Frame Choices" %}
* Aluminium
* Timber/Aluminium
{% endtab %}
{% endtabs %}

To add more Transparent Exterior Wall Assemblies, simply click on the **New Assembly** button.

<div align="left"><figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="153"><figcaption><p>Create a new Assembly.</p></figcaption></figure></div>

Customize as needed and ensure the **Area(%)** adds up to a 100%, validating the area.&#x20;

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Customize all transparent wall assemblies and validate. </p></figcaption></figure>

When you click Update, depending on the choices made, the **Life Cycle Emissions chart** pertaining to the Enclosure assemblies will change.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Life Cycle Emissions chart before changes.</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Life Cycle Emissions chart after changes.</p></figcaption></figure>

Click out of the Enclosure Assembly Configurator to see changes to the carbon emissions values in the **Enclosure accordion**.

<div align="left"><figure><img src="../../../.gitbook/assets/image (4).png" alt="" width="350"><figcaption><p>Updated carbon emissions values in Enclosure accordion.</p></figcaption></figure></div>

### Roofing Specification

The specification of the roofing assemblies. These specification levels do not describe specific assemblies. Instead, they approximate the 80th, 50th, and 20th percentile of the distribution of all roofing options.&#x20;

<details>

<summary>Roofing Specification Choices (Carbon Intensity)</summary>

* **Low Carbon (20th percentile).** 20th percentile of GWP for roofing assemblies.&#x20;

- **Average (50th percentile).** 50th percentile of GWP for roofing assemblies.&#x20;

* **High Carbon (80th percentile).** 80th percentile of GWP for roofing assemblies.&#x20;

</details>

<div align="left"><figure><img src="../../../.gitbook/assets/image (3) (1).png" alt="" width="350"><figcaption><p>Choose from pre-defined roofing carbon intensities.</p></figcaption></figure></div>

**Roofing Reuse**

The reuse of the roofing assembly for a given percentage of the building’s total roof area. _Note that these measures only affect upfront emissions; refurbishments are counted normally._&#x20;

#### Roofing Service Life

The length of time over which a majority of the roofing will be replaced.
