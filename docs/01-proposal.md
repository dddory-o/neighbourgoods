# 1. Project Proposal

## 1.1. Project Team and Supervisor

**Team Members:**

| Team Member | Responsibility |
| --- | --- |
| Skakova Tomiris | Frontend and Mobile Application Development |
| Orynbassarova Dinara | Backend Development and System Architecture |
| Dauletbayeva Aitolkyn | Database Design and Quality Assurance |

**Academic Supervisor:** Salkenov Aldiyar

**University:** Astana IT University

## 1.2. Project Overview

The project proposes the development of a distributed platform that enables residents of local residential communities to organise and participate in group purchases of essential goods. The platform will consolidate individual requests into collective orders and provide a shared environment for managing purchasing conditions, quantities, deadlines, and collection arrangements.

The proposed solution will include a Flutter mobile application, a backend application, and a database. These components will communicate through defined interfaces to support coordinated access by multiple users.

The initial version will focus on non-perishable essential goods, including household cleaning products, personal hygiene items, and packaged food with a long shelf life.

## 1.3. Problem Statement

Group purchases within residential communities may be coordinated through messaging applications and spreadsheets. Although these tools support communication, they require organisers to collect requests, calculate quantities, track changes, and communicate order updates manually.

This process may result in missed requests, inconsistent records, calculation errors, and uncertainty regarding purchasing deadlines and collection arrangements. As participation increases, maintaining accurate information may become more time-consuming.

The project will investigate these challenges and develop a dedicated platform for managing the group purchasing process. The initial problem assumptions will be validated through discussions with potential users. Verified findings will inform the final requirements and project scope.

## 1.4. Target Users

The platform will primarily serve two user groups:

- **Residents:** Individuals who join a residential community, browse available group purchases, submit requests, and monitor the progress of their orders.
- **Community Organisers:** Authorised members who establish communities, coordinate purchasing arrangements with suppliers, create group purchases, monitor participation, and manage collection information.

An organiser may also participate in purchases as a resident. In the initial version, suppliers will communicate with organisers outside the platform and will not require separate user accounts.

## 1.5. Project Aim

The aim of the project is to design, implement, and evaluate a distributed platform that supports the organisation of group purchases of essential goods within local residential communities by consolidating requests, maintaining consistent purchasing information, and providing transparent status tracking.

## 1.6. Project Objectives

To achieve this aim, the team will:

1. Investigate the needs and current purchasing practices of potential users through interviews or structured discussions.
2. Review relevant scientific literature and compare existing systems using consistent evaluation criteria.
3. Define functional and non-functional requirements, priorities, and measurable acceptance criteria.
4. Compare technological alternatives and justify the selected implementation approach.
5. Design the system architecture, database structure, user interfaces, and component interactions.
6. Develop a Flutter mobile application and supporting backend functionality.
7. Implement access control, request aggregation, purchasing deadlines, and status management.
8. Verify system functionality, data consistency, and behaviour under concurrent user actions.
9. Evaluate usability and selected operational outcomes against an agreed baseline.
10. Maintain traceable development records through Git, YouTrack, documentation, and peer review.

## 1.7. Proposed Operating Model

A community organiser will create a residential community and provide an invitation code to prospective members. Residents will join the community and access its available group purchases.

Before publishing a purchase, the organiser will confirm the proposed terms with a supplier. Each purchase will specify the available goods, unit prices, minimum quantities, closing deadline, and collection arrangements.

Residents will select goods and submit the required quantities. The platform will calculate individual order totals and aggregate quantities across participating residents. Participants will be able to modify or cancel their requests before the purchasing deadline.

Once the deadline is reached, the platform will prevent further changes and determine whether the stated minimum quantities have been met. Purchases meeting these conditions will await organiser confirmation. Purchases that do not meet the conditions will be marked as unsuccessful.

Following confirmation, the organiser will update the purchase status and provide collection details. Individual orders will be marked as collected when goods are issued to participants.

This operating model is preliminary and will be refined following user research and supervisor review.

## 1.8. Project Scope

### 1.8.1. Included Functionality

The initial implementation will cover:

- User registration and authentication.
- Creation of residential communities and membership through invitation codes.
- Role-based access for residents and organisers.
- Creation and publication of group purchases.
- Management of goods, prices, minimum quantities, and deadlines.
- Submission, modification, and cancellation of individual requests before closure.
- Automatic calculation of order totals and aggregate quantities.
- Purchase and individual order status tracking.
- Basic notifications concerning purchasing milestones.
- Publication of collection information and recording of completed collection.

Payments will initially take place outside the platform. Where payment tracking is included, the status will be recorded manually by the organiser and will not represent automated bank verification.

### 1.8.2. Excluded Functionality

The initial implementation will exclude:

- Integrated payment processing and escrow services.
- Delivery route optimisation and fleet management.
- Dedicated supplier accounts and automated supplier integrations.
- Perishable goods requiring specialised storage or transport.
- A full-featured messaging service.
- Recommendation systems based on artificial intelligence.

Any subsequent expansion will be assessed against available time, user needs, and supervisor approval.

## 1.9. Technical Approach and Engineering Complexity

Flutter and Dart are proposed for the mobile application. Node.js and PostgreSQL are preliminary candidates for the backend and data storage. Final selections will follow a documented comparison of suitable alternatives.

The distributed architecture will separate the client application, backend processing, and persistent storage. The architectural design will define communication interfaces, component responsibilities, failure handling, and the authoritative location of purchasing data.

Key engineering challenges include:

- Maintaining correct aggregate quantities during concurrent updates.
- Preventing changes after a purchase has closed.
- Enforcing access restrictions between communities and user roles.
- Managing valid transitions between purchasing statuses.
- Handling failed requests and repeated submissions without creating duplicate participation records.

These challenges will guide architectural decisions and verification activities.

## 1.10. Expected Outcomes and Evaluation

The project is expected to deliver:

1. A functioning mobile application supporting the principal group purchasing scenario.
2. A backend application and database with documented interfaces and access rules.
3. A requirements specification, architectural diagrams, and interface prototype.
4. A documented verification and evaluation report.
5. A Git repository containing source code, documentation, review history, and links to YouTrack tasks.

Evaluation will consider functional correctness, access control, concurrent request handling, and usability. Proposed measures include task completion time, user error frequency, and successful completion of key scenarios without assistance.

Where feasible, the same organisational scenario will be compared with a baseline process using messaging and spreadsheets. Numerical targets and measurement conditions will be established before evaluation. Financial savings will only be assessed where comparable price and purchasing data are available.

## 1.11. Expected Practical Contribution

The platform is intended to provide residential communities with a structured method for coordinating collective purchases. Its anticipated contribution is improved visibility of participation, quantities, deadlines, and collection status, together with reduced reliance on manual record keeping.

The project will also demonstrate the application of mobile development, distributed system design, database management, access control, and software verification to a practical community purchasing scenario. The extent of these benefits will be determined through evaluation.