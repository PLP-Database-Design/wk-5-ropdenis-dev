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
| Planning & Risk Identification| 1 Day|1 Day |Completed|
| Test Case Design & Environment Setup| 2 Days | 1 Day|Completed |
| Test Execution & Defect Logging|2 Days | - | in progress|
| Regression, metrics & report submission|2 Days | - | pending |
## Risk Analysis

### Risks

| ID | Feature | Risk Description | Likelihood | Impact | Priority | Mitigation Strategy |
|----|---------|------------------|------------|--------|----------|---------------------|
|R-01 | Leaderboard| Leaderboard fails to persist after refresh or browser close| 1| 3| High| Use localStorage for persistence; add automated test to verify leaderboard remains intact after refresh or reopen.|
|R-02 | Bonus |Bonus score miscalculation | 2| 3| High| Create risk‑based tests around sequences (e.g., solve 3 puzzles with/without hints) to confirm exact doubling semantics; add unit tests for scoring function.|
|R-03 |Hint system |Hint award mismatch — incorrect deduction or wrong reduced score applied|2 | 3| High| Add tests covering hint flow: check immediate deduction, final award value, and interactions with bonus rounds.|
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
|TC-03 |Hint system | Check hint deducts 2 points and reduced reward applies|Score immediately -2 on hint use, final award +5 | Works as expected| passed|R-03 |
|TC-04 |Reset Function | Verify Reset clears score and “Bonus at” counter|“Score: 0”, “Solved: 0”, “Bonus at: 3” displayed after reset |works correctly |passed |R-04 |
|TC-05 |Negative Test — Leaderboard Sorting|Validate sorting order and tie handling |Scores displayed in descending order; ties stable | Works correctly | Passed|R-05|
|TC-06 | LocalStorage Corruption| Test how system handles malformed leaderboard data|On load, the system detects invalid data, clears leaderboard, and continues without crashing| Not executed — requires manual injection of corrupted localStorage entries |Skipped | R-06|
|TC-07 |Usability Test - UI Responsiveness |Ensure layout adapts properly to small screen sizes |UI scales without breaking |Works as expected | passed| - |
|TC-08 |Negative Test — Invalid Input handling |Enter blank or special characters as guess | Display validation message and do not advance puzzle or award points| works correctly| passed| - |

## Defects

| ID | Issue Title | Severity | Risk ID | Status | GitHub Link |
|----|-------------|----------|---------|--------|-------------|
|D-01 |Bonus applied twice when using hint during bonus round | High | R-02| Fixed| |
|D-02 | Hint deduction not reflected immediately|medium |R-03 |Fixed | |
|D-03 |Leaderboard fails numeric sorting for tied scores |Medium |R-05 | Fixed| |

## Metrics

- Test Case Pass Percent: (7/8) × 100 = 88%
- Defect Density: (3/8) × 100 = 0.38
- Risk Coverage Percent: (5/6) × 100 = 83%
- Regression Success Rate: (3/3) × 100 = 100%

### Defect Summary

- Total Defects Logged:3 
- Critical High: 1 (D-01)
- Fix Rate: (3/3) × 100 = 100%

## Test Control & Project Management

### Phases

| Phase | Deliverable | Actual Output | Variance | Owner |
|-------|-------------|---------------|----------|-------|
| | | | | |

**Progress Tracking Method:**  
**Change Control Notes:**

## Lessons Learned

- Most Defect Prone Feature: 
- Risk Analysis Impact: 
- Team Communication Effectiveness: 
- Improvements for Next Cycle: 

## Attachments

- 

## Sign Off

| Name | Role | Initials | Date |
|------|------|-----------|------|
| | Test Manager | | |
| | Risk Analyst | | |
| | Test Executor | | |

## Overall Summary

**Statement:** 

**Test Status:** ☐ Completed / ☐ In Progress / ☐ Deferred
