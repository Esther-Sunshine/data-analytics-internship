# HealthConnect Clinic — Data Analytics Track
**AnalystLab Africa Experience Lab**

## Project

**Central question:** How can HealthConnect Clinic use data and AI to reduce missed appointments and
improve the patient support experience?

HealthConnect Clinic is a fictional healthcare provider seeking to reduce missed appointments, improve
appointment attendance, and make better use of appointment slots. This repo tracks the Data Analytics
track's contribution across the Experience Lab internship.

**Resources:** `HealthConnect_Appointment_Data.csv` (5,000 fictional appointment records, unmodified),
`HealthConnect_Data_Dictionary.xlsx`, HealthConnect Clinic Knowledge Base.

---

## Progression

| Week | Focus | Status |
|---|---|---|
| 4 | Problem understanding, resource review, solution planning | ✅ Complete |
| 5 | Analysis, development, initial implementation | ✅ Complete |
| 6 | Integration, advanced development & validation | ✅ Track output complete · integration in progress |
| 7 | Testing, refinement, end-to-end validation | ⏳ Not started |
| 8 | Final integration & presentation | ⏳ Not started |

---

### Week 4 — Problem Understanding

Defined the track's role, reviewed the dataset and Knowledge Base, and proposed five business
questions/KPIs to investigate in Week 5.

**Key findings:** dataset is clean (no duplicates/invalid values); 48.5% baseline no-show rate; booking
lead time and prior no-show history flagged as the two strongest early candidates; reminders showed
only a modest early association; 737 Sunday-appointment records flagged as conflicting with stated
clinic policy.

**Files:** [`week4/HealthConnect_Week4_Project_Summary.pdf`](./week4/HealthConnect_Week4_Project_Summary.pdf)

### Week 5 — Analysis & Initial Implementation

Executed the Week 4 plan in full: calculated all five KPIs with chi-square significance testing, built a
six-panel dashboard, and produced 7 business insights and 5 recommendations. Saved a processed,
derived dataset separately from the original source file.

**Key findings:** booking lead time is the strongest single driver (27.8% → 60.5% no-show rate,
p<0.001); prior no-show history is the second-strongest (43.5% → 68.8%); the two compound to an
80–81% no-show rate in the highest-risk segment; reminders are modestly effective overall but much
more so for higher-risk patients; distance is a threshold effect above ~20km.

**Files:**
[`week5/HealthConnect_Week5_Initial_Analytics_Report.docx`](./week5/HealthConnect_Week5_Initial_Analytics_Report.docx) ·
[`week5/HealthConnect_Week5_Project_Summary.docx`](./week5/HealthConnect_Week5_Project_Summary.docx)

*(The Week 5 notebook is not duplicated here — it's carried forward and extended inside the Week 6 notebook below, since Week 6 builds directly on top of it rather than starting fresh.)*

### Week 6 — Integration, Advanced Development & Validation

Did not repeat the Week 5 EDA. Instead: validated whether the Week 5 findings survive multivariate
control, ranked them by practical (effect-size) rather than just statistical importance, checked their
consistency across patient/appointment segments, resolved an outstanding data-quality question
analytically, and opened a formal cross-track integration with Data Science.

**What's new:**
- Multivariate logistic regression — lead time, prior no-shows, distance and reminders all remain
  significant after controlling for age, gender and appointment type.
- Effect-size ranking (Cramér's V) — lead time sits in a different tier of importance from every other
  factor tested.
- Subgroup consistency checks — the lead-time effect holds across every appointment type, age group
  and gender.
- Reminder channel breakdown — SMS outperforms Email and WhatsApp, especially for higher-risk
  patients.
- Sunday-anomaly sensitivity check — confirms the Week 4/5 data-quality flag is not distorting any
  reported KPI.
- Cancellation deep dive — brought forward from the Week 5 "future work" list.
- Quantified business impact and refined recommendations.
- Cross-track integration with Data Science — **in progress**, see integration evidence log.

**Files:**
[`week6/HealthConnect_Week6_Advanced_Analytics_Report.docx`](./week6/HealthConnect_Week6_Advanced_Analytics_Report.docx) ·
[`week6/HealthConnect_Week6_Project_Summary.docx`](./week6/HealthConnect_Week6_Project_Summary.docx) ·
[`week6/HealthConnect_Week6_Analytics_Report_Notebook.ipynb`](./week6/HealthConnect_Week6_Analytics_Report_Notebook.ipynb) ·
[`docs/week6_integration_evidence.md`](./docs/week6_integration_evidence.md)

---

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
├── docs/
│   └── week6_integration_evidence.md
└── data/
    └── HealthConnect_Appointment_Data_processed.csv
```

## Data note

The original source file is never modified. All derived work is saved separately as
`HealthConnect_Appointment_Data_processed.csv` (adds lead-time band, prior-no-show band, distance
band, and risk-tier columns).

## Current status

Track-specific Week 6 output: **complete**.
Cross-track integration (Data Analytics → Data Science): **in progress** — request sent, response
pending (see `docs/week6_integration_evidence.md`).
Next: Week 7 testing and refinement.
