# 9. Verification and Evaluation Plan

## 9.1. Purpose

This plan defines how the project team will verify system correctness and evaluate whether the proposed platform supports the organisation of group purchases within residential communities.

Verification will assess compliance with the requirements in [Section 6 — Requirements Specification](06-requirements.md). Evaluation will examine usability and organisational effort using representative tasks and a baseline workflow.

All targets in this section are planned criteria. They do not represent completed tests or measured results.

## 9.2. Verification Stages

| Stage | Scope | Limitations |
| --- | --- | --- |
| **HTML Prototype** | Navigation, quantity selection, cost calculations, request changes, manual purchasing transitions, and local data retention | Cannot demonstrate secure authorisation, server-side deadlines, shared storage, or concurrent-user correctness |
| **Integrated Platform** | Flutter client, backend API, database, authentication, community permissions, deadlines, and concurrent operations | Requires a reproducible test environment and implemented functionality |

Prototype checks will support interface refinement. Passing them will not establish that the full platform’s requirements have been satisfied.

## 9.3. Planned Functional Checks

| ID | Scenario | Expected Result | Applicable Stage |
| --- | --- | --- | --- |
| VT-01 | Submit a request for two packages priced at 900 ₸ each | One request is saved with a total of 1,800 ₸ | Both |
| VT-02 | Change the requested quantity | The individual total and aggregate quantity are recalculated correctly | Both |
| VT-03 | Cancel a request while collection is open | The request becomes inactive and its quantity is excluded from the aggregate | Both |
| VT-04 | Close a purchase that meets every minimum quantity | The purchase moves to Awaiting Confirmation | Both; one product per purchase in the prototype |
| VT-05 | Close a purchase below a minimum quantity | The purchase becomes Unsuccessful under the agreed business rules | Both |
| VT-06 | Attempt to change a request after closure | The change is rejected and stored quantities remain unchanged | Both; server enforcement in the integrated platform |
| VT-07 | Confirm a purchase and prepare collection | Only valid transitions are accepted | Both |
| VT-08 | Record collection twice for the same order | Collection remains recorded once without duplicate effects | Both |
| VT-09 | Submit invalid quantities, prices, or required fields | Invalid data is rejected with an understandable message | Both |
| VT-10 | Join a community using an invalid code | Membership is not created | Integrated platform |
| VT-11 | Attempt an organiser action as a resident | The backend rejects the operation | Integrated platform |
| VT-12 | Request private information from another community or participant | Unauthorised information is not returned | Integrated platform |
| VT-13 | Retry a submission following a timeout | No duplicate participation record or repeated quantity change is created | Integrated platform |
| VT-14 | Modify requests concurrently with purchase closure | Totals remain correct and changes after the deadline are rejected | Integrated platform |
| VT-15 | Interrupt a network connection during submission | The client reports uncertainty and retrieves the authoritative state before confirming the outcome | Integrated platform |

Additional checks will cover completed purchasing workflows, notification behaviour, and backup restoration when the corresponding features are available.

## 9.4. Verification Methods

The team will use:

- **Manual interface checks** for navigation, displayed information, validation messages, and prototype interactions.
- **Unit tests** for calculations, threshold evaluation, and purchasing transition rules.
- **API and integration tests** for authentication, authorisation, persistence, and component interaction.
- **Concurrent-operation tests** for request updates, duplicate submissions, and closure.
- **Performance tests** for selected operations under documented load.
- **User task observation** for usability and clarity.

Test data will be synthetic. Each repeatable scenario will begin from a known state.

## 9.5. Usability Evaluation

An exploratory usability evaluation is planned with five potential users. Recruitment will seek participants with differing levels of group purchasing experience.

Participants will receive task descriptions and a brief introduction without a demonstration of the required interaction sequence.

| Task | Observable Completion |
| --- | --- |
| Find a relevant purchase | Opens the correct purchase |
| Identify purchasing conditions | Correctly identifies package size, total cost, cancellation conditions, and collection information |
| Submit a request | Saves the requested quantity and reaches confirmation |
| Modify or cancel a request | Completes the requested change while collection is open |
| Check fulfilment information | Finds the purchasing status and available collection details |

The HTML prototype will be evaluated only for implemented interactions. Community joining and other unavailable functions will be assessed after implementation.

For each task, the observer will record completion, time, errors, requests for assistance, and participant comments. Timing will start when the task is presented and end on correct completion or abandonment. Moderator assistance will be recorded; assisted completion will not count as unassisted success.

The preliminary target is that at least four of five participants complete the principal participation scenario without assistance. Results will be reported as counts alongside percentages because of the small sample.

## 9.6. Baseline Comparison

The integrated platform will be compared with a defined workflow using messaging and a spreadsheet.

The comparison will use the same purchasing conditions and equivalent datasets. A reference scenario will include ten participant requests across three products, followed by quantity changes and cancellations.

The organiser will be asked to:

1. Consolidate the requests.
2. Apply the specified changes.
3. Calculate final product quantities and individual totals.
4. Determine whether the purchasing thresholds are met.
5. Prepare the final participant order summary.

A reference answer will be prepared before testing. Both approaches must produce the same required output.

Where feasible, each evaluator will perform both workflows using equivalent datasets. The order will be alternated to reduce learning effects. Setup time and task execution time will be recorded separately.

The current HTML prototype does not support the complete comparison scenario. Any preliminary prototype comparison will use only shared, implemented tasks and will be reported separately.

## 9.7. Metrics and Proposed Criteria

| Metric | Measurement | Proposed Criterion |
| --- | --- | --- |
| **Mandatory requirement verification** | Mandatory requirements with passing evidence divided by all mandatory requirements | Every mandatory requirement has passing evidence before final acceptance |
| **Calculation accuracy** | Comparison with independently prepared expected totals | Exact agreement in the defined scenarios |
| **Access control** | Unauthorised actions and data requests in the test suite | All defined attempts rejected |
| **Concurrent consistency** | Comparison of accepted operations with final stored requests and totals | No lost accepted changes, duplicate effects, or invalid totals |
| **Unassisted task completion** | Participants completing the principal scenario without help | At least four of five |
| **Task completion time** | Time taken for correct completion | Report individual values and median |
| **Organiser effort** | Time required to produce a correct summary in each workflow | Compare measured times; no improvement percentage assumed in advance |
| **Error count** | Incorrect quantities, totals, omissions, or duplicate entries | Compare against the reference answer |
| **Response time** | Client-observed latency for selected API operations | At least 95% complete within two seconds under reference conditions |

A reduction in organisational time will only be reported when the output is also correct. Faster completion with incorrect results will not be treated as an improvement.

## 9.8. Performance and Reliability Conditions

Performance testing will follow the reference conditions in [Section 6 — Requirements Specification](06-requirements.md):

- At least 1,000 participation records.
- Twenty concurrent test users.
- A five-minute measured period after warm-up.
- Purchase-list retrieval, purchase-detail retrieval, and request-update operations.
- Separate reporting of server processing time and client-observed latency.

Reports will document hardware, software versions, network conditions, dataset, request mix, latency percentiles, and error rates. Failed requests will be reported separately rather than excluded without explanation.

Deadline checks will use server time. Boundary scenarios will include requests before, at, and after closure, together with repeated closure attempts.

## 9.9. Evidence and Defect Management

Each test record will contain:

| Field | Required Information |
| --- | --- |
| **Test ID** | Unique identifier |
| **Requirement Reference** | Related functional or non-functional requirement |
| **Version** | Commit identifier or submission tag |
| **Preconditions** | Accounts, roles, purchasing state, and initial data |
| **Steps** | Reproducible actions |
| **Expected Result** | Defined acceptance outcome |
| **Actual Result** | Observed behaviour |
| **Status** | Not Run, Passed, Failed, or Blocked |
| **Evidence** | Relevant logs, screenshots, or automated output |
| **Issue Reference** | YouTrack task where applicable |

Defects will be recorded in YouTrack with reproduction steps, impact, responsibility, and expected correction. Failed scenarios will be repeated after fixes, together with checks of affected behaviour.

User evaluation records will use participant codes and omit unnecessary personal information.

## 9.10. Acceptance and Reporting

The implementation will be considered ready for final submission when:

- All mandatory requirements have been verified.
- No unresolved defect prevents the principal workflow or violates required access and data integrity rules.
- Evaluation results and limitations are documented.
- Setup and verification instructions are reproducible.
- Outstanding optional functionality is clearly identified.

The final report will distinguish planned tests, completed checks, and unresolved issues. The initial Google Forms survey provides requirements evidence; it will not be presented as proof of application usability or operational effectiveness.

**Plan status:** Prepared for subsequent verification and evaluation. No test outcomes are claimed in this section.