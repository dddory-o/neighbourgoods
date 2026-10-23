# 6. Requirements Specification

## 6.1. Purpose and Status

This specification defines the initial functional and non-functional requirements for the distributed platform for group purchasing of essential goods within local residential communities.

The requirements are derived from the proposed project scope, literature review, and existing system comparison. They remain provisional pending analysis of survey responses and supervisor review. They must not be interpreted as confirmed user findings.

Each requirement has a unique identifier, priority, and acceptance criteria to support implementation and verification.

## 6.2. User Roles

| Role | Responsibilities and Access |
| --- | --- |
| **Resident** | Joins communities, browses purchases, manages personal requests, and views purchasing and collection information |
| **Organiser** | Creates and manages a community, publishes purchases, reviews participant requests, and manages confirmation and collection |

Roles are assigned within each community. An organiser may also participate as a resident. Organiser permissions in one community do not grant management access to another community.

Suppliers will interact with organisers outside the platform in the initial implementation.

## 6.3. Priorities

| Priority | Meaning |
| --- | --- |
| **Must Have** | Required to complete the principal purchasing workflow correctly |
| **Should Have** | Important supporting functionality that may be deferred if necessary |
| **Could Have** | Optional functionality considered after mandatory requirements are satisfied |

## 6.4. Functional Requirements

| ID | Requirement | Priority | Acceptance Criteria |
| --- | --- | --- | --- |
| FR-01 | User registration and authentication | Must Have | A user can create an account with valid credentials and sign in. Duplicate account identifiers and invalid credentials are rejected. Signing out removes the client’s authenticated session |
| FR-02 | Community creation | Must Have | An authenticated user can create a community with a name and description. The creator receives organiser permissions for that community |
| FR-03 | Community membership | Must Have | An authenticated user can join using a valid invitation code. Invalid codes are rejected, and repeated joining does not create duplicate membership |
| FR-04 | Community access control | Must Have | Members can access their community’s purchases. A non-member cannot retrieve private purchasing information or submit a request, including through direct API calls |
| FR-05 | Purchase creation and publication | Must Have | An organiser can save a draft and publish it after providing required product details, prices, units, minimum quantities, closing time, and payment and collection conditions |
| FR-06 | Purchase browsing | Must Have | A member can view purchases in a selected community and open their details, including products, prices, thresholds, deadline, organiser, and current status |
| FR-07 | Submission of participation requests | Must Have | A member can select available products and positive whole-number quantities while collection is open. The server calculates the total and returns confirmation of the saved request |
| FR-08 | Request modification and cancellation | Must Have | Before the closing time, a participant can modify or cancel their own request. Attempts after closure are rejected without changing stored quantities |
| FR-09 | Quantity aggregation | Must Have | The system displays aggregate quantities for each product. Cancelled requests are excluded, and successful changes are reflected in subsequent retrievals |
| FR-10 | Deadline enforcement | Must Have | At or after the server-defined closing time, new requests and participant changes are rejected. The purchase is subsequently recorded in the appropriate closed state |
| FR-11 | Threshold evaluation | Must Have | At closure, the system evaluates the minimum quantity for every listed product. The outcome follows the purchasing rules defined in Section 6.5 |
| FR-12 | Organiser confirmation | Must Have | Only an authorised organiser can confirm an eligible purchase after checking supplier availability. Reaching the threshold alone does not mark a purchase as confirmed |
| FR-13 | Purchase cancellation | Must Have | An organiser can cancel an unfinished purchase with a recorded reason. Participants can view the cancellation and reason; participation records remain available |
| FR-14 | Collection management | Must Have | The organiser can publish final collection details and mark a confirmed purchase as ready for collection. Each active participant can view their own allocation and collection information |
| FR-15 | Individual collection recording | Must Have | An organiser can mark an active participant’s order as collected. Repeating the action does not create duplicate collection records |
| FR-16 | Participant and order overview | Must Have | The organiser can view active participants, requested quantities, calculated totals, and collection states for purchases they manage |
| FR-17 | Purchase completion | Must Have | A purchase can be marked completed after all active participant orders have been recorded as collected |
| FR-18 | Personal request history | Should Have | A resident can retrieve their previous requests and associated purchase outcomes without accessing another resident’s private history |
| FR-19 | In-application notifications | Should Have | Confirmation, cancellation, and readiness for collection generate a visible notification for affected participants |
| FR-20 | Manual payment tracking | Could Have | An organiser can record payment receipt against a participant’s order. The interface identifies this as a manual record rather than automated bank verification |

## 6.5. Proposed Business Rules

The following rules establish a consistent initial workflow. They require confirmation by the team and supervisor.

| ID | Rule |
| --- | --- |
| BR-01 | Each purchase belongs to exactly one community |
| BR-02 | Only members of that community may participate |
| BR-03 | A user has one participation record per purchase, containing the requested product quantities |
| BR-04 | Products in the initial version are ordered as whole units or packages. Package size and unit of measurement must be stated |
| BR-05 | A purchase specifies one currency. Monetary calculations use exact decimal arithmetic or integer minor units |
| BR-06 | Published prices, minimum quantities, and the closing time cannot be changed after publication. If these conditions cannot be honoured, the organiser cancels the purchase and may create a replacement |
| BR-07 | At closure, every listed product must meet its minimum quantity. Otherwise, the entire purchase is marked unsuccessful; partial fulfilment is outside the initial scope |
| BR-08 | The server determines whether a deadline has passed. Device clock settings do not affect eligibility |
| BR-09 | Payments take place outside the platform. The platform does not transfer funds or automatically verify external payments |
| BR-10 | Cancelled and unsuccessful purchases retain their records for participant reference |
| BR-11 | Once collection has started, any cancellation must preserve existing collection records and identify unresolved orders. External refunds or disputes are handled outside the platform |

## 6.6. Purchase Lifecycle

| Status | Meaning | Permitted Next Status |
| --- | --- | --- |
| **Draft** | The organiser is preparing the purchase | Open for Requests |
| **Open for Requests** | Members may submit, modify, or cancel requests before the deadline | Awaiting Confirmation, Unsuccessful, Cancelled |
| **Awaiting Confirmation** | Collection has closed and all thresholds have been met | Confirmed, Cancelled |
| **Confirmed** | The organiser has confirmed fulfilment arrangements | Ready for Collection, Cancelled |
| **Ready for Collection** | Goods are available at the stated collection location | Completed, Cancelled |
| **Completed** | All active orders have been collected | Terminal state |
| **Unsuccessful** | At least one minimum quantity was not met | Terminal state |
| **Cancelled** | The organiser has cancelled the purchase with a reason | Terminal state |

Individual participation records will separately indicate whether a request is active, cancelled, ready for collection, or collected. Purchase cancellation must not erase the fact that an individual order was already collected.

## 6.7. Non-Functional Requirements

Performance and usability targets below are proposed evaluation targets. They are not measured results.

| ID | Requirement | Priority | Acceptance Criteria |
| --- | --- | --- | --- |
| NFR-01 | Authentication and credential protection | Must Have | Passwords are stored using an established salted password-hashing mechanism. Passwords and authentication tokens do not appear in application logs |
| NFR-02 | Server-side authorisation | Must Have | Automated checks confirm that residents cannot manage purchases, read another participant’s private request, or access another community without permission |
| NFR-03 | Secure communication | Must Have | The deployed client communicates with the backend over HTTPS |
| NFR-04 | Input validation | Must Have | Invalid quantities, prices, dates, and identifiers are rejected by the server. Rejected requests leave existing data unchanged |
| NFR-05 | Concurrent data consistency | Must Have | Tests with concurrent request changes and purchase closure preserve correct totals and prevent acceptance of changes after closure |
| NFR-06 | Duplicate submission handling | Must Have | Retrying the same submission after a timeout does not create duplicate participation records or apply the same quantity change twice |
| NFR-07 | Network failure handling | Must Have | A failed or uncertain request produces a clear message. The client does not display success without confirmation and can retrieve the authoritative server state |
| NFR-08 | Personal data protection | Must Have | Residents cannot retrieve other participants’ contact details or individual allocations. Organisers receive only information required to manage their community’s purchases |
| NFR-09 | Response time | Should Have | At least 95% of purchase-list retrieval, purchase-detail retrieval, and request-update operations complete within two seconds under the documented reference conditions |
| NFR-10 | Usability | Should Have | At least four of five representative participants complete the join-and-request scenario without moderator assistance after receiving the task description |
| NFR-11 | Traceability | Must Have | Purchase status changes and collection actions record the responsible user and server timestamp |
| NFR-12 | Reproducibility and maintainability | Must Have | Another team member can configure and run the available implementation and checks using repository instructions and example configuration |
| NFR-13 | Backup and recovery | Should Have | A database backup can be restored in a test environment, with selected records checked for completeness |

### Reference Performance Conditions

The initial performance evaluation will use:

- A documented reference server and database environment.
- A dataset containing at least 1,000 participation records.
- Twenty concurrent test users.
- A five-minute measured period following warm-up.
- Separate reporting of server processing time and client-observed latency.

Hardware, network conditions, software versions, error rate, and test scripts will be recorded with the results. Targets may be revised before evaluation if the agreed deployment environment requires different conditions.

## 6.8. Scope Exclusions

The initial implementation does not include:

- Integrated banking payments, escrow, or automated refunds.
- Supplier accounts and automated supplier integrations.
- Delivery routing or fleet management.
- Automated negotiation or price optimisation.
- A full-featured messaging service.
- Perishable goods requiring specialised storage.
- Formal verification of residential address ownership.

An invitation code controls access to a community but does not independently verify that a user resides at a particular address.

## 6.9. Verification and Change Management

Each mandatory requirement will be linked to a YouTrack task and corresponding verification evidence. Depending on the requirement, evidence may include an automated test, a documented manual check, or a user evaluation result.

Changes following survey analysis or supervisor feedback will retain the requirement identifier where appropriate and record the reason for revision. A requirement will be marked completed only when its acceptance criteria have been satisfied.

**Specification status:** Initial draft pending survey analysis and confirmation of business rules.