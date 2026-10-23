# 3. Literature Review

## 3.1. Purpose and Scope

This review examines research relevant to the development of a distributed platform for group purchasing of essential goods within local residential communities. It covers four areas: group purchasing mechanisms, trust and community participation, technology acceptance, and data consistency.

The selected source base comprises eight scientific publications and four official technical resources. Seven scientific publications were published between 2022 and 2024. The foundational Spanner paper is included to support the discussion of consistency in distributed systems.

This is a preliminary review. Publications available only through abstracts or publisher summaries require full-text examination before the final submission.

## 3.2. Group Purchasing Mechanisms

Research on group purchasing examines how collective demand, purchasing thresholds, and pricing conditions influence transactions. *Research on Optimal Group-Purchase Threshold and Pricing Strategy of Community Group Purchase* investigates threshold and pricing decisions through mathematical modelling. It provides a basis for treating the minimum purchasing quantity as an explicit condition of a group purchase.

A related study, *An Efficient Algorithm for the Joint Replenishment Problem with Quantity Discounts, Minimum Order Quantity and Transport Capacity Constraints*, considers purchasing decisions involving quantity discounts, minimum orders, and transport restrictions. Its scope demonstrates that procurement outcomes depend on several constraints rather than order volume alone.

These studies address different decision problems. The first focuses on group purchasing thresholds and pricing, while the second concerns joint replenishment and inventory-related constraints. Their models cannot be transferred directly to occasional purchases organised by residential communities.

For the proposed platform, the practical implication is to record supplier conditions explicitly, including unit prices, units of measurement, minimum quantities, and deadlines. Automated price optimisation is outside the initial scope. Any claim of financial savings will require comparison with actual alternative purchasing costs.

## 3.3. Trust and Community Participation

Trust is an important consideration in community purchasing. *Influence of Multi-Role Interactions in Community Group-Buying on Consumers’ Lock-In Purchasing Intention From a Fixed Leader* examines how the organiser’s commercial and interpersonal roles relate to trust and continued purchasing intentions. The study uses data from 430 consumers and distinguishes trust in the organiser from trust in community group buying.

*New marketing strategies for online group-buying business from a social interaction theory perspective* analyses 406 questionnaires using fuzzy-set qualitative comparative analysis. It identifies combinations of social interaction, perceived benefits, quality, and trust associated with purchasing intentions. This approach suggests that participation should be considered through several interacting factors.

Privacy introduces a further consideration. *Accessing the Influence of Consumer Participation on Purchase Intention Toward Community Group Buying Platform* examines community identification as a mediator between participation and purchasing intentions. The authors report that privacy concerns weaken the relationship between community identification and purchase intention.

For the proposed platform, these findings support consideration of clear organiser information, transparent purchasing conditions, and restricted access to personal data. These are design implications proposed by the project team; the studies do not directly validate the planned interface or invitation mechanism.

## 3.4. Technology Acceptance and User Experience

Zhang, Hassan, and Migin’s *Exploring the Consumers’ Purchase Intention on Online Community Group Buying Platform during Pandemic* applies the Unified Theory of Acceptance and Use of Technology alongside perceived risk theory. Based on 280 responses, the study reports positive relationships between purchase intention and performance expectancy, effort expectancy, and social influence.

These findings support attention to perceived usefulness and ease of use. However, the pandemic setting limits direct generalisation to everyday purchasing practices in the proposed target communities.

The experimental study *Who do you want to purchase with?* investigates how an initiator’s account naming strategy affects purchasing intentions. Its findings indicate that identity presentation can influence user perceptions. The available publisher summary does not establish a requirement for formal identity verification or public disclosure of personal information.

Accordingly, the project will evaluate whether potential users can understand purchasing conditions and complete the principal participation scenario. Interface effectiveness will be assessed through user testing rather than inferred from literature alone.

## 3.5. Distributed Processing and Data Integrity

The Spanner paper describes a globally distributed database supporting externally consistent transactions. Although its scale exceeds the requirements of this project, it provides a foundational reference for discussing consistent processing across distributed components.

The proposed platform faces a smaller but relevant consistency problem: multiple residents may modify requests while an organiser closes a purchase. The implementation must preserve correct totals and prevent invalid changes after closure.

PostgreSQL documentation on transaction isolation and constraints provides implementation guidance for concurrent operations and integrity rules. These resources will inform the database evaluation; their inclusion does not constitute a final technology selection.

For the mobile application, Flutter’s architecture guide recommends separating presentation responsibilities from data handling. OWASP ASVS provides a basis for defining and verifying applicable security controls for the backend application.

## 3.6. Structured Source Analysis

The limitations below describe boundaries of applicability to this project and should not all be interpreted as limitations explicitly stated by the original authors.

| No. | Source | Approach or Focus | Relevance to the Project | Limitation or Review Status |
| --- | --- | --- | --- | --- |
| 1 | [Influence of Multi-Role Interactions in Community Group-Buying…](https://doi.org/10.3389/fpsyg.2022.903221), 2022 | Empirical analysis of organiser roles, trust, and purchasing intentions | Supports attention to organiser responsibility and trust | Purchasing intentions do not establish actual adoption |
| 2 | [New marketing strategies for online group-buying business…](https://doi.org/10.3389/fpsyg.2022.953799), 2022 | Questionnaire study and fsQCA | Supports consideration of interacting participation factors | Findings require validation in the target community |
| 3 | [Accessing the Influence of Consumer Participation…](https://doi.org/10.3389/fpsyg.2022.887959), 2022 | Participation, community identification, and privacy concerns | Informs community features and privacy requirements | Does not validate a specific membership mechanism |
| 4 | [Exploring the Consumers’ Purchase Intention…](https://doi.org/10.3390/su15032433), 2023 | Questionnaire study using technology acceptance and perceived risk theories | Informs usability and perceived usefulness evaluation | Pandemic context limits generalisation |
| 5 | [Who do you want to purchase with?](https://doi.org/10.1016/j.jretconser.2024.103956), 2024 | Three experiments concerning initiator naming | Informs consideration of organiser presentation | Preliminary analysis based on publisher information |
| 6 | [Research on Optimal Group-Purchase Threshold and Pricing Strategy…](https://doi.org/10.3390/math11244951), 2023 | Mathematical modelling of thresholds and pricing | Informs explicit purchasing conditions | Full-text assessment remains outstanding |
| 7 | [An Efficient Algorithm for the Joint Replenishment Problem…](https://doi.org/10.3390/math11041012), 2023 | Optimisation under quantity and transport constraints | Informs analysis of procurement constraints | Inventory replenishment differs from residential purchasing; full-text assessment remains outstanding |
| 8 | [Spanner: Google’s Globally-Distributed Database](https://www.usenix.org/conference/osdi12/technical-sessions/presentation/corbett), 2012 | Distributed database architecture and transaction consistency | Provides foundational consistency concepts | Architecture operates at a substantially larger scale |
| 9 | [Flutter: Guide to app architecture](https://docs.flutter.dev/app-architecture/guide) | Official architectural guidance | Informs separation of interface and data responsibilities | Technical guidance rather than empirical research |
| 10 | [PostgreSQL: Transaction Isolation](https://www.postgresql.org/docs/current/transaction-iso.html) | Official concurrency documentation | Informs concurrent request processing | Correctness also depends on application logic |
| 11 | [PostgreSQL: Constraints](https://www.postgresql.org/docs/current/ddl-constraints.html) | Official integrity constraint documentation | Informs quantity validation, uniqueness, and relationships | Database constraints do not cover all business rules |
| 12 | [OWASP Application Security Verification Standard](https://owasp.org/projects/asvs) | Security requirements and verification framework | Informs applicable backend security checks | Controls must be selected according to project scope |

## 3.7. Implications for the Proposed Platform

The reviewed sources support five preliminary design priorities:

1. Clear presentation of the organiser and purchasing conditions.
2. Explicit management of minimum quantities, deadlines, and order totals.
3. A straightforward participation process evaluated with potential users.
4. Controlled access to community and personal information.
5. Consistent processing of concurrent changes and purchasing status transitions.

The literature does not establish demand within the specific residential communities targeted by this project. Local interviews and prototype evaluation will therefore be used to validate requirements and assess applicability.

The project’s expected contribution is the implementation and evaluation of a coordinated purchasing workflow for local residential communities. Claims concerning usability, operational improvements, or financial benefits will be supported by project evaluation rather than assumed in advance.