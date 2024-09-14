<!--
This is a template for [Documenting Architecture Decisions - Michael Nygard](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions).

You can use [adr-tools](https://github.com/npryce/adr-tools) for managing the ADR files.

In each ADR file, write the following sections.
-->
# 1. Sbom Generation Tool Selection

Date: 2024-08-09

## Status
<!--
A decision may be "proposed" if the project stakeholders haven't agreed with it yet, or "accepted" once it is agreed.
If a later ADR changes or reverses a decision, it may be marked as "deprecated" or "superseded" with a reference to
its replacement.
-->
Proposed

## Context
<!--
This section describes the forces at play, including technological, political, social, and project local. These forces
are probably in tension, and should be called out as such. The language in this section is value-neutral. It is simply
describing facts.
-->
> What is the issue that we're seeing that is motivating this decision or change?

For phase 1, the Tiger Team selected [keycloak](https://github.com/keycloak/keycloak) as a java open source project to create a SBOM for. Since different ecosystems have different support by different tools, we did an un-official
trade study of different SBOM generation tools to decide what was best to use for this first project.

## Decision
<!--
This section describes our response to these forces. It is stated in full sentences, with active voice. "We will …"
-->
> What is the change that we're proposing and/or doing?

The tiger team is proposing we use [trivy](https://github.com/aquasecurity/trivy) and analyze source of the keycloak project.

- [Un-official Trade Study](https://github.com/CISA-SBOM-Community/SBOM-Generation/issues/7)

This decision is based on the following factors:

- Analysis of the components discovered in comparison of other tools
- Ability to generate both CycloneDX and SPDX SBOMs
- Completness of the depenency graph
- Compliance with the NTIA Minimum Elements

### Honorable Mentions

#### Syft

[Syft](https://github.com/anchore/syft) met most of the requirements but ultimated decided against for three reasons.

- Number of duplicate components
  - We found Syft generated a lot of duplicate componets in the sbom which increases it size and complexity without adding value
- Source code scanning maven build variables
  - Some build variables for component names were not expanded resulting in variable names being used for component identification
- Jar scanning dependency graph incomplete
  - Syft Jar scanning added hashes to the sboms, but lacked the dependency graph information

#### cyclonedx-maven-plugin

[cyclonedx-maven-plugin](https://github.com/CycloneDX/cyclonedx-maven-plugin) definitely produced the best "per component" completeness of the NTIA Minimum Elements, but was decided against for two reasons.

- No SPDX Support
  - A requirement for this tiger team is to support both major SBOM formats. [cyclonedx-maven-plugin](https://github.com/CycloneDX/cyclonedx-maven-plugin) only supports CycloneDX
- Needs to be added to all project `pom.xml` files
  - We want to avoid directly modifying the configuration files of Keycloak for the purpose of this example workflow. If this were to be incorporated directly into the project this would not be an issue.

:note: If you only need CycloneDX sboms for a java project, we'd recommend teams investigate this tool.

## Consequences
<!--
This section describes the resulting context, after applying the decision. All consequences should be listed here, not
just the "positive" ones. A particular decision may have positive, negative, and neutral consequences, but all of them
affect the team and project in the future.
-->
> What becomes easier or more difficult to do because of this change?

Some information will be harder to enrich later in the SBOM Generation Pipeline.

Specifically:

- hashes
