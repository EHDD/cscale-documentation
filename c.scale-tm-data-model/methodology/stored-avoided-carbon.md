# Stored and Avoided Carbon

The overview of how c.scale calculates stored and avoided carbon is detailed on the [model structure](model-structure.md#calculating-operational-carbon) page. Below, we give additional detail about how c.scale calculates emissions from all the sources contributing to a project's stored and avoided carbon.

## Biogenic Carbon

Living systems present a particular challenge for carbon emission accounting. Static emission factors are sufficient for manmade or mineral materials, but biogenic materials—those materials, such as forest products, originating from living systems—can’t be as easily summarized. Through photosynthesis, living materials remove carbon from the atmosphere as they grow; the removal of carbon dioxide from the atmosphere and its storage in biogenic materials is called referred to in EPIC as "carbon storage." But there are also emissions associated with the processing and maintenance of biogenic materials. And, eventually, biogenic materials are stored in landfills where they continue to store carbon, are recycled, or are combusted for energy and release their stored carbon back into the atmosphere.

### Carbon storage in timber

To account for the life cycle emissions of biogenic materials including carbon storage, c.scale follows the recent guidance of the American Center for Life Cycle Assessment (ACLCA) in accounting for their carbon emissions (see citation in Data and References). This guidance is applied to accounting for the biogenic carbon in forest products (lumber, plywood, and mass timber assemblies) as well as to biogenic carbon stored in the landscape. To understand the tradeoffs in biogenic materials, life cycle stages for the end-of-life of biogenic materials are counted upfront, even if they aren’t included for other products.

In c.scale, the emissions and carbon storage associated with biogenic structural materials are accounted for at the beginning of the project.&#x20;

**The carbon emitted in the production of biogenic materials is accounted separately from stored biogenic carbon**. The carbon emissions related to material production (arising from processes such as the use of machinery and transportation) are counted as embodied carbon.

**Carbon storage in lumber, plywood, and mass timber assemblies can only be counted if those materials are sourced from responsibly managed forests**. Practically, this can mean a number of things.  In c.scale, we identify three criteria contributing to the claim that wood products are responsibly sourced. While c.scale does not prevent the user from counting the carbon storage benefits on other terms (as the list below is nonexhaustive), we recommend meeting at least two out of the three criteria below in order to claim climate benefits from carbon storage:&#x20;

* **Transparency and traceability in the supply chain (required)**. Transparency and traceability in the supply chain. Claims can be made about the environmental attributes of timber are impossible to verify without transparency and traceability in the supply chain. This means that a project team should be able to identify:
  1. The source forest(s) or supply area(s)
     * _This is the area from which a primary manufacturer sources most or all of its logs, typically a circle drawn around the location of the site of the mill, with the size being dictated by the maximum hauling distance of the logs._
  2. The primary manufacturer mill(s)
     * _E.g., sawmill, veneer mill, chip mill, etc._
  3. The fabrication shop (for engineered timber).
* **Increasing forest carbon stocks (optional)**. Carbon storage in wood products can only be claimed if the carbon stock of the source forest is maintained or increasing. This means that the forest area is managed and regenerates in a way that either preserves or increases the average level of carbon stored in vegetation and soils, or that high conservation value or high carbon stock forests are not replaced by less ecological valuable and carbon rich production forests.
* **Certified, recycled, or reclaimed wood (optional)**. The use of recycled or reclaimed wood prolongs its storage of carbon and can displace the use of virgin timber. Certification by the Forest Stewardship Council (FSC) ensures that sound forestry, audit, and reporting practices are used.

**c.scale assumes that lumber, plywood, and mass timber assemblies are landfilled, recycled, or combusted for energy at the end of their useful life**. The mix of landfilling, combustion, and recycling is determined by the EPA analysis of US disposal in 2018. The emissions from these three activities are calculated with the EPA’s Waste Reduction Model (v15).

### Carbon storage in landscapes and green roofs

c.scale measures the annual carbon storage of in living and growing landscape. We assume that all plantings will achieve maturity across the building project's reference period. Carbon storage in the landscape is accrued year over year by amortizing the total carbon storage in mature landscapes over the model's reference period.&#x20;

Globally, the storage of carbon in plants is a major carbon sink. There are a number of imperatives for greening our built environment—such as [addressing a history of racist redlining](https://ehp.niehs.nih.gov/doi/full/10.1289/EHP7495), [reducing urban heat island](https://www.sciencedirect.com/science/article/abs/pii/S1618866718306411), or [contributing to mental wellness](https://www.sciencedirect.com/science/article/abs/pii/S0033350613002862)—that add positive co-benefits to the carbon storage potential of green space.&#x20;

In c.scale, landscaped area is assumed to approach its maximum storage potential (its "carrying capacity") over a 40 year period. The amount of carbon that a landscape can store is location-dependent (i.e., a landscape in Miami can store more carbon than one of a similar size in Arizona).&#x20;

Maintaining carbon storage in landscape requires maintenance. Emissions from the maintenance of carbon-storing landscape are assessed as embodied emissions. The storage potential of a landscape or green roof depends on its area, its specification (low, moderate, or high storage), and the location of the project.&#x20;

Note that there is no option in EPIC to describe turfgrass, as turfgrass is a net emitter.

Developing a "greenfield" site (one that has not been previously developed) will release carbon dioxide into the atmosphere. How EPIC calculates these emissions is described in the [Embodied Carbon](embodied-carbon.md#emissions-from-greenfield-development) section of the methodology.&#x20;

## Avoided carbon from surplus energy generation

Once production from an onsite solar array has zero'ed out annual electricity use, c.scale assumes all additional energy generated by the array displaces generation of electricity by the electrical grid. The avoided emissions from surplus onsite energy generation are calculated as the emissions that this displaced energy would have incurred.&#x20;

This method assumes that there is no curtailment of PV production, and that the carbon emissions of grid electricity when solar energy is produced is substantially similar to the annual average emissions. In locations with a high proportion of solar on the grid, _these assumptions will not hold_ and skepticism of c.scale's calculation of avoided emissions is warranted. Read more about curtailment in [this publication ](https://www.nrel.gov/docs/fy14osti/60983.pdf)(pdf) from there National Renewable Energy Laboratory.&#x20;

The assumption of displacement generation will not hold true in all locations, and some skepticism of this estimate is encouraged. Two interrelated situations where c.scale's assumptions of displaced generation will not hold are when:

* Daytime (i.e., when solar is available) emissions from the electrical grid are significantly lower than the national average.
* Surplus energy generation is expected to be curtailed by the utility.  For an overview of curtailment in the United States, we recommend [this report from NREL](https://www.nrel.gov/docs/fy14osti/60983.pdf) (pdf).

If you are interested in further analysis of hourly emissions, [please reach out](mailto:epic@ehddd.com).&#x20;
