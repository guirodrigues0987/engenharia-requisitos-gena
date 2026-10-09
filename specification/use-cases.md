# Use Cases - Eventus System

The flows detailed here involve multiple actors, conditional decisions and exceptions - scenarios in which User Stories alone are not enough. Points that depend on a definition not yet made by the stakeholders are marked **[OPEN POINT]**, referencing the corresponding gap, and **were not filled in with assumptions**.

---

## UC-01 - Register for an Event/Activity

**Primary actor:** Participant
**Secondary actors:** Finance team (paid events)
**Precondition:** Authenticated participant; event/activity with open registration.
**Postcondition (success):** Registration recorded; receipt issued (FR-02).

**Main flow:**
1. The participant selects an event/activity in the catalog (FR-01).
2. The system checks spot availability (BR-04).
3. The system checks for a schedule conflict with another already confirmed registration of the participant (BR-05).
4. If the event is free, the system confirms the registration immediately.
5. If the event is paid, the system forwards the participant to the payment flow (BR-02).
6. The system issues a receipt (FR-02).

**Alternative flows:**
- **3a. Schedule conflict detected:** the system prevents the registration. **[OPEN POINT - G-07]** the exact behavior (full block, warning with option to proceed, alternative suggestion) was not defined by the stakeholders.
- **2a. Sold out:** the participant is directed to UC-02 (Join Waitlist).
- **5a. Moment of spot reservation:** **[OPEN POINT - G-06]** it is not defined whether the spot is reserved at the start of the payment process or only after confirmation. Until this rule is validated, the system must not assume automatic reservation before confirmation, to avoid overbooking.

---

## UC-02 - Join Waitlist

**Primary actor:** Participant
**Precondition:** Event/activity with no spots left (BR-04).

**Main flow:**
1. The system informs the participant that there are no spots available.
2. The participant chooses to join the waitlist.
3. The system records the participant in the waitlist of the event/activity.

**[OPEN POINT - G-03]** The waitlist promotion mechanics (order of arrival, automatic promotion when a spot opens, deadline for the participant to confirm) were not defined in the elicitation material. This use case deliberately does not describe the promotion step, so as not to lead the development team to an unvalidated behavior.

---

## UC-03 - Cancel Registration

**Primary actor:** Participant
**Precondition:** Active registration; the event allows cancellation (BR-03).

**Main flow:**
1. The participant requests cancellation of their own registration, without contacting the organization.
2. The system checks whether the event allows cancellation (BR-03).
3. The system checks whether the cancellation is within the allowed period. **[OPEN POINT - G-01]** no deadline is defined.
4. The system carries out the cancellation and releases the spot.
5. The system forwards the case for refund evaluation, if the event is paid (see UC-04).

**Alternative flow:**
- **2a. Event does not allow cancellation:** the system informs the participant that this registration cannot be cancelled by themselves (BR-03).

---

## UC-04 - Process Refund

**Primary actor:** Finance team
**Secondary actor:** Participant (originator via UC-03)
**Precondition:** Paid registration cancelled.

**Main flow:**
1. The system forwards the case to the finance team after a cancellation in a paid event.
2. The finance team evaluates refund eligibility.
3. If eligible, the finance team processes the refund.

**[OPEN POINT - G-02]** The criterion that defines when a participant is entitled to a refund was not gathered in the interviews ("in some cases the participant is entitled to a refund, in others not"). This use case does not assume a criterion (e.g. a deadline of X days) - the eligibility decision remains a manual evaluation by the finance team until the rule is validated with the stakeholders.

---

## UC-05 - Issue Certificate

**Primary actor:** Participant
**Precondition:** Event already held.

**Main flow:**
1. The participant requests the certificate after the event (FR-04).
2. The system checks whether the issuing conditions have been met.
3. The system generates the certificate and makes it available to the participant.

**[OPEN POINT - G-04]** It is not defined whether issuing is automatic for every registrant or conditional on attendance confirmation. Step 2 of this use case is intentionally generic until that definition is made.

---

## UC-06 - View Participants of an Activity

**Primary actor:** Speaker
**Precondition:** Authenticated speaker; activity under their responsibility.

**Main flow:**
1. The speaker selects one of their activities.
2. The system shows the list of registered participants (FR-16).

**[OPEN POINT - G-08]** The set of participant data shown to the speaker (name only? email? company?) was not defined. Since it involves personal data, this definition must consider data minimization principles before implementation - it is recommended to treat it as a privacy requirement to validate (see `analysis/non-functional-requirements.md`).

---

## Traceability Matrix (Use Cases -> Requirements -> Rules)

| Use Case | Functional Requirements | Business Rules | Gaps involved |
|----------|-------------------------|----------------|---------------|
| UC-01 | FR-01, FR-02, FR-05, FR-07 | BR-02, BR-04, BR-05, BR-09 | G-06, G-07 |
| UC-02 | FR-08 | BR-04 | G-03 |
| UC-03 | FR-03 | BR-03, BR-07 | G-01 |
| UC-04 | FR-14 | BR-06 | G-02 |
| UC-05 | FR-04 | BR-08 | G-04 |
| UC-06 | FR-16 | - | G-08 |
