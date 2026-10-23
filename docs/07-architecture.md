# 7. System Architecture and Diagrams

## 7.1. Architectural Overview

The proposed platform follows a client–server architecture comprising a mobile application, a backend application, and a database. These components communicate across defined network interfaces and have separate responsibilities.

Flutter and Dart are selected for mobile development. Node.js with Express and PostgreSQL remain proposed technologies pending confirmation of the implementation baseline.

The backend is initially designed as a modular application. Its internal modules represent logical responsibilities and are not assumed to be independently deployed microservices.

| Architectural Element | Responsibility |
| --- | --- |
| **Mobile Application** | Presents resident and organiser interfaces, captures input, and displays server-confirmed information |
| **Backend Application** | Enforces access rules, processes requests, manages purchasing states, and coordinates database operations |
| **Database** | Stores users, memberships, purchases, participation records, and collection information |

The database is the authoritative source of persisted purchasing information. Values displayed by the mobile application must be refreshed from the backend following relevant operations.

## 7.2. System Context Diagram

![System Context Diagram](diagrams/01-system-context.png)

*Figure 7.1. System Context Diagram.*

The context diagram presents the platform’s boundary, principal users, and surrounding purchasing relationships.

| Actor | Interaction |
| --- | --- |
| **Resident** | Joins a community, browses purchases, submits or cancels requests, and views order and collection information |
| **Community Organiser** | Creates a community, manages its purchasing activities, reviews requests, and records collection |
| **External Supplier** | Agrees on product availability, prices, quantities, and fulfilment conditions with the organiser outside the platform |

Suppliers do not access the platform directly in the initial scope. Their relationship with the organiser represents an external business interaction rather than an API integration.

Organiser permissions apply only within the relevant community.

## 7.3. Container Diagram

![Container Diagram](diagrams/02-use-case.png)

*Figure 7.2. Container Diagram.*

The container diagram provides an additional view of the main executable and storage elements.

The mobile application communicates with the backend through an HTTPS API using JSON messages. The backend accesses the database through its database driver and configured connection.

Residents and organisers use the same mobile application, with available actions determined by their community roles. The client does not connect directly to the database.

This separation supports independent client development, central enforcement of purchasing rules, and controlled access to persistent data.

## 7.4. Use Case Diagram

![Use Case Diagram](diagrams/03-component.png)

*Figure 7.3. Use Case Diagram.*

The use case diagram identifies the principal actions available to each role.

| Actor | Principal Use Cases |
| --- | --- |
| **Resident** | Register; sign in; join a community using an invitation code; browse purchases; submit, modify, or cancel a request; view purchasing and collection status |
| **Community Organiser** | Create a community; create and publish a purchase; view participants and requests; confirm or cancel a purchase; publish collection details; record collection; complete a purchase |

The organiser inherits resident capabilities and may participate in purchases. This relationship does not grant management permissions outside the organiser’s own community.

Detailed acceptance criteria and restrictions are defined in [Section 6 — Requirements Specification](06-requirements.md).

## 7.5. Component Diagram

![Component Diagram — Draft](diagrams/04-container.png)

*Figure 7.4. Component Diagram — Draft.*

The component diagram describes the internal responsibilities of the mobile and backend applications.

### Mobile Application Components

| Component | Responsibility |
| --- | --- |
| **UI Screens and Navigation** | Displays screens and handles navigation between community, purchasing, and order views |
| **State Management** | Maintains presentation state, loading indicators, and operation results |
| **HTTP API Client** | Sends authenticated requests, interprets responses, and reports communication failures |

### Backend Components

| Component | Responsibility |
| --- | --- |
| **API Router** | Routes incoming requests to the relevant application functions |
| **Authentication Module** | Verifies credentials and establishes authenticated user identity |
| **Authorisation Layer** | Checks membership, community roles, and ownership for protected operations |
| **Community Module** | Manages community creation, invitation codes, and memberships |
| **Purchase Management Module** | Manages purchase details, publication, confirmation, cancellation, and collection states |
| **Participation and Aggregation Module** | Processes individual requests and calculates aggregate quantities |
| **Deadline Processing** | Identifies purchases due for closure and initiates threshold evaluation |

Authorisation applies to all protected operations. Client-side visibility of a button does not determine whether an action is permitted.

Deadline processing may run within the backend process or as a scheduled process. Its deployment arrangement remains an implementation decision.

## 7.6. Data Organisation

The database contains the following logical data groups:

| Data Group | Contents |
| --- | --- |
| **Users** | Account identifiers and authentication-related records |
| **Communities and Memberships** | Community details, member associations, and community-specific roles |
| **Purchases and Purchase Items** | Purchasing conditions, deadlines, product details, prices, and thresholds |
| **Participation and Participation Items** | Individual requests, quantities, and cancellation information |
| **Collection Records** | Collection states, responsible organiser, and timestamps |
| **Activity Records** | Significant purchasing state changes and their authors |

These groups represent logical entities within the proposed database, rather than separate database deployments.

## 7.7. Principal Processing Scenarios

### Participation Request

1. A resident selects products and quantities in the mobile application.
2. The client submits the request to the backend.
3. The backend verifies identity, membership, input validity, purchase status, and the server-defined deadline.
4. The request is saved within an appropriately coordinated database operation.
5. The backend returns confirmation and current request information.
6. The client updates its displayed state.

The client displays success only after receiving confirmation. If the result is uncertain because of a connection failure, it retrieves the current server state before presenting a final outcome.

### Purchase Closure

1. Deadline processing identifies a purchase whose closing time has been reached.
2. The backend coordinates closure with any concurrent participation changes.
3. Final active quantities are evaluated against the purchasing thresholds.
4. If every product meets its minimum quantity, the purchase moves to **Awaiting Confirmation**.
5. Otherwise, it moves to **Unsuccessful**, following the proposed business rules.

API requests independently check the deadline. A delay in scheduled processing must therefore not allow participants to submit changes after the closing time.

### Collection

1. The organiser confirms fulfilment arrangements and publishes final collection information.
2. The purchase moves to **Ready for Collection** when goods are available.
3. The organiser records collection for each participant.
4. The purchase moves to **Completed** after all active orders have been collected.

## 7.8. Consistency and Failure Handling

The main consistency risk occurs when request changes and purchase closure happen concurrently. The implementation will use database transactions and an appropriate coordination mechanism, such as locking or conditional updates, to preserve a valid outcome.

The required behaviour is:

- Accepted changes are included in the final quantities.
- Changes evaluated at or after the closing time are rejected.
- Repeated submissions do not create duplicate participation records.
- Cancellation and quantity changes preserve accurate totals.
- Invalid purchasing state transitions are rejected.
- Collection actions remain traceable.

The exact transaction and locking strategy will be documented and verified during implementation.

Network failures will be handled through explicit error reporting and retrieval of authoritative state. External payment outcomes will not be inferred from application requests because payments are outside the initial integration scope.

## 7.9. Architectural Boundaries

The initial architecture includes network-separated client, backend, and storage responsibilities. It does not assume database replication, multi-region deployment, or independently deployed business microservices.

External supplier communication and payment processing remain outside the platform. Any future integration will require additional interfaces, requirements, and verification.

The proposed architecture will be reviewed with the supervisor to confirm that its distributed responsibilities and engineering scope meet the diploma objectives.

## 7.10. Diagram Deliverables

The repository must contain both editable diagram sources and readable exports.

| Diagram | Purpose | Required Files |
| --- | --- | --- |
| **System Context Diagram** | Defines users, system boundary, and external relationships | Editable source and readable export |
| **Use Case Diagram** | Defines actor capabilities | Editable source and readable export |
| **Component Diagram — Draft** | Defines internal responsibilities and dependencies | Editable source and readable export |
| **Container Diagram** | Provides an additional deployment-oriented overview | Editable source and readable export |

All diagram labels must remain consistent with the requirements and technology comparison. Proposed technologies must be identified accordingly.

**Architecture status:** Initial design pending implementation validation and supervisor review.