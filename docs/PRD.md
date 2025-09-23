# Product Requirements Document (PRD)
**Product:** AI Vacation Planner  
**Doc Version:** v1.3 (post launch)  
**Status:** Shipped (MVP Q1 2025, Monetization Q2 2025) In Maintenance/Optimization  
**Doc Owner:** Product Manager (you)  
**Last Updated:** Sep 22, 2025

---

## 1) Vision & Context
**Vision:** Become the most trusted AI assistant for end-to-end leisure travel planning by solving three decisions simultaneously:  
1) *Where to go*, 2) *When to go*, 3) *When to book* — optimized for **budget, weather, and interests**.

**Context:** Travel planning is fragmented across blogs, weather guides, OTAs, and price trackers. Users restart research multiple times as costs and conditions change. We centralize this into a single, AI-driven flow.

---

## 2) Problem Statement
Users face friction at every step:
- Destination uncertainty (too many choices, fear of missing out).
- Season/weather confusion; events/crowds vs affordability.
- Price volatility → peak-season sticker shock late in the process.
- Re-work to find off-peak windows or alternative destinations.
- No clear guidance on **when to book**.

**Impact:** Time wasted, overspend, and lower trip satisfaction.

---

## 3) Goals & Non-Goals
### Goals (2025)
- Reduce planning time by **≥70%** vs manual multi-site research.
- Deliver **accurate “best time to book”** guidance (≥80% accuracy; achieved **85%** by Sep 2025).
- Improve user savings by **≥15%** on flights/hotels (achieved **~18%**).
- Achieve **CSAT ≥ 4.5/5** and **NPS ≥ 50** (achieved **4.6/5** and **54**).

### Non-Goals (2025)
- Visa processing or insurance underwriting.
- Owning booking inventory (we integrate via affiliates/OTAs).
- Corporate travel policy management (future consideration).

---

## 4) Target Users & Personas (summary)
- **Explorer**: Flexible on destination/dates; wants inspiration + value.  
- **Anchored Traveler**: Fixed destination (family/couples); needs best-visit month and booking window.  
- **Backpacker/Student**: Highly price sensitive; prefers hostels/off-peak.  
- **Bleisure**: Short stay, maximizes productivity + one curated experience.

(Full details in `/docs/personas.md`.)

---

## 5) Value Proposition
- **One place** to plan: destination, seasonality, costs, and booking timing.
- **Transparent trade-offs**: peak vs shoulder vs off-season.
- **Alternatives & hidden gems** that fit user’s vibe at lower cost.
- **Dynamic re-planning** (premium) for disruption resilience.

---

## 6) Success Metrics (KPIs & Targets)
| KPI | Target | Result (Sep 2025) |
|-----|--------|-------------------|
| Planning time saved | ≥ 70% | **72%** |
| Booking window accuracy | ≥ 80% | **85%** |
| Avg. user savings | ≥ 15% | **~18%** |
| CSAT | ≥ 4.5/5 | **4.6/5** |
| NPS | ≥ 50 | **54** |
| Repeat usage (30/90d) | ≥ 40% | **43%** |
| ARR (premium + affiliate) | ≥ $1.0M | **$1.2M** |

(Workbook: `/processes/KPI_Dashboard.xlsx`.)

---

## 7) Scope Overview
### In-Scope (v1.0–v1.2 shipped)
- Input capture (dates/flexible, budget, location(s), transport mode, food/culture/weather prefs, free-text goals).
- **Explorer Mode**: destination suggestions + best travel windows + alternatives.
- **Anchored Traveler**: best time to visit + **best time to book** (flights/hotels/activities).
- Cost breakdown (flights/hotels/activities) with confidence bands.
- Itinerary builder (day-by-day with styles: Relaxed/Adventure/Family/Luxury).
- Alerts for price movements and booking deadlines.
- PDF/email export; basic account/profile; multi-language content.
- OTA affiliate links; premium tier + dynamic re-planning.

### Out of Scope (2025)
- Group cost splitting, visa filing, flight check-in, loyalty wallet.

---

## 8) Core Use Cases
1. **“Plan for me” (Explorer)**: “Warm, $3k budget, vegetarian food, arts & beach, Apr/May.”  
2. **“I must go to Japan” (Anchored)**: “This year, 10 days, kid-friendly, what month & when to book?”  
3. **“I picked Italy but it’s pricey in July”** → Suggest **shoulder-season** or **alt destinations** with similar weather/culture.  
4. **“Re-plan mid-trip” (Premium)**: Weather turns; swap outdoor/indoor and reschedule bookings.

---

## 9) Functional Requirements (FR)
### FR-1 Input & Profile
- **FR-1.1** Form captures: dates (fixed or flexible), location(s) or open-ended vibes, budget, transport mode, food/culture/weather prefs, accessibility needs, free-text goals.
- **FR-1.2** Save profiles & prior itineraries; allow edits and re-runs.

**Acceptance Criteria (AC)**
- AC-1: All fields persist per session; input validation with friendly errors.
- AC-2: Free-text goals influence itinerary content (see Telemetry).

---

### FR-2 Destination Discovery (Explorer)
- **FR-2.1** Generate ≥3 destination options with: summary, best months, expected weather, top experiences, indicative cost.
- **FR-2.2** Provide **hidden-gem alternatives** with rationale (cost, crowds, similar weather/culture).

**AC**
- AC-1: Each option includes an at-a-glance card: “Why here / Best months / Cost / Top 3 highlights.”
- AC-2: At least one **lower-cost alternative** is presented with % savings estimate.

---

### FR-3 Anchored Traveler (Best Time to Visit & Book)
- **FR-3.1** For a fixed destination, return: best months (primary/secondary), peak vs shoulder pros/cons.
- **FR-3.2** Recommend **booking windows** per transport/hotel/activity, with **confidence score** and savings band.
- **FR-3.3** Show seasonal itineraries (e.g., cherry blossom vs autumn foliage) and availability caveats.

**AC**
- AC-1: Booking windows rendered as “Book in 3–5 weeks (85% confidence), est. save 12–18%”.
- AC-2: Present at least two seasonal variants with differences called out.

---

### FR-4 Itinerary Builder
- **FR-4.1** Day-by-day plan with activity durations, travel time buffers, meals, and rest time.
- **FR-4.2** **Styles**: Relaxed/Adventure/Family/Luxury toggle that rewrites the plan.
- **FR-4.3** Swap suggestions if weather forecast contradicts planned outdoor items (premium = automatic re-plan).

**AC**
- AC-1: Each day has 3–6 timed items; over-scheduling warnings.
- AC-2: Style toggle changes ≥50% of activities and tone.

---

### FR-5 Cost Estimation & Budget Fit
- **FR-5.1** Provide total and per-category estimates (flight, lodging, activities, local transport, food).
- **FR-5.2** Display min/median/max with data source attribution; note exchange rate assumptions.

**AC**
- AC-1: Budget overage is flagged with alternatives (date shift or destination swap).
- AC-2: Estimates include a timestamp + “prices can change” disclaimer.

---

### FR-6 Price Prediction & Booking Windows
- **FR-6.1** Predict favorable booking windows for flights/hotels; show **confidence bands** and last-date-to-book alerts.
- **FR-6.2** Explainability: display the key drivers (seasonality, historical trend, events).
- **FR-6.3** Activities booking timing (e.g., museum passes, popular tours).

**AC**
- AC-1: Predictions expose **confidence %** and ± price band.
- AC-2: If model confidence <60%, fallback heuristic and disclaimer are shown.

---

### FR-7 Notifications & Alerts
- **FR-7.1** Users can opt in to email/push for price drops or window deadlines.
- **FR-7.2** Quiet hours and frequency caps.

**AC**
- AC-1: Opt-in per itinerary; unsubscribe in one click.
- AC-2: ≤1 alert/day default; bursting allowed for major drops (>10%).

---

### FR-8 Export & Share
- **FR-8.1** Export itinerary as PDF/email with summary + links.
- **FR-8.2** Shareable link for partner review; read-only unless collaborator access granted.

**AC**
- AC-1: PDF includes date stamp, total budget, and booking window box.
- AC-2: Shared link respects privacy (no PII leakage).

---

### FR-9 Localization & Accessibility
- **FR-9.1** Languages: EN, FR, ES, HI, JA (content & itinerary text).
- **FR-9.2** Accessibility: keyboard navigation; readable color contrast; large text option.

**AC**
- AC-1: All UI strings pulled from i18n files.
- AC-2: WCAG 2.1 AA checks pass on key flows.

---

### FR-10 Admin & Content Controls
- **FR-10.1** Feature flags for gradual rollout.
- **FR-10.2** Content rules (e.g., safety advisories) are managed centrally.

**AC**
- AC-1: PM can toggle Explorer/Anchored enhancements per locale.
- AC-2: Audit log for admin actions.

---

## 10) Data & AI/ML Requirements
**Inputs:** User prefs + historical flight/hotel prices, seasonal weather norms, events/festivals, destination metadata, safety advisories, exchange rates.  
**Outputs:** Ranked destinations, seasonal windows, bookings timing (with confidence), itineraries, alternatives.

**Modeling:**
- Price prediction: time-series (e.g., Prophet-style / gradient boosting) + seasonal/event features; localized by route/region.
- Itinerary generation: rules + LLM prompt templates; content safety filters.
- Confidence scoring: calibrated via historical backtests; show 50/80% bands.

**Evaluation:**
- **MAPE** for price predictions; **Hit-rate** for “book now vs wait”.
- **Human eval** for itinerary relevance (3-point scale) + CSAT correlation.
- Drift monitoring monthly; retrain triggers if MAPE worsens >20% over baseline.

**Data Governance:**
- PII minimization; hashed user IDs; retention 12 months (configurable).
- Consent banners; data export/delete requests supported.

---

## 11) Integrations & APIs
- Weather (seasonal norms + 10-day forecast)
- Flights & Hotels (search/price history, affiliate deep links)
- Events/Festivals calendars
- Currency rates
- Email/push notifications (ESP)
- Optional: Safety advisories / travel advisories feed

**Resiliency:** Caching, request backoff, provider failover.

---

## 12) UX Requirements (IA & Flows)
**Primary flows:**  
1) **Explorer**: Input → 3 options → pick one → itinerary style → export/alerts.  
2) **Anchored**: Destination → best time to visit → best time to book → seasonal itinerary → export/alerts.  
3) **Premium re-plan**: Disruption → propose adjusted plan → confirm changes.

**UX Tenets:**  
- Plain-language explanations (“Why we recommend this month”).  
- Transparent trade-offs & costs; confidence scores, not absolutes.  
- Helpful defaults; low-friction edits.

---

## 13) Performance, Reliability & SLOs
- P50 recommendation time: **<5s**, P95 **<12s** (cache warm <2s).
- Itinerary export ≤4s P95.
- Alert delivery: 99% in ≤5 min of trigger.
- Availability: **99.9%** core API.

---

## 14) Analytics & Telemetry
- Funnel: Viewed suggestions → Itinerary chosen → Alerts enabled → Click-through to OTA.
- Content metrics: % using Anchored vs Explorer; style usage; alt destination acceptance rate.
- Model cards: Booking window accuracy by route/season; confidence calibration drift.
- Teardown dashboards in `/processes/KPI_Dashboard.xlsx`.

---

## 15) Experimentation
- A/B: Style-matched itineraries vs generic (launched Q2; +9% CSAT, +6% booking clicks).
- A/B: Confidence band UI variants; explanation depth vs clicks.
- Holdouts for model updates (10%).

---

## 16) Rollout & Release
- Feature-flagged beta → locale waves → global.
- Notable releases:
  - **v1.0 (Mar 2025):** MVP (Explorer, costs, export)
  - **v1.1 (Apr 2025):** Anchored + booking windows
  - **v1.2 (Jun 2025):** Alerts, premium, OTA links

(Release notes: `/communication/release_notes_v1.md`.)

---

## 17) Risks & Mitigations
| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| API downtime | High | Med | Caching + provider fallback |
| GDPR/PII issues | High | Med | Consent, minimization, deletion flows |
| Model misguides bookings | Med | Med | Confidence bands + clear rationale + backtests |
| Seasonal spikes overwhelm | Med | High | Queue & rate-limit alerts; autoscale |
| Competitive pressure (OTAs) | High | Med | Differentiation: Anchored + explainability + re-plan |

(Full register: `/processes/Risk_Register.xlsx`.)

---

## 18) Dependencies & Costs
- Provider SLAs (weather, flights/hotels, events).
- ESP costs for alerts; affiliate agreements.
- Cloud inference costs (LLM + price models).
- Localization & content ops for new markets.

---

## 19) Open Questions (vNext)
- Add **group planning** (cost split, availability poll)?
- Add **multi-city** trip generator?
- Bring **loyalty balances** into price advice?
- Extend **visas/health requirements** checker depth per country?

---

## 20) Glossary
- **Anchored Traveler:** User with fixed destination (or fixed dates).  
- **Booking Window:** Time interval predicted to yield best average prices.  
- **Confidence Band:** Uncertainty interval (e.g., ±10%, 80% confidence).

---

## 21) Sample Schemas (for engineers)
**User Input (JSON)**
```json
{
  "dates": {"type": "flexible", "month_range": ["2025-04","2025-05"], "nights": 7},
  "locations": ["open"],
  "budget_total": 3000,
  "transport": ["flight"],
  "prefs": {"weather": "warm", "food": "vegetarian", "culture": ["art","markets"]},
  "goals_free_text": "beach + museums, avoid crowds, walkable areas",
  "accessibility": {"low_mobility": false},
  "anchored_destination": null
}


**Itinerary (JSON excerpt)**
{
  "destination": "Valencia, Spain",
  "best_travel_window": {"start":"2025-05-10","end":"2025-05-25","why":"shoulder season, mild weather"},
  "booking_advice": {"flight":"book 3-5 weeks in advance","hotel":"book 2-4 weeks"},
  "confidence": {"flight":0.84,"hotel":0.81},
  "budget": {"total_est": 2850, "bands":{"p10":2450,"p50":2850,"p90":3350}},
  "style": "Relaxed",
  "days":[
    {"day":1,"items":[{"time":"AM","type":"activity","name":"Old Town walking tour","duration_min":120},
                      {"time":"PM","type":"beach","name":"Malvarrosa","duration_min":180}]}
  ]
}

