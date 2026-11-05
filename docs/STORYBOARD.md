# Ticket Reservation System — Storyboard & Progress

## Goal
Allow passengers to find trips, choose available seats, reserve tickets, and manage bookings. Administrators maintain schedules and seat inventory.

## Progress board
Move each story through **Backlog → To Do → In Progress → Review → Done** as work proceeds. The statuses below are initial planning statuses; update them to reflect implementation progress.

| ID | Story | Priority | Status | Depends on |
|---|---|---:|---|---|
| US-01 | Search trips by origin, destination, and travel date | High | Backlog | — |
| US-02 | View trip details, prices, and available seats | High | Backlog | US-01 |
| US-03 | Select an available seat and reserve a ticket | High | Backlog | US-02 |
| US-04 | Receive and view booking confirmation/details | High | Backlog | US-03 |
| US-05 | Cancel an eligible reservation and release its seat | Medium | Backlog | US-03 |
| US-06 | Prevent invalid, duplicate, or conflicting bookings | High | Backlog | US-03 |
| US-07 | Admin creates and updates trips and seat inventory | Medium | Backlog | — |

## Story details and acceptance criteria

### US-01 — Search trips
**As a** passenger, **I want** to search by origin, destination, and date, **so that** I can find trips that suit my travel plans.

Acceptance criteria:
- Origin, destination, and travel date are required.
- Origin and destination must be different.
- A valid search shows matching trips.
- A search with no matches shows a clear empty-state message.
- Invalid or past travel dates are rejected with a helpful message.

### US-02 — View trip and seat availability
**As a** passenger, **I want** to see trip details and available seats, **so that** I can make an informed choice.

Acceptance criteria:
- Results show origin, destination, departure time, price, and availability.
- Only seats currently available for the selected trip can be chosen.
- No availability is clearly indicated.

### US-03 — Reserve a ticket
**As a** passenger, **I want** to choose an available seat and reserve it, **so that** my place on the trip is secured.

Acceptance criteria:
- Required passenger details and one available seat are required.
- A successful reservation creates a unique booking reference.
- The chosen seat is no longer available to other passengers.
- If another passenger reserves the seat first, the conflicting request is rejected and availability is refreshed.

### US-04 — View booking details
**As a** passenger, **I want** to view my booking details, **so that** I can verify my trip and reservation.

Acceptance criteria:
- Booking details show booking reference, passenger, trip, departure, seat, price, and status.
- Unknown booking references do not reveal another passenger's booking and show a useful error.

### US-05 — Cancel a reservation
**As a** passenger, **I want** to cancel an eligible booking, **so that** I can release my seat when plans change.

Acceptance criteria:
- Only eligible bookings can be cancelled, according to the cancellation policy.
- A successful cancellation updates the booking status and releases the seat.
- Repeated cancellation requests do not create inconsistent state.
- The passenger receives a cancellation confirmation or a clear reason for rejection.

### US-06 — Protect booking integrity
**As a** system, **I want** to validate booking requests, **so that** invalid data and double-bookings are prevented.

Acceptance criteria:
- Required fields are validated.
- A seat cannot be booked twice for the same trip.
- Invalid passenger details and invalid trip/seat combinations are rejected.
- Failed reservations do not consume a seat or create a confirmed booking.

### US-07 — Manage trips and inventory
**As an** administrator, **I want** to create and update trips and seat inventory, **so that** passengers see accurate availability.

Acceptance criteria:
- Authorized administrators can create and update valid trips.
- Invalid schedules and seat counts are rejected.
- Updated trip and availability data is reflected in passenger searches.
- Unauthorized users cannot change inventory.

## Suggested GitHub workflow
- Track each story as a GitHub Issue using the IDs above in issue titles.
- Add issues to a GitHub Project board with the five status columns listed above.
- Assign an owner and link related implementation/test pull requests to each issue.
- Move a story to **Done** only when its acceptance criteria pass and changes are reviewed.
- Update this table as a simple progress summary; the live Project board should be the source of truth.

## Definition of Done
- Acceptance criteria are implemented and tested.
- Relevant tests pass and changes are reviewed.
- User-facing validation and error states are understandable.
- Documentation is updated where needed.
