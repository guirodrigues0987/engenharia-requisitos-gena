# Acceptance Criteria - Eventus System

Given/When/Then format, organized by User Story. Scenarios that depend on a rule not yet defined by the stakeholders are marked **[TO VALIDATE]** instead of assuming a behavior - so the criteria do not lead the team to build/test something nobody has decided.

## US-01 - View available events
- **Given** there are events with open registration, **when** the participant opens the catalog, **then** the system shows all available events in a single listing.

## US-02 - Receive registration receipt
- **Given** the participant has completed a registration, **when** the registration is confirmed, **then** the system issues a receipt.
- **[TO VALIDATE]** receipt delivery channel (email, logged-in area, etc.) - depends on G-05.

## US-03 - Cancel registration
- **Given** an event that allows cancellation and a registration within the allowed period, **when** the participant requests cancellation, **then** the system cancels the registration and releases the spot.
- **Given** an event that does not allow cancellation, **when** the participant tries to cancel, **then** the system informs that this registration cannot be cancelled by the participant.
- **[TO VALIDATE]** definition of "within the allowed period" - depends on G-01.

## US-04 - Issue certificate
- **Given** an event that has already taken place, **when** the participant requests the certificate, **then** the system generates and provides the document, respecting the current issuing condition.
- **[TO VALIDATE]** whether the issuing condition requires attendance confirmation - depends on G-04.

## US-05 - Register for multiple activities on the same day
- **Given** the participant selects two activities with no schedule conflict, **when** they confirm both registrations, **then** the system records both normally.
- **Given** the participant selects two activities at the same time, **when** they try to register for the second one, **then** the system prevents the registration due to a schedule conflict.
- **[TO VALIDATE]** whether the system should only block or also suggest alternatives - depends on G-07.

## US-06 - Automatic spot control
- **Given** an event with available spots, **when** a registration is confirmed, **then** the number of available spots is decremented automatically.
- **Given** an event with no available spots, **when** a new participant tries to register, **then** the system directs them to the waitlist (UC-02).

## US-07 - Waitlist
- **Given** a sold-out event, **when** a participant asks to join the waitlist, **then** the system records their position.
- **[TO VALIDATE]** criteria and method for promoting people from the waitlist when a spot opens up - depends on G-03.

## US-09 - Follow registrations in real time
- **Given** an event with ongoing registrations, **when** the organizer opens the event dashboard, **then** the system shows the current number of registered participants.

## US-11 - Confirm payment
- **Given** a registration pending payment, **when** the finance team confirms the payment, **then** the system releases the participant's registration.
- **Given** a registration pending payment that has not been confirmed, **when** the defined payment deadline expires, **then** **[TO VALIDATE]** - there is no defined rule on the expiration of unpaid registrations; the behavior must not be assumed.

## US-12 - Process refund
- **Given** a paid registration cancelled within the eligibility criteria, **when** the finance team evaluates the case, **then** the refund is processed.
- **[TO VALIDATE]** the objective refund eligibility criteria - depends on G-02.

## US-14 - Speaker views participants
- **Given** an activity under the speaker's responsibility, **when** they open the list of registered participants, **then** the system shows the participants with the data set approved for this profile.
- **[TO VALIDATE]** which personal data fields are shown - depends on G-08 and a privacy/data protection (LGPD) definition.
