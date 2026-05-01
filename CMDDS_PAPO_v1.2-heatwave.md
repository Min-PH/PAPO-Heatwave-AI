# CMDDS — PAPO Heatwave Framework
## Conceptual Model Design Documentation for Simulation (CMDDS)
**Version:** 1.2  
**Date:** 2026-05-01  
**Author:** Min Wu  
**Affiliation:** Zilber College of Public Health, University of Wisconsin-Milwaukee  
**Contact / GitHub:** https://github.com/Min-PH/PAPO-Heatwave-AI

**Cite:** Min Wu. CMDDS for PAPO–Heatwave v1.2 – Conceptual Simulation Framework. Zenodo. DOI: 10.5281/zenodo.18637394

> **★ v1.2 update note (May 2026).** This version integrates findings from the MOKG-PH analytical review of PAPO–Heatwave (Case #002-C, April 2026). The review confirmed strong alignment with MOKG-PH principles in 8 of 10 design decisions and identified two pre-deployment resolutions plus several elevations from "recommended" to "required" status for Complex cases. All changes preserve v1.1 structure; new or elevated content is marked with ★ throughout.

## Overview
This document provides a developer-facing CMDDS for the Policy-Aware Personalized Opportunity (PAPO) 
framework applied to heatwave response. It is written for AI developers, data scientists, and simulation 
engineers who want to prototype, simulate, or extend PAPO in real cities.
The CMDDS defines what to simulate and why, while deliberately leaving how to implement (code, parameters, platforms) open. 
This makes it suitable for agent-based models, system dynamics, discrete-event simulation, digital twins, 
and VR-supported decision environments.

★ **v1.2 framing.** This CMDDS is also the Stage 1 knowledge-graph specification and Simulation-First Protocol artifact for PAPO under the MOKG-PH governance framework. It is simultaneously a simulation grammar for developers and a structured KG specification for governance review. Implementations targeting operational deployment must satisfy the Pre-Deployment Checklist (new in v1.2, see end of document) before any real population is exposed to PAPO-driven recommendations.

-------------------------
## CMDDS Step 1 — System Purpose, Simulation Goals & Policy Boundary

### System Purpose
Extreme heat events evolve on hourly to daily timescales, while public policy and institutional workflows 
are comparatively slow. Individuals—especially vulnerable populations—often face high cognitive and logistical 
barriers when translating heat alerts into feasible action.
PAPO addresses this gap by translating heat emergency policy into personalized, feasible, and actionable 
opportunities in near real time.
The purpose of this CMDDS is to enable simulations that test whether, when, and for whom policy-aware opportunity
 delivery improves heatwave response.

### Core Simulation Questions (Answerable by Design)
Simulations built from this CMDDS should be able to answer specific, concrete questions, such as:
#### 1.	Timing & Triggers
 -	How early must a policy trigger activate for personalized opportunities to meaningfully reduce missed interventions?
 -	What happens if activation is delayed by 6, 12, or 24 hours?
#### 2.	Feasibility vs. Alerts
 -	How do opportunity-based interventions compare to standard heat alerts in terms of uptake?
 -	Which constraints (distance, transport, capacity) dominate failure modes?
#### 3.	Equity & Distribution
 -	Which population subgroups benefit most or least from PAPO-style interventions?
 -	How do equity gaps change as resource capacity scales up or down?
 -	★ How do underserved populations (rural / geographically isolated, language-barrier, no-digital-access) fare relative to digitally reachable urban populations?
#### 4.	System Stress & Capacity
 -	Where do bottlenecks emerge under extreme heat scenarios?
 -	Which resources saturate first (cooling centers, transport, volunteers)?
#### 5.	★ Bias & Fairness (Required for Complex cases)
 -	When historical training data is biased (e.g., overrepresentation of car-owning recipients), what is the disparity delta in opportunity rates across affected groups?
 -	Does applying a fairness constraint (e.g., demographic parity) close the gap to a governance-approved threshold?

These questions are intentionally simulation-first and do not require clinical outcome modeling.

### Candidate Cities for Simulation (Data-Ready, Heat-Exposed)
To lower the barrier for contributors, simulations may focus on data-ready, heat-prone cities, such as:

*	United States: Phoenix, Austin, Houston, Los Angeles, Miami, Cary (NC)
*	International: Singapore, Paris, Madrid

These cities offer combinations of:

*	Recurrent extreme heat
*	Open climate and census data
*	Publicly documented heat emergency policies

Contributors are encouraged to fork this repo and adapt PAPO to their own city or region.

★ **Equity sentinel for city selection.** Open-data-ready cities may overrepresent well-resourced urban contexts. Forks should flag — and where possible offset — the systematic exclusion of rural or less-resourced jurisdictions from validation. Cross-context comparison (e.g., a major metro paired with a less-resourced or rural region) is encouraged.

### Explicit Non-Goals (Important for Developers)
This CMDDS does not aim to:

*	Predict individual clinical outcomes or mortality
*	Model human thermoregulation or physiology
*	Forecast weather or climate
*	Optimize or automatically generate policy

Simulations are exploratory, comparative, and stress-testing oriented, not predictive or prescriptive.

-----------------------
## CMDDS Step 2 — Conceptual Entities, Attributes, and Inputs

This step defines the entities, attributes, and data inputs required to simulate PAPO–Heatwaves. The CMDDS supports
 two temporal phases using the same core entities and logic: Pre-Heatwave (optional) and During Heatwave (minimum required).
  Simulation implementations may model either or both phases.

### Temporal Phases
#### Pre-Heatwave (Preparation / Priming)
Establishes policy constraints, resource capacity, and baseline vulnerability.
Optional but recommended for simulations examining timing, readiness, and equity.
#### During Heatwave (Response / Execution)
Activates policy triggers and delivers personalized opportunities under real-world constraints.
Required for all PAPO–Heatwaves simulations.

### Core Conceptual Entities
#### 1.	Individuals / Households
Residents exposed to heat risk and potential recipients of personalized opportunities.
#### 2.	Policy and Institutional Systems
Public health agencies, emergency management, and service providers that define rules, priorities, and constraints.
#### 3.	Opportunity Resources
Cooling centers, transportation services, community volunteers, wellness checks, and related assets.
#### 4.	Environmental Context
Heat severity and duration represented as scenario inputs (not weather forecasting).
#### 5.	★ Underserved-Population Equity Pathways (Required Nodes)
Explicit modeling of populations who are systematically under-reached by digital, English-language, and urban-resource-dense delivery channels:

*	Rural / geographically isolated individuals (cross-zone resource access required)
*	Limited-English-proficiency populations (translation and culturally competent outreach pathways)
*	No-digital-access populations (non-app, non-text delivery channels: voice, in-person, trusted community intermediary)

These nodes are required for the strategic feedback loop to operate correctly after the first deployed season. Without them, the strategic loop cannot detect or correct systematic exclusion of underserved groups.

### Entity Attributes and Inputs
#### Phase A — Pre-Heatwave Inputs (Optional)
Policy / Institutional Inputs (Static)
Used to initialize the Policy Input Layer:

*	Strategic intent and equity priorities
*	Eligibility thresholds and escalation rules
*	Standard operating procedures and agency roles
*	Resource inventories (facilities, vehicles, staff, volunteers)
*	Spatial distribution of services (GIS)
*	Baseline neighborhood vulnerability indicators

Individual / Household Inputs (Static or Self-Reported)
Used to initialize the Personalized Opportunity Engine:

*	Home location and housing characteristics (e.g., AC access)
*	Demographics and baseline vulnerability factors
*	Chronic health risk indicators
*	Mobility, disability, or caregiver needs
*	Preferred communication channels
*	Digital access constraints
*	★ Language preference and English-proficiency indicator
*	★ Geographic isolation indicator (distance to nearest cooling center, transit availability)

Pre-heatwave simulations may model registration, pre-authorization, or reduced response latency, but these are not required.

#### Phase B — During Heatwave Inputs (Required)
Policy / System Inputs (Dynamic)

*	Heat alerts and emergency triggers
*	Active policy rules and timelines
*	Real-time service availability and capacity
*	Transportation status and routing constraints
*	Community outreach signals and unmet-need reports

Individual / Context Inputs (Dynamic)

*	Current or inferred location
*	Recent activity or movement indicators
*	Connectivity and reachability status
*	Check-in events or non-response
* Self-reported cooling behavior or distress
* Service utilization events
* Caregiver or neighbor alerts

### Attribute Categories and State Updates
Attributes are categorized as:

* Static: baseline vulnerability, housing, access needs
* Contextual: location, routines, communication preferences
*	Dynamic: exposure, opportunity availability, uptake, resource capacity

Simulations are assumed to operate in discrete time steps (e.g., hourly or daily), with state updates driven 
by policy triggers, opportunity delivery, and feedback.

This step defines what data exists and when it becomes active, not how it is modeled. Parameterization, data sources, 
and AI methods are intentionally left to downstream implementations.

### Resource Pools (Required for Stress Testing)
Simulations must model opportunity resources as exhaustible, location aware pools with dynamic availability:

*	Cooling center slots (capacity per facility, real-time occupancy)
*	Transport vehicles (fleet size, range, round-trip time, driver shifts)
*	Volunteer network (response probability, travel time, availability windows)

Resource state is updated every time step: allocation reduces availability; completion of trip or visit replenishes it.
Without this, simulations cannot detect bottlenecks or test feasibility-driven failure modes.

### ★ Bias Injection (Required for Complex Cases — elevated from Recommended in v1.1)
To test equity robustness, implementers **must** inject historical bias into opportunity ranking or eligibility models for any deployment-bound implementation. For example:

*	Train a simple ML ranker on data where 80% of past recipients had personal vehicles.
*	Measure the disparity in opportunity rates between car-owning and car-less groups (the **disparity delta**).
*	Compare against a fairness constrained version (e.g., demographic parity).
*	Confirm the disparity delta meets a governance-approved threshold before deployment authorization.

★ **Status change rationale.** v1.1 framed bias injection as optional. The MOKG-PH review (Case #002-C) determined that for Complex cases involving AI-driven opportunity ranking under scarcity, a passive bias audit is insufficient — active injection testing is required to surface equity/prediction conflicts before any real population is exposed to the system. Forks that omit this step have not met the Complex case pre-deployment gate.

This step defines what data exists and when it becomes active, not how it is modeled. Parameterization, data sources, and AI methods are intentionally left to downstream implementations.

-------------------------------
## CMDDS Step 3 — Core Translation & State Transition Logic

The defining function of PAPO–Heatwaves is the translation of institutional heat emergency policy into personalized, feasible micro-opportunities under real-world constraints. This logic operates continuously across simulation time steps
  and applies to both pre-heatwave and during-heatwave phases.
Different simulation paradigms (agent-based, system dynamics, discrete-event, hybrid) may operationalize this logic differently, but the translation sequence must be preserved.

### Translation and Transition Stages
#### 1. Policy Activation and Rule Evaluation

*	Environmental and institutional signals (e.g., heat alerts, emergency declarations) activate policy rules.
*	Eligibility thresholds, protection priorities, and operational constraints are evaluated.
*	Policy state transitions from inactive to active based on predefined triggers.

Output: active policy rules and authorized intervention space.

#### 2. Risk and Feasibility Assessment

*	Individual baseline vulnerability is combined with dynamic exposure and contextual constraints.
*	Feasibility checks evaluate access, mobility, capacity limits, and timing.
*	Behavioral non-uptake and friction are treated as expected constraints, not errors.

Output: prioritized individuals and feasible intervention sets.

#### 3. Personalized Opportunity Generation

*	Policy-constrained options are translated into concrete, actionable micro-opportunities.
*	Opportunities are specific, time-bound, and resource-aware (e.g., nearest available cooling center with accessible transport).
*	No opportunity is generated if feasibility criteria are not met.
*	If no feasible opportunity exists (resource exhaustion, geographic inaccessibility, conflicting rules), the engine must output a null or empty set. This is not an error state—it is a required failure mode that triggers escalation.

Output: feasible, individualized opportunity candidates (or null).

#### 4. Opportunity Delivery and Escalation

*	Opportunities are delivered via appropriate channels (e.g., text, voice, app, human outreach).
*	**Human-system handover (★ governance sign-off required in v1.2):** Define a clear boundary. Low-risk, reversible actions (e.g., sending an informational text) may be fully automated; actions involving resource commitment or physical safety (e.g., dispatching transport, volunteer entry) require explicit human authorization. Each deployment fork must specify this boundary in writing and obtain governance sign-off before Stage 2 deployment authorization. Simulate delay, rejection, or manual override.
*	Delivery failures or non-response may trigger escalation pathways (e.g., in-person checks).
*	Human supervision and accountability are assumed for escalated actions.

Output: delivered opportunities and delivery status updates.

#### 5. Feedback and State Update

*	Uptake, non-uptake, delays, and resource utilization are recorded.
*	System states are updated for individuals, resources, and policy context.
*	Two feedback loops must be distinguished:
    *	Tactical loop (minutes to hours): real-time reallocation of existing resources (e.g., reroute idle transport, open overflow cooling).
    *	Strategic loop (months to years): post season aggregation to update eligibility criteria, budget planning, and vulnerability definitions.
    *	Conflating these loops risks instability or policy inertia; simulations should implement them separately.
*	★ The strategic loop must include explicit pathways for revising eligibility criteria when post-season data reveals systematic under-reach of underserved populations (rural, language barrier, no digital access). Without this, the loop cannot self-correct equity gaps.
*	Aggregated, privacy-preserving feedback informs subsequent cycles.

Output: updated system state for next simulation step.

### State Transition Scope
State transitions may include:

*	Individual risk and exposure status
*	Opportunity availability and exhaustion
*	Resource capacity and bottlenecks
*	Policy escalation or de-escalation

Transitions are event-driven and time-stepped, depending on simulation design.

### Interpretation Constraints

*	This logic supports exploratory and comparative simulation, not prediction.
*	Outputs reflect system responsiveness, feasibility, and equity signals.
*	Clinical outcomes and physiological effects are explicitly out of scope.

This step defines the non-negotiable logic core of PAPO–Heatwaves. All downstream simulations must preserve this translation
 structure, even when implementation details differ.

---------------------------
## ★ CMDDS Step 3.5 — Simulation-First Protocol (NEW in v1.2)

PAPO–Heatwave is a Complex case under the MOKG-PH governance framework. Complex cases require a Simulation-First Protocol — a structured pre-deployment gate that must be cleared before any real population is exposed to PAPO-driven recommendations. The CMDDS itself provides the structural specification; per-city forks must implement and run the protocol.

The protocol comprises seven required components. All must be addressed before deployment authorization.

| # | Component | What the simulation must do | Source in this CMDDS |
|---|---|---|---|
| 1 | Synthetic population scenarios | Generate realistic populations across both Pre-Heatwave and During-Heatwave phases for the target city | Step 2 entity attributes |
| 2 | Prioritization rule comparison (≥2 rules) | Run at least two rules from the five-rule table and compare outcomes; governance must select the deployment rule | Step 4 Prioritization Rules |
| 3 | Resource scarcity stress test | Vary resource pool capacity to identify bottlenecks and the threshold at which null outputs become common | Step 2 Resource Pools |
| 4 | Equity metric pre-selection | Select the equity metric **before** the simulation is run; document selection rationale; do not default to "no metric" (equivalent to efficiency-only optimization) | Step 4 Equity Metrics |
| 5 | Timing sensitivity test | Test activation delays of 6, 12, and 24 hours; document the critical threshold at which intervention effectiveness degrades | Step 1 Core Simulation Question 1 |
| 6 | Bias injection test | Train a ranker on biased historical data; measure disparity delta; apply fairness constraint; confirm delta meets governance threshold | Step 2 Bias Injection (Required) |
| 7 | Failure mode / null output coverage | Verify that null outputs trigger correct escalation pathways for all five trigger types (resource exhaustion, geographic inaccessibility, policy conflict, non-response, cascading depletion) | Step 3 §3 + Step 4 |

A fork that completes all seven components and documents the results in a public log entry has met the Complex case pre-deployment gate. A fork that omits any component has not.

---------------------------
## CMDDS Step 4 — Simulation Outputs, Interpretation, and Limits

### Scope and Assumptions – Read Before Simulating
This CMDDS defines a logical pathway, not an operational system. It rests on several simplifying assumptions that fail under real-world conditions. Simulations are intended to stress test these assumptions, not to validate the framework as a turnkey solution.

Explicit assumptions embedded in this CMDDS:

1.	Policy is machine-readable – We assume eligibility criteria, thresholds, and rules can be unambiguously encoded. In practice, policy often contains discretion, contradiction, or underspecified terms.
2.	★ A feasible opportunity always exists – The PAPO translation sequence as drawn assumes the engine can always generate an intervention. **Null output is a required architectural element of the framework (Step 3.3), not an optional fork-level extension.** Implementations that omit it have not implemented PAPO.
3.	Resources are sufficient – Many illustrations assume infinite capacity. Real heatwaves require prioritization under scarcity.
4.	★ Human-system handover is resolvable – We do not prescribe who authorizes what; this must be specified per deployment **with explicit governance sign-off** (Step 3 §4). Deployments without a documented, signed-off handover boundary are not authorized to proceed past Stage 2.
5.	Feedback operates on a single timescale – The CMDDS now separates tactical and strategic loops; simulations must respect this separation.
6.	Data are unbiased – Historical data used to train opportunity rankers will systematically under represent marginalized groups unless fairness constraints are added. ★ Bias injection testing (Step 2) is required for Complex cases.
7.	★ Underserved populations are reachable through standard channels – In practice, rural, language-barrier, and no-digital-access populations are systematically under-reached. Forks must include explicit equity pathways for these groups (Step 2 §5).

Failure to explicitly model these assumptions will produce optimistic, non generalizable results.
We publish this CMDDS as a shared grammar, not a finished architecture. Local forks must extend it with triage rules, bias audits, equity metrics, and explicit allocation logic.

### Outputs of Interest
Simulations derived from this CMDDS may examine:

*	Opportunity uptake, timing, and non-uptake
*	Missed, delayed, or infeasible interventions
*	Resource utilization, saturation, and bottlenecks
*	Differential impacts across vulnerability groups or locations
*	★ Differential reach across underserved populations (rural / language barrier / no digital access)
*	Sensitivity to timing, capacity, access, and policy triggers
*	Comparative performance of different prioritization rules (see below)
*	★ Disparity delta from bias injection tests, before and after fairness constraints

Outputs may be generated at individual, neighborhood, or system levels.

### Prioritization Rules (Required under Scarcity)
When demand exceeds supply, a prioritization rule must be superimposed on the PAPO logic. This rule is not derivable from clinical risk or policy eligibility alone—it is a normative choice. Simulate and compare at least two of the following:

| Rule               | Definition                                                                 |
|--------------------|---------------------------------------------------------------------------|
| Clinical risk only | Priority based on age + comorbidities + exposure (no barrier weighting). |
| Equity weighted    | Clinical risk × barrier index (e.g., no AC, mobility, food desert).      |
| Random lottery     | Equal probability among eligible individuals.                             |
| Easiest first      | Minimize resource consumption per intervention (e.g., nearest cooling centre, shortest transport). |
| Worst off first    | Maximize urgency (e.g., highest indoor temperature, longest exposure).    |

Measure: final health status distribution (or proxy, e.g., time to opportunity), resource utilization, and equity metrics.

★ **Governance decision required.** Selection among these rules is a normative governance decision, not a technical optimization. Each deployment fork must (a) compare at least two rules in simulation, (b) document the rationale for the deployed rule, and (c) obtain governance sign-off before deployment.

### Equity Metrics (Define Before You Run)

Choose one or more — each encodes a different ethical commitment:

| Metric              | Definition |
|---------------------|------------|
| Equal allocation    | Same proportion served across groups (e.g., by income, race, disability). |
| Equal outcomes      | Post-event health status equalized (or proxy measure, e.g., mean indoor temperature). |
| Prioritizing        | Weighted benefit allocation — greater weight assigned to worse-off individuals. |
| Sufficient          | Ensure everyone reaches a minimum safety threshold (e.g., access to cooling within 1 hour). |

> ⚠️ **Important (★ elevated to governance action in v1.2):**  
> Defaulting to "no metric" implicitly optimizes for efficiency alone — which systematically disadvantages the populations PAPO is designed to serve.  
> The equity metric must be selected, documented, and approved by the deployment's governance body **before** any simulation run. Always state the selected equity metric explicitly in simulation results.

### Interpretation Guidance
Simulation outputs should be interpreted as:

*	Indicators of system responsiveness and feasibility
*	Comparative signals across scenarios, cities, or policies
*	Evidence of equity gaps in opportunity distribution
*	Stress-test results under constrained resources

Outputs do not represent individual-level prediction or causal inference.

### Ethical and Scope Limits

*	No clinical outcomes or health predictions are implied
*	Weather and physiological modeling are out of scope
*	Data aggregation is assumed to be privacy-preserving
*	Human oversight is integral to intervention delivery
*	Simulations are exploratory, not operational decision engines

### Use in Downstream Implementations
Downstream forks may:

*	Add city-specific metrics or visualizations
*	Integrate digital twins or VR environments
*	Compare PAPO against alert-only baselines
*	Add new failure modes (e.g., sensor noise, policy conflict, resource shock)

All extensions should clearly document assumptions and deviations from this CMDDS.

This step ensures that simulation results are interpretable, comparable, and ethically bounded, while remaining
 flexible for diverse implementation approaches.

---------------------------
## ★ Pre-Deployment Checklist (NEW in v1.2)

Before any real population is exposed to PAPO-driven recommendations, the deployment fork must satisfy every item below. This checklist consolidates the requirements distributed across Steps 1–4 and the Simulation-First Protocol.

| # | Requirement | Location in this CMDDS | Status |
|---|---|---|---|
| 1 | Per-city parameterization of resource pools, population vulnerability, and policy constraints | Step 2 | ☐ |
| 2 | All seven Simulation-First Protocol components run and documented | Step 3.5 | ☐ |
| 3 | Bias injection performed; disparity delta measured against governance-approved threshold | Step 2 (Bias Injection) | ☐ |
| 4 | Equity metric selected, documented, and approved before simulation run | Step 4 (Equity Metrics) | ☐ |
| 5 | Prioritization rule compared (≥2 rules) and deployment rule approved by governance | Step 4 (Prioritization Rules) | ☐ |
| 6 | Human-system handover boundary specified in writing with governance sign-off | Step 3 §4 | ☐ |
| 7 | Underserved-population equity pathways (rural, language barrier, no digital access) modeled as explicit nodes | Step 2 §5 | ☐ |
| 8 | Null output escalation pathways implemented and verified functional for all five trigger types | Step 3 §3 + Step 4 | ☐ |
| 9 | Jurisdictional compliance check completed for the deployment city | Step 1 (Candidate Cities) | ☐ |
| 10 | Rollback trigger and human-in-the-loop gate configured for live operation | Step 3 §4 + governance | ☐ |

Items 6 and 7 were the two pre-deployment resolutions flagged by the MOKG-PH review (Case #002-C). They are not optional.

---------------------------
## Illustrative Heatwave Scenario (Non-Normative)

An older adult living alone in a metropolitan area, with limited mobility, cardiovascular disease, and no functional
 air conditioning, is unlikely to act on generalized heat alerts alone. Under PAPO, institutional heat emergency policy
  is translated into personalized opportunities by integrating vulnerability profiles with real-time environmental 
  and resource signals.
The system identifies a nearby staffed cooling center, arranges accessible transportation, and coordinates community 
volunteer support under supervision. Aggregated feedback informs future responses for similarly vulnerable populations.

This scenario assumes resource availability. In a full simulation, the same individual might receive null if the cooling center is full, no transport is available, and volunteers are exhausted. That failure outcome is as informative as success.
________________________________________
This repository provides the CMDDS artifact for PAPO heatwave applications. Simulation implementations are intentionally 
left open and are expected to reside in forks or downstream projects.

## Related References
- **Springer Textbook:** Wu, M. (2026). *AI for Public Health*. Springer. ISBN 978-3032158710.
- **SSRN Preprint:** Wu, Min, *PAPO: A Policy-Aware Personalized Opportunity Framework for Heatwave Public Health Interventions* (February 08, 2026). Available at SSRN: https://ssrn.com/abstract=6198260
- **★ MOKG-PH Case Report:** Wu, M. (April 2026). *PAPO-Heatwave MOKG-PH Case Analysis Report* (Case #002-C). MOKG-PH framework analysis that triggered this v1.2 update; identifies five structural gaps in MOKG-PH v1.1 (resolved in MOKG-PH v1.2) and two pre-deployment resolutions for PAPO forks.

## Changelog
**v1.0** — Initial release; defines entities, inputs, logic, outputs, and temporal phases for PAPO–Heatwaves.

**v1.1** — Added simulation-specific modules: resource pools, null output failure mode, human-system handover, separated feedback loops, prioritization rules, equity metrics, bias injection, and explicit assumption/scope box.

**★ v1.2 (May 2026)** — Integrates findings from the MOKG-PH analytical review of PAPO–Heatwave (Case #002-C, April 2026):

1. **Bias injection elevated from Recommended to Required** for Complex cases (Step 2). Disparity delta must be measured against a governance-approved threshold before deployment.
2. **Human-system handover boundary requires explicit governance sign-off** before Stage 2 deployment authorization (Step 3 §4; assumption #4).
3. **Equity metric pre-selection elevated to a required governance action** before any simulation run (Step 4 Equity Metrics).
4. **Underserved-population equity pathways added as required entity nodes**: rural / geographically isolated, limited-English-proficiency, no-digital-access populations (Step 2 §5; assumption #7; Step 3 §5 strategic loop).
5. **Null output reframed as a required architectural element** of PAPO, not an optional fork-level extension (Step 4 assumption #2).
6. **Prioritization rule selection clarified as a normative governance decision** requiring sign-off (Step 4 Prioritization Rules).
7. **Simulation-First Protocol formalized** as a new Step 3.5 with seven required components for Complex cases.
8. **New Pre-Deployment Checklist** consolidating all gate requirements before live deployment.
9. **New simulation question category (Bias & Fairness)** added to Step 1 Core Simulation Questions.
10. **Equity sentinel added to candidate-city selection** (Step 1) to flag systematic exclusion of rural / less-resourced contexts.

All v1.1 content is preserved; v1.2 additions are marked with ★ throughout.
