# Project charter: Realtime Quiz platform

| Field    | Value                              |
|----------|------------------------------------|
| Version  | 1.0 (draft for sponsor approval)   |
| Date     | 2026-09-29                         |
| Sponsor  | Head of the IT department          |
| PM       | [Name], supervising lecturer       |

## 1. Purpose and justification
Lecturers spend about 300 hours a year marking quizzes by hand and get no live feedback on how students understand a topic during class. The project delivers the Realtime Quiz platform, where instructors author multiple-choice quizzes and run timed live sessions that students join with a 6-character code, with instant scores and a leaderboard. The benefit is less marking time, immediate feedback and a department-owned tool with no per-seat licence. The numbers and the comparison with buying a SaaS product are in [business-case.md](business-case.md), which recommends option C (build).

## 2. Objectives and success criteria
| #  | Objective (what will be true)                                   | Success criterion (number + week) |
|----|-----------------------------------------------------------------|-----------------------------------|
| O1 | All 8 Must features work together in one live demo               | 8 of 8 Must features demonstrated live, week 7 |
| O2 | A real class uses the platform in a pilot                        | 50 participants in one live session, 0 blocking defects, week 14 |
| O3 | Live updates reach every participant quickly                     | Broadcast latency <= 500 ms at the 95th percentile with 100 simulated students in week 12 and during the pilot in week 14 |
| O4 | The code is tested and the build stays healthy                   | Line coverage >= 80 % and CI green on every merge, checked weekly from week 7 to week 14 |
| O5 | The project stays within its effort and cash limits              | <= 490 h and <= 200 USD cash, reported at every weekly status review, weeks 1 to 14 |

## 3. High-level scope
In scope:
- Quiz authoring module (multiple-choice questions)
- Live session module with a timer per question and several concurrent sessions
- Instant feedback, scoring and leaderboard
- Accounts and role-based access for instructor, student and guest
- Instructor analytics and reporting
- Results export (CSV and PDF)
- Responsive screens for students and instructors
- Production deployment package and operations runbook
- Automated test suite and load-test report

Out of scope:
- Native mobile apps
- Question types other than multiple choice
- Video conferencing
- LMS integration
- Multi-node scaling (one server instance only)

## 4. Milestones
| Week | Milestone                                                              | Ends process group         |
|------|------------------------------------------------------------------------|----------------------------|
| 1    | Charter approved, team formed                                          | Initiating                 |
| 3    | Project management plan baselined; repository, CI and deployment skeleton running | Planning        |
| 5    | Accounts, roles and quiz authoring complete                            | Executing                  |
| 7    | MVP demo (live session core, scoring, leaderboard; all Must features)  | Executing                  |
| 10   | Analytics, export, notifications, media and chat complete              | Executing                  |
| 12   | Feature freeze; load test with 100 simulated students passed           | Monitoring and controlling |
| 14   | Pilot with 50 students, closure                                        | Closing                    |

## 5. Budget summary
Effort:  students 4 x 14 x 8 h = 448 h; PM 14 x 3 h = 42 h; total 448 + 42 = 490 h
Cash:    hosting 4 months x 25 USD = 100 USD; domain 15 USD; tools 60 USD
         cash lines = 100 + 15 + 60 = 175 USD
         reserve 200 - 175 = 25 USD, which is 25 / 175 = 14.3 % of the cash lines
         total 175 + 25 = 200 USD (the cash cap)

## 6. Assumptions
- The four students are available 8 h/week each for all 14 weeks, and the PM 3 h/week.
- The Linode VPS at gicitc.com is available from week 1 and costs about 25 USD per month.
- 50 students and at least one instructor can attend a pilot session in week 14.
- The campus network allows WebSocket traffic, or the SockJS fallback works.

## 7. Constraints
- Duration: 14 weeks from 2026-09-29; the MVP demo is in week 7 and the pilot in week 14.
- Cash: at most 200 USD, with hosting at about 25 USD per month.
- Effort: 490 h in total (448 h students, 42 h PM); no paid developers.
- Technical: one server instance on 2 vCPU and 2 GB RAM; no secrets in the repository.

## 8. High-level risks
- The campus proxy may block WebSocket (response: SockJS fallback, test in the campus network early).
- Late answers may race with the closing of a question, and client clocks drift (response: server-authoritative timer).
- Could features may creep into the MVP (response: change control through the sponsor, see section 9).

## 9. Project manager authority
The PM decides alone: re-planning inside the 490 h and 200 USD, task assignment, sprint content and the order of Should and Could features. The sponsor must approve in writing within 5 working days: adding scope, moving the week-7 demo or the week-14 pilot, and spending beyond the 25 USD reserve.

## 10. Approval
Sponsor: ____________________  Date: ________
PM:      ____________________  Date: ________
