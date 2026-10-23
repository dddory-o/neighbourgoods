# 5. Technology Comparison

## 5.1. Purpose and Evaluation Criteria

This section compares technological alternatives for implementing the distributed platform for group purchasing of essential goods within local residential communities.

The comparison covers four decisions: the client application, backend framework, database, and communication approach. Alternatives are assessed against the project’s requirements, including:

- Support for resident and organiser workflows.
- Correct processing of related purchasing data.
- Maintainability and testability.
- Development and deployment effort.
- Compatibility with the team’s experience.
- Operational complexity.

Flutter has been selected as the client development framework. Backend, database, and communication choices remain preliminary recommendations pending team confirmation. No comparative performance benchmarks have been conducted.

## 5.2. Client Application

The client application will support community membership, browsing purchases, submitting requests, and viewing purchasing and collection information.

| Alternative | Relevant Capabilities | Project Considerations |
| --- | --- | --- |
| **Flutter — Dart** | Cross-platform application development with a shared widget-based interface | Requires Dart knowledge, platform configuration, and testing on target devices |
| **React Native — JavaScript or TypeScript** | Mobile development using React and native components | Requires React knowledge and attention to platform-specific behaviour |
| **Responsive web application — HTML, CSS, and JavaScript** | Browser-based access through a link without a separate application installation | Mobile integration and background behaviour depend on browser capabilities |

Flutter and React Native provide approaches to cross-platform application development. Flutter uses its own widget and rendering architecture, while React Native introduces React-based development with native components.

**Selected option: Flutter.**

Flutter is consistent with the project’s planned mobile implementation. It will support a shared application structure for resident and organiser interfaces. The initial target platform and supported devices will be documented before implementation.

The selection does not imply that Flutter is universally faster or more usable than the alternatives. Interface quality will be evaluated through prototype and application testing.

## 5.3. Backend Framework

The backend will enforce permissions, manage communities and purchases, process participant requests, and maintain valid purchasing states.

| Alternative | Relevant Capabilities | Project Considerations |
| --- | --- | --- |
| **Node.js with Express — JavaScript or TypeScript** | Routing and middleware for HTTP APIs | Validation, authentication, data access, and application structure require explicit integration |
| **Django — Python** | Integrated data models, authentication facilities, and an administrative interface | The mobile API requires an appropriate API implementation, and the team must understand Django conventions |
| **Spring Boot — Java** | Stand-alone applications with Spring configuration and supporting integrations | Requires familiarity with Java, Spring conventions, and the selected supporting modules |

Express provides a relatively minimal framework for web applications and APIs. Django offers a more integrated framework, while Spring Boot supports stand-alone Spring applications with automatic configuration.

**Preliminary recommendation: Node.js with Express.**

Express is a candidate for implementing the platform’s HTTP API with clearly separated modules for authentication, communities, purchases, and participation.

This recommendation must be checked against the backend developer’s experience. If the team is substantially more experienced with Django or Spring Boot, that experience may justify a different selection.

Regardless of framework, purchasing rules and access control will be enforced on the server.

## 5.4. Database

The platform will store related information about users, communities, memberships, purchases, products, and participant requests. Database selection must support both relationships and correct concurrent updates.

| Alternative | Relevant Capabilities | Project Considerations |
| --- | --- | --- |
| **PostgreSQL** | Relational tables, integrity constraints, transactions, and configurable isolation | Requires deliberate schema design and appropriate transaction handling |
| **MySQL with InnoDB** | Relational storage, transactions, locking, and foreign-key support | Provides a viable relational alternative; concurrency behaviour must be considered during implementation |
| **MongoDB** | Document-based storage, single-document atomic operations, and multi-document transactions | Document boundaries and cross-document consistency require careful design |

PostgreSQL documents transaction isolation mechanisms, while MySQL’s InnoDB supports transactional processing. MongoDB supports multi-document transactions as well as atomic single-document operations; it should therefore not be excluded on the incorrect assumption that it lacks transaction support.

**Preliminary recommendation: PostgreSQL.**

A relational model is a suitable starting point because the proposed entities have explicit relationships. PostgreSQL is recommended for further evaluation, while MySQL remains a reasonable alternative.

The database choice alone will not guarantee correctness. For example, submitting a request and closing the same purchase must be coordinated so that a request cannot be accepted after closure. Transaction boundaries, constraints, and concurrent-operation tests will address this requirement.

## 5.5. Communication Between Components

The mobile application must communicate with the backend to retrieve purchases, submit requests, and obtain updated statuses. Background processing may also be required.

The alternatives below are implementation configurations rather than mutually exclusive protocols: HTTP, WebSocket, and queues serve different purposes.

| Configuration | Intended Use | Benefits | Trade-offs |
| --- | --- | --- | --- |
| **HTTPS API with manual or periodic refresh** | Client requests and server responses | Direct interaction model and straightforward request-level testing | Updates become visible after a refresh; repeated polling creates additional requests |
| **HTTPS API with WebSocket updates** | Standard API operations plus live updates while connected | Can deliver changes without repeated polling | Requires connection management, reconnection, and state synchronisation |
| **HTTPS API with a background work queue** | Standard API operations plus asynchronous server tasks | Separates tasks such as notification delivery from interactive requests | Adds infrastructure, retry handling, and duplicate-processing considerations |

WebSocket supports two-way communication over a persistent connection. A work queue instead distributes background tasks to consumers. A queue does not directly replace the mobile application’s API or provide live client updates.

**Preliminary recommendation: an HTTPS API with explicit refresh behaviour.**

The initial implementation can retrieve current information when a screen opens, after a successful change, and when the user requests a refresh. Periodic refresh may be added where justified.

WebSocket updates and a message broker will be considered if validated requirements demonstrate a need. Notification delivery while the application is closed requires a separate mechanism and will not be assumed to follow from an active WebSocket connection.

## 5.6. Proposed Technology Baseline

| Component | Proposed Technology | Decision Status |
| --- | --- | --- |
| Mobile application | Flutter and Dart | Selected direction |
| Backend | Node.js with Express | Preliminary recommendation |
| Database | PostgreSQL | Preliminary recommendation |
| Client–server communication | HTTPS API with JSON | Preliminary recommendation |
| Live updates and background messaging | To be determined from requirements | Not selected |

The proposed architecture separates the mobile client, backend application, and persistent storage. Its final deployment structure and distributed responsibilities will be documented in the architectural design.

## 5.7. Validation of Technical Decisions

The team will verify the proposed baseline through a small implementation covering authentication, retrieval of a purchase, submission of a participant request, and purchase closure.

Validation will focus on:

1. Correct access restrictions between users and communities.
2. Accurate quantities during concurrent request changes.
3. Rejection of changes after purchase closure.
4. Prevention of duplicate records following repeated submissions.
5. Clear client behaviour after network failures.
6. Reproducible setup and testing.

The technical comparison will be updated if implementation evidence, team experience, or supervisor feedback supports a different choice.

## 5.8. Official References

1. [Flutter — Architectural Overview](https://docs.flutter.dev/resources/architectural-overview)
2. [React Native — Introduction](https://reactnative.dev/docs/getting-started)
3. [Express — Official Documentation](https://expressjs.com/)
4. [Django — Overview](https://www.djangoproject.com/start/overview/)
5. [Spring Boot — Project Overview](https://spring.io/projects/spring-boot/)
6. [PostgreSQL — Transaction Isolation](https://www.postgresql.org/docs/current/transaction-iso.html)
7. [MySQL — Introduction to InnoDB](https://dev.mysql.com/doc/refman/8.4/en/innodb-introduction.html)
8. [MongoDB — Transactions](https://www.mongodb.com/docs/manual/core/transactions/)
9. [MDN — WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
10. [RabbitMQ — Work Queues](https://www.rabbitmq.com/tutorials/tutorial-two-javascript)

**Date of review:** 24 October 2026.