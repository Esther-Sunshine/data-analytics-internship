# Week 6 Cross-Track Integration Evidence — Data Analytics → Data Science

**Track collaborated with:** Data Science
**Status as of submission:** In progress — outreach sent, response pending

---

## 1. Context

The Data Science track intern (finishing their own Week 5) reached out independently to report they
had completed feature selection (with statistical testing), missing-value handling (treating "no
reminder sent" as its own category rather than dropping rows), encoding, scaling, and a trained
baseline no-show model — originally framed as a handoff to the ML Engineering track.

This was redirected into a specific Data Analytics ↔ Data Science exchange, since the Week 6 brief
requires validated output, not just a status update.

## 2. What was requested from Data Science

1. Confirmation of which Week 5-flagged features were used in the final model:
   booking lead time, prior no-show count, distance to clinic, reminder status.
2. Model performance specifically on the highest-priority segment identified in Week 5/6:
   patients with 3+ prior no-shows and 15+ day booking lead time (80.9% actual no-show rate).
3. Feature importance ranking (coefficients, tree-based importances, or SHAP — whichever is available).

## 3. What was provided to Data Science (in return)

- Multivariate-validated driver ranking (odds ratios, controlling for confounders)
- Effect-size ranking (Cramér's V) — lead time and prior no-shows identified as the two drivers
  worth prioritising as features
- Reminder-channel effectiveness breakdown (SMS most effective, especially for higher-risk patients)
- Updated highest-priority segment definition

## 4. Outreach record

**Date sent:** [fill in — date you sent the message]
**Channel:** [fill in — e.g. WhatsApp / Slack / email]

> Message sent (paraphrased): "Thanks for reaching out — I'm on Data Analytics and could use a few
> specifics for my Week 6 validation work: which features made your final cut, your model's
> performance on the high-risk segment (3+ prior no-shows, 15+ day lead time), and what ranked as
> most important in your model. Happy to send my full KPI writeup and risk-segment breakdown if
> useful for your feature engineering."

## 5. Outcome

**Response received:** Not yet, as of [fill in — submission date].
**What changes once a response arrives:** Section 6 of the Advanced Analytics & Decision Support
Report will be updated with the actual feature confirmation, segment-level performance, and feature
importance — resolving whether a simple rule-based risk flag or the Data Science model is the better
basis for HealthConnect's recommended intervention (see report Section 5).

This is logged as an open, evidenced dependency rather than represented as closed, consistent with
the Week 6 requirement that collaboration produce a genuine exchange, not simply a message sent.

## 6. Follow-up (update this section once resolved)

- [ ] Feature confirmation received
- [ ] Segment-level performance received
- [ ] Feature importance received
- [ ] Report Section 6 and Section 5 recommendation updated accordingly
