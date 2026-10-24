# Neighbourgoods — Distributed Platform for Joint Procurement of Essential Goods

Diploma project, Astana IT University.
A distributed platform that lets residents of a local residential community organise and join group purchases of essential goods.

## Problem Statement

Group purchases in residential communities are usually coordinated through messaging apps and spreadsheets. Organisers have to collect requests, calculate quantities, track changes and announce updates manually. This can lead to missed requests, inconsistent records, calculation errors and unclear deadlines or collection arrangements.

The project investigates these problems and builds a dedicated platform for managing the group purchasing process. Initial assumptions are validated through a user questionnaire and prototype evaluation; they are not treated as confirmed facts.

## Target Users

- **Residents** — join a community, browse group purchases, submit/modify/cancel requests, track order and collection status.
- **Community organisers** — create a community, publish purchases, confirm them with a supplier, publish collection details and record collection. An organiser can also take part as a resident.

Suppliers communicate with organisers outside the platform and have no accounts in the initial version.

## Expected Outcomes

- A Flutter mobile application supporting the main group purchasing scenario.
- A backend application and database with documented interfaces and access rules.
- Requirements specification, architecture diagrams and an interface prototype.
- A documented verification and evaluation report.
- A Git repository with source code, documentation, review history and links to YouTrack tasks.

## Team

| Member | Role |
|---|---|
| Skakova Tomiris | Frontend and mobile application development |
| Orynbassarova Dinara | Backend development and system architecture |
| Dauletbayeva Aitolkyn | Database design and quality assurance |

**Academic supervisor:** Salkenov Aldiyar

## Scope

**Included:** registration and authentication; communities and invitation codes; resident/organiser roles; creation and publication of group purchases; goods, prices, minimum quantities and deadlines; submission, modification and cancellation of requests; automatic totals and aggregate quantities; purchase and order status tracking; basic notifications; collection information and collection recording.

**Excluded:** integrated payments and escrow, delivery routing, supplier accounts and integrations, perishable goods, a full messaging service, AI recommendations. Payments take place outside the platform.

Full details: [docs/01-proposal.md](docs/01-proposal.md).

## Current Status

Stage: **analysis, design and prototyping** (pre-defense 1).

| Area | Status |
|---|---|
| Proposal and scope | Done |
| Evidence of relevance (questionnaire) | Done, exploratory; response counts being reconciled |
| Literature review, existing systems, technology comparison | Done (draft) |
| Requirements and acceptance criteria | Initial draft |
| Architecture diagrams | Done (initial design), supervisor review pending |
| HTML prototype | Done, user evaluation pending |
| Verification and evaluation plan | Done (plan only, no test results yet) |
| Supervisor feedback | Done |
| Application (Flutter, backend, database) | Not started |

The complete application is not implemented yet. The HTML prototype demonstrates selected interface interactions only.

## Selected Technologies

| Component | Technology | Status |
|---|---|---|
| Mobile application | Flutter, Dart | Selected |
| Backend | Spring Boot — Java | Preliminary recommendation |
| Database | PostgreSQL | Preliminary recommendation |
| Client–server communication | HTTPS API with JSON | Preliminary recommendation |

Alternatives and reasoning: [docs/05-technology-comparison.md](docs/05-technology-comparison.md).

## Project Management

- **YouTrack:** https://neighbourgoods.youtrack.cloud/projects/NG
- Branches and commits reference YouTrack task IDs, for example `NG-30-readme` and `NG-30: Add project README`.
- Changes go to `main` through pull requests reviewed by another team member.
- Each pre-defense submission is marked with a Git tag (`pre-defense-1`, `pre-defense-2`, `final-pre-defense`).

## Documentation

| # | Document |
|---|---|
| 1 | [Project proposal](docs/01-proposal.md) |
| 2 | [Evidence of relevance](docs/02-relevance-evidence.md) (figures in [docs/evidence](docs/evidence)) |
| 3 | [Literature review](docs/03-literature-review.md) |
| 4 | [Existing system comparison](docs/04-existing-systems.md) |
| 5 | [Technology comparison](docs/05-technology-comparison.md) |
| 6 | [Requirements specification](docs/06-requirements.md) |
| 7 | [Architecture and diagrams](docs/07-architecture.md) |
| 8 | [UX and interactive prototype](docs/08-prototype.md) |
| 9 | [Verification and evaluation plan](docs/09-verification-plan.md) |
| 10 | [Project management and risks](docs/10-project-management-risks.md) |

## Repository Structure

```
.
├── README.md
├── docs/        project documentation and evidence figures
├── diagrams/    PlantUML sources (.puml) and exports (.png, .svg)
└── UX/          interactive HTML prototype (index.html)
```

Source code, tests and configuration examples will be added when implementation starts.

## Diagrams

Editable PlantUML sources and exports are in [diagrams](diagrams): system context, use case, component (draft) and container diagrams.

## How to Run the Prototype

No installation is needed.

1. Download or clone the repository.
2. Open `UX/index.html` in a web browser.
3. Use the role switch to see organiser controls. The reset button restores the demonstration data.

Data is stored in the browser (localStorage) and is not shared between users or devices. There is no backend yet.

## Setup and Testing

Setup, execution and testing instructions for the application will be added as soon as runnable code is available.
