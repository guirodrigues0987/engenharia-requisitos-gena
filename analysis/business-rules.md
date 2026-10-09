# Business Rules - Eventus System

Business rules are facts and policies of the domain, distinct from system behavior (which is recorded in the Functional Requirements and detailed in the Use Cases).

| ID | Business Rule | Status |
|----|---------------|--------|
| BR-01 | An event/activity can be free or paid. | Defined |
| BR-02 | Registrations for paid events are only confirmed after payment is confirmed by the finance team. | Defined |
| BR-03 | Not every event allows registration cancellation; the permission is defined per event. | Defined |
| BR-04 | When the spots of an event/activity run out, new registrations go to a waitlist. | Defined (promotion mechanics pending - G-03) |
| BR-05 | A participant cannot register for two activities with conflicting schedules. | Defined (handling of conflict attempts pending - G-07) |
| BR-06 | The right to a refund varies by event/situation; it is not a single rule for the whole system. | **Pending objective criteria - G-02** |
| BR-07 | The deadline until which a participant can cancel a registration is not the same for all events. | **Pending definition - G-01** |
| BR-08 | The certificate is issued only after the event takes place. | Defined (issuing condition - automatic or by attendance confirmation - pending: G-04) |
| BR-09 | The moment a spot is actually reserved (start of payment vs. payment confirmation) has not yet been defined. | **Pending - G-06** |

> Rules marked "Pending" were **explicitly kept open** in the specification artifacts (they were not filled in with AI assumptions). See the rationale in section 5 of `README.md`.
