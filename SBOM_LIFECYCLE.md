# SBOM Life Cycle

![https://raw.githubusercontent.com/CISA-SBOM-Community/SBOM-Generation/main/assets/lifecycle.svg]

# Generation
The generation incorporates the steps required to generate an NTIA Minimum Elements and/or Framing Document SBOM. The life cycle is format agnostic and is the same for both SPDX and CycloneDX (even though the tools may differ).

## Creation
The creation step is where SBOM is conceived. The level of "completeness" of this SBOM will vary a great amount depending on the tool used, as well as what language you're working with. It will also matter if the SBOM is a source or build SBOM. Using build SBOMs is recommended to achieve higher completeness.

You should ideally have an SBOM that captures all transient dependencies with hashes for all components (and sub-components).

## Augmentation
The augmentation phase is where we merge in data that cannot be automatically generated in the creation phase. This include, but is not limited to information, such as:

* Information about the author
* Licensing information
* Information about the supplier

The objective of this phase is to fill in information mandated by NTIA Minimum Elements.

## Enrichment
The enrichment phase may or may not be needed, depending on the tool used in the creation phase. The objective of this phase is to ensure that we capture all mandatory data about our components (and sub-components), such as licensing. This step often requires the tool to reach out to a 3rd party database, such as a packaging sites.

## Signing (optional)
The next step is the optional signing phase. Only when we have reached our desired level of completeness can we sign off an SBOM. This can either be cryptographically signed (ideally), or a simple checksum hash.

Ideally, this all all happens in the same CI/CD run as the generation.

## Consolidation
The consolidation phase is where we tie together multiple SBOMs. For even small projects, you are likely to have multiple SBOMs. For instance, you may have a container SBOM and an application SBOM. This phase is about creating a top-level SBOM that references the two (or more) SBOMs.

Note that the Consolidation step could also be done in the Collaboration phase of the life cycle.

# Collaboration
The collaboration phase is about distributing the SBOM from the CI/CD pipeline to internal or external stakeholders. Depending on the industry, there maybe specific platforms available.

There is also an attempt to create an open standard for sharing and discovering SBOMs under CycloneDX called Transparency API Exchange (TEA), which is also known as Project Koala.

# Analysis
The analysis phase is when the SBOM is actually used. There are largely two buckets of use cases for SBOMS: license and/or security compliance. There are a large number of tools (both proprietary and open source) available for this phase.

