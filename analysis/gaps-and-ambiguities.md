# Gaps and Ambiguities - Eventus System

Items identified in section 4 (Notes) of the elicitation document, complemented by terminology inconsistencies found during the analysis.

## Explicit gaps (cited in the original document)

| ID | Gap | Impact |
|----|-----|--------|
| G-01 | Deadline for cancelling a registration is not defined. | Affects FR-03 / BR-07. |
| G-02 | Refund eligibility criteria are not defined. | Affects FR-14 / BR-06. |
| G-03 | Waitlist mechanics (order, automatic or manual promotion) are not defined. | Affects FR-08 / BR-04. |
| G-04 | It is not defined whether the certificate is issued automatically or depends on attendance confirmation. | Affects FR-04 / BR-08. |
| G-05 | Channel for sending receipts and notifications (email, SMS, push) is not defined. | Affects FR-02. |
| G-06 | Moment of spot reservation (start of payment vs. confirmation) is not defined. | Affects FR-07 / BR-09. |
| G-07 | Handling of registration attempts in activities with conflicting schedules is not defined (automatic block? warning?). | Affects FR-05 / BR-05. |
| G-08 | Which participant data the speaker may view was not defined. | Affects FR-16 - risk of improper exposure of personal data. |
| G-09 | No non-functional requirement (security, performance, availability, accessibility, privacy) was gathered with the stakeholders. | Affects the whole system - see `non-functional-requirements.md`. |

## Ambiguities identified during the analysis

| ID | Ambiguity | Handling |
|----|-----------|----------|
| A-01 | The terms "event", "workshop" and "activity" are used partially interchangeably in the document (e.g. an "event" can contain several parallel "workshops"/"activities"). | Formalized in `glossary.md`, with an event -> activity hierarchy. |
| A-02 | The organizer's statement "workshops happening at the same time must run simultaneously" describes the schedule (parallel tracks), while the participant's statement "register for several workshops on the same day" is about registering for multiple activities - not necessarily at the same time. The two statements are not contradictory, but were initially confused as if they were the same rule. | Separated into BR-05 (schedule conflict at registration) and a schedule note (outside the scope of a requirement; it is a characteristic of the scheduling data model). |

**Next step:** all gaps (G-01 to G-09) were kept as open points in the specification artifacts (user stories, use cases and acceptance criteria) instead of being resolved with assumptions. This was a deliberate decision when using the AI - see section 5 of `README.md`.
