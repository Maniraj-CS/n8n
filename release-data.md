# Software Release Data

## Resource 1: Release Overview

* **Product:** NextWave CRM
* **Release Version:** 2.5
* **Planned Release Date:** 18-Sep-2026
* **Release Type:** Feature and Maintenance Release
* **Release Owner:** Development Team
* **QA Owner:** QA Team
* **Deployment Owner:** DevOps Team
* **Target Environment:** Production
* **Previous Version:** 2.4
* **Release Status:** Under Review
* **Main Goal:** Introduce new customer management features, improve reporting, and resolve bugs.

---

# Resource 2: Changes

| ID    | Type    | Area                | Change                 | Status    | Description                                             |
| ----- | ------- | ------------------- | ---------------------- | --------- | ------------------------------------------------------- |
| CH001 | Feature | Customer Management | Customer Tagging       | Completed | Add custom tags to customer profiles.                   |
| CH002 | Feature | Dashboard           | Sales Dashboard Filter | Completed | Filter dashboard data by date, salesperson, and region. |
| CH003 | Feature | Notifications       | Follow-up Reminder     | Completed | Add reminders for customer follow-up.                   |
| CH004 | Feature | Reports             | PDF Report Export      | Completed | Export reports as PDF.                                  |
| CH005 | Feature | User Management     | Role Permission Update | Completed | Add detailed user permissions.                          |
| CH006 | Bug Fix | Login               | Session Timeout Fix    | Completed | Fix login session timeout behavior.                     |
| CH007 | Bug Fix | Customer Search     | Search Result Fix      | Completed | Fix customer search result issues.                      |
| CH008 | Bug Fix | Dashboard           | Total Calculation Fix  | Completed | Fix incorrect dashboard total calculations.             |
| CH009 | Bug Fix | Email               | Email Formatting Fix   | Completed | Fix email formatting issues.                            |
| CH010 | Bug Fix | Mobile              | Mobile Menu Fix        | Completed | Fix mobile menu behavior.                               |
| CH011 | Bug Fix | Reports             | Date Filter Fix        | Completed | Fix report date filtering.                              |
| CH012 | Bug Fix | Notifications       | Duplicate Reminder Fix | Completed | Fix duplicate follow-up reminders.                      |

---

# Resource 3: QA Test Evidence

| Test ID | Area                | Test Case                   | Result | Priority | Notes                                         |
| ------- | ------------------- | --------------------------- | ------ | -------- | --------------------------------------------- |
| T001    | Customer Management | Create/assign tags          | Passed | High     | Works as expected.                            |
| T002    | Customer Management | Remove tags                 | Passed | Medium   | No issue.                                     |
| T003    | Dashboard           | Filter by date              | Passed | High     | Works as expected.                            |
| T004    | Dashboard           | Filter by salesperson       | Passed | High     | Works as expected.                            |
| T005    | Dashboard           | Filter by region            | Passed | Medium   | Works as expected.                            |
| T006    | Notifications       | Generate reminder           | Passed | High     | Works as expected.                            |
| T007    | Notifications       | Prevent duplicate reminders | Passed | High     | Works as expected.                            |
| T008    | Reports             | Export report PDF           | Passed | High     | Works as expected.                            |
| T009    | Reports             | Export large report PDF     | Passed | Medium   | Passed when exporting more than 1,000 records. |
| T010    | User Management     | Assign permissions          | Passed | High     | Works as expected.                            |
| T011    | Login               | Normal session timeout      | Passed | High     | Works as expected.                            |
| T012    | Customer Search     | Partial customer name       | Passed | Medium   | Works as expected.                            |
| T013    | Dashboard           | Monthly totals              | Passed | High     | Works as expected.                            |
| T014    | Email               | Formatting                  | Passed | Medium   | Works as expected.                            |
| T015    | Mobile              | Navigation                  | Passed | Medium   | Works as expected.                            |
| T016    | Reports             | Date filtering              | Passed | High     | Works as expected.                            |
| T017    | Regression          | Existing customer creation  | Passed | High     | Works as expected.                            |
| T018    | Regression          | Existing sales opportunity  | Passed | High     | Works as expected.                            |
| T019    | Regression          | Existing reporting          | Passed | High     | Works as expected.                            |
| T020    | Security            | Role-based access           | Passed | High     | Works as expected.                            |

---

---

# Resource 5: Release Rules

## RELEASE RECOMMENDATION

The recommendation must be exactly one of:

`Ready`

`Conditional`

`Not Ready`

Determine the recommendation using the Release Rules provided in the current input.

### STEP 1 — CHECK NOT READY

First, check all explicit Not Ready rules.

If ANY unresolved defect has `Critical` severity, the recommendation MUST be:

`Not Ready`

This rule comes before all Conditional and Ready rules.

For an unresolved Critical defect:

* Do not return `Conditional`.
* Do not wait for risk acceptance.
* Do not use risk acceptance as an exception.
* Do not use a workaround as an exception.
* Do not use pending human review as an exception.
* The defect must be resolved before the release can proceed.

Therefore:

`Critical + unresolved` = `Not Ready`

If the provided Release Rules identify another issue as explicitly blocking release, apply that rule and return `Not Ready`.

### STEP 2 — CHECK CONDITIONAL

Only perform this step if NO Not Ready rule applies.

Return `Conditional` only when:

* the Release Rules allow the release to proceed conditionally, AND
* a required action, confirmation, investigation, approval, or risk acceptance is still incomplete.

For example, if a Medium defect requires confirmed risk acceptance and that confirmation is not present, the release may be `Conditional` if the Release Rules allow it.

Do not use Conditional when an explicit Not Ready rule applies.

### STEP 3 — CHECK READY

Only perform this step if:

* no Not Ready rule applies, AND
* no incomplete Conditional requirement applies.

Return `Ready` only when all applicable Ready requirements are satisfied.

### DECISION ORDER

Always evaluate in this exact order:

1. Explicit Not Ready rule
2. Conditional rule
3. Ready rule

Never evaluate Conditional before checking Not Ready.

### IMPORTANT

The Release Rules are authoritative.

Do not invent a blocking condition.

However, when the provided Release Rules explicitly state that an unresolved Critical defect must block release, that rule MUST be followed.

For example:

Input:
`BUG204 = Critical + Open`

Release Rule:
`Critical unresolved defect → release should not proceed until resolved`

Required output:

`"recommendation": "Not Ready"`

Do NOT produce:

`"recommendation": "Conditional"`

even if risk acceptance is pending.

---

## QA Failure Rules

### Critical Test Failure

* Release should be **Not Ready**.

### High-Priority Test Failure

* Investigation is required before approval.

### Medium-Priority Test Failure

* Assess business impact and workaround.

### Low-Priority Test Failure

* Document the failure and assess acceptability.

### Regression Failure

* Requires careful review.

### Security Failure

* Release should not proceed until the failure is reviewed/resolved.

---

## General Rules

* AI can assess the release but cannot approve production.
* The Technical Lead makes the final production decision.
* Any unresolved Critical or High defect must be clearly highlighted.
* Medium defects must include business impact and workaround information.
* Accepted known issues must be included in the final report.
* Failed tests must not be hidden or minimized just because most tests passed.
* Incomplete, conflicting, or uncertain information must be identified and sent for human review.
* A workaround does not automatically mean that a risk has been accepted.
* Risk acceptance must only be considered confirmed when the input explicitly states that it is confirmed.
* If required risk acceptance is not confirmed, it must be identified as pending human review.

---

# Current Release Notes

## Known Issues

### BUG201

* **Severity:** Medium
* **Status:** Open
* **Related QA Test:** T009
* **Issue:** Large PDF exports fail above 1,000 records.
* **Workaround:** Filter reports into smaller date ranges.
* **Risk Acceptance:** Not explicitly confirmed.

### BUG202

* **Severity:** Medium
* **Status:** Open
* **Issue:** Notifications may be delayed during high activity.
* **Workaround:** Refresh the notification page.
* **Risk Acceptance:** Not explicitly confirmed.

### BUG203

* **Severity:** Low
* **Status:** Open
* **Issue:** Long customer names wrap incorrectly on small screens.
* **Workaround:** No workaround required.
* **Risk Acceptance:** Not explicitly required/confirmed.

---
### Critical Defect Rule

If any unresolved defect has Critical severity, the release is Not Ready.

A Critical unresolved defect must be resolved before the release can proceed.

Risk acceptance, a workaround, or pending human review does not allow the release to proceed while the Critical defect remains unresolved.

---

# Release Decision Authority

* **AI System:** Provides release-readiness assessment.
* **Technical Lead:** Makes the final production decision.
* **AI must not claim production approval.**
