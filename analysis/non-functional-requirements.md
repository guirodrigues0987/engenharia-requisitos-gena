# Non-Functional Requirements - Eventus System

The elicitation document explicitly states, in section 4 (Notes):

> "No requirements related to security, performance, availability, accessibility and data privacy were gathered."

That is, **no non-functional requirement has been validated with the stakeholders**. For this reason, this list does not present definitive NFRs - only **candidates to validate**, inferred from the characteristics of the domain (payments, personal data, real-time spot control). No numeric value (SLA, response time, uptime) was assigned, since that would require a business decision that is not in the original material.

| ID | Category | NFR candidate (to validate with stakeholders) | Rationale |
|----|----------|-----------------------------------------------|-----------|
| NFRc-01 | Security | Payment data must be handled by a secure gateway/process, with no storage of sensitive card data by the system itself. | There is a payment and refund flow (FR-12 to FR-14). |
| NFRc-02 | Privacy / data protection (LGPD) | Participants' personal data (email, tax ID, etc.) must have profile-based restricted access, especially for the Speaker profile. | FR-16 exposes participant data to a third profile; scope undefined (G-08). |
| NFRc-03 | Performance | Spot/registration counts (FR-07, FR-10) must handle concurrent users registering simultaneously, without causing overbooking. | Real-time automatic spot control mentioned by the organizer. |
| NFRc-04 | Availability | The system must be available during registration opening periods, when traffic tends to be highest. | Replacing manual spreadsheets/forms suggests concentrated usage peaks. |
| NFRc-05 | Accessibility | The registration interface must follow basic accessibility guidelines (WCAG), since the participant audience is broad and non-technical. | The target audience is external (conference/workshop attendees). |

**Handling decision:** it was decided to **formally record the NFR gap** (see `gaps-and-ambiguities.md`, G-09) instead of assuming values. The NFRs above are marked as *candidates*, not approved requirements.
