# HealthConnect Clinic — Data Analytics Track
AnalystLab Africa Experience Lab

## Project
**Central question:** How can HealthConnect Clinic use data and AI to reduce missed appointments and improve the patient support experience?

HealthConnect Clinic is a fictional healthcare provider seeking to reduce missed appointments, improve appointment attendance, and make better use of appointment slots. This repo tracks the Data Analytics track's contribution across the Experience Lab internship.

**Resources:** `HealthConnect_Appointment_Data.csv` (5,000 fictional appointment records, unmodified), `HealthConnect_Data_Dictionary.xlsx`, HealthConnect Clinic Knowledge Base.

## Progression

| Week | Focus | Status |
|---|---|---|
| 4 | Problem understanding, resource review, solution planning | ✅ Complete |
| 5 | Analysis, development, initial implementation | ✅ Complete |
| 6 | Integration, advanced development & validation | ✅ Complete |
| 7 | Testing, refinement, end-to-end validation | ✅ Complete |
| 8 | Final integration & presentation | ✅ Complete |

## Week 4 — Problem Understanding
Defined the track's role, reviewed the dataset and Knowledge Base, and proposed five business questions/KPIs to investigate in Week 5.

**Key findings:** dataset is clean (no duplicates/invalid values); 48.5% baseline no-show rate; booking lead time and prior no-show history flagged as the two strongest early candidates; reminders showed only a modest early association; 737 Sunday-appointment records flagged as conflicting with stated clinic policy.

**Files:** `week4/HealthConnect_Week4_Project_Summary.pdf`

## Week 5 — Analysis & Initial Implementation
Executed the Week 4 plan in full: calculated all five KPIs with chi-square significance testing, built a six-panel dashboard, and produced 7 business insights and 5 recommendations. Saved a processed, derived dataset separately from the original source file.

**Key findings:** booking lead time is the strongest single driver (27.8% → 60.5% no-show rate, p<0.001); prior no-show history is the second-strongest (43.5% → 68.8%); the two compound to an 80–81% no-show rate in the highest-risk segment; reminders are modestly effective overall but much more so for higher-risk patients; distance is a threshold effect above ~20km.

**Files:** `week5/HealthConnect_Week5_Initial_Analytics_Report.docx` · `week5/HealthConnect_Week5_Project_Summary.docx`

*(The Week 5 notebook is not duplicated here — it's carried forward and extended inside the Week 6 notebook below, since Week 6 builds directly on top of it rather than starting fresh.)*

## Week 6 — Integration, Advanced Development & Validation
Did not repeat the Week 5 EDA. Instead: validated whether the Week 5 findings survive multivariate control, ranked them by practical (effect-size) rather than just statistical importance, checked their consistency across patient/appointment segments, resolved an outstanding data-quality question analytically, and opened a formal cross-track integration with Data Science.

**What's new:**
- **Multivariate logistic regression** — lead time, prior no-shows, distance and reminders all remain significant after controlling for age, gender and appointment type.
- **Effect-size ranking (Cramér's V)** — lead time sits in a different tier of importance from every other factor tested.
- **Subgroup consistency checks** — the lead-time effect holds across every appointment type, age group and gender.
- **Reminder channel breakdown** — SMS outperforms Email and WhatsApp, especially for higher-risk patients.
- **Sunday-anomaly sensitivity check** — confirms the Week 4/5 data-quality flag is not distorting any reported KPI.
- **Cancellation deep dive** — brought forward from the Week 5 "future work" list.
- Quantified business impact and refined recommendations.
- **Cross-track integration with Data Science** — outreach sent, no response received (see integration evidence log).

**Files:** `week6/HealthConnect_Week6_Advanced_Analytics_Report.docx` · `week6/HealthConnect_Week6_Project_Summary.docx` · `week6/HealthConnect_Week6_Analytics_Report_Notebook.ipynb` · `docs/week6_integration_evidence.md`

## Week 7 — Testing, Refinement & End-to-End Validation
Week 7 moved the Data Analytics track from validated to tested: every core KPI, effect size, and model result from Week 6 was either reproduced from raw data, backed with a formal significance test, or checked for stability under resampling.

**What was tested:**
- Reproducibility of all 5 KPIs, the Cramér's V effect-size ranking, and the multivariate logistic regression — all reproduced exactly from raw data.
- The Sunday-appointment anomaly and reminder-channel claims, previously argued descriptively, retested with formal chi-square tests.
- The highest-priority patient segment definition, retested across four threshold combinations for sensitivity.
- The self-built baseline model (Week 6), retested under 5-fold stratified cross-validation instead of a single train/test split.

**Key findings:**
- The reminder-channel claim only partially held up: SMS beats WhatsApp significantly (p=0.023), but not Email (p=0.448) — recommendation narrowed accordingly.
- The high-risk segment's 80.9% no-show rate is threshold-sensitive (64–81% depending on definition) — reframed as a graduated risk tier.
- Logistic Regression outperformed Random Forest on every cross-validation fold, not just on average — confirmed as the recommended candidate model.
- Resolved a Week 6 limitation: the high-risk-segment recall test (n=20, too small to trust) was retested via out-of-fold prediction (n=66): recall 100%, precision 81.8%.
- New issue found: model errors cluster by booking lead time — flagged for Week 8 threshold tuning.

**Cross-track status:** Data Science had not responded since the Week 6 outreach. Rather than leave the dependency unaddressed, Week 7 re-tested the model estimate DS would eventually need to benchmark against — see `docs/week7_crosstrack_evidence.md`.

**Files:** `week7/HealthConnect_Week7_Analytics_Testing_Refinement_Report.docx` · `week7/HealthConnect_Week7_Testing_Refinement_Notebook.ipynb` · `week7/HealthConnect_Week7_Project_Summary.docx` · `docs/week7_crosstrack_evidence.md`

## Week 8 — Final Integration & Presentation
The final week: packaging every validated finding from Weeks 4–7 into a finished analytics deliverable, an honest account of the unresolved cross-track dependency, a native BI dashboard, and an individual project presentation.

**What's new:**
- **Final Analytics & Decision Support Package** — consolidated KPIs, effect sizes, validated model, business insights, recommendations and an executive summary into one final report.
- **Final dashboard, two ways** — a static summary chart for the written report, and a rebuilt, interactive **Power BI dashboard** (multi-page, with navigation) sourced from the same validated figures, for portfolio use.
- **HC-POD Final Integration record** — the Data Science dependency opened in Week 6 was never closed despite repeated outreach across Weeks 6–7. Week 8 documents this honestly as an evidenced, unresolved dependency rather than presenting collaboration that didn't happen. A self-built, cross-validated model (Section 7 of the Week 7 report) stands in as the predictive component in its place.
- **End-to-End Integration Walkthrough** — a full account of the problem, data, analytics, predictive component, and business value, including what could not be integrated and why.
- **Individual final presentation video** — a 5–10 minute recorded walkthrough of the track contribution, testing/refinement process, and honest cross-track outcome.

**Key findings carried into final recommendations:**
- Booking lead time remains the dominant, validated driver of no-shows (Cramér's V 0.184; OR 4.24) — the primary lever for intervention.
- The final recommended model (Logistic Regression) is deployable but has a documented, uncorrected lead-time-dependent error pattern, flagged for any future ML Engineering follow-up.
- Reminder strategy: SMS prioritised for higher-risk patients specifically, without discontinuing Email.
- The Sunday-appointment anomaly (737 records) remains operationally open, though confirmed not to distort any KPI.

**Files:** `week8/HealthConnect_Week8_Final_Integration_and_Analytics_Package.docx` · `week8/HealthConnect_Week8_Video_Presentation_Script.docx` · `week8/HealthConnect_PowerBI_Data.xlsx` · `week8/HealthConnect_PowerBI_Dashboard.pbix` · `assets/HealthConnect_Final_Dashboard.png` · `docs/week8_hcpod_integration_record.md`

## Repo structure
```
├── README.md
├── week4/
│   └── HealthConnect_Week4_Project_Summary.pdf
├── week5/
│   ├── HealthConnect_Week5_Initial_Analytics_Report.docx
│   └── HealthConnect_Week5_Project_Summary.docx
├── week6/
│   ├── HealthConnect_Week6_Advanced_Analytics_Report.docx
│   ├── HealthConnect_Week6_Project_Summary.docx
│   └── HealthConnect_Week6_Analytics_Report_Notebook.ipynb
├── week7/
│   ├── HealthConnect_Week7_Analytics_Testing_Refinement_Report.docx
│   ├── HealthConnect_Week7_Testing_Refinement_Notebook.ipynb
│   └── HealthConnect_Week7_Project_Summary.docx
├── week8/
│   ├── HealthConnect_Week8_Final_Integration_and_Analytics_Package.docx
│   ├── HealthConnect_Week8_Video_Presentation_Script.docx
│   ├── HealthConnect_PowerBI_Data.xlsx
│   └── HealthConnect_PowerBI_Dashboard.pbix
├── assets/
│   └── HealthConnect_Final_Dashboard.png
├── docs/
│   ├── week6_integration_evidence.md
│   ├── week7_crosstrack_evidence.md
│   └── week8_hcpod_integration_record.md
└── data/
    └── HealthConnect_Appointment_Data_processed.csv
```

## Data note
The original source file is never modified. All derived work is saved separately as `HealthConnect_Appointment_Data_processed.csv` (adds lead-time band, prior-no-show band, distance band, and risk-tier columns).

## Project outcome
Across eight weeks, the Data Analytics track moved from problem definition through exploratory analysis, multivariate validation, formal statistical and cross-validated testing, to a final, decision-ready package: five validated KPIs, a stability-tested predictive model, and evidence-based recommendations — with every limitation, correction, and unresolved dependency documented transparently along the way.

## Current status

Track-specific Week 6 output: **complete**.
Cross-track integration (Data Analytics → Data Science): **in progress** — request sent, response
pending (see `docs/week6_integration_evidence.md`).
Next: Week 7 testing and refinement.
