# Cloud-Native Product Delivery Platform

A portfolio project that treats a cloud delivery platform as a **product**: defining the problem, the users, the requirements, and the measurable outcomes before choosing technology. It is extended with an **AI Delivery Insights Assistant** that explains failed pipelines from supplied evidence.

> **This is a simulated scenario** built for learning and portfolio purposes. The stakeholders and requirements are fictional, and all data comes from sample applications and simulated inputs. Nothing here is a production system, and results are documented as they are measured.

## The problem
Teams in an engineering organization each set up their own infrastructure, deployments, security checks, and monitoring. The result is inconsistent delivery, duplicated effort, late security feedback, and unclear costs. This project defines a **golden path** from source code to an operational AWS workload.

**Golden path:** Source Code → Pull Request → Automated Validation → Security Scanning → Container Build → Artifact Storage → Deployment → Health Validation → Operational Visibility

## Start here
1. [Product brief](docs/01-product/PRODUCT_BRIEF.md)
2. [Progress log](docs/PROGRESS_LOG.md)

## Status
| Area | Status |
|---|---|
| Product definition | In progress |
| Backlog and requirements | Not started |
| Architecture and ADRs | Not started |
| Sample application | Not started |
| Infrastructure as code | Not started |
| CI/CD and security | Not started |
| Operations and cost | Not started |
| AI assistant | Not started |
| Acceptance report | Not started |

## What is implemented vs planned
Updated every week. Anything not listed as implemented is planned or simulated.

| Capability | Implemented | Simulated | Planned |
|---|---|---|---|
| _Nothing yet_ | | | |

## Repository structure
```
docs/            Product, requirements, architecture, delivery, validation, AI
application/     Sample application delivered through the platform
infrastructure/  Terraform
ai-assistant/    AI Delivery Insights Assistant prototype
.github/         GitHub Actions workflows
```

## Security
No secrets, credentials, API keys, or Terraform state files are committed to this repository. See `.gitignore`.
