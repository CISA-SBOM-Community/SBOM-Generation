# SBOM Life Cycle

![SBOM Life Cycle Diagram](https://raw.githubusercontent.com/CISA-SBOM-Community/SBOM-Generation/main/assets/lifecycle.svg)

# Authoring

The authoring incorporates the steps required to generate an NTIA's [Minimum Elements](https://www.ntia.gov/sites/default/files/publications/sbom_minimum_elements_report_0.pdf) and/or [Framing Software Component Transparency: Establishing a Common Software Bill of Materials (SBOM)](https://docs.google.com/document/d/1uddfhPqflTOeYK7ZJjS4gGa8pspwez6mhJUjTrvu4J4/edit) (Third Edition). The life cycle is format-agnostic and is the same for both SPDX and CycloneDX (even though the tools may differ).

This should be considered complementary to CISA's [Software Bill of Materials (SBOM) Sharing Lifecycle Report](https://www.cisa.gov/sites/default/files/2023-04/sbom-sharing-lifecycle-report_508.pdf).

## Generation

The generation step is where an SBOM is conceived. The level of "completeness" of this SBOM will vary greatly depending on the tool used, as well as what language you're working with. It will also matter if the SBOM is a source or build SBOM. Using build SBOMs is recommended to achieve higher completeness.

You should ideally have an SBOM that captures all transient dependencies with hashes for all components (and sub-components).

## Validation

A minimum validation would be to ensure the resultant SBOM meets the format requirements for the standard. This can be done by running utilities or validating against schemas provided by the format standard community. Additional validation can include semantic validation, validating the SBOM meets the minimum requirements, and enhances SBOM quality.  

## Augmentation

The augmentation phase is where we merge in data that cannot be automatically generated in the creation phase. This includes, but is not limited to, information such as:

* Information about the author
* Licensing information
* Information about the supplier

The objective of this phase is to fill in information mandated by NTIA Minimum Elements.

## Enrichment

The enrichment phase may or may not be needed, depending on the tool used in the creation phase. The objective of this phase is to ensure that we capture all mandatory data about our components (and sub-components), such as licensing. This step often requires the tool to reach out to a third-party database, such as packaging sites.

## Signing (optional)

The next step is the optional signing phase. Only when we have reached our desired level of completeness can we sign off an SBOM. This can either be cryptographically signed (ideally), or a simple checksum hash.

Ideally, this all happens in the same CI/CD run as the generation.

## Document Linking (optional)

Even for a small SBOM implementation, you are likely to generate dozens of SBOMs across containers and various language stacks. Instead of merging them into a single, consolidated SBOM, we recommend structuring them hierarchically. For example, microservices can be grouped into their own SBOMs, forming intermediate layers that are then tied together into a top-level SBOM. This hierarchical approach retains critical context about where components reside (e.g., which services or microservices they belong to) while providing a structured view of dependencies. In CycloneDX, this can be achieved using `externalReferences` to link SBOMs, while SPDX supports similar linking mechanisms. This method ensures clarity, scalability, and maintainability across complex software stacks.

## Consolidation

The consolidation phase is where we tie together multiple SBOMs. For even small projects, you are likely to have multiple SBOMs. For instance, you may have a container SBOM and an application SBOM. This phase is about creating a top-level SBOM that references the two (or more) SBOMs.

Note that the consolidation step could also be done in the transportation phase of the life cycle.

# Transportation

The transportation phase is about distributing the SBOM from the CI/CD pipeline to internal or external stakeholders. Depending on the industry, there may be specific platforms available.

There is also an attempt to create an open standard for sharing and discovering SBOMs under CycloneDX called [Transparency API Exchange](https://github.com/CycloneDX/transparency-exchange-api) (TEA), which is also known as Project Koala.

Inspiration has also been drawn from the [CISA SBOM Sharing Primer](https://www.cisa.gov/sites/default/files/2024-05/SBOM%20Sharing%20Primer.pdf).

# Analysis

The analysis phase is when the SBOM is actually used. There are largely two buckets of use cases for SBOMs: license and/or security compliance. There are a large number of tools (both proprietary and open-source) available for this phase.
