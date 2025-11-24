## ADDED Requirements

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

### Requirement: Single-question-per-page layout
The system SHALL provide a "Single Question" prototype where exactly one question is shown per screen, with vertically stacked radio buttons and a clear progress indicator.

#### Scenario: One question per screen
- **WHEN** a respondent opens the Single Question prototype
- **THEN** the first screen SHALL show only the instructions (or the first question) and navigation controls to start or proceed
- **AND** each subsequent screen SHALL show exactly one question with four vertically stacked radio buttons.

#### Scenario: Progress indication
- **WHEN** a respondent is answering questions in the Single Question prototype
- **THEN** the UI SHALL show how many questions have been completed and/or how many remain (e.g., "10/50", a progress bar, or both)
- **AND** the respondent SHALL be able to move forward to the next question and back to the previous question without losing already selected answers.

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
- **AND** no server-side APIs or databases SHALL be required for the basic MOC behavior.


