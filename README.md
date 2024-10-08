# SBOM Generation Reference Implementations

## Why This Matters

Creating high-quality Software Bills of Materials (SBOMs) is crucial for software transparency and security. However, the current landscape lacks a "golden path" for consistent SBOM generation. This project aims to bridge that gap by providing reference implementations that adheres to our [SBOM Lifecycle](https://github.com/CISA-SBOM-Community/SBOM-Generation/blob/main/SBOM_LIFECYCLE.md).

## Meeting

Tuesdays @ 10am Eastern / 7am Pacific

- [Teams Meeting Link](https://gov.teams.microsoft.us/l/meetup-join/19%3agcch%3ameeting_1fa6f7bb9186450fa64a2f0c0c497131%40thread.v2/0?context=%7b%22Tid%22%3a%22b18f006c-b0fc-467d-b23a-a35b5695b5dc%22%2c%22Oid%22%3a%226bb34de0-3fc5-496b-bf75-8faac6ae6e1a%22%7d)
- [Meeting Notes](https://docs.google.com/document/d/1ZWDFWVd5XStE2iOX041Q-uB0VdHXUnIB0YyAnIRSs5s/edit)

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

## Contribution

We welcome contributions from anyone in the community and especially individuals with:

- DevSecOps experience (GitLab & GitHub platforms).
- Open-source project experience (asynchronous collaboration).

Please read the [Contribution Guidance](CONTRIBUTING.md).

## Join the Effort

We invite you to participate in this effort to standardize SBOM creation. Stay tuned for further updates!
