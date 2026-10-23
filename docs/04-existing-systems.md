# 4. Existing System Comparison

## 4.1. Purpose and Method

This section compares three existing platforms relevant to the proposed system: **Open Food Network**, **Buying Club Software**, and **100sp**. These platforms were selected because they support collective purchasing, coordination by an organiser, or consolidation of individual requests.

The comparison uses eight consistent criteria covering membership, order aggregation, purchasing thresholds, deadlines, organiser responsibilities, order changes, progress information, and collection.

The analysis is based on publicly available official documentation and platform descriptions. It does not constitute hands-on testing. **“Not confirmed” indicates insufficient evidence in the reviewed materials and should not be interpreted as proof that a feature is unavailable.**

## 4.2. Selected Systems

### Open Food Network

Open Food Network supports food enterprises, purchasing groups, and collective ordering. Its Group Buy functionality consolidates customer demand to meet bulk purchasing quantities. Customers can specify acceptable quantity ranges, allowing managers to adjust allocations within those limits.

The platform also supports shops restricted to approved customers and ordering cycles with opening and closing dates. These capabilities make it relevant to community-based purchasing.

Its principal relevance to this project is the combination of membership controls, collective quantities, and scheduled ordering. The proposed platform will focus specifically on essential goods and residential communities, although Open Food Network documentation already accommodates purchasing groups formed by friends and neighbours.

### Buying Club Software

Buying Club Software supports purchasing clubs whose members combine individual requests into consolidated orders. Managers can establish ordering periods, monitor totals, compile supplier orders, and distribute shared cases among members. Products can be configured for ordering only when a complete shared quantity has been filled.

The platform is a close functional reference for request aggregation and organiser workflows. Its documented receiving and collection processes also provide useful examples of allocating delivered goods to individual members.

The proposed project will investigate a mobile workflow centred on residential communities. Any improvement in usability must be demonstrated through evaluation rather than assumed from the choice of interface.

### 100sp

100sp is a joint purchasing platform in which organisers publish purchasing offers and participants place orders. Its rules define organiser responsibilities, purchasing conditions, payment arrangements, and collection procedures. Participants may cancel orders during the request collection stage; cancellation becomes restricted after the purchase status changes.

The platform provides a relevant reference for purchasing stages, cancellation rules, and collection management. A dedicated mechanism for closed residential communities with invitation codes was not confirmed in the reviewed materials.

## 4.3. Comparative Analysis

| Criterion | Open Food Network | Buying Club Software | 100sp |
| --- | --- | --- | --- |
| **Restricted group access** | Shops can restrict access to approved customers | Members access the club through manager-provided accounts | Dedicated closed residential groups not confirmed |
| **Aggregation of individual requests** | Group Buy and bulk order management | Consolidated club orders and shared cases | Joint purchases coordinated by organisers |
| **Collective purchasing threshold** | Bulk quantity thresholds | Shared quantities can require complete fulfilment before ordering | Minimum purchasing conditions appear in listings; automatic enforcement of a collective threshold not confirmed |
| **Ordering deadline** | Opening and closing dates for order cycles | Opening and closing dates and times | Time-limited purchases and collection deadlines |
| **Organiser management** | Shop managers and order-cycle coordinators | Club managers or order facilitators | Purchase organisers |
| **Order modification or cancellation** | Configurable customer changes and manager editing | Manager adjustments documented; full customer cancellation procedure requires further verification | Participant cancellation during request collection |
| **Order progress information** | Order, payment, and shipment states | Filled and unfilled shared quantities, order totals, and final records | Purchase statuses and participant information |
| **Collection support** | Collection or delivery arrangements and fulfilment recording | Allocation documents and collection workflow | Collection points and collection rules |

**Sources:** Official Open Food Network guides, Buying Club Software feature descriptions, and 100sp guidance and rules.

A minimum value for an individual order is distinguished from a threshold for the entire collective purchase.

## 4.4. Implications for the Proposed Platform

The comparison demonstrates that collective ordering, purchasing deadlines, organiser management, and collection support are established capabilities. The project therefore requires a clear focus on the needs of its intended residential communities.

The proposed scope will prioritise:

- **Community-based organisation:** Membership, roles, and purchases associated with a particular residential community.
- **Essential goods:** Purchasing scenarios involving non-perishable food, household cleaning products, and personal hygiene items.
- **A mobile participation workflow:** Joining a community, selecting a purchase, submitting a request, and monitoring collection information.
- **Transparent conditions:** Visible prices, total costs, minimum quantities, deadlines, and collection arrangements.
- **Consistent processing:** Correct request totals and valid purchasing states during concurrent user actions.

These priorities represent proposed design decisions rather than demonstrated advantages over existing platforms. Their relevance will be assessed using survey findings and prototype evaluation.

## 4.5. Conclusion

The reviewed platforms provide established approaches to collective purchasing and useful references for the proposed system. The project’s justification will depend on identifying the needs of selected residential communities and evaluating how effectively the implementation addresses them.

A workflow based on messaging and spreadsheets will be considered separately as a baseline for evaluating organisational effort, task completion time, and errors.

## 4.6. Official Sources

1. [Open Food Network — Software Platform](https://openfoodnetwork.org/software-platform/)
2. [Open Food Network — Group Buy for Bulk Ordering](https://guide.openfoodnetwork.org/basic-features/products-1/group-buy-for-bulk-ordering)
3. [Open Food Network — Customer Frequently Asked Questions](https://guide.openfoodnetwork.org/shopping-with-open-food-network/frequently-asked-questions)
4. [Open Food Network — Order Cycles](https://guide.openfoodnetwork.org/basic-features/shopfront/order-cycle)
5. [Open Food Network — Manage Orders](https://guide.openfoodnetwork.org/basic-features/orders/view-orders)
6. [Buying Club Software — Features](https://www.buyingclubsoftware.com/features/)
7. [Buying Club Software — Tour](https://www.buyingclubsoftware.com/tour/)
8. [100sp — How the Platform Works](https://www.100sp.ru/site/howTo)
9. [100sp — Purchasing Rules](https://www.100sp.ru/help/2)

**Date of review:** 23 October 2026.