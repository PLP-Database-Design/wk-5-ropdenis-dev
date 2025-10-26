# 🧪 Final Group Test Report Template — Word Puzzle Game Plus

**Level:** Intermediate QA | **Week 5:** Test Management

**Course:** Software Testing & Quality Assurance  
**Module:** Test Management (Week 5)  
**Project Type:** Group Assessment  
**Submission Date:** 2025-10-28

## Team Information

| Role | Name | Responsibilities |
|------|------|------------------|
| Test Manager | Brian Mbaka| Planning, scheduling, coordination, metric tracking |
| Risk Analyst |Denis kiptum | Risk identification, prioritization, test design linkage |
| Test Executor |Wilson  | Execution, evidence capture, defect logging |

## Group Rules

- Each student must belong to only one group.
- Duplicate membership or multiple submissions will result in invalidation.
- Every group member must contribute towards this project

## Project Overview

**System Under Test:** Word Puzzle Game Plus  
**Technology Stack:** HTML, CSS, JavaScript  
**Environment:** Chrome Browser (Desktop)

### Features Under Test

| Feature | Description | Risk Category |
|---------|-------------|---------------|
| Reset Game | Clears score and progress instantly |Functional |
| Leaderboard | Stores top 3 scores in localStorage |Data Integrity|
| Bonus Round | Every 3 puzzles → doubles score |Logic |

## Test Plan

### Objectives

- Verify correctness and stability of new features: Reset Game, Leaderboard (top‑3 persistence), Bonus Round (every 3 puzzles → score ×2).

- Ensure data integrity across sessions (localStorage) and correct score calculation.

- Identify high‑risk defects early and maintain traceability via GitHub Issues.

### Scope

**In Scope:**
- Functional testing of gameplay that is : guess, hint, bonus, reset, leaderboard.
- Risk-based validation for scoring, bonus, and persistence logic.
- UI usability for clarity of bonus and hint feedback.

**Out of Scope:**
- Mobile layout testing beyond basic responsiveness.
- Server-level load testing.

### Tools & Resources

- People: Test Manager, Risk Analyst, Test Executor
- Tools: Chrome , Chrome DevTools GitHub (Issues + Project board), a screen capture tool, Google Sheets for metrics.

### Schedule

| Phase | Planned Duration | Actual Duration | Status |
|-------|------------------|-----------------|--------|
| Planning & Risk Identification| 3 Days |2 Days |Completed|
| Test Case Design & Environment Setup| 2 Days | 1 Day|Completed |
| Test Execution & Defect Logging|4 Hours | 3 Hours|Completed|
| Regression, metrics & report submission|10 Hours| 5 Hours |Completed |
## Risk Analysis

### Risks

| ID | Feature | Risk Description | Likelihood | Impact | Priority | Mitigation Strategy |
|----|---------|------------------|------------|--------|----------|---------------------|
|R-01 | Leaderboard| Leaderboard fails to persist after refresh or browser close| 1| 3| High| Use localStorage for persistence; add automated test to verify leaderboard remains intact after refresh or reopen.|
|R-02 | Bonus |Bonus score miscalculation | 2| 3| High| Create risk‑based tests around sequences (e.g., solve 3 puzzles with/without hints) to confirm exact doubling semantics; add unit tests for scoring function.|
|R-03 |Hint system |Hint logic mismatch — incorrect deduction : wrong reduced score, Hint button active before puzzle load (causing confusion)|2 | 3| High| Add tests covering hint flow: verify deduction, award value, and ensure Hint is disabled until puzzle is active.|
|R-04 |Reset Function |Bonus counter not resetting after Reset Game | 1 | 2 |Low| Verify Reset to clear the 'Solved' count and Bonus at counter; add test asserting Bonus at: 3 after reset.|
|R-05 |Leadrerboard | Incorrect sorting or tie handling in leaderboard display| 1| 2 | medium |Boundary tests for leaderboard with large integers and ties; ensure numeric sort, stable tie-break (timestamp). |
|R-06 |User Interface |LocalStorage corruption causing missing or broken leaderboard| 1 | 3 |Low | Read-with-validate: wrap localStorage reads in try/catch, validate data structure and types before rendering includes tests that inject malformed entries.|

### Risk Coverage

- Tested Risks Percent:
(5 / 6) × 100 = 83%
 
 validated : (2/ 6) × 100 = 33%
 
 monitored : (3/ 6) × 100 = 50%
- Untested Risks Percent:
  
  Open : (1 / 6) × 100 = 17%


   PIE CHART

Validated 

████████░░░░░░░░░░░░░░░░░░ 33%

Monitored (Low Impact) 

█████████████████░░░░░░░░░ 50%

Needs Fix   
    ██████░░░░░░░░░░░░░░░░░░░ 17%


## Test Cases

| ID | Feature | Objective | Expected Result | Actual Result | Status | Risk Link |
|----|---------|-----------|----------------|---------------|--------|-----------|
|TC-01 | Leaderboard Persistence|Verify leaderboard remains intact after page refresh or browser reopen | Top 3 scores persist correctly| Works as expected| Passed| R-01|
|TC-02 |Bonus Logic |Confirm bonus (×2) applies after every 3 solved puzzles | Score doubles exactly at 3rd puzzle solved| Works correctly|passed |R-02 |
|TC-03 |Hint system |Verify hint deduction, reduced award and correct behavior when no puzzle is active.|Hint button remains inactive or triggers “Please start a New puzzle” message before a word is displayed|Hint button displays hint meaning with no puzzle shown (confusing)|Fail|R-03 |
|TC-04 |Reset Function | Verify Reset clears score and “Bonus at” counter|“Score: 0”, “Solved: 0”, “Bonus at: 3” displayed after reset |works correctly |passed |R-04 |
|TC-05 |Negative Test — Leaderboard Sorting|Validate sorting order and tie handling |Scores displayed in descending order; ties stable | Works correctly | Passed|R-05|
|TC-06 | LocalStorage Corruption| Test how system handles malformed leaderboard data|On load, the system detects invalid data, clears leaderboard, and continues without crashing|works as Expected |Passes | R-06|
|TC-07 |Usability Test - UI Responsiveness |Ensure layout adapts properly to small screen sizes |UI scales without breaking |Works as expected | passed| - |
|TC-08 |Negative Test — Invalid Input handling |Enter blank or special characters as guess | Display validation message and do not advance puzzle or award points| works correctly| passed| - |

## Defects

| ID | Issue Title | Severity | Risk ID | Status | GitHub Link |
|----|-------------|----------|---------|--------|-------------|
|D-01 |Hint button active before New Puzzle| High | R-03| Open |https://github.com/PLP-Database-Design/wk-5-ropdenis-dev/issues/3|
|D-02 | Hint deduction not reflected immediately|medium |R-03 |Open | https://github.com/PLP-Database-Design/wk-5-ropdenis-dev/issues/4|
|D-03 | Bonus not doubling consistently on 3rd correct answer|Medium |R-02| Closed – Expected Behavior| https://github.com/PLP-Database-Design/wk-5-ropdenis-dev/issues/5|
|D-04 | Leaderboard  persistance of the top-3 after closing tab| Low | R-01|closed-Works as Expected |https://github.com/PLP-Database-Design/wk-5-ropdenis-dev/issues/6|

## Metrics

| Metric | Formula | solution  |
|----|-------------|----------|
|Test Case Pass Percent | (Passed / Total) × 100| 7/ 8 × 100 = 87% |
|Defect Density |Defects / Test Cases |(4/8) × 100 = 0.5 |  
|Risk Coverage Percent |(Tested Risks / Total Risks) × 100 | 5 / 6 × 100 ≈ 83%| 
|Regression Success Rate | (Passed Regression / Total Regression) × 100| 8 / 8 × 100 = 100%| 

### Defect Summary

- Total Defects Logged:4
- Critical High : 1 (D-01)
- Fix Rate: (4/4) × 100 = 100%

## Test Control & Project Management

### Phases

| Phase | Deliverable | Actual Output | Variance | Owner |
|-------|-------------|---------------|----------|-------|
|Planning & Risk Identification|Test Plan & Risk Analysis | Completed test plan and 6 risks identified| none| Test Manager & Risk Analyst|
|Test Case Design & Environment Setup| Test Case Design & Environment Setup|8 test cases prepared; environment :Chrome, localStorage ready |none | Test Executor & Risk Analyst|
|Test Execution & Defect Logging |Execute Test Cases & Log Defects |4 defects executed (D-01, D-02,Closed D-03 and D-04)|Minor delay for hint usability verification | Test Executor|
|Regression, metrics & report submission| Metrics tables, Risk Coverage, Reflection|Completed metrics & report draft |Minor adjustments needed for TC-03 usability addition | Test Manager & Risk Analyst|

**Progress Tracking Method:**  
- Daily check-ins on GitHub Issues.
- Test case execution tracked in the Test Cases table (Pass/Fail).
- Metrics updated after each test cycle (Defect Density, Risk Coverage, Pass Rate).

**Change Control Notes:**
- Risk R-03 updated to include Hint button usability issues.
- TC-03 added to cover Hint button usability defect.
- D-03 removed as actual behavior matched expected.

## Lessons Learned

- Most Defect Prone Feature: Hint System (multiple issues with deduction timing and button usability).
- Risk Analysis Impact: Risk-based testing helped prioritize Hint and Bonus flows first, preventing major scoring errors.
- Team Communication Effectiveness: Daily GitHub updates and Slack messages improved coordination; minor delays occurred due to clarifying bonus rules.
- Improvements for Next Cycle: 
. Include usability test scenarios earlier.
. Automate leaderboard persistence and bonus calculations verification.
. Improve clarity of scoring rules in test documentation.

## Attachments

- 

## Sign Off

| Name | Role | Initials | Date |
|------|------|-----------|------|
|Brian Mbaka | Test Manager |Bm |26 Oct 2025 |
|Denis KIptum | Risk Analyst |DK |26 Oct 2025 |
|Wilson | Test Executor |W |26 Oct 2025 |

## Overall Summary

**Statement:** 
- All planned tests for Word Puzzle Game Plus have been executed, defects were logged with linked risks, and key features like Bonus, Hint, and Leaderboard were fully verified.
**Test Status:** ☑ Completed / ☐ In Progress / ☐ Deferred
