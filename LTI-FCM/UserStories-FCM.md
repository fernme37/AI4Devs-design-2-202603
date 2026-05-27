# 1. GENERATE USER STORIES

## PROMPT 01

You are a Product Manager and Business Analyst, based on PRD document (LTI-FCM.md) generate at least 2 User Stories with any of the following formats/templates:

```
- "As a [user role], I want to [goal] so that I can [benefit]"
- "As a [type of user], I want to [perform an action] to [gain a benefit]"
```

Remember to follow the the good practices to create user stories and apply the INVEST criteria on them.
Add acceptance criteria in format BDD (Behavior-Driven Development)(Given/When/Then).

The whole user story format must be:

Title
User story (description with the previou user story template indicated)
Acceptance criteria (BDD)
Additional notes (if neccesary)
Related user stories (if apply)
INVEST evaluation (checklist)

# ATS User Stories

These user stories are based on the ATS PRD in `LTI-FCM.md` and follow INVEST criteria. Acceptance criteria are written in BDD format.

---

## 1. AI-Powered Candidate Shortlisting

### User story

As a recruiter, I want to automatically rank applicants based on their match with a job description so that I can identify the most relevant candidates faster.

### Acceptance criteria (BDD)

**Scenario 1: Rank candidates after receiving applications**

Given a published job has defined required skills, experience level, location, and employment type  
And multiple candidates have submitted applications with resumes  
When the recruiter opens the candidate list for that job  
Then the system displays candidates ordered by match score from highest to lowest  
And each candidate shows the main matching factors used to calculate the score.

**Scenario 2: Filter candidates by minimum match score**

Given the recruiter is viewing ranked candidates for a job  
When the recruiter applies a minimum match score filter  
Then the system only displays candidates who meet or exceed that score  
And the total number of visible candidates is updated.

**Scenario 3: Handle incomplete resume data**

Given a candidate resume cannot be fully parsed  
When the system calculates the candidate match score  
Then the system marks the profile as partially parsed  
And the candidate remains visible in the list with an explanation of missing data.

### Additional notes

The ranking must support recruiter review and must not automatically reject candidates without human confirmation.

### Related user stories

- Candidate profile creation from resume parsing
- Recruiter candidate filtering and search
- Hiring manager candidate review

### INVEST evaluation (checklist)

- Independent: Can be developed without requiring the full analytics or interview modules.
- Negotiable: Match criteria and score explanation details can be refined during backlog grooming.
- Valuable: Reduces manual screening effort and accelerates recruiter decision-making.
- Estimable: Scope can be estimated around ranking, filtering, and score explanation.
- Small: Focused on candidate ranking for a single job opening.
- Testable: Acceptance criteria verify ranking, filtering, and incomplete data behavior.

---

## 2. Candidate Application Status Tracking

### User story

As a candidate, I want to view the real-time status of my job application so that I can understand where I am in the hiring process without contacting the recruiter.

### Acceptance criteria (BDD)

**Scenario 1: View current application status**

Given a candidate has submitted an application  
And the candidate is logged into the candidate portal  
When the candidate opens the application details page  
Then the system displays the current application status  
And the system displays the last status update date.

**Scenario 2: Show hiring process stages**

Given the company has configured a hiring pipeline for the job  
When the candidate views the application status  
Then the system displays the hiring stages in order  
And highlights the current stage.

**Scenario 3: Notify candidate when status changes**

Given the candidate has an active application  
When the recruiter changes the application status  
Then the system sends a notification to the candidate  
And the candidate portal displays the updated status.

### Additional notes

Candidate-facing statuses should be clear and friendly, avoiding internal-only labels such as "requisition review queue" or "manager pending sync."

### Related user stories

- Candidate communication management
- Automated workflow notifications
- Recruiter pipeline management

### INVEST evaluation (checklist)

- Independent: Can be implemented for the candidate portal without requiring AI screening.
- Negotiable: Status labels and notification channels can be adjusted by product and HR teams.
- Valuable: Improves candidate experience and reduces recruiter follow-up messages.
- Estimable: Scope is limited to displaying status, stages, and status-change notifications.
- Small: Focused on one candidate-facing workflow.
- Testable: Acceptance criteria verify display, stage highlighting, and notifications.

---

## 3. Smart Interview Scheduling

### User story

As a recruiter, I want to schedule interviews using calendar availability and automatic time-zone handling so that I can coordinate interviews faster and avoid scheduling errors.

### Acceptance criteria (BDD)

**Scenario 1: Suggest available interview slots**

Given a recruiter selects a candidate and one or more interviewers  
And all selected users have connected calendars  
When the recruiter opens the interview scheduling tool  
Then the system suggests available time slots that work for all selected participants.

**Scenario 2: Create interview with video meeting link**

Given the recruiter selects an available time slot  
When the recruiter confirms the interview  
Then the system creates the interview event  
And adds a video meeting link  
And sends calendar invitations to the candidate and interviewers.

**Scenario 3: Display candidate local time**

Given the candidate is in a different time zone than the recruiter  
When the interview invitation is generated  
Then the system displays the interview time in the candidate's local time zone  
And stores the interview time consistently in the system.

### Additional notes

Calendar and video integrations may initially support one provider and later expand to Google Workspace, Microsoft Teams, and Zoom.

### Related user stories

- Interview reminder notifications
- Interview feedback submission
- Candidate portal interview visibility

### INVEST evaluation (checklist)

- Independent: Can be delivered as part of the interview module without requiring offer management.
- Negotiable: Supported calendar providers and slot rules can be prioritized incrementally.
- Valuable: Reduces coordination effort and improves candidate experience.
- Estimable: Scope can be estimated by calendar availability lookup, event creation, and notification flow.
- Small: Focused on scheduling a single interview.
- Testable: Acceptance criteria verify slot suggestions, event creation, and time-zone handling.

---

## 4. Recruitment KPI Dashboard

### User story

As an HR leader, I want to monitor recruitment KPIs in a real-time dashboard so that I can identify bottlenecks and improve hiring performance.

### Acceptance criteria (BDD)

**Scenario 1: View key recruitment metrics**

Given the HR leader is logged into the ATS  
When the HR leader opens the recruitment dashboard  
Then the system displays time-to-hire, candidate funnel conversion, open jobs, and offer acceptance rate  
And each metric is calculated from current recruitment data.

**Scenario 2: Filter metrics by department and date range**

Given the dashboard contains recruitment data across multiple departments  
When the HR leader selects a department and date range  
Then the system updates all dashboard metrics based on the selected filters.

**Scenario 3: Highlight recruitment bottlenecks**

Given one hiring stage has a higher-than-expected candidate delay  
When the dashboard loads  
Then the system highlights the stage as a potential bottleneck  
And displays the average time candidates spend in that stage.

### Additional notes

Dashboard metrics should be role-based so HR leaders can access organization-level insights while recruiters may see only assigned jobs.

### Related user stories

- Recruiter productivity reporting
- Candidate funnel analytics
- Predictive hiring insights

### INVEST evaluation (checklist)

- Independent: Can start with operational dashboard metrics before predictive analytics is added.
- Negotiable: KPI definitions and thresholds can be refined with HR stakeholders.
- Valuable: Supports data-driven hiring decisions and process optimization.
- Estimable: Scope can be estimated around defined metrics, filters, and bottleneck indicators.
- Small: Focused on a first dashboard version with core KPIs.
- Testable: Acceptance criteria verify displayed metrics, filtering, and bottleneck highlighting.

# 2. GENERATE BACKLOG

## PROMPT 02

You are a Prompt Engineer, create a prompt that generate the backlog for the previous user stories created

## PROMPT 03

You are a Product Manager, Business Analyst, and Agile Product Owner with experience in ATS (Applicant Tracking System) products.

Based on the previous user stories created, generate a structured product backlog that can be used by a Scrum team to plan and execute the first MVP release of the ATS.

The backlog must be derived from the existing user stories and acceptance criteria. Do not invent unrelated features. If a backlog item requires an assumption, clearly document it.

For each backlog item, include:

- Backlog item ID
- Epic
- Feature or module
- Backlog item title
- User story reference
- Description
- Priority using MoSCoW: Must Have, Should Have, Could Have, Won't Have for MVP
- Business value
- Acceptance criteria in BDD format using Given/When/Then
- Dependencies
- Estimated effort using story points
- Suggested sprint or release phase
- Definition of Done
- Risks or considerations, if applicable

Organize the backlog using the following structure:

1. Backlog overview
2. MVP scope summary
3. Backlog table
4. Detailed backlog items
5. Dependency map
6. Suggested sprint plan
7. Out-of-scope items for MVP
8. Assumptions

Apply good Agile backlog practices:

- Backlog items must be clear, small, and testable.
- Each item must deliver business or user value.
- Items must be prioritized according to MVP needs.
- Dependencies must be explicit.
- Acceptance criteria must be measurable.
- Technical tasks should be included only when they are necessary to deliver a user-facing story.
- Avoid duplicate backlog items.

Is very important prioritize/order and add a justification.

Use Markdown format.

## 1. Backlog Overview

This backlog defines the first MVP release for an AI-powered Applicant Tracking System based on the previous user stories:

1. AI-Powered Candidate Shortlisting
2. Candidate Application Status Tracking
3. Smart Interview Scheduling
4. Recruitment KPI Dashboard

The backlog is prioritized to first deliver the minimum recruitment workflow needed to create value: candidates apply, recruiters review ranked candidates, candidates track status, interviews are scheduled, and HR leaders monitor basic hiring performance.

---

## 2. MVP Scope Summary

### MVP Goal

Deliver a usable ATS MVP that helps recruiters reduce manual screening effort, improves candidate transparency, supports interview coordination, and gives HR leaders visibility into basic recruitment KPIs.

### MVP Must-Have Capabilities

- Candidate ranking by match score
- Candidate match explanation
- Candidate application status tracking
- Hiring pipeline stage visibility
- Status-change notification
- Interview scheduling
- Calendar invitation and video meeting support
- Basic recruitment KPI dashboard

### Prioritization Logic

The backlog is ordered by business dependency and MVP value:

1. Candidate and application data must exist before ranking, status tracking, interviews, or dashboards can work.
2. AI shortlisting provides the strongest recruiter productivity value.
3. Candidate status tracking improves candidate experience and reduces manual communication.
4. Interview scheduling supports the next stage of the hiring funnel.
5. KPI dashboards depend on application, status, and interview data, so they come later.

---

## 3. Backlog Table


| Order | ID         | Epic                 | Backlog Item                                         | Priority    | Story Points | Sprint            | Justification                                                         |
| ----- | ---------- | -------------------- | ---------------------------------------------------- | ----------- | ------------ | ----------------- | --------------------------------------------------------------------- |
| 1     | ATS-BL-001 | Candidate Management | Store candidate applications and resume metadata     | Must Have   | 5            | Sprint 1          | Foundation for screening, status tracking, interviews, and reporting. |
| 2     | ATS-BL-002 | AI Screening         | Parse resume data for candidate matching             | Must Have   | 8            | Sprint 1          | Required before candidate ranking can provide useful results.         |
| 3     | ATS-BL-003 | AI Screening         | Generate candidate-job match score                   | Must Have   | 8            | Sprint 2          | Core value of AI-powered shortlisting.                                |
| 4     | ATS-BL-004 | AI Screening         | Display ranked candidate list with score explanation | Must Have   | 5            | Sprint 2          | Enables recruiters to act on the AI screening result.                 |
| 5     | ATS-BL-005 | AI Screening         | Filter candidates by minimum match score             | Should Have | 3            | Sprint 2          | Improves recruiter efficiency once ranking exists.                    |
| 6     | ATS-BL-006 | Candidate Portal     | Display current application status                   | Must Have   | 5            | Sprint 3          | Core candidate transparency feature.                                  |
| 7     | ATS-BL-007 | Candidate Portal     | Display hiring pipeline stages                       | Must Have   | 5            | Sprint 3          | Helps candidates understand where they are in the process.            |
| 8     | ATS-BL-008 | Notifications        | Notify candidates when application status changes    | Should Have | 5            | Sprint 3          | Reduces recruiter follow-up work and improves candidate experience.   |
| 9     | ATS-BL-009 | Interview Management | Suggest available interview slots                    | Must Have   | 8            | Sprint 4          | Core scheduling capability and major recruiter time-saver.            |
| 10    | ATS-BL-010 | Interview Management | Create interview event with video meeting link       | Must Have   | 5            | Sprint 4          | Completes the scheduling workflow.                                    |
| 11    | ATS-BL-011 | Interview Management | Display interview time in candidate local time zone  | Should Have | 3            | Sprint 4          | Reduces scheduling errors and improves candidate experience.          |
| 12    | ATS-BL-012 | Analytics            | Display core recruitment KPI dashboard               | Must Have   | 8            | Sprint 5          | Gives HR leaders visibility into MVP recruitment performance.         |
| 13    | ATS-BL-013 | Analytics            | Filter dashboard by department and date range        | Should Have | 5            | Sprint 5          | Makes KPI data actionable for HR leaders.                             |
| 14    | ATS-BL-014 | Analytics            | Highlight recruitment bottlenecks                    | Could Have  | 5            | Sprint 5 or Later | Valuable insight, but can be deferred if MVP timeline is tight.       |


---

## 4. Detailed Backlog Items

### ATS-BL-001: Store Candidate Applications and Resume Metadata

**Epic:** Candidate Management  
**Feature or module:** Candidate Application Management  
**User story reference:** AI-Powered Candidate Shortlisting, Candidate Application Status Tracking  
**Priority:** Must Have  
**Business value:** Creates the data foundation for screening, status tracking, interview scheduling, and reporting.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 1  

**Description:**  
Allow the ATS to store submitted candidate applications, including candidate identity, job reference, resume file metadata, submission date, and current application status.

**Acceptance criteria (BDD):**

Given a candidate submits an application  
When the application is saved  
Then the system stores the candidate profile, job reference, resume metadata, submission date, and initial status.

Given a recruiter opens the applications list for a job  
When applications exist for that job  
Then the system displays the stored applications.

**Dependencies:** None  
**Definition of Done:** Data is stored, retrievable, linked to a job, and covered by basic validation tests.  
**Risks or considerations:** Candidate personal data must be handled securely.

---

### ATS-BL-002: Parse Resume Data for Candidate Matching

**Epic:** AI Screening  
**Feature or module:** Resume Parsing  
**User story reference:** AI-Powered Candidate Shortlisting  
**Priority:** Must Have  
**Business value:** Enables structured candidate evaluation instead of manual resume reading.  
**Estimated effort:** 8 story points  
**Suggested sprint or release phase:** Sprint 1  

**Description:**  
Extract structured information from resumes, including skills, experience, education, certifications, and parsing status.

**Acceptance criteria (BDD):**

Given a candidate uploads a resume  
When the resume parser processes the file  
Then the system extracts relevant candidate information.

Given a resume cannot be fully parsed  
When parsing finishes  
Then the system marks the candidate profile as partially parsed  
And stores the missing-data explanation.

**Dependencies:** ATS-BL-001  
**Definition of Done:** Resume data is extracted, stored, and incomplete parsing is visibly flagged.  
**Risks or considerations:** Resume formats may vary widely.

---

### ATS-BL-003: Generate Candidate-Job Match Score

**Epic:** AI Screening  
**Feature or module:** Candidate Matching  
**User story reference:** AI-Powered Candidate Shortlisting  
**Priority:** Must Have  
**Business value:** Reduces manual screening effort and helps recruiters identify strong candidates faster.  
**Estimated effort:** 8 story points  
**Suggested sprint or release phase:** Sprint 2  

**Description:**  
Calculate a match score between each candidate and a job using required skills, experience, location, and employment type.

**Acceptance criteria (BDD):**

Given a job has defined requirements  
And candidates have parsed resume data  
When the matching process runs  
Then each candidate receives a match score.

Given some candidate data is incomplete  
When the score is calculated  
Then the system still generates a score  
And marks the score as based on partial data.

**Dependencies:** ATS-BL-001, ATS-BL-002  
**Definition of Done:** Match scores are generated consistently and stored for recruiter review.  
**Risks or considerations:** Scoring must be explainable and should not automatically reject candidates.

---

### ATS-BL-004: Display Ranked Candidate List With Score Explanation

**Epic:** AI Screening  
**Feature or module:** Recruiter Candidate Review  
**User story reference:** AI-Powered Candidate Shortlisting  
**Priority:** Must Have  
**Business value:** Allows recruiters to act on the match score during screening.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 2  

**Description:**  
Show candidates ordered by match score, including the main matching factors behind each score.

**Acceptance criteria (BDD):**

Given a recruiter opens the candidate list for a job  
When match scores are available  
Then candidates are displayed from highest score to lowest score.

Given a candidate has a match score  
When the recruiter views the candidate row or profile  
Then the system displays the main matching factors.

**Dependencies:** ATS-BL-003  
**Definition of Done:** Recruiter can view ranked candidates and score explanations.  
**Risks or considerations:** Score explanation must be clear enough to support human decision-making.

---

### ATS-BL-005: Filter Candidates by Minimum Match Score

**Epic:** AI Screening  
**Feature or module:** Recruiter Candidate Review  
**User story reference:** AI-Powered Candidate Shortlisting  
**Priority:** Should Have  
**Business value:** Helps recruiters focus on the most relevant applicants.  
**Estimated effort:** 3 story points  
**Suggested sprint or release phase:** Sprint 2  

**Description:**  
Allow recruiters to filter the candidate list using a minimum match score.

**Acceptance criteria (BDD):**

Given the recruiter is viewing ranked candidates  
When the recruiter applies a minimum score filter  
Then only candidates meeting or exceeding the score are displayed.

Given the filter is applied  
When the visible list changes  
Then the system updates the visible candidate count.

**Dependencies:** ATS-BL-004  
**Definition of Done:** Filter works reliably and can be cleared.  
**Risks or considerations:** Filtering should not be confused with candidate rejection.

---

### ATS-BL-006: Display Current Application Status

**Epic:** Candidate Portal  
**Feature or module:** Application Status Tracking  
**User story reference:** Candidate Application Status Tracking  
**Priority:** Must Have  
**Business value:** Improves candidate transparency and reduces manual recruiter follow-ups.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 3  

**Description:**  
Allow candidates to view the current status of their submitted application.

**Acceptance criteria (BDD):**

Given a candidate has submitted an application  
And the candidate is logged into the candidate portal  
When the candidate opens the application details page  
Then the system displays the current application status  
And the last status update date.

**Dependencies:** ATS-BL-001  
**Definition of Done:** Candidate can securely view only their own application status.  
**Risks or considerations:** Status labels must be candidate-friendly.

---

### ATS-BL-007: Display Hiring Pipeline Stages

**Epic:** Candidate Portal  
**Feature or module:** Application Status Tracking  
**User story reference:** Candidate Application Status Tracking  
**Priority:** Must Have  
**Business value:** Helps candidates understand where they are in the process.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 3  

**Description:**  
Show the ordered hiring stages for a job and highlight the candidate’s current stage.

**Acceptance criteria (BDD):**

Given a job has a configured hiring pipeline  
When the candidate views application status  
Then the system displays the stages in order  
And highlights the current stage.

**Dependencies:** ATS-BL-006  
**Definition of Done:** Candidate can see a clear visual or structured representation of the hiring process.  
**Risks or considerations:** Internal-only workflow states should not be exposed directly.

---

### ATS-BL-008: Notify Candidates When Application Status Changes

**Epic:** Notifications  
**Feature or module:** Candidate Communication  
**User story reference:** Candidate Application Status Tracking  
**Priority:** Should Have  
**Business value:** Improves candidate experience and reduces recruiter communication workload.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 3  

**Description:**  
Send a notification when a recruiter changes a candidate’s application status.

**Acceptance criteria (BDD):**

Given a candidate has an active application  
When the recruiter changes the application status  
Then the system sends a notification to the candidate  
And the candidate portal displays the updated status.

**Dependencies:** ATS-BL-006  
**Definition of Done:** Candidate receives status-change notification and portal status is updated.  
**Risks or considerations:** Notification preferences may be needed in future releases.

---

### ATS-BL-009: Suggest Available Interview Slots

**Epic:** Interview Management  
**Feature or module:** Smart Interview Scheduling  
**User story reference:** Smart Interview Scheduling  
**Priority:** Must Have  
**Business value:** Reduces scheduling effort for recruiters.  
**Estimated effort:** 8 story points  
**Suggested sprint or release phase:** Sprint 4  

**Description:**  
Suggest interview time slots based on recruiter, interviewer, and candidate availability.

**Acceptance criteria (BDD):**

Given a recruiter selects a candidate and interviewers  
And selected users have connected calendars  
When the recruiter opens the scheduling tool  
Then the system suggests available time slots that work for all selected participants.

**Dependencies:** ATS-BL-001  
**Definition of Done:** Recruiter can see valid suggested slots for selected participants.  
**Risks or considerations:** MVP may support only one calendar provider.

---

### ATS-BL-010: Create Interview Event With Video Meeting Link

**Epic:** Interview Management  
**Feature or module:** Smart Interview Scheduling  
**User story reference:** Smart Interview Scheduling  
**Priority:** Must Have  
**Business value:** Completes the interview scheduling workflow and reduces manual setup.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 4  

**Description:**  
Create an interview calendar event, generate a video meeting link, and send invitations.

**Acceptance criteria (BDD):**

Given the recruiter selects an available time slot  
When the recruiter confirms the interview  
Then the system creates the interview event  
And adds a video meeting link  
And sends calendar invitations to the candidate and interviewers.

**Dependencies:** ATS-BL-009  
**Definition of Done:** Interview event is created and participants receive invitations.  
**Risks or considerations:** Video meeting provider integration may be limited in MVP.

---

### ATS-BL-011: Display Interview Time in Candidate Local Time Zone

**Epic:** Interview Management  
**Feature or module:** Smart Interview Scheduling  
**User story reference:** Smart Interview Scheduling  
**Priority:** Should Have  
**Business value:** Reduces missed interviews and scheduling confusion.  
**Estimated effort:** 3 story points  
**Suggested sprint or release phase:** Sprint 4  

**Description:**  
Display interview time in the candidate’s local time zone while storing a consistent system time.

**Acceptance criteria (BDD):**

Given the candidate is in a different time zone than the recruiter  
When the interview invitation is generated  
Then the system displays the interview time in the candidate's local time zone  
And stores the interview time consistently in the system.

**Dependencies:** ATS-BL-010  
**Definition of Done:** Candidate-facing interview time is localized and system storage remains consistent.  
**Risks or considerations:** Candidate time zone must be known or inferred reliably.

---

### ATS-BL-012: Display Core Recruitment KPI Dashboard

**Epic:** Analytics  
**Feature or module:** Recruitment Dashboard  
**User story reference:** Recruitment KPI Dashboard  
**Priority:** Must Have  
**Business value:** Gives HR leaders visibility into recruitment performance.  
**Estimated effort:** 8 story points  
**Suggested sprint or release phase:** Sprint 5  

**Description:**  
Display time-to-hire, candidate funnel conversion, open jobs, and offer acceptance rate.

**Acceptance criteria (BDD):**

Given the HR leader is logged into the ATS  
When the HR leader opens the recruitment dashboard  
Then the system displays time-to-hire, candidate funnel conversion, open jobs, and offer acceptance rate  
And each metric is calculated from current recruitment data.

**Dependencies:** ATS-BL-001, ATS-BL-006, ATS-BL-010  
**Definition of Done:** Dashboard displays accurate MVP recruitment metrics.  
**Risks or considerations:** Some metrics may require simplified MVP definitions.

---

### ATS-BL-013: Filter Dashboard by Department and Date Range

**Epic:** Analytics  
**Feature or module:** Recruitment Dashboard  
**User story reference:** Recruitment KPI Dashboard  
**Priority:** Should Have  
**Business value:** Makes dashboard insights more actionable.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 5  

**Description:**  
Allow HR leaders to filter KPI dashboard data by department and date range.

**Acceptance criteria (BDD):**

Given the dashboard contains recruitment data across multiple departments  
When the HR leader selects a department and date range  
Then the system updates all dashboard metrics based on the selected filters.

**Dependencies:** ATS-BL-012  
**Definition of Done:** Dashboard filters update all metrics consistently.  
**Risks or considerations:** Department data must be available in job or requisition records.

---

### ATS-BL-014: Highlight Recruitment Bottlenecks

**Epic:** Analytics  
**Feature or module:** Recruitment Dashboard  
**User story reference:** Recruitment KPI Dashboard  
**Priority:** Could Have  
**Business value:** Helps HR leaders identify hiring process delays.  
**Estimated effort:** 5 story points  
**Suggested sprint or release phase:** Sprint 5 or later  

**Description:**  
Highlight hiring stages where candidates spend more time than expected.

**Acceptance criteria (BDD):**

Given one hiring stage has a higher-than-expected candidate delay  
When the dashboard loads  
Then the system highlights the stage as a potential bottleneck  
And displays the average time candidates spend in that stage.

**Dependencies:** ATS-BL-012, ATS-BL-013  
**Definition of Done:** Dashboard identifies delayed stages using defined threshold logic.  
**Risks or considerations:** Thresholds must be defined with HR stakeholders.

---

## 5. Dependency Map

```text
ATS-BL-001 Candidate Applications
    -> ATS-BL-002 Resume Parsing
        -> ATS-BL-003 Match Score
            -> ATS-BL-004 Ranked Candidate List
                -> ATS-BL-005 Score Filtering

ATS-BL-001 Candidate Applications
    -> ATS-BL-006 Current Application Status
        -> ATS-BL-007 Hiring Pipeline Stages
        -> ATS-BL-008 Status Change Notifications

ATS-BL-001 Candidate Applications
    -> ATS-BL-009 Available Interview Slots
        -> ATS-BL-010 Interview Event + Video Link
            -> ATS-BL-011 Candidate Local Time Zone

ATS-BL-001 Candidate Applications
ATS-BL-006 Application Status
ATS-BL-010 Interview Event
    -> ATS-BL-012 KPI Dashboard
        -> ATS-BL-013 Dashboard Filters
            -> ATS-BL-014 Bottleneck Highlighting
```

---

## 6. Suggested Sprint Plan

### Sprint 1: Data Foundation and Resume Parsing

- ATS-BL-001: Store candidate applications and resume metadata
- ATS-BL-002: Parse resume data for candidate matching

**Justification:** These items are foundational. Without candidate and resume data, AI ranking, candidate tracking, scheduling, and analytics cannot work.

### Sprint 2: AI Candidate Shortlisting

- ATS-BL-003: Generate candidate-job match score
- ATS-BL-004: Display ranked candidate list with score explanation
- ATS-BL-005: Filter candidates by minimum match score

**Justification:** Delivers the strongest recruiter-facing productivity improvement early in the MVP.

### Sprint 3: Candidate Status Transparency

- ATS-BL-006: Display current application status
- ATS-BL-007: Display hiring pipeline stages
- ATS-BL-008: Notify candidates when application status changes

**Justification:** Improves candidate experience and reduces recruiter communication overhead.

### Sprint 4: Interview Scheduling

- ATS-BL-009: Suggest available interview slots
- ATS-BL-010: Create interview event with video meeting link
- ATS-BL-011: Display interview time in candidate local time zone

**Justification:** Supports the next stage of the recruitment workflow after screening and status management.

### Sprint 5: Recruitment Analytics

- ATS-BL-012: Display core recruitment KPI dashboard
- ATS-BL-013: Filter dashboard by department and date range
- ATS-BL-014: Highlight recruitment bottlenecks

**Justification:** Analytics becomes more meaningful once application, status, and interview data already exist.

---

## 7. Out-of-Scope Items for MVP


| Item                                 | Reason                                                                 |
| ------------------------------------ | ---------------------------------------------------------------------- |
| Automatic candidate rejection        | Requires careful compliance and bias controls.                         |
| Multi-provider calendar support      | MVP can start with one provider.                                       |
| Advanced predictive hiring analytics | Requires more historical data.                                         |
| Full HRIS/payroll integration        | Belongs to later onboarding workflows.                                 |
| Digital offer management             | Not part of the previous user stories.                                 |
| Advanced diversity analytics         | Valuable, but not required for the first MVP based on current stories. |
| Candidate chatbot                    | Not included in the previous user stories.                             |
| Multi-language candidate portal      | Not required by current acceptance criteria.                           |


---

## 8. Assumptions

- The MVP supports one company tenant initially.
- A basic job and candidate application model already exists or is delivered as part of Sprint 1.
- Resume parsing may use a simple first version before advanced semantic AI is added.
- Calendar integration starts with one provider only.
- Video meeting generation can use the same provider as the calendar integration.
- Candidate notifications initially use email.
- KPI definitions for MVP are simplified and agreed with HR stakeholders.
- Recruiters remain responsible for final candidate decisions; AI ranking is advisory only.

# 3. GENERATE TICKETS

## PROMPT 04

You are a Prompt Engineer, create a prompt that generate the tickets for the previous backlog created, only the tickets for the user story "3. Smart Interview Scheduling"

## PROMPT 05

```markdown
You are a Product Manager, Business Analyst, Agile Product Owner, and Technical Delivery Lead with experience in ATS (Applicant Tracking System) products.

Based on the previous product backlog created, generate implementation-ready delivery tickets only for the user story:

## 3. Smart Interview Scheduling

User story:
"As a recruiter, I want to schedule interviews using calendar availability and automatic time-zone handling so that I can coordinate interviews faster and avoid scheduling errors."

Use only the backlog items related to this user story:

- ATS-BL-009: Suggest available interview slots
- ATS-BL-010: Create interview event with video meeting link
- ATS-BL-011: Display interview time in candidate local time zone

Do not generate tickets for AI screening, candidate status tracking, or recruitment KPI dashboard.

For each ticket, include:

- Ticket ID
- Ticket title
- Related backlog item ID
- Related user story
- Ticket type: Feature, Backend, Frontend, Integration, QA, UX, or Technical Enablement
- Description
- User value
- Priority
- Dependencies
- Acceptance criteria in BDD format using Given/When/Then
- Technical notes
- Data or API requirements
- Edge cases
- Definition of Done
- Estimated effort using story points
- Suggested sprint
- Testing considerations

Organize the output using the following structure:

1. Scope summary
2. Ticket list table
3. Detailed tickets
4. Ticket dependency order
5. Testing strategy
6. Assumptions
7. Out-of-scope items

Apply good ticket-writing practices:

- Tickets must be clear, small, testable, and implementation-ready.
- Each ticket must map to one of the Smart Interview Scheduling backlog items.
- Split large work into frontend, backend, integration, and QA tickets when useful.
- Prioritize/order tickets logically and add a short justification for the order.
- Do not duplicate tickets.
- Do not include unrelated ATS features.
- Include enough detail for a Scrum team to estimate and implement the work.
- Keep the MVP scope focused on one calendar provider and one video meeting provider unless otherwise stated.

Use Markdown format.
```

## TICKETS

## 1. Scope Summary

This ticket set covers only **User Story 3: Smart Interview Scheduling** for the ATS MVP.

The goal is to let recruiters schedule interviews by selecting a candidate and interviewers, viewing available time slots, confirming an interview, generating a video meeting link, sending calendar invitations, and showing the interview time in the candidate’s local time zone.

### Included Backlog Items


| Backlog ID | Scope                                               |
| ---------- | --------------------------------------------------- |
| ATS-BL-009 | Suggest available interview slots                   |
| ATS-BL-010 | Create interview event with video meeting link      |
| ATS-BL-011 | Display interview time in candidate local time zone |


### Prioritization Logic

Tickets are ordered by implementation dependency:

1. Configure interview data model and provider assumptions.
2. Integrate calendar availability.
3. Build backend slot suggestion.
4. Build recruiter scheduling UI.
5. Create event and video meeting.
6. Handle candidate time-zone display.
7. Add QA coverage.

---

## 2. Ticket List Table


| Order | Ticket ID   | Title                                          | Backlog Item                         | Type                 | Priority    | Story Points | Sprint   | Justification                                                                        |
| ----- | ----------- | ---------------------------------------------- | ------------------------------------ | -------------------- | ----------- | ------------ | -------- | ------------------------------------------------------------------------------------ |
| 1     | ATS-TKT-001 | Define interview scheduling data model         | ATS-BL-009 / ATS-BL-010 / ATS-BL-011 | Technical Enablement | Must Have   | 3            | Sprint 4 | Required foundation for storing interviews, attendees, times, links, and time zones. |
| 2     | ATS-TKT-002 | Integrate calendar availability provider       | ATS-BL-009                           | Integration          | Must Have   | 5            | Sprint 4 | Required before available slots can be suggested.                                    |
| 3     | ATS-TKT-003 | Build available slot suggestion API            | ATS-BL-009                           | Backend              | Must Have   | 5            | Sprint 4 | Core backend logic for finding common available times.                               |
| 4     | ATS-TKT-004 | Build recruiter interview scheduling UI        | ATS-BL-009                           | Frontend             | Must Have   | 5            | Sprint 4 | Allows recruiters to use suggested slots.                                            |
| 5     | ATS-TKT-005 | Create interview event with video meeting link | ATS-BL-010                           | Integration          | Must Have   | 5            | Sprint 4 | Completes the scheduling workflow.                                                   |
| 6     | ATS-TKT-006 | Send interview invitations to participants     | ATS-BL-010                           | Backend              | Must Have   | 3            | Sprint 4 | Ensures candidate and interviewers receive interview details.                        |
| 7     | ATS-TKT-007 | Display candidate local interview time         | ATS-BL-011                           | Frontend             | Should Have | 3            | Sprint 4 | Reduces scheduling confusion across time zones.                                      |
| 8     | ATS-TKT-008 | Add interview scheduling QA coverage           | ATS-BL-009 / ATS-BL-010 / ATS-BL-011 | QA                   | Must Have   | 3            | Sprint 4 | Validates the complete workflow before MVP release.                                  |


---

## 3. Detailed Tickets

### ATS-TKT-001: Define Interview Scheduling Data Model

**Related backlog item ID:** ATS-BL-009 / ATS-BL-010 / ATS-BL-011  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Technical Enablement  
**Priority:** Must Have  
**Estimated effort:** 3 story points  
**Suggested sprint:** Sprint 4  

### Description

Define the data structure required to support interview scheduling, including interview records, participants, scheduled time, duration, meeting URL, status, and time-zone fields.

### User Value

Provides the reliable foundation needed to store and retrieve scheduled interviews.

### Dependencies

None.

### Acceptance Criteria

**Scenario 1: Store interview scheduling data**

Given a recruiter schedules an interview  
When the interview is saved  
Then the system stores the candidate, job application, interviewers, scheduled time, duration, status, and meeting URL.

**Scenario 2: Store time-zone information**

Given the candidate has a known time zone  
When the interview is saved  
Then the system stores the candidate time zone  
And stores the scheduled interview time in a consistent system format.

### Technical Notes

- Store system time in UTC.
- Store candidate time zone using IANA format, for example `America/Chihuahua`.
- Interview status examples: `scheduled`, `cancelled`, `completed`.

### Data or API Requirements

Suggested interview fields:


| Field                  | Description                |
| ---------------------- | -------------------------- |
| `id`                   | Interview ID               |
| `application_id`       | Related application        |
| `candidate_id`         | Candidate                  |
| `interviewer_user_ids` | Interviewers               |
| `scheduled_at_utc`     | Interview date/time in UTC |
| `duration_minutes`     | Interview duration         |
| `candidate_timezone`   | Candidate local time zone  |
| `meeting_url`          | Video meeting link         |
| `status`               | Interview status           |


### Edge Cases

- Candidate time zone is missing.
- Interview has multiple interviewers.
- Meeting URL is not available at save time.

### Definition of Done

- Interview data structure is defined.
- Interview can store participants, schedule, meeting link, and time-zone values.
- Data validation rules are documented.
- Basic persistence tests pass.

### Testing Considerations

- Validate required fields.
- Validate UTC date storage.
- Validate missing optional meeting URL handling.

---

### ATS-TKT-002: Integrate Calendar Availability Provider

**Related backlog item ID:** ATS-BL-009  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Integration  
**Priority:** Must Have  
**Estimated effort:** 5 story points  
**Suggested sprint:** Sprint 4  

### Description

Integrate one calendar provider for MVP to retrieve recruiter and interviewer availability.

### User Value

Allows the system to suggest realistic interview slots instead of requiring manual coordination.

### Dependencies

- ATS-TKT-001

### Acceptance Criteria

**Scenario 1: Retrieve participant availability**

Given selected interviewers have connected calendars  
When the system requests availability  
Then the calendar provider returns busy and free time windows.

**Scenario 2: Handle unavailable calendar connection**

Given one selected interviewer has no connected calendar  
When the system requests availability  
Then the system returns a clear availability error  
And does not suggest invalid slots for that interviewer.

### Technical Notes

- MVP supports one calendar provider.
- Use calendar free/busy availability where available.
- Availability should be requested for a configurable date range.

### Data or API Requirements

Required API capability:

```text
GET /calendar/availability?participantIds=&dateFrom=&dateTo=&durationMinutes=
```

Expected response:

```json
{
  "participants": [
    {
      "userId": "123",
      "timezone": "America/Chihuahua",
      "busySlots": []
    }
  ]
}
```

### Edge Cases

- Calendar provider timeout.
- Expired calendar credentials.
- Participant has all-day busy events.
- Participant has no availability in selected date range.

### Definition of Done

- Calendar availability can be retrieved for selected participants.
- Provider errors are handled.
- Unavailable calendar connections are reported clearly.
- Integration tests cover success and failure responses.

### Testing Considerations

- Mock provider success response.
- Mock provider timeout.
- Mock missing calendar authorization.
- Verify busy slots are returned correctly.

---

### ATS-TKT-003: Build Available Slot Suggestion API

**Related backlog item ID:** ATS-BL-009  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Backend  
**Priority:** Must Have  
**Estimated effort:** 5 story points  
**Suggested sprint:** Sprint 4  

### Description

Create backend logic to calculate common available interview slots based on candidate, recruiter, and interviewer availability.

### User Value

Saves recruiter time by automatically identifying interview times that work for all selected participants.

### Dependencies

- ATS-TKT-001
- ATS-TKT-002

### Acceptance Criteria

**Scenario 1: Suggest available interview slots**

Given a recruiter selects a candidate and one or more interviewers  
And all selected users have connected calendars  
When the recruiter opens the interview scheduling tool  
Then the system suggests available time slots that work for all selected participants.

**Scenario 2: No common availability**

Given selected participants have no overlapping availability  
When the system calculates interview slots  
Then the system displays that no available slots were found.

### Technical Notes

- Suggested slots should respect interview duration.
- Suggested slots should exclude busy calendar periods.
- Suggested slots should be sorted by earliest available time.
- MVP can use default working hours if candidate availability is not connected.

### Data or API Requirements

Required endpoint:

```text
POST /interviews/suggest-slots
```

Example request:

```json
{
  "candidateId": "CAND-001",
  "interviewerUserIds": ["USR-101", "USR-102"],
  "dateFrom": "2026-06-01",
  "dateTo": "2026-06-07",
  "durationMinutes": 60
}
```

Example response:

```json
{
  "suggestedSlots": [
    {
      "startsAtUtc": "2026-06-02T16:00:00Z",
      "endsAtUtc": "2026-06-02T17:00:00Z"
    }
  ]
}
```

### Edge Cases

- Duration is longer than available windows.
- Date range is invalid.
- Interviewer list is empty.
- Candidate record does not exist.

### Definition of Done

- API returns common available slots.
- API returns clear empty-state response when no slots exist.
- Input validation is implemented.
- Unit tests cover slot calculation logic.

### Testing Considerations

- Test overlapping availability.
- Test no overlap.
- Test multiple interviewers.
- Test invalid date range.
- Test different interview durations.

---

### ATS-TKT-004: Build Recruiter Interview Scheduling UI

**Related backlog item ID:** ATS-BL-009  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Frontend  
**Priority:** Must Have  
**Estimated effort:** 5 story points  
**Suggested sprint:** Sprint 4  

### Description

Build the recruiter-facing scheduling interface where recruiters select interviewers, duration, date range, and an available slot.

### User Value

Gives recruiters a usable workflow for scheduling interviews quickly.

### Dependencies

- ATS-TKT-003

### Acceptance Criteria

**Scenario 1: Recruiter views suggested slots**

Given the recruiter selects a candidate and interviewers  
When suggested slots are available  
Then the UI displays the available slots in chronological order.

**Scenario 2: Recruiter selects a slot**

Given suggested slots are displayed  
When the recruiter selects one slot  
Then the selected slot is highlighted  
And the recruiter can continue to confirm the interview.

### Technical Notes

- UI should show loading, empty, and error states.
- Slot display should include date, time, duration, and participant availability.
- Recruiter should be able to change selected interviewers and refresh suggestions.

### Data or API Requirements

Consumes:

```text
POST /interviews/suggest-slots
```

### Edge Cases

- No slots returned.
- Slot suggestion API fails.
- Recruiter changes date range after slots load.
- Selected slot becomes unavailable before confirmation.

### Definition of Done

- Recruiter can request and view suggested slots.
- Recruiter can select a slot.
- UI handles loading, empty, and error states.
- Frontend tests cover main UI states.

### Testing Considerations

- Test slot list rendering.
- Test selected slot state.
- Test empty state.
- Test API error state.

---

### ATS-TKT-005: Create Interview Event With Video Meeting Link

**Related backlog item ID:** ATS-BL-010  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Integration  
**Priority:** Must Have  
**Estimated effort:** 5 story points  
**Suggested sprint:** Sprint 4  

### Description

Create the confirmed interview event in the calendar provider and generate a video meeting link.

### User Value

Completes the scheduling workflow and removes manual calendar/video setup for recruiters.

### Dependencies

- ATS-TKT-001
- ATS-TKT-002
- ATS-TKT-003
- ATS-TKT-004

### Acceptance Criteria

**Scenario 1: Create interview event**

Given the recruiter selects an available time slot  
When the recruiter confirms the interview  
Then the system creates the interview event  
And stores the scheduled interview details.

**Scenario 2: Add video meeting link**

Given the interview event is created  
When the calendar provider supports video meeting links  
Then the system adds a video meeting link to the interview event  
And stores the meeting URL.

### Technical Notes

- MVP uses one video meeting provider.
- Calendar event should include title, participants, time, duration, and meeting link.
- Store the provider event ID if available.

### Data or API Requirements

Required endpoint:

```text
POST /interviews
```

Example request:

```json
{
  "applicationId": "APP-001",
  "candidateId": "CAND-001",
  "interviewerUserIds": ["USR-101"],
  "startsAtUtc": "2026-06-02T16:00:00Z",
  "durationMinutes": 60
}
```

Example response:

```json
{
  "interviewId": "INT-001",
  "status": "scheduled",
  "meetingUrl": "https://video.example.com/interview/INT-001"
}
```

### Edge Cases

- Calendar provider fails after interview is saved.
- Video meeting link generation fails.
- Selected slot is no longer available.
- One participant invitation fails.

### Definition of Done

- Confirmed interview creates a calendar event.
- Video meeting link is generated and stored.
- Interview record is saved with scheduled status.
- Integration tests cover successful event creation and provider failure.

### Testing Considerations

- Test successful event creation.
- Test provider failure.
- Test missing meeting link.
- Test duplicate confirmation prevention.

---

### ATS-TKT-006: Send Interview Invitations to Participants

**Related backlog item ID:** ATS-BL-010  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Backend  
**Priority:** Must Have  
**Estimated effort:** 3 story points  
**Suggested sprint:** Sprint 4  

### Description

Send interview invitations to candidate and interviewers after the interview is confirmed.

### User Value

Ensures all participants receive interview details without manual recruiter communication.

### Dependencies

- ATS-TKT-005

### Acceptance Criteria

**Scenario 1: Send calendar invitations**

Given an interview is successfully created  
When the system finalizes the event  
Then the candidate and interviewers receive calendar invitations.

**Scenario 2: Include interview details**

Given invitations are sent  
When participants open the invitation  
Then the invitation includes interview date, time, duration, participants, and video meeting link.

### Technical Notes

- Invitations may be sent through the calendar provider.
- Email notification can be used as fallback if calendar invitation delivery is not available.
- Invitation content should include candidate-local time where possible.

### Data or API Requirements

Uses interview event data from:

```text
POST /interviews
```

### Edge Cases

- Candidate email is missing.
- Interviewer email is missing.
- Calendar provider sends partial failures.
- Meeting URL is missing.

### Definition of Done

- Invitations are sent to all valid participants.
- Invitation content includes required details.
- Failed invitation delivery is logged or surfaced.
- Tests cover full and partial invitation scenarios.

### Testing Considerations

- Test candidate invitation.
- Test interviewer invitation.
- Test missing participant email.
- Test invitation provider failure.

---

### ATS-TKT-007: Display Candidate Local Interview Time

**Related backlog item ID:** ATS-BL-011  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** Frontend  
**Priority:** Should Have  
**Estimated effort:** 3 story points  
**Suggested sprint:** Sprint 4  

### Description

Display interview time in the candidate’s local time zone in candidate-facing interview details and invitations where applicable.

### User Value

Prevents confusion and missed interviews caused by time-zone differences.

### Dependencies

- ATS-TKT-001
- ATS-TKT-005
- ATS-TKT-006

### Acceptance Criteria

**Scenario 1: Display candidate local time**

Given the candidate is in a different time zone than the recruiter  
When the interview invitation is generated  
Then the system displays the interview time in the candidate's local time zone  
And stores the interview time consistently in the system.

**Scenario 2: Candidate time zone is missing**

Given the candidate time zone is unknown  
When interview details are displayed  
Then the system displays the interview time with a clear time-zone label  
And does not display an incorrect local time.

### Technical Notes

- Store `scheduled_at_utc`.
- Convert display time using candidate time zone.
- Use explicit time-zone labels in UI and notifications.

### Data or API Requirements

Required fields:

```json
{
  "scheduledAtUtc": "2026-06-02T16:00:00Z",
  "candidateTimezone": "America/Chihuahua",
  "displayTime": "2026-06-02 10:00 AM America/Chihuahua"
}
```

### Edge Cases

- Candidate time zone is missing.
- Candidate time zone is invalid.
- Daylight saving time changes.
- Recruiter and candidate are in the same time zone.

### Definition of Done

- Candidate-facing time is displayed in local time when available.
- UTC time remains the stored source of truth.
- Missing or invalid time-zone cases are handled safely.
- Tests cover time-zone conversion.

### Testing Considerations

- Test different recruiter and candidate time zones.
- Test same time zone.
- Test missing candidate time zone.
- Test daylight saving boundary.

---

### ATS-TKT-008: Add Interview Scheduling QA Coverage

**Related backlog item ID:** ATS-BL-009 / ATS-BL-010 / ATS-BL-011  
**Related user story:** 3. Smart Interview Scheduling  
**Ticket type:** QA  
**Priority:** Must Have  
**Estimated effort:** 3 story points  
**Suggested sprint:** Sprint 4  

### Description

Create and execute QA test coverage for the complete Smart Interview Scheduling workflow.

### User Value

Ensures recruiters can reliably schedule interviews and candidates receive correct interview information.

### Dependencies

- ATS-TKT-003
- ATS-TKT-004
- ATS-TKT-005
- ATS-TKT-006
- ATS-TKT-007

### Acceptance Criteria

**Scenario 1: Complete scheduling workflow**

Given a recruiter selects a candidate and interviewers  
When the recruiter selects a suggested slot and confirms the interview  
Then the interview is created  
And a video meeting link is generated  
And invitations are sent to all participants.

**Scenario 2: Time-zone validation**

Given the candidate is in a different time zone  
When the interview is created  
Then the candidate-facing time is displayed in the candidate’s local time zone.

**Scenario 3: Provider failure handling**

Given the calendar provider is unavailable  
When the recruiter attempts to schedule an interview  
Then the system displays a clear error  
And does not create an incomplete interview without warning.

### Technical Notes

- Include happy path, empty state, and failure path tests.
- Include API and UI-level test cases.

### Data or API Requirements

Test coverage should include:

- `POST /interviews/suggest-slots`
- `POST /interviews`
- Calendar provider mock
- Video meeting provider mock

### Edge Cases

- No available slots.
- Expired calendar credentials.
- Missing candidate email.
- Missing candidate time zone.
- Video meeting link generation failure.

### Definition of Done

- QA test cases are documented.
- Critical test cases pass.
- Defects are logged with severity.
- MVP scheduling workflow is verified end-to-end.

### Testing Considerations

- Manual exploratory testing for recruiter workflow.
- Automated API tests for slot suggestion and interview creation.
- Mocked integration tests for calendar and video provider failures.

---

## 4. Ticket Dependency Order

```text
1. ATS-TKT-001 Define interview scheduling data model
   -> 2. ATS-TKT-002 Integrate calendar availability provider
      -> 3. ATS-TKT-003 Build available slot suggestion API
         -> 4. ATS-TKT-004 Build recruiter interview scheduling UI
            -> 5. ATS-TKT-005 Create interview event with video meeting link
               -> 6. ATS-TKT-006 Send interview invitations to participants
                  -> 7. ATS-TKT-007 Display candidate local interview time
                     -> 8. ATS-TKT-008 Add interview scheduling QA coverage
```

### Order Justification

The data model must come first because all scheduling records depend on it. Calendar integration and slot suggestion are needed before the recruiter UI can display real options. Event creation and invitations complete the workflow. Time-zone display depends on stored interview time and candidate time-zone data. QA comes last after the workflow is testable end-to-end.

---

## 5. Testing Strategy

### Unit Testing

- Slot calculation logic
- Date range validation
- Time-zone conversion
- Interview data validation

### Integration Testing

- Calendar availability provider mock
- Video meeting link generation mock
- Calendar invitation delivery
- Provider timeout and error handling

### Frontend Testing

- Suggested slot rendering
- Loading, empty, and error states
- Slot selection behavior
- Confirmation flow
- Candidate local time display

### End-to-End Testing

Primary E2E scenario:

Given a recruiter selects a candidate and interviewers  
When the recruiter chooses a suggested slot and confirms the interview  
Then the interview is created with a video meeting link  
And invitations are sent  
And the candidate sees the correct local interview time.

---

## 6. Assumptions

- MVP supports one calendar provider.
- MVP supports one video meeting provider.
- Calendar availability is available for recruiters and interviewers.
- Candidate availability may not be connected in MVP.
- Candidate time zone is captured from profile, application, browser setting, or recruiter input.
- Interview time is stored in UTC.
- Candidate and interviewer emails are available.
- Recruiter authentication and candidate/application records already exist from previous MVP work.

---

## 7. Out-of-Scope Items


| Item                               | Reason                                                |
| ---------------------------------- | ----------------------------------------------------- |
| Multi-calendar provider support    | MVP is limited to one provider.                       |
| Candidate self-scheduling          | Not included in the Smart Interview Scheduling story. |
| Interview rescheduling workflow    | Not part of the current acceptance criteria.          |
| Interview cancellation workflow    | Not part of the current acceptance criteria.          |
| Automated reminders                | Related, but not included in this backlog scope.      |
| Interview feedback forms           | Related to evaluation, not scheduling.                |
| Panel interview optimization rules | Too advanced for MVP.                                 |
| AI scheduling assistant            | Future enhancement beyond current backlog.            |


# 4. ESTIMATE EFFORT FOR THE TICKETS

## PROMPT 06

You are a Prompt Engineer, create a prompt for estimate the effort of the previous tickets for the user story "3. Smart Interview Scheduling", give me the best two options of the techniques like Montecarlo to calculate the effort with the pros and cons to pick one

## PROMPT 07

```markdown
You are an Agile Estimation Facilitator, Product Manager, Business Analyst, and Technical Delivery Lead with experience estimating software delivery work for ATS (Applicant Tracking System) products.

Based on the previous implementation-ready tickets for the user story:

## 3. Smart Interview Scheduling

Estimate the delivery effort for the following tickets:

- ATS-TKT-001: Define interview scheduling data model
- ATS-TKT-002: Integrate calendar availability provider
- ATS-TKT-003: Build available slot suggestion API
- ATS-TKT-004: Build recruiter interview scheduling UI
- ATS-TKT-005: Create interview event with video meeting link
- ATS-TKT-006: Send interview invitations to participants
- ATS-TKT-007: Display candidate local interview time
- ATS-TKT-008: Add interview scheduling QA coverage

Before estimating, recommend the best two effort estimation techniques for this context. One of the options must be Monte Carlo simulation.

For each technique, include:

- Technique name
- Short explanation
- Why it fits this Smart Interview Scheduling work
- Required inputs
- Pros
- Cons
- When to use it
- Risks or limitations
- Recommendation score from 1 to 5

Then compare both techniques and recommend which one should be used for this estimation, with a clear justification.

After selecting the technique, estimate the effort for each ticket and the full user story.

For each ticket, include:

- Ticket ID
- Ticket title
- Related backlog item
- Complexity level: Low, Medium, High
- Uncertainty level: Low, Medium, High
- Estimated effort in story points
- Estimated effort range: optimistic, most likely, pessimistic
- Main estimation drivers
- Assumptions
- Risks
- Confidence level
- Estimation notes

Organize the output using this structure:

1. Estimation context
2. Recommended estimation techniques
3. Technique comparison table
4. Selected estimation technique and justification
5. Ticket-level estimates
6. Total effort estimate
7. Confidence and risk analysis
8. Recommendations for backlog refinement
9. Final conclusion

Apply good Agile estimation practices:

- Keep estimates relative, not exact time commitments.
- Use story points as the primary unit.
- Use ranges when uncertainty is high.
- Consider technical complexity, integration risk, testing effort, unknowns, and dependencies.
- Clearly separate assumptions from facts.
- Do not estimate unrelated tickets.
- Do not include tickets outside the Smart Interview Scheduling user story.
- If using Monte Carlo, explain the needed historical throughput or cycle-time data and how the simulation would be interpreted.
- If there is not enough historical data for Monte Carlo, state how the team can approximate the model or why another method may be better for the first estimate.

Use Markdown format.
```

## PROMPT 08

The technique chosen for the effor estimation is going to be the "Option 1: Planning Poker with Fibonacci Story Points"

## ESTIMATIONS

## Planning Poker Estimates

Technique selected: **Planning Poker with Fibonacci Story Points**


| Ticket ID   | Ticket title                                   | Estimate | Complexity | Uncertainty | Justification                                                                              |
| ----------- | ---------------------------------------------- | -------- | ---------- | ----------- | ------------------------------------------------------------------------------------------ |
| ATS-TKT-001 | Define interview scheduling data model         | 3        | Low        | Low         | Small foundational work with clear fields and relationships.                               |
| ATS-TKT-002 | Integrate calendar availability provider       | 8        | High       | High        | External integration, provider permissions, free/busy API, and error handling add risk.    |
| ATS-TKT-003 | Build available slot suggestion API            | 8        | High       | Medium      | Requires overlap logic, duration rules, participant availability, and edge-case handling.  |
| ATS-TKT-004 | Build recruiter interview scheduling UI        | 5        | Medium     | Medium      | Needs slot display, participant selection, loading/error states, and confirmation flow.    |
| ATS-TKT-005 | Create interview event with video meeting link | 8        | High       | High        | Calendar event creation plus video link generation introduces integration and retry risks. |
| ATS-TKT-006 | Send interview invitations to participants     | 5        | Medium     | Medium      | Invitation delivery and partial failure handling add moderate complexity.                  |
| ATS-TKT-007 | Display candidate local interview time         | 3        | Medium     | Medium      | Manageable if UTC storage and time-zone library support already exist.                     |
| ATS-TKT-008 | Add interview scheduling QA coverage           | 5        | Medium     | Medium      | Requires end-to-end, integration, provider failure, and time-zone test coverage.           |


## Total Estimate


| Estimate type               | Story points |
| --------------------------- | ------------ |
| Total selected estimate     | 45           |
| Recommended planning buffer | 55-60        |
| Pessimistic range           | 73           |


## Delivery Note

The most likely estimate is **45 story points**. Because the highest-risk tickets are the calendar provider integration and video meeting event creation, I would plan this as more than one sprint unless the team already has calendar/video integration infrastructure available.