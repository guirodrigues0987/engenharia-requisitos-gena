# User Stories - Eventus System

Format: **As a** [persona], **I want** [action], **so that** [benefit]. Each story references its source Functional Requirement(s) and, when applicable, the corresponding gap.

## Participant

**US-01** - As a participant, I want to see all available events in a single place, so that I can choose which ones to register for without checking scattered sources.
*(FR-01)*

**US-02** - As a participant, I want to receive a receipt right after registering, so that I have confirmation that my registration was recorded.
*(FR-02 - delivery channel not yet defined, see G-05)*

**US-03** - As a participant, I want to cancel my registration without contacting the organization, so that I can resolve it quickly when I cannot attend.
*(FR-03 - cancellation deadline not defined, see G-01; not every event allows cancellation, see BR-03)*

**US-04** - As a participant, I want to issue my certificate after the event, so that I have proof of my participation.
*(FR-04 - automatic or attendance-based issuing condition not defined, see G-04)*

**US-05** - As a participant, I want to register for several workshops on the same day, so that I make the most of my visit to the event.
*(FR-05 - the system must prevent registration in activities with conflicting schedules, see BR-05 and G-07)*

## Organizer

**US-06** - As an organizer, I want the system to track the number of spots automatically, so that I do not have to update spreadsheets by hand.
*(FR-07)*

**US-07** - As an organizer, I want a waitlist to be created when an event sells out, so that I do not lose interested participants when spots open up.
*(FR-08 - waitlist promotion mechanics not defined, see G-03)*

**US-08** - As an organizer, I want to define whether an event allows registration cancellation, so that I have flexibility according to each event's policy.
*(FR-09, BR-03)*

**US-09** - As an organizer, I want to follow the number of registered participants in real time, so that I have operational visibility while promoting the event.
*(FR-10)*

**US-10** - As an organizer, I want to manage the participants registered in my events, so that I have control over who is confirmed.
*(FR-11)*

## Finance team

**US-11** - As a finance team member, I want to confirm payments for paid registrations, so that the participant's spot is released correctly.
*(FR-12, FR-13, BR-02)*

**US-12** - As a finance team member, I want to process refunds when the participant is entitled to one, so that the cancellation is settled financially.
*(FR-14 - refund eligibility criteria not defined, see G-02)*

## Speaker

**US-13** - As a speaker, I want to view the schedule of my activities, so that I can organize myself in advance.
*(FR-15)*

**US-14** - As a speaker, I want to view the list of participants registered in my activities, so that I know my audience beforehand.
*(FR-16 - exactly which data is visible to the speaker was not defined; requires privacy validation, see G-08)*

---

**Note on non-functional requirements:** no user stories were written for security, performance, availability, accessibility and privacy because no NFR was validated with stakeholders (see `analysis/non-functional-requirements.md`). Turning speculative NFRs into user stories would give the false impression that these requirements have already been agreed upon.
