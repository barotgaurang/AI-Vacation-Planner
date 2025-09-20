# AI Vacation Planner
**Personalized itineraries, optimal travel windows, and smarter booking advice — delivered by AI.**  
**Status:** Completed Q2 2025 | **Results Updated:** Sep 2025

---

## What’s in this Repository
- **Roadmap & Delivery (Completed 2025):** [`roadmap/product_roadmap_v1.md`](roadmap/product_roadmap_v1.md)
- **Product Requirements:** [`docs/PRD.md`](docs/PRD.md)
- **Statement of Work:** [`docs/SOW.md`](docs/SOW.md)
- **User Stories & Backlog:** [`docs/user_stories_backlog.md`](docs/user_stories_backlog.md)
- **Personas & Journeys:** [`docs/personas.md`](docs/personas.md)
- **Competitor Analysis:** [`docs/competitor_analysis.md`](docs/competitor_analysis.md)
- **MVP Scope:** [`docs/MVP_scope.md`](docs/MVP_scope.md)
- **Agile Practices:** [`processes/agile_ceremonies.md`](processes/agile_ceremonies.md)
- **KPIs Dashboard (Excel):** [`processes/KPI_Dashboard.xlsx`](processes/KPI_Dashboard.xlsx)
- **Risk Register (Excel):** [`processes/Risk_Register.xlsx`](processes/Risk_Register.xlsx)
- **Release Notes v1:** [`communication/release_notes_v1.md`](communication/release_notes_v1.md)
- **Onboarding Guide:** [`communication/onboarding_doc.md`](communication/onboarding_doc.md)
- **Demo Script:** [`communication/demo_script.md`](communication/demo_script.md)
- **Experiments (A/B):** [`experiments/ab_test_itinerary_styles.md`](experiments/ab_test_itinerary_styles.md)
- **Retrospective:** [`experiments/retrospective.md`](experiments/retrospective.md)
- **Market & Seasonality Research:** [`research/market_research.md`](research/market_research.md) | [`research/seasonal_constraints.md`](research/seasonal_constraints.md)

> This repository focuses on **product management deliverables**. Any prototype code (if added) will live under `/prototype/` and is not required to assess the product work.

---

## Problem
Planning a vacation is **fragmented** and **time-consuming**:
1. Users don’t know **where** to go (or when).
2. If a destination is chosen, they must research **best time to visit** (weather, events, peak seasons).
3. Then they compare **flights/hotels/activities** and realize peak periods are **expensive**.
4. They start over — looking for **off-peak dates** or **alternative destinations** with similar weather/experiences.

**Result:** Analysis paralysis, overspending, and suboptimal trips.

---

## Solution Overview
An AI assistant that:
- Generates **personalized itineraries** from preferences (budget, dates, weather, culture, food).
- For **Explorers**: suggests destinations, travel windows, and hidden-gem alternatives.
- For **Anchored Travelers**: if a user *must* visit a specific destination, recommends:
  - **Best time to visit** (seasonality, events, crowd levels).
  - **Best time to book** (flight/hotel pricing windows with confidence scores).
  - Seasonal itineraries with trade-offs (peak vs shoulder).

**Outputs:** Itineraries, cost estimates, alternatives, alerts, export to PDF/email.

---

## Who It’s For (Personas)
- **Explorer:** Flexible, inspiration-seeking, budget-aware.
- **Anchored Traveler:** Fixed destination or dates (families, couples).
- **Backpacker/Student:** Price sensitive; prefers off-peak and hostels.
- **Business + Leisure (Bleisure):** Short trips optimized for productivity + culture.

See detailed personas & journeys → [`docs/personas.md`](docs/personas.md)

---

## Feature Set (MVP → Growth)
**MVP (Q3 2024)**
- Input capture (dates/flexible dates, budget, transport mode, food & culture, weather prefs, free-text goals)
- Destination recommendations + alternative “hidden gems”
- **Seasonality/weather mapping**
- Basic cost breakdown (flights/hotels/activities)
- Export itinerary (PDF/email)
- Feedback loop per itinerary

**Anchored Traveler (Q3 2024)**
- **Best time to visit** + **best time to book**
- Seasonal itineraries incl. festivals/events
- Peak vs off-peak trade-offs

**Optimization & Growth (Q4 2024)**
- Price monitoring & **booking alerts**
- **Itinerary styles** (Relaxed/Adventure/Family/Luxury)
- Multi-language content (EN, FR, ES, HI, JA)
- OTA affiliate integrations

**Monetization (Q4 2024)**
- **Premium tier:** concierge itineraries & **dynamic re-planning** (flight/weather changes)
- Airline loyalty & travel advisory integrations (visa/safety)

Details → [`roadmap/product_roadmap_v1.md`](roadmap/product_roadmap_v1.md) | [`docs/MVP_scope.md`](docs/MVP_scope.md)

---

## Differentiators
- Not just “where to go” — also **when to travel** and **when to book**.
- Transparent **confidence scores** on predictions; clear **trade-offs** (cost vs crowd vs weather).
- **Hidden-gem alternatives** that match user’s weather/culture goals at lower cost.
- **Dynamic re-planning** for disruptions (premium).

---

## Results (as of Sep 2025)
- **Adoption:** 52,400 itineraries generated  
- **Engagement:** 43% repeat usage rate  
- **User Satisfaction:** CSAT **4.6/5**, NPS **54**  
- **Savings:** ~**$310** average savings per trip; **~18%** off flight/hotel spend  
- **Prediction Accuracy:** **85%** for “best time to book”  
- **Revenue (ARR):** **$1.2M** (premium + affiliate)  
- **Completion:** Project **finished Q2 2025**, now in maintenance & optimization

KPIs & notes → [`processes/KPI_Dashboard.xlsx`](processes/KPI_Dashboard.xlsx)

---

## Architecture (High-Level)
**(Design-focused; code-agnostic)**

- **Input Layer:** Preferences form + free-text goals  
- **Recommendation Engine:** LLM-powered planner + rules for seasonality/weather/cost  
- **Pricing Intelligence:** Historical + trending price data, **booking window predictions**  
- **Content Layer:** Itinerary generator; style templates; localization  
- **Alerting:** Price-drop & timeline reminders (email/push-ready)  
- **Integrations:** Weather, flights/hotels, events, OTA affiliates  
- **Governance:** Privacy, consent, data minimization, GDPR

(Architecture notes live in PRD & Roadmap.)

---

## Data, Privacy & Compliance
- **Data Sources:** Weather APIs, flight/hotel price providers, events datasets, public tourism info  
- **Data Handling:** Consent-based, **minimum PII**, anonymized metrics, retention controls  
- **Compliance:** GDPR principles, user data export/delete workflows (documented in PRD)

Risks & mitigations → [`processes/Risk_Register.xlsx`](processes/Risk_Register.xlsx)

---

## Delivery & Process
- **Methodology:** Agile (2-week sprints), roadmap-driven  
- **Ceremonies:** Planning, daily standups, reviews, retros (templates included)  
- **Artifacts:** PRD, SOW, backlog with acceptance criteria, KPIs dashboard, risk register  
- **Releases:** Versioned notes & stakeholder comms

More → [`processes/agile_ceremonies.md`](processes/agile_ceremonies.md) | [`communication/release_notes_v1.md`](communication/release_notes_v1.md)

---

## Experiments & Learnings
- **A/B:** Style-matched itineraries improved CSAT **+9%** and booking intent **+6%**  
- **Insight:** “Anchored traveler” flow = highest retention; transparency (when to book; why) builds trust  
- **Action:** Confidence bands on price predictions; better alternatives in peak periods

Docs → [`experiments/ab_test_itinerary_styles.md`](experiments/ab_test_itinerary_styles.md) | [`experiments/retrospective.md`](experiments/retrospective.md)

---

## Demo & Onboarding
- **Onboarding Guide:** [`communication/onboarding_doc.md`](communication/onboarding_doc.md)  
- **Demo Script (6–8 min):** [`communication/demo_script.md`](communication/demo_script.md)

> Note: This repo emphasizes product artifacts. A lightweight UI/CLI prototype can be added later under `/prototype/`.

---

## Roadmap & Status
- **Completed Phases:** MVP, Anchored Flow, Optimization & Growth, Monetization (Q1–Q2 2025)  
- **Ongoing (Q3 2025):** Scaling, localization, partnerships, continuous improvement  
- Full detail → [`roadmap/product_roadmap_v1.md`](roadmap/product_roadmap_v1.md)

---
