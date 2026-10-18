# Business case: live quizzes for the IT department

## 1. Problem
Lecturers mark quiz answers by hand and cannot see during class who has understood. Assumptions:
- lecturers running quizzes: 10
- marking time per lecturer per week: 1 h
- teaching weeks per year: 30
- notional value of one hour: 10 USD (students are unpaid; used to compare)

Marking time per year = 10 x 1 x 30 = 300 h. Value = 300 x 10 = 3,000 USD per year.

## 2. Options
| Option | Description | One-off cost | Annual cost | Annual benefit |
|--------|-------------|--------------|-------------|----------------|
| A      | Do nothing  | 0            | 0           | 0              |
| B      | Buy SaaS (assumed 15 USD per lecturer per month; replace with a real price and cite page and date) | 0 | 10 x 15 x 12 = 1,800 | 300 h x 10 = 3,000 |
| C      | Build Realtime Quiz with the charter budget | 490 h x 10 = 4,900 (notional; real cash is 200 USD) | hosting 12 x 25 = 300 | 3,000 marking + 1,800 SaaS fee avoided = 4,800 |

## 3. Comparison
Payback in years = one-off cost / net annual benefit.

| Option | Net annual benefit | Payback (years) | Sensitivity (6 lecturers) |
|--------|--------------------|-----------------|---------------------------|
| B      | 3,000 - 1,800 = 1,200 | 0 (no one-off cost) | benefit 6 x 1 x 30 x 10 = 1,800; licence 6 x 15 x 12 = 1,080; net 1,800 - 1,080 = 720 |
| C (vs buying B) | 3,000 + 1,800 - 300 = 4,500 | 4,900 / 4,500 = 1.09 | benefit 1,800 + 1,080 - 300 = 2,580; payback 4,900 / 2,580 = 1.90 |
| C (vs doing nothing) | 3,000 - 300 = 2,700 | 4,900 / 2,700 = 1.81 | benefit 1,800 - 300 = 1,500; payback 4,900 / 1,500 = 3.27 |

Note: the 1,800 "SaaS fee avoided" is only a benefit if the real alternative is B. Against doing nothing, C's net benefit is 2,700 and payback 1.81 years. Both views are shown so the sponsor sees the difference.

## 4. Benefits not priced
- Learning outcome: the team practises a full project cycle (capstone).
- Data ownership: student results stay on a department server.
- No per-seat limit: any number of lecturers and students without extra fees.

## 5. Risks per option
- A: marking load stays; students see tools elsewhere and expect them; no learning outcome.
- B: per-seat fees grow with adoption; data stored by a third party; limited customisation.
- C: the campus proxy may block WebSocket; Spring Boot 4 and Spring Security 7 are newer than most tutorials; Could features may creep into the MVP; the product needs an operator after week 14.

## 6. Recommendation and review gate
Recommend **option C**. Payback is 1.09 years against buying and 1.81 years against doing nothing (1.90 and 3.27 with 6 lecturers); real cash is only 200 USD because the effort is student time. The department also keeps its data and gains the learning outcome. Review gate: if the week-7 MVP demo fails, buy option B for next semester and treat the build as a two-semester project.
