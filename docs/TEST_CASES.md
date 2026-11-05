# Ticket Reservation System — Test Cases

These are functional test cases derived from the storyboard. Replace sample data with fixtures supported by the implementation. Unless noted otherwise, each test starts with a valid trip and test passenger in a clean test environment.

| ID | Feature | Preconditions / Test data | Steps | Expected result | Priority |
|---|---|---|---|---|---|
| TC-01 | Search matching trips | A trip exists for the selected route and future date | Enter origin, destination, and date; submit search | Matching trip is displayed with correct schedule, price, and availability | High |
| TC-02 | Search with no results | No trip exists for selected route/date | Search that route/date | Clear no-results message appears; no unrelated trip is shown | Medium |
| TC-03 | Required search fields | Search form is available | Submit with origin, destination, or date missing | Search is not submitted; required field validation is shown | High |
| TC-04 | Same origin and destination | Search form is available | Set origin and destination to the same location; submit | Search is rejected with a useful validation message | Medium |
| TC-05 | Past travel date | Search form is available | Select a date in the past; submit | Search is rejected and no booking can be made for that date | High |
| TC-06 | View trip details | A matching trip exists | Open the trip from search results | Correct origin, destination, departure, price, and seat availability are shown | High |
| TC-07 | Successful reservation | Trip has an available seat; passenger details are valid | Select the trip and seat, enter details, and confirm | Booking is created with a unique reference; confirmation shows correct details; seat becomes unavailable | High |
| TC-08 | Missing passenger information | Trip has an available seat | Leave a required passenger field blank and confirm | Validation is shown; no confirmed booking is created; seat remains available | High |
| TC-09 | Invalid passenger information | Trip has an available seat | Enter malformed or out-of-range passenger data and confirm | Invalid data is rejected; no booking is created | High |
| TC-10 | Seat already booked | Seat is already reserved on the selected trip | Attempt to reserve that seat | Reservation is rejected; existing booking remains unchanged; availability is accurate | High |
| TC-11 | Concurrent reservation conflict | Two sessions select the same last available seat | Confirm both reservations as close together as possible | At most one reservation succeeds; the other receives a conflict/availability message; inventory remains consistent | High |
| TC-12 | Booking details | A booking exists for the passenger | Open the booking using its reference and authorized passenger context | Correct reference, trip, passenger, seat, price, and status are displayed | High |
| TC-13 | Unknown booking reference | No booking exists for the supplied reference | Request booking details using the unknown reference | A not-found message appears; no other booking or passenger data is disclosed | High |
| TC-14 | Successful cancellation | Booking is confirmed and meets cancellation policy | Cancel the booking | Status changes to cancelled; seat becomes available; confirmation is shown | High |
| TC-15 | Cancellation outside policy | Booking is not eligible for cancellation | Attempt cancellation | Cancellation is rejected with the applicable reason; booking and inventory remain unchanged | Medium |
| TC-16 | Repeat cancellation | Booking is already cancelled | Submit cancellation again | Operation is safely handled; no duplicate release or inconsistent inventory occurs | Medium |
| TC-17 | Admin creates trip | Authorized admin; valid schedule and seat count | Submit a new valid trip | Trip is saved and appears in passenger search with correct availability | Medium |
| TC-18 | Invalid admin schedule | Authorized admin | Submit a trip with missing fields, invalid times, or a negative seat count | Validation errors appear; invalid trip is not saved | High |
| TC-19 | Unauthorized inventory update | User is not an administrator | Attempt to create or update a trip/seat inventory | Access is denied; inventory is unchanged | High |
| TC-20 | Updated availability shown | Admin has changed valid seat inventory | Search for the affected trip after the update | Search results reflect the latest inventory and cannot show more seats than are actually available | High |

## Suggested execution tracking
Record results in a GitHub Issue, pull request, or CI test report using this format:

| Test ID | Result (Not run / Pass / Fail / Blocked) | Build or commit | Notes / issue link |
|---|---|---|---|
| TC-01 | Not run | — | — |

## Notes
- Add automated unit, integration, or end-to-end tests for the cases that match the project's architecture.
- Test authorization and data privacy in addition to the happy path.
- For booking concurrency, verify the reservation is atomic so two requests cannot claim the same seat.
- Keep cancellation eligibility consistent with the system's documented policy.
