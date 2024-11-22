# Governance

## Principles

The CISA SBOM Community SBOM Reference Implementation Tiger Team adheres to the following principles:

- __Open__: This project is intended for public use and are considered a public good
- __Welcoming and respectful__: See [Code of Conduct](CODE_OF_CONDUCT.md)
- __Patience__: Expect to move slower together than fast alone
- __Transparent and accessible__: Work and collaboration should be done in public. Please create issues and use community channels to discuss contributions before implementation.
- __Merit__: Ideas and contributions are accepted according to their technical merit and alignment with project goals, scope, design principles, and most importantly stability for existing users.

## Goals

This project will create example pipelines/workflows in GitHub and GitLab demonstrating how to generate quality SBOMs for various software types:

### SBOM Type

This activity only covers [SBOMs of Type Source or Build](https://www.cisa.gov/sites/default/files/2023-04/sbom-types-document-508c.pdf) as SBOMs of other types are typically not curated by the maintainers of Open Source software but instead by consumers of Open Source software. For Source and Build SBOMs, the contents of the SBOM describing the artifact will only include what is being distributed and will not contain information about prospective uses of the software during or after installation or running of the software. That information is captured in separate SBOM types (ie Deployment, Runtime).

> In the context of this document, the “source” is defined as a snapshot of the source code made available to download, such as in a tgz archive.
> The “build” is the artifacts that are built by the project and released. These could be tgz archives, but also other artifacts such as rpm, deb, or zip.

### Phase 1

- Java Application
- Container Image with Python (Django) application

### Phase 2

- Go Application
- Container Image with Go application

__Stretch Goal__: Workflows for creating SBOMs with multiple dependency trees (SBOM nesting)

### Phase 3

- "Legacy" C or C++ Application

These examples will function independently on public or private GitHub/GitLab instances and be reusable through GitLab CI/CD or GitHub Actions.

## "Done" Definition

The project will be considered "done" when:

- Each application has a corresponding GitHub and GitLab project.
- Workflows in these projects create SBOMs that:
  - Meet and exceed NTIA Minimum Elements.
  - Align with relevant Community Tiger Team whitepapers.
    - [SBOM Sharing Primer](https://www.cisa.gov/sites/default/files/2024-05/SBOM%20Sharing%20Primer.pdf)
    - [Framing Software Component Transparency Third Edition (DRAFT)](https://docs.google.com/document/d/1uddfhPqflTOeYK7ZJjS4gGa8pspwez6mhJUjTrvu4J4/edit?usp=sharing)
  - Are stored following OpenSSF guidance (including examples for importing into tools like DependencyTrack).
- A white paper documents:
  - Hurdles encountered during development.
  - Solutions implemented to achieve consistent messaging.
  - Areas for future improvement.

### Deliverables

- Public GitHub projects for each application.
- Public GitLab projects for each application.
- White paper outlining project learnings and future directions.

## In Scope

- Functioning GitHub Actions or GitLab CI/CD pipelines generating high-quality SBOMs.
- SBOMs adhering to NTIA Minimum Elements and exceeding expectations.
- SBOMs aligning with Community Tiger Team whitepaper recommendations.
- Documentation of limitations due to immature tooling.
- OpenSSF-compliant SBOM storage with import examples into other Open Source tools like DependencyTrack.
- Open-source tooling within pipelines/workflows (commercially-owned open-source tools allowed).
- Community feedback loop on generated SBOM completeness.
- SBOM generation in multiple formats/tools (JSON preferred, minimum CDX 1.5, minimum SPDX 2.3).
- Prioritization of Open Source and then Open Source with Commercial Backing tools.
- Automation (write-once, repeatable workflows).

## Out of Scope

- Non-open-source licensed tools.
- Complex systems-of-systems.
- A new open-source project to create GitHub Actions or GitLab Pipelines for others to consume.
- Tool deployments requiring maintenance or cost.
- SBOM signing (future Tiger Team initiative).

## Timeline

This project has an estimated end date of __January 14, 2025__, and has several intermediate due dates for each phase.

- Phase 1 (duration 6 weeks)
  - Expected completion __September 10, 2024__
- Phase 2 (duration 6 weeks)
  - Expected completion __October 22, 2024__
- Phase 3 (duration 6 weeks)
  - Expected completion __December 3, 2024__
- White Paper Completion (duration 6 weeks)
  - Expected completion __January 14, 2025__