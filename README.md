# Requirements Engineering with GenAI - Event Management System (Eventus)

Practical assignment for the Requirements Engineering course (AI postgraduate program). The goal was to analyze the provided elicitation document (the Eventus system) and, with the support of Generative AI, identify requirements, business rules, gaps and ambiguities, and select and produce the most suitable specification artifacts.

> The original course material and the interviews were written in Portuguese; the artifacts in this repository are in English.

## Repository structure

```
engenharia-requisitos-gena/
├── analysis/
│   ├── functional-requirements.md
│   ├── non-functional-requirements.md
│   ├── business-rules.md
│   └── gaps-and-ambiguities.md
├── specification/
│   ├── user-stories.md
│   ├── use-cases.md
│   ├── acceptance-criteria.md
│   └── glossary.md
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

## 1. Chosen specification artifacts

- **User Stories**
- **Use Cases**
- **Acceptance Criteria (Given/When/Then)**
- **Domain Glossary**

## 2. Why these artifacts were considered the most suitable

The system involves **five stakeholder profiles** with very different needs (participant, organizer, finance team, speaker, IT team), taken from direct statements in the interviews - this favors **User Stories**, which preserve each stakeholder's voice in the format "As a [persona], I want [action], so that [benefit]".

Several flows are conditional and multi-actor (registration with payment, cancellation with rules that vary per event, waitlist, refund) - user stories alone do not detail exceptions and decisions enough. For that reason **Use Cases** were written, describing the main flow, alternative flows and - deliberately - explicitly marking where a business rule is missing, instead of presuming a behavior.

The **Acceptance Criteria** in Given/When/Then complement the stories by making each behavior verifiable and testable, and also flag, scenario by scenario, what still depends on validation with the stakeholders (marked `[TO VALIDATE]`).

The **Glossary** was included because the elicitation uses "event", "workshop" and "activity" partially interchangeably - a real ambiguity risk between technical and business teams. The glossary also formalizes the registration and payment *statuses*, which are currently implicit in the stakeholders' statements.

It was decided **not to produce** a full IEEE-SRS style specification document, BPMN diagrams or interface prototypes at this point - rationale in section 5.

## 3. GenAI tool used

**Claude** (Anthropic) was used, in the Claude (Cowork) environment.

## 4. How the AI supported the different stages of the assignment

1. **Structuring the raw material** - the interview text was organized into Functional Requirements, Non-Functional Requirements, Business Rules and Gaps/Ambiguities, referencing each item to the statement it came from.
2. **Artifact recommendation** - based on the project profile (multiple actors, conditional flows, ambiguous terminology), the AI suggested user stories, use cases, acceptance criteria and a glossary as options, explaining the reason for each before any writing.
3. **Writing the artifacts** - the AI drafted the first versions of the four chosen artifacts, always referencing back the source FR/BR (traceability).
4. **Active flagging of gaps** - at every point of the original material marked as "not defined" (section 4 of the elicitation document), the AI was instructed **not to presume a plausible answer**, but to mark the passage as an open point (`[OPEN POINT]` in use cases, `[TO VALIDATE]` in acceptance criteria), citing the corresponding gap.

## 5. AI suggestions accepted, modified or discarded

| AI suggestion | Decision | Rationale |
|---------------|----------|-----------|
| Separate the raw material into FR, NFR, Business Rules and Gaps before writing any artifact | **Accepted** | Gave clear traceability: every story/use case points back to its origin. |
| Combination of User Stories + Use Cases + Acceptance Criteria + Glossary | **Accepted** | Covers both the stakeholder's voice and the complex conditional flows, without requiring artifacts too heavy for the project's current level of definition. |
| Fill in the Non-Functional Requirements with plausible values (e.g. "response time < 2s", "99.9% availability") | **Discarded** | The elicitation document itself states that no NFR was gathered. Assuming numbers would create a false sense of a validated requirement. NFRs were documented only as *candidates to validate* (`non-functional-requirements.md`). |
| Automatically define refund criteria, cancellation deadline, waitlist mechanics and certificate issuing rule | **Discarded** | These are gaps explicitly recorded by the interviewers themselves (section 4 of the document). Filling them with "reasonable" AI answers would risk the development team treating an assumption as a validated decision. The open points were kept and flagged in all artifacts. |
| Generate a single specification document in the IEEE 830 (SRS) standard | **Discarded** | With 9 gaps and at least 4 pending business rules, a full SRS would give the false impression that the specification is closed. User stories and use cases convey the same content with more transparency about what is still incomplete. |
| Create BPMN diagrams of the flows | **Discarded** | It would require a specialized graphical tool and a level of process definition that the material does not yet support; the Mermaid (ER) diagram already covers the need for a structural view at this stage. |
| Produce interface prototypes (wireframes) | **Discarded for now** | High-priority gaps (G-01, G-06, G-07, G-08) directly affect the registration/cancellation screens; prototyping before these definitions would generate rework. It remains a next step after validation with stakeholders. |
| Detail the personal data fields visible to the speaker (UC-06) | **Modified** | The AI initially suggested a list of fields (name, email, company). It was decided not to fix these fields, treating the definition as pending a privacy/data protection (LGPD) analysis (G-08), since the decision involves a risk of exposing personal data. |
| Schedule conflict rule (BR-05) written from the organizer's and participant's two statements | **Modified** | The AI initially treated the two statements ("workshops at the same time" and "register for several workshops on the same day") as the same rule. On review they were separated: one is about the schedule (parallel tracks), the other about preventing conflicting registration for the same participant - recorded in `gaps-and-ambiguities.md` (A-02). |

## 6. Suggested next steps

Validate with the stakeholders the 9 gaps listed in `analysis/gaps-and-ambiguities.md`, prioritizing those that block core features (G-01 cancellation, G-02 refund, G-06 spot reservation, G-07 schedule conflict) before moving on to interface prototypes or detailed data modeling.

## License

[MIT](LICENSE)
