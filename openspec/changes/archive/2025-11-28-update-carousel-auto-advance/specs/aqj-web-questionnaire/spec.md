## MODIFIED Requirements
### Requirement: Carousel layout
The system SHALL provide a "Carousel" prototype where each question is presented on a separate slide, respondents can move between slides horizontally using swipe gestures and/or explicit "Next"/"Previous" controls, and answering a question automatically advances to the next slide (showing the summary instead when the final question is answered).

#### Scenario: Carousel slide navigation
- **WHEN** a respondent uses the Carousel prototype
- **THEN** each slide SHALL display exactly one question with four vertically stacked radio buttons
- **AND** the respondent SHALL be able to move to the next or previous slide using visible controls
- **AND** the UI SHOULD support horizontal swipe gestures on touch devices where feasible
- **AND** selecting an answer SHALL automatically advance to the next slide unless the respondent is already on Question 50, in which case the summary view SHALL open.

#### Scenario: Preserved answers across slides
- **WHEN** a respondent navigates away from a question slide and then returns to it
- **THEN** any previously selected answer for that question SHALL remain selected until explicitly changed or the form is reset.

#### Scenario: Persistent slide progress indicator
- **WHEN** a respondent is on any carousel slide
- **THEN** the UI SHALL prominently display the current question number and total (e.g., "12 / 50") near the top of the viewport
- **AND** a progress dot bar SHALL also be positioned near the header so the respondent can glance at it without scrolling
- **AND** the dot map SHALL mirror the answered/unanswered state in real time even while the carousel auto-advances.

