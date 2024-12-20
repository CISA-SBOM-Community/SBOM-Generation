# Kubectl (Go) SBOM Generation

This workflow illustrates creation of SPDX and CycloneDX SBOMs for a golang application. [Kubectl](https://github.com/kubernetes/kubectl) is used as an example due to its wide use and complexity. The workflow is well commented and can be used as a reference implementation for your own projects.

- [.github/workflows/phase_2_kubectl.yml](../.github/workflows/phase_2_kubectl.yml)

## Reference Impelementation Objectives

- Create both SPDX and CycloneDX SBOMs using open source tools
- Showcase the additional SBOM lifecycle steps
- Provide sample tools and implementation for others to use

![SBOM Lifecycle](../assets/lifecycle.svg)

- `Generate SBOM with Trivy` Job
  - __Tool__
    - [trivy](https://github.com/aquasecurity/trivy)
  - __Notes__
    - Analyze the kubectl source code using [trivy](https://github.com/aquasecurity/trivy). There are several great open source sbom generation tools, and this could easily be replaced with a tool of your choice.
- `Augment Kubectl SPDX` and `Augment Kubectl CycloneDX` Jobs
  - __Tool__
    - [sbomasm](https://github.com/interlynk-io/sbomasm)
  - __Notes__
    - There is metadata that typically cannot be determined through analysis. This is metadata that needs to be determined by the author of the primary component and author of the SBOM document. Examples of this information are project description, SBOM author, and supplier.
    - There are multiple ways to augment this metadata, you can use [jq](https://jqlang.github.io/jq/), write a custom application, or merge a static SBOM into a generated one.
- `Enrich Kubectl SPDX` and `Enrich Kubectl CycloneDX` Jobs
  - __Tool__
    - [parlay](https://github.com/snyk/parlay)
  - __Notes__
    - SBOM generation tools usually find components and their dependencies by analyzing package manager configuration files. This _usually_ does not provide enough information to meet NTIA minimum elements, and tools like [parlay](https://github.com/snyk/parlay) can enrich components in an SBOM by looking up additional component metadata from external databases.
- `Display SBOM quality score through sbomqs` Job
  - __Tool__
    - [sbomqs](https://github.com/interlynk-io/sbomqs)
