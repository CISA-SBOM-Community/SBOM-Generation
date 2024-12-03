# SBOM Generation Reference Implementations

## Why This Matters

Creating high-quality Software Bills of Materials (SBOMs) is crucial for software transparency and security. However, the current landscape lacks a "golden path" for consistent SBOM generation. This project aims to bridge that gap by providing reference implementations that adhere to our [SBOM Lifecycle](https://github.com/CISA-SBOM-Community/SBOM-Generation/blob/main/SBOM_LIFECYCLE.md).

## How This Is Different

There are several open-source tools that assist with SBOM generation (shout out to [Syft](https://github.com/anchore/syft) and [Trivy](https://github.com/aquasecurity/trivy)), but there are two key steps these tools don't perform.

- `Augmentation` : They will not populate top-level metadata (we call this the "augmentation" step) to include license, supplier, and description information.
- `Enrichment` : They don't often add additional items for each component in the SBOM from open data sets (we call this the "enrichment" step), which adds the NTIA required fields to each component.

These reference implementations create a complete set of automated steps that anyone can use to create more "complete" SBOMs that demostrate `Augmentation` and `Enrichment`.

## Reference Implementation

All reference implementations follow a very similar flow and can easily be adapted to other applications or languages. We're always looking to add additional implementations; pull requests are welcome!

- Keycloak (Java) - [Description](phase_1/keycloak/README.md) - [GitHub Workflow](.github/workflows/phase_1_keycloak.yml) - [GitLab Pipeline](https://gitlab.com/cisa-sbom-community/SBOM-Generation/-/blob/main/.gitlab/ci/phase_1_keycloak.yml?ref_type=heads)
- Django Application (Python) - [GitHub Workflow](.github/workflows/phase_1_python.yml) - [GitLab Pipeline](https://gitlab.com/cisa-sbom-community/SBOM-Generation/-/blob/main/.gitlab/ci/phase_1_python.yml?ref_type=heads)
- kubectl (Go) - [GitHub Workflow](.github/workflows/phase_2_kubectl.yml) - [GitLab Pipeline](https://gitlab.com/cisa-sbom-community/SBOM-Generation/-/blob/main/.gitlab/ci/phase_2_kubectl.yml?ref_type=heads)

## Meeting

This Tiger Team meets weekly to further refine and improve working examples. Anyone is welcome to join!

Tuesdays @ 10am Eastern / 7am Pacific

- [Teams Meeting Link](https://gov.teams.microsoft.us/l/meetup-join/19%3agcch%3ameeting_1fa6f7bb9186450fa64a2f0c0c497131%40thread.v2/0?context=%7b%22Tid%22%3a%22b18f006c-b0fc-467d-b23a-a35b5695b5dc%22%2c%22Oid%22%3a%226bb34de0-3fc5-496b-bf75-8faac6ae6e1a%22%7d)
- [Meeting Notes](https://docs.google.com/document/d/1ZWDFWVd5XStE2iOX041Q-uB0VdHXUnIB0YyAnIRSs5s/edit)

## Contribution

We welcome contributions from anyone in the community, especially individuals with:

- DevSecOps experience (GitLab and GitHub platforms).
- Open-source project experience (asynchronous collaboration).

Please read the [Contribution Guidance](CONTRIBUTING.md).

## Join the Effort

We invite you to participate in this effort to standardize SBOM creation. Stay tuned for further updates!
