# Goal and Scope

**C.Scale** is a whole life carbon calculation engine estimating emissions from the construction, renovation, and operation of buildings. **When highly-detailed energy modeling and life cycle assessment aren't affordable or practicable, teams use C.Scale.**

C.Scale is designed for use during site and feasibility studies, requests for proposals, pre-design, in retrospective analysis, or in other situations where a whole-building life cycle assessments and/or energy models are not practicable.&#x20;

The model allows a user to enter a strict minimum of project parameters to test a wide range of the most meaningful carbon reductions strategies. It is the calculation engine behind numerous web applications and research efforts focused on both forward-looking planning and retrospective analysis of carbon emissions from buildings and the built environment.

We ship features continuously, and have an exciting roadmap for the year ahead. Features are developed in response to user feedback, to incorporate improved data, and to refine the tool's methodology. Something you'd like to see? Reach out.&#x20;

## Goal

**C.Scale** provides directionally accurate guidance for specific projects by helping to identify which carbon reduction strategies a project should pursue, and helps to guide decarbonization of portfolios and portions of the building stock where C.Scale assumptions have been tested (i.e., in North America and the EU).&#x20;

## Scope

**C.Scale** is an whole life carbon model, integrating assessments of embodied, operational, and landscape carbon in a data model to capture the entire carbon footprint of the project.

By default, all emissions associated with the building are included in the model's scope of analysis.&#x20;

### Geographic Coverage

In countries where our users are based, we use country-level data. Additional countries are added regularly, usually in response to user requests.&#x20;

<details>

<summary>Country-Level Data in C.Scale</summary>

* Australia
* Belgium
* Canada
* Denmark
* Finland
* France
* Germany
* Italy
* Norway
* Spain
* Sweden
* United Kingdom

</details>

Where country-level data is not available, we use generic regional background data. Background data sets currently include:&#x20;

* North America (NAM)
* Europe (EU)
* Rest of World (RoW)

### Time Horizon

**C.Scale** is a time series model and can calculate emissions over a time horizon of either 30 or 60 years. Support for additional time horizons is under development. &#x20;

### Reference Service Life

C.Scale assumes a building's reference service life of 60 years.&#x20;

### Life Cycle Stages

**C.Scale** integrates data from life cycle stages (sometimes called "life cycle modules") A1-A5, B2-B6, and C2-C4. These correspond to the impacts of the materials used in the project, emissions from construction, their replacement over time, and the project’s operational energy use. When biogenic carbon is counted, some end-of-life impacts (from modules C2-C4) are assessed during the product phase (see section on [Biogenic Carbon](the-c.scale-tm-data-model/embodied-carbon/stored-avoided-carbon.md#biogenic-carbon)). End-of-life (C2-C4) emissions for structure are only assessed when a 60 year time horizon is selected.

C.Scale also includes a model of fugitive refrigerant emissions (B1) and of benefits from the export of renewable energy to the utility (D2).&#x20;

<figure><img src=".gitbook/assets/EPIC - Included LIfe Cycle Stages.png" alt=""><figcaption><p>Highlighted stages are included in the C.Scale model.</p></figcaption></figure>

### Embodied Carbon Scope

**C.Scale** includes an assessment of embodied carbon from the following sources:

* Building structure and foundation
* Construction activities
* Cladding, glazing, and roofing assemblies and their replacement over time
* Interior fit-outs and their replacement over time
* MEP systems and their replacement over time
* PV arrays and their replacement over time
* Regular landscape maintenance, assessed annually
* Hardscape on the building site

### Operational Carbon Scope

**C.Scale** considers operational emissions from the following sources:

* Emissions from the combustion of methane gas in the building
* Upstream leakage of methane gas as a proportion of methane gas combusted in the building
* Upstream emissions from the generation of electricity delivered to the site
* Refrigerant leakage annually and at the end of the equipment's life.&#x20;

### Stored Carbon Scope

**C.Scale** includes an estimate of carbon storage in timber structural systems and site landscaping. Carbon storage in planting is calculated over the time horizon then annualized. Carbon storage in building structure is assigned to the first year of the project. C.Scale's method for calculating carbon storage in timber structural systems is detailed in the section on [stored and avoided carbon](the-c.scale-tm-data-model/embodied-carbon/stored-avoided-carbon.md).

### Adjusting the Analysis Scope

In C.Scale, you can add or remove some life cycle modules and building components from the scope of an assessment using the `include` toggles in each section of the request body. When comparing results between C.Scale and other tools, or between any estimates of carbon emissions, _the scope of each analysis must be identical._

## Uncertainty

_<mark style="color:green;">Inclusion of an uncertainty estimate is coming soon to the public web application.</mark>_

Anecdotal evidence has put C.Scale results (modeled without any customization) within 5-30% of the estimates generated by whole building Life Cycle Assessment and hourly operational carbon assessment for buildings where C.Scale was used either in early project stages or _post facto_.

Every attempt has been made to ensure that C.Scale describes a typical building (i.e. a building similar to those in our database) whose characteristics match those you enter in the tool. However, unreported characteristics may make a particular building atypical in ways that it is beyond the scope of C.Scale to describe. For instance, the use of particularly high-carbon and high-cost finish materials (e.g., a building where all the millwork is in gold leaf) is not covered by C.Scale. It is impossible to preemptively describe all cases where C.Scale might deviate from a particular building (the possibilities are literally endless) but, as your project progresses, we recommend that your team remains aware of how any deviation from "typical" design will affect the project's climate goals.

Customizing any model parameters removes them from the calculation of uncertainty. We assume that custom data represents commitments made by the project team.
