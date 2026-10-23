# 10. Project Management and Risks

## 10.1. Current Project Status

The project is currently at the analysis, design, and prototyping stage. A GitHub repository has been established and contains the project materials uploaded to date.

The prepared work includes project documentation, preliminary requirements, architectural materials, an interactive HTML prototype, and a verification and evaluation plan. The repository contents must be checked against the submission checklist to confirm that the latest versions are included.

A YouTrack project has not yet been created. Task tracking, assignment, and links between tasks and repository changes therefore remain outstanding. This is an unmet submission requirement and a priority organisational action.

The complete application has not yet been implemented. The HTML prototype demonstrates selected user interactions and does not represent the planned integrated platform.

## 10.2. Proposed Allocation of Responsibilities

The following allocation provides a working division of responsibilities. Names and final assignments must be confirmed by the team.

| Team Member | Primary Responsibility | Expected Deliverables |
| --- | --- | --- |
| **Skakova Tomiris — Frontend Developer** | User interface design and client development | Prototype refinement, Flutter screens, navigation, API integration, and interface documentation |
| **Orynbassarova Dinara — Backend Developer** | Server architecture and purchasing logic | API specification, authentication, community permissions, purchase lifecycle, and deadline processing |
| **Dauletbayeva Aitolkyn — Database and QA Lead** | Data design and verification coordination | Database schema, integrity rules, test scenarios, verification records, and evaluation coordination |

All members will contribute to research, documentation, integration, and peer review. Responsibility for an area does not remove the requirement for another member to review significant changes.

Individual contributions will be evidenced through identifiable commits, deliverables, and review activity.

## 10.3. Project Milestones

| Milestone | Main Deliverables | Completion Condition | Target |
| --- | --- | --- | --- |
| **M1. Analysis and initial design** | Proposal, survey analysis, literature review, comparisons, requirements, diagrams, prototype, and evaluation plan | Materials are consistent, reviewed, and available in the repository | 24 October 2026 submission |
| **M2. Development planning** | YouTrack project, assigned backlog, confirmed responsibilities, and agreed technical baseline | Priority tasks have owners, deadlines, and acceptance criteria | Immediate next action |
| **M3. Initial implementation** | Client structure, backend foundation, database, and authentication | A reproducible implementation supports basic authenticated interaction | Date to be agreed |
| **M4. Core workflow integration** | Communities, purchases, participation, closure, and collection | The principal resident and organiser scenarios work across components | Date to be agreed |
| **M5. Verification and evaluation** | Functional checks, concurrency checks, usability sessions, and baseline comparison | Results and outstanding defects are documented | Before final acceptance |
| **M6. Submission preparation** | Updated documentation, demonstration, limitations, and tagged version | Submission materials and access are verified | According to university schedule |

Milestone dates will be agreed with the supervisor and recorded in the project management system. The completion of a milestone will depend on its deliverables rather than documentation status alone.

## 10.4. Repository Management

The existing GitHub repository will remain the primary record of project development.

The team will apply the following workflow:

1. Define a meaningful work item and its expected outcome.
2. Create a task or feature branch.
3. Commit coherent changes with descriptive messages.
4. Open a Pull Request explaining the changes and verification performed.
5. Obtain review from another team member.
6. Address comments before merging into `main`.

Once YouTrack is available, task identifiers will be included in branch names and commit or Pull Request descriptions. Tasks will contain links back to the relevant repository changes.

Previous work will be linked retrospectively where appropriate without inventing earlier task dates, review records, or development history.

Passwords, API keys, and unnecessary personal information will not be committed. Example configuration files will use placeholder values.

## 10.5. Outstanding YouTrack Setup

The following actions are required to establish task tracking:

| Action | Expected Result |
| --- | --- |
| Create the project and invite the team | A shared workspace with appropriate access |
| Establish task states | Open, In Progress, In Review, and Done |
| Create the initial backlog | Traceable work items covering outstanding analysis, development, and verification |
| Assign responsibility and priority | Each task has a named owner and an agreed priority |
| Define acceptance criteria and deadlines | Completion can be checked against an expected outcome |
| Link repository changes | Tasks reference relevant commits or Pull Requests |
| Add the project link to README | Reviewers can access the planning record |

Suggested initial tasks include reconciling the survey response count, completing full-text literature checks, updating diagram labels, confirming the technology baseline, and defining the API and database schema.

## 10.6. Dependencies

| Dependency | Effect on Subsequent Work |
| --- | --- |
| Final survey analysis | Informs user priorities and revisions to requirements |
| Confirmed purchasing rules | Required before finalising status transitions and closure logic |
| Agreed API specification | Enables consistent frontend and backend integration |
| Database design | Supports persistent requests, memberships, and integrity controls |
| Authentication and authorisation | Required before meaningful access-control verification |
| Integrated implementation | Required for concurrent-user and performance testing |
| Supervisor feedback | May require changes to scope, architecture, or evaluation |

Dependencies will be recorded in task descriptions to make blocked work visible.

## 10.7. Initial Risk Register

The ratings below are preliminary team assessments and will be reviewed as development progresses.

| ID | Risk | Likelihood | Impact | Mitigation and Response | Proposed Owner |
| --- | --- | --- | --- | --- | --- |
| R-01 | Scope expands beyond available time | Medium | High | Prioritise mandatory requirements; defer optional integrations and advanced features | Whole team |
| R-02 | YouTrack setup remains incomplete | High | High | Create the project, assign the backlog, and add links to README as an immediate action | Designated coordinator |
| R-03 | Frontend and backend use incompatible data formats | Medium | High | Agree on API examples, validation rules, and error responses before integration | Frontend and backend developers |
| R-04 | Concurrent updates produce incorrect quantities | Medium | High | Define transaction boundaries and verify update and closure scenarios | Backend and database leads |
| R-05 | Survey evidence does not demonstrate sufficient demand | Medium | Medium | Retain negative findings, refine the target scenario, and evaluate the prototype with potential users | Whole team |
| R-06 | Documentation and diagrams become inconsistent | Medium | Medium | Review affected documents whenever requirements or architecture change | Whole team |
| R-07 | Work is concentrated in one member or delayed | Medium | High | Assign bounded tasks, identify blockers early, and redistribute work where necessary | Whole team |
| R-08 | Development environment issues delay implementation | Medium | Medium | Verify tool installation early and maintain reproducible setup instructions | Each component owner |
| R-09 | Private data or credentials enter the repository | Low | High | Review files before committing and use configuration examples and de-identified research data | Whole team |

## 10.8. Progress Monitoring and Change Control

The team proposes weekly progress reviews and additional coordination before integration or submission milestones.

Each review will cover completed deliverables, current blockers, upcoming tasks, and changes to risks or dependencies. Supervisor meeting frequency will be agreed separately.

Changes to scope or technical decisions will record:

- The reason for the change.
- Affected requirements and deliverables.
- The responsible team member.
- The expected effect on the schedule.
- The review outcome.

Tasks will be marked completed only after their acceptance criteria have been met.

## 10.9. Immediate Actions Before Submission

- [ ] Confirm that all prepared materials are uploaded in their latest versions.
- [ ] Complete README information, including team responsibilities and current limitations.
- [ ] Create YouTrack and populate assigned, prioritised tasks.
- [ ] Verify repository access for the supervisor and committee.
- [ ] Include editable diagram sources and the HTML prototype.
- [ ] Reconcile survey figures to one reporting cut-off.
- [ ] Record actual supervisor feedback and corresponding revisions.
- [ ] Tag the submitted version and provide a summary of completed and outstanding work.

**Management status:** GitHub repository established with initial materials; YouTrack setup and formal task traceability remain outstanding.