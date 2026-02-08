# CMDDS — PAPO Heatwave Framework
## Conceptual Model Design Documentation for Simulation (CMDDS)
**Version:** 1.0  
**Date:** 2026-02-06  
**Author:** Min Wu  
**Affiliation:** Zilber College of Public Health, University of Wisconsin-Milwaukee  
**Contact / GitHub:** https://github.com/Min-PH/PAPO-Heatwave-AI

## Overview
This document provides a developer-facing CMDDS for the Policy-Aware Personalized Opportunity (PAPO) 
framework applied to heatwave response. It is written for AI developers, data scientists, and simulation 
engineers who want to prototype, simulate, or extend PAPO in real cities.
The CMDDS defines what to simulate and why, while deliberately leaving how to implement (code, parameters, platforms) open. 
This makes it suitable for agent-based models, system dynamics, discrete-event simulation, digital twins, 
and VR-supported decision environments.

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
#### 4.	System Stress & Capacity
 -	Where do bottlenecks emerge under extreme heat scenarios?
 -	Which resources saturate first (cooling centers, transport, volunteers)?
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

Output: feasible, individualized opportunity candidates.

#### 4. Opportunity Delivery and Escalation

*	Opportunities are delivered via appropriate channels (e.g., text, voice, app, human outreach).
*	Delivery failures or non-response may trigger escalation pathways (e.g., in-person checks).
*	Human supervision and accountability are assumed for escalated actions.

Output: delivered opportunities and delivery status updates.

#### 5. Feedback and State Update

*	Uptake, non-uptake, delays, and resource utilization are recorded.
*	System states are updated for individuals, resources, and policy context.
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
## CMDDS Step 4 — Simulation Outputs, Interpretation, and Limits

This step defines what simulation outputs represent, how they should be interpreted, and the boundaries within which results are valid.

### Outputs of Interest
Simulations derived from this CMDDS may examine:

*	Opportunity uptake, timing, and non-uptake
*	Missed, delayed, or infeasible interventions
*	Resource utilization, saturation, and bottlenecks
*	Differential impacts across vulnerability groups or locations
*	Sensitivity to timing, capacity, access, and policy triggers

Outputs may be generated at individual, neighborhood, or system levels.

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

All extensions should clearly document assumptions and deviations from this CMDDS.

This step ensures that simulation results are interpretable, comparable, and ethically bounded, while remaining
 flexible for diverse implementation approaches.

---------------------------
## Illustrative Heatwave Scenario (Non-Normative)

An older adult living alone in a metropolitan area, with limited mobility, cardiovascular disease, and no functional
 air conditioning, is unlikely to act on generalized heat alerts alone. Under PAPO, institutional heat emergency policy
  is translated into personalized opportunities by integrating vulnerability profiles with real-time environmental 
  and resource signals.
The system identifies a nearby staffed cooling center, arranges accessible transportation, and coordinates community 
volunteer support under supervision. Aggregated feedback informs future responses for similarly vulnerable populations.
________________________________________
This repository provides the CMDDS artifact for PAPO heatwave applications. Simulation implementations are intentionally 
left open and are expected to reside in forks or downstream projects.

## Related References
- **Springer Textbook:** Min Wu. *AI for Public Health: PAPO–Heatwaves Chapter.* Springer, 2026. DOI: [Insert DOI]  
- **SSRN Preprint:** [Insert Link]  

## Changelog
v1.0 — Initial release; defines entities, inputs, logic, outputs, and temporal phases for PAPO–Heatwaves.


