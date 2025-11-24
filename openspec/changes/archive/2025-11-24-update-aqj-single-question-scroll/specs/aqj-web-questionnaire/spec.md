## RENAMED Requirements
- FROM: `### Requirement: Single-question-per-page layout`
- TO: `### Requirement: Single-question scroll layout`

## MODIFIED Requirements

### Requirement: Single-question scroll layout
The single-question variant SHALL present all 50 questions as vertically stacked cards on a single page so that respondents can scroll, skim, and edit answers without modal navigation.

#### Scenario: All questions visible via scroll
- **WHEN** a respondent opens the single-question form
- **THEN** the UI SHALL render multiple question cards at once on the same page
- **AND** scrolling SHALL reveal the remaining questions without requiring “Next/Previous” navigation buttons.

#### Scenario: Inline editing and quick review
- **WHEN** a respondent wants to revise any answer
- **THEN** tapping or scrolling back to the corresponding card SHALL allow immediate editing without leaving the current page
- **AND** the progress indicator (answered count / remaining count / dot map) SHALL continue to reflect the live state even though all items coexist on one screen.

### Requirement: Completion validation and summary
AQ-J forms SHALL provide both a strict validation flow (prevent completion until every question is answered) and a relaxed demo flow (allow completion even if some answers are missing) while always disclosing the unanswered count to the respondent.

#### Scenario: Strict validation remains available
- **WHEN** strict mode is active (e.g., for production surveys)
- **THEN** attempting to finish with unanswered questions SHALL still block completion and highlight the first missing question, as defined previously.

#### Scenario: Relaxed demo summary
- **WHEN** relaxed demo mode is enabled (e.g., for the single-question scroll variant)
- **THEN** the respondent MAY open the summary even if unanswered questions remain
- **AND** the summary header SHALL state how many questions are unanswered and list or highlight them so the respondent can optionally scroll back to fill them later.

