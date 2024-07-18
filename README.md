# SBOM Generation Reference Implementations

## Why This Matters

Creating high-quality Software Bills of Materials (SBOMs) is crucial for software transparency and security. However, the current landscape lacks a "golden path" for consistent SBOM generation. This project aims to bridge that gap by providing reference implementations.

## Goals

This project will create example pipelines/workflows in GitHub and GitLab demonstrating how to generate quality SBOMs for various software types:

### Phase 1

- Java Application
- Python Container Image

### Phase 2

- Go Application
- Container Image with Go application

~Stretch Goal~: Workflows for creating SBOMs with multiple dependency trees (SBOM nesting)

### Phase 3

- "Legacy" C or C++ Application

These examples will function independently on public or private GitHub/GitLab instances and be reusable through GitLab CI/CD or GitHub Actions.

## "Done" Definition

The project will be considered "done" when:

- Each application has a corresponding GitHub and GitLab project.
- Workflows in these projects create SBOMs that:
  - Meet and exceed NTIA Minimum Elements.
  - Align with relevant Community Tiger Team whitepapers.
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

## Timeline & Contribution

This project has an estimated end date of [Target End Date]. We welcome contributions from individuals with:

- DevSecOps experience (GitLab & GitHub platforms).
- Open-source project experience (asynchronous collaboration).

## Join the Effort

We invite you to participate in this effort to standardize SBOM creation. Stay tuned for further updates!
