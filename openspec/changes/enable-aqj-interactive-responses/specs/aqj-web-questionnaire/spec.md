## ADDED Requirements

### Requirement: Immediate question start
Each AQ-J web form variant SHALL skip personal-information inputs and begin directly at Question 1 so respondents can start answering immediately.

#### Scenario: First screen is Question 1
- **WHEN** a respondent opens any AQ-J form URL
- **THEN** the first interactive screen SHALL present Question 1 with the four-point scale
- **AND** no additional fields (e.g.,氏名/職業/年齢) SHALL be required before answering.

### Requirement: Local answer state tracking
AQ-J forms SHALL maintain the respondent's selections for all 50 questions within the browser session only, allowing navigation back/forth without losing answers.

#### Scenario: Answers persist during session
- **WHEN** a respondent selects an answer for a question and navigates away within the same session
- **THEN** returning to that question SHALL show the previously selected value until the respondent resets or reloads the page.

#### Scenario: No server persistence
- **WHEN** a respondent completes or resets the form
- **THEN** no network request SHALL be issued to store answers externally, and a full page reload SHALL clear all answers.

### Requirement: Completion validation and summary
Before showing completion, AQ-J forms SHALL verify that all 50 questions are answered, guide the user to any missing responses, and upon success display a summary view of the answers.

#### Scenario: Missing answers highlighted
- **WHEN** a respondent attempts to finish with unanswered questions
- **THEN** the UI SHALL list the missing question numbers, focus or scroll to the first missing question, and prevent completion until all responses are provided.

#### Scenario: Summary view after completion
- **WHEN** all 50 responses are provided
- **THEN** the form SHALL present a completion state summarizing every question number and the chosen value (e.g., table or downloadable text) so the respondent can copy or review their answers.

### Requirement: Variant-specific completion flow
Each AQ-J form variant SHALL integrate completion and validation controls that suit its navigation model (dropdown sections, single-question pages, carousel slides).

#### Scenario: Dropdown variant completion controls
- **WHEN** the dropdown form detects unanswered questions after a review action
- **THEN** it SHALL expand the corresponding section(s) automatically and show inline error text.

#### Scenario: Single-question and carousel navigation
- **WHEN** there are unanswered questions in the single-question or carousel variant
- **THEN** invoking the completion/review action SHALL jump to the earliest unanswered question so the respondent can resolve it immediately.

