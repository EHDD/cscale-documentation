# Stored Carbon

## Biogenic Carbon

Living systems present a particular challenge for carbon emission accounting. Static emission factors are sufficient for manmade or mineral materials, but biogenic materials—those materials, such as forest products, originating from living systems—can’t be as easily summarized. Through photosynthesis, living materials remove carbon from the atmosphere as they grow; and return that carbon to the atmosphere as emissions when they decompose or combust. While the primary mechanisms of biogenic carbon sequestration, storage, and emissions are well understood, they are inconsistently applied and reported across various product and building standards, making comparison and reporting at a building scale challenging.

Biogenic carbon can be reported using one of two approaches:&#x20;

* **Biogenic Carbon Emissions (GWP-bio):** When reported as an emission, GWP-bio must be calculated separately from fossil emissions and will include multiple greenhouse gases, such as carbon dioxide, methane, and nitrous oxide. Quantification and reporting of biogenic carbon emissions differ between ISO and EN standards and are currently not harmonized across North American and European EPDs. Additionally, some emissions, such as those associated with the burning of biomass during manufacturing, are often omitted based on the assumption that biomass from sustainable forestry and other land management will rapidly grow back and can be assumed to be carbon neutral.&#x20;
* **Biogenic Carbon Storage (stored carbon):** Biogenic carbon (C) contained in bio-based materials can also be reported as an inventory metric. This value represents the quantity of carbon that was previously sequestered over the growth of the plant material and which is stored in the building materials during their useful life. Stored carbon is a simplified metric that does not represent all the complexity of biogenic carbon emissions during production or end of life, that the GWP-bio approach (described above) entails. It also does not include any representation of near-term emissions or how or when the carbon stock eventually leaves the "product system." For these reasons, stored carbon is reported separately from emissions and should not be combined with GWP-total. These values can be used as inputs to models that value short-term and durable carbon storage, such as the [Construction Stored Carbon Standard](https://climatecleanup.org/constructionstoredcarbon/) by Climate Cleanup.&#x20;

## C.Scale approach&#x20;

C.Scale reports all embodied fossil carbon emissions  (GWP-fossil) associated with manufacturing, use, and end-of-life of bio-based materials, but does not include the "negative emissions" from biogenic carbon stored in the product entering the "product system" in modules A1-3, nor the release of CO2 back to the atmosphere in C3. The model adopts a carbon balance approach over the lifetime of the building. Biogenic carbon storage is only shown as additional information.  Currently, C.Scale does not report biogenic carbon emissions (GWP-bio) per life cycle stage.&#x20;

This approach is compatible with the approach adopted by the [Carbon Leadership Forum WBLCA Benchmarking Study v2 (2024)](https://carbonleadershipforum.org/clf-wblca-v2/), and is comparible to results from [OneClick's (TRACI) WBLCA tool](https://oneclicklca.zendesk.com/hc/en-us/articles/360015036640-Biogenic-Carbon), and [Tally](https://choosetally.com/methods/) (excluding biogenic carbon).&#x20;

Fossil emissions (GWP-fossil) associated with the extraction, transportation, manufacturing, and disposal of bio-based materials are always counted in the C.Scale model and are reported in the life cycle stage in which they occur. C.Scale assumes that lumber, plywood, and mass timber assemblies are landfilled, recycled, or combusted for energy at the end of their useful life. The mix of landfilling, combustion, and recycling is determined by the EPA analysis of US disposal in 2018. The emissions from these three activities are calculated with the EPA’s Waste Reduction Model (v15).

This approach differs from other methods and regulatory standards, such as E15804+A2, where biogenic carbon is reported as an emission (GWP-bio) that can be summed with other emissions (GWP-fossil, GWP-luluc). C.Scale aims to expand this functionality in the future.&#x20;

## Carbon storage in wood products

To calculate stored carbon, C.Scale follows an equation provided in EN16449 and referenced by ISO21930 and EN15804+A2 that estimates the carbon content per volume of product. As materials represented in the C.Scale model are generic, rather than product-specific, the dataset uses standard assumptions for density and moisture content.

Carbon Storage is expressed with the following equation:

$$
P_{CO2}=  44/12* cf* (\frac{ ρ_ω*V_ω}{1+ω/100})
$$

Where:

&#x20;$$P_{CO2}$$ = the biogenic carbon oxidized as carbon dioxide emissions from the product system into the atmosphere

44/12 = ratio of molecular mass of CO2 and C molecules

$$cf$$ = carbon fraction of woody biomass (oven dry mass), 0.5 used as a default value

$$w$$ = moisture content of the product, 15% used as a default value

$$ρ_ω$$  = density of woody biomass at that moisture content (kg/m3)

&#x20;$$V_w$$ = volume of solid wood product at that moisture content (m3)

&#x20;

For engineered wood products, wood volume content  $$V_w = VP *$$ % wood or bio content in full product

&#x20;$$VP$$ =gross volume of the wood-based product



**Carbon storage in lumber, plywood, and mass timber assemblies should only be counted if those materials are sourced from responsibly managed forests**. Practically, this can mean a number of things. In C.Scale, we identify three criteria contributing to the claim that wood products are responsibly sourced. While C.Scale does not prevent the user from counting the carbon storage benefits on other terms (as the list below is non-exhaustive), we recommend meeting at least two out of the three criteria below in order to claim climate benefits from carbon storage:

* **Transparency and traceability in the supply chain (required)**. Transparency and traceability in the supply chain. Claims can be made about the environmental attributes of timber are impossible to verify without transparency and traceability in the supply chain. This means that a project team should be able to identify:
  1. The source forest(s) or supply area(s)
     * _This is the area from which a primary manufacturer sources most or all of its logs, typically a circle drawn around the location of the site of the mill, with the size being dictated by the maximum hauling distance of the logs._
  2. The primary manufacturer (_sawmill, veneer mill, chip mill, etc.)_
  3. The fabrication shop (for engineered timber).
* **Increasing forest carbon stocks (optional)**. Carbon storage in wood products can only be claimed if the carbon stock of the source forest is maintained or increasing. This means that the forest area is managed and regenerates in a way that either preserves or increases the average level of carbon stored in vegetation and soils, or that high conservation value or high carbon stock forests are not replaced by less ecologically valuable and carbon-rich production forests.
* **Certified, recycled, or reclaimed wood (optional)**. The use of recycled or reclaimed wood prolongs its storage of carbon and can displace the use of virgin timber. Certification by the Forest Stewardship Council (FSC) ensures that sound forestry, audit, and reporting practices are used.

**C.Scale assumes that lumber, plywood, and mass timber assemblies are landfilled, recycled, or combusted for energy at the end of their useful life**. The mix of landfilling, combustion, and recycling is determined by the EPA analysis of US disposal in 2018. The emissions from these three activities are calculated with the EPA’s Waste Reduction Model (v15).

## Carbon storage in landscape and site features&#x20;

C.Scale measures the annual carbon storage of in living and growing landscapes. We assume that all plantings will achieve maturity across the building project's reference period. Carbon storage in the landscape is accrued year over year by amortizing the total carbon storage in mature landscapes over the model's reference period.

Globally, the storage of carbon in vegetation and soils is a major carbon sink. There are a number of imperatives for greening our built environment—such as [addressing a history of racist redlining](https://ehp.niehs.nih.gov/doi/full/10.1289/EHP7495), [reducing urban heat island](https://www.sciencedirect.com/science/article/abs/pii/S1618866718306411), or [contributing to mental wellness](https://www.sciencedirect.com/science/article/abs/pii/S0033350613002862)—that add positive co-benefits to the carbon storage potential of green space.

In C.Scale, the landscaped area is assumed to approach its maximum storage potential (its "carrying capacity") over a 60-year period after site disturbance. The amount of carbon that a landscape can store is location-dependent (i.e., a landscape in Miami can store more carbon than one of a similar size in Arizona).

Many designed landscapes undergo regular maintenance. Emissions from the maintenance of carbon-storing landscapes are assessed as embodied emissions. The storage potential of a landscape or green roof depends on its area, its specification (low, moderate, or high storage), and the location of the project.



## Timing of Carbon Storage

Carbon storage in structural materials is assessed once in the first year of the project, and landscape sequestration is assessed each year. Biogenic carbon sequestration is evaluated with the following expression:

$$
Carbon\ Storage=x_i\ast C_i+\ \sum_{t=1}^{m}\ A_k\ast C_k
$$

Where $$x_i$$ is the quantity of structural wood products $$i$$, $$C_i$$ is the carbon content per unit $$i$$,$$A_k$$ is the area A of planting type k, and $$C_k$$ is the carbon sequestration in year $$t$$ per area of planting $$k$$.

