# aqj-web-questionnaire Specification

## Purpose
TBD - created by archiving change add-aqj-mobile-questionnaire-mocks. Update Purpose after archive.
## Requirements
### Requirement: AQ-J web questionnaire content
The system SHALL present the full 50-item AQ Japanese adult questionnaire, including instructions, numbering, item wording, and the 4-point response scale, as defined in `AQ_Adult_Japanese.md`.

#### Scenario: Full questionnaire is rendered
- **WHEN** a respondent opens any AQ-J web form prototype
- **THEN** the form SHALL include the standard instructions and all 50 items in their original order
- **AND** each item SHALL offer exactly four response options corresponding to the original 1–4 scale semantics.

### Requirement: Mobile-first layout constraints
The system SHALL provide a mobile-first layout for all AQ-J web form prototypes, optimized for smartphone screens in portrait orientation, avoiding horizontal scrolling and horizontal Likert matrices.

#### Scenario: No horizontal scrolling on smartphones
- **WHEN** a respondent views any AQ-J prototype on a smartphone with a viewport width of at least 320px
- **THEN** all question text and response controls SHALL be readable and operable without requiring horizontal scrolling.

#### Scenario: Vertical options or dropdowns only
- **WHEN** response options are displayed
- **THEN** they MUST be rendered either as vertically stacked radio buttons or as a single-select dropdown
- **AND** there MUST NOT be any horizontally scrolling radio button groups or matrix-style grids where options extend off-screen.

### Requirement: Dropdown variant layout
The system SHALL provide a "Dropdown" prototype where all 50 questions are displayed on a single page, each with its question text and a single-select dropdown for choosing a value from 1 to 4.

#### Scenario: Dropdown page layout
- **WHEN** a respondent opens the Dropdown prototype
- **THEN** they SHALL see all 50 questions arranged vertically on a single scrollable page
- **AND** each question SHALL include a labelled dropdown with the four response options mapped to the original scale meanings.

#### Scenario: Section-based chunking
- **WHEN** a respondent scrolls through the Dropdown prototype
- **THEN** the 50 questions SHALL be grouped into logical sections (e.g., blocks of up to 10 questions) with collapsible or paginated containers
- **AND** the UI SHALL indicate the question range within each section (e.g., "Questions 1–10") to reduce cognitive load.

#### Scenario: Mobile-friendly dropdown interaction
- **WHEN** a respondent interacts with any dropdown on a smartphone
- **THEN** the tap target for opening the dropdown and selecting an option SHALL be large enough for finger input
- **AND** the dropdown SHALL open in a way that does not obscure the entire question text permanently (e.g., native mobile dropdown UI that can be dismissed).

### Requirement: Carousel layout
The system SHALL provide a "Carousel" prototype where each question is presented on a separate slide, and respondents can move between slides horizontally using swipe gestures and/or explicit "Next"/"Previous" controls.

#### Scenario: Carousel slide navigation
- **WHEN** a respondent uses the Carousel prototype
- **THEN** each slide SHALL display exactly one question with four vertically stacked radio buttons
- **AND** the respondent SHALL be able to move to the next or previous slide using visible controls
- **AND** the UI SHOULD support horizontal swipe gestures on touch devices where feasible.

#### Scenario: Preserved answers across slides
- **WHEN** a respondent navigates away from a question slide and then returns to it
- **THEN** any previously selected answer for that question SHALL remain selected until explicitly changed or the form is reset.

#### Scenario: Persistent slide progress indicator
- **WHEN** a respondent is on any carousel slide
- **THEN** the UI SHALL prominently display the current question number and total (e.g., "12 / 50") so the respondent always knows their position in the sequence.

### Requirement: Separate entry points per variant
The system SHALL expose three separate entry points (HTML files or routes) so that each AQ-J web form prototype can be opened independently, for example when hosted on GitHub Pages.

#### Scenario: Direct URLs for each prototype
- **WHEN** the prototypes are deployed to a static host such as GitHub Pages
- **THEN** there SHALL be a direct URL for each of the three variants (Dropdown, Single Question, Carousel)
- **AND** opening each URL SHALL load the corresponding variant without requiring any additional navigation.

### Requirement: Static hosting compatibility
The system SHALL implement all AQ-J web form prototypes using only static assets (HTML, CSS, and JavaScript) without server-side runtime dependencies, so they can be hosted on GitHub Pages.

#### Scenario: Static assets only
- **WHEN** the prototypes are built and deployed
- **THEN** all functionality (including navigation between questions, progress indication, and answer retention within a session) SHALL work using only client-side code
- **AND** no server-side APIs or databases SHALL be required for the basic demo behavior.

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
AQ-J forms SHALL provide both a strict validation flow (prevent completion until every question is answered) and a relaxed demo flow (allow completion even if some answers are missing) while always disclosing the unanswered count to the respondent.

#### Scenario: Strict validation remains available
- **WHEN** strict mode is active (e.g., for production surveys)
- **THEN** attempting to finish with unanswered questions SHALL still block completion and highlight the first missing question, as defined previously.

#### Scenario: Relaxed demo summary
- **WHEN** relaxed demo mode is enabled (e.g., for the single-question scroll variant)
- **THEN** the respondent MAY open the summary even if unanswered questions remain
- **AND** the summary header SHALL state how many questions are unanswered and list or highlight them so the respondent can optionally scroll back to fill them later.

### Requirement: Variant-specific completion flow
Each AQ-J form variant SHALL integrate completion and validation controls that suit its navigation model (dropdown sections, single-question pages, carousel slides).

#### Scenario: Dropdown variant completion controls
- **WHEN** the dropdown form detects unanswered questions after a review action
- **THEN** it SHALL expand the corresponding section(s) automatically and show inline error text.

#### Scenario: Single-question and carousel navigation
- **WHEN** there are unanswered questions in the single-question or carousel variant
- **THEN** invoking the completion/review action SHALL jump to the earliest unanswered question so the respondent can resolve it immediately.

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

