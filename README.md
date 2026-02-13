### PAPO–Heatwaves-AI (CMDDS for PAPO-Heatwaves) Readme File

# Readme: CMDDS — PAPO Heatwave Framework
## Conceptual Model Design Documentation for Simulation (CMDDS)
**Version:** 1.1  
**Date:** 2026-02-12  
**Author:** Min Wu  
**Affiliation:** Zilber College of Public Health, University of Wisconsin-Milwaukee  
**Contact / GitHub:** https://github.com/Min-PH/PAPO-Heatwave-AI

## Overview
This repository contains the Conceptual Model Design Documentation for Simulation (CMDDS) for PAPO–Heatwaves — a policy-aware, opportunity-oriented framework for simulating heatwave response at the city or community level.

Version 1.1 adds explicit simulation requirements derived from stress testing the original conceptual framework. It now defines what every simulation must implement to be considered a valid PAPO extension, including:
* Exhaustible, location aware resource pools
* Null output failure mode (no feasible opportunity → escalation)
* Separated tactical (real time) and strategic (post event) feedback loops
* Prioritization rules under scarcity
* Equity metrics and bias injection recommendations

The CMDDS specifies what should be simulated (purpose, entities, logic, and limits) without prescribing how to implement it. It is intentionally implementation-agnostic, enabling downstream developers to build:

*	agent-based simulations
*	system dynamics or hybrid models
*	digital twins of city heat-response systems
*	VR / immersive environments for training, planning, or public communication

This repository is a conceptual specification, not a runnable implementation. CMDDS is meant to be forked, adapted, and instantiated across different local contexts, simulation paradigms, and technical stacks. Developers should treat this repository as a scaffolding for design, not as executable code or a fully parameterized model. Early forks are expected to diverge, experiment, and even contradict one another; such variation is intentional and part of the design philosophy.

Ongoing maintenance of this repository is minimal. Users are encouraged to fork this repo and implement simulations tailored to their own cities or use cases.
________________________________________
## What This Repository Is (and Is Not)
This repository provides:

*	A complete CMDDS artifact for PAPO–Heatwaves V1.1
*	Clear system purpose, boundaries, and explicitly listed assumptions
*	Non negotiable translation logic from policy → personalized opportunity
*	Simulation required components: resource pools, failure modes, feedback separation, prioritization rules, equity metrics
*	Simulation-ready questions and outputs
*	A clean conceptual “core” designed for reuse

## This repository does NOT provide:

*	Executable simulation code
*	City-specific parameter values
*	Weather forecasting or physiological heat models
*	Optimized or predictive outputs

Simulations built from this CMDDS are exploratory and comparative, not predictive.
________________________________________
## Core Design Philosophy
PAPO–Heatwaves assumes that:

*	Heatwaves evolve faster than institutional decision cycles
*	Individuals face real constraints (mobility, access, cognition)
*	Policies only matter if they translate into feasible actions
*	Equity emerges from opportunity design, not alerts alone

The CMDDS separates core logic from local context:
Core logic stays the same. Context-specific variables change.


PAPO–Heatwaves (core)  
      ↓ fork  
PAPO–Heatwaves–YourCity

Core logic must be preserved. Context specific variables (demographics, resource locations, policy thresholds) change per fork.
  
________________________________________
## CMDDS Structure (v1.1)
This CMDDS is organized into four steps:

### Step 1 — System Purpose & Simulation Questions
Defines answerable simulation questions, such as:

*	How quickly do policy-triggered opportunities reach vulnerable populations?
*	Where do capacity bottlenecks emerge under extreme heat?
*	How do timing and access constraints affect equity outcomes?
*	What happens when no feasible opportunity exists?
*	Which prioritization rule minimizes equity gaps under scarcity?

To reduce implementation difficulty, the framework supports small, modular simulation projects, rather than a single monolithic model.

### Step 2 — Conceptual Entities, Attributes, and States
Defines simulation entities including:

*	Individuals / households
*	Policy and institutional systems
*	Opportunity resources (cooling centers, transport, volunteers)
*	Environmental context

v1.1 Requirement: Resources must be modeled as exhaustible, location aware pools with dynamic availability.
v1.1 Recommendation: Inject historical bias into opportunity ranking to test equity robustness.

### Step 3 — Policy-to-Feasible-Opportunity Logic
Defines the core translation mechanism:

*	policy triggers → eligibility rules
*	vulnerability + context → feasible micro-opportunities
*	If no feasible opportunity exists → output NULL (required)
*	Opportunity delivery under human system handover (authorization boundaries must be defined)
*	Two feedback loops (tactical + strategic) – must be separated

This logic must be preserved across implementations, regardless of simulation method.

### Step 4 — Outputs, Interpretation, and Limits
Defines:

*  What simulation outputs mean — and what they do not.
*  Explicit assumptions (policy machine readable, resources sufficient, data unbiased, etc.) — all are stress test targets
*  Prioritization rules (clinical risk only, equity weighted, random, easiest first, worst off first) — at least two must be compared
*  Equity metrics (equal allocation, equal outcomes, prioritizing, sufficient) — choose and report one
*  Ethical boundaries, non-goals, and interpretation guidance are explicit.

## Required Components for a Valid PAPO Simulation

Any fork claiming to implement **PAPO–Heatwaves** must include the following components:

| Component            | Requirement |
|----------------------|------------|
| Resource pools       | Cooling center slots, transport vehicles, volunteers — exhaustible, spatially located, and replenished over time. |
| Feasibility failure  | Opportunity engine must output `NULL` when no resource is available or constraints cannot be satisfied. Escalation pathways (e.g., waitlist, manual review) must be explicitly modeled. |
| Feedback separation  | Tactical loop (minutes/hours) for real-time reallocation; strategic loop (months/years) for policy updates. Conflation of loops is not permitted. |
| Prioritization rule  | At least two rules from the enumerated prioritization set must be compared under scarcity conditions. |
| Equity metric        | At least one equity metric must be defined *before* simulation and reported in disaggregated form by group. |

---

### Strongly Recommended Enhancements

- **Bias injection:**  
  Train the opportunity ranker on historically biased data and compare with a fairness-constrained version.

- **Failure mode injection:**  
  Introduce perturbations such as sensor noise, policy conflict, or sudden resource shocks.


## Assumptions – Read Before Forking

This CMDDS deliberately simplifies several real-world complexities.  
Simulations should **stress-test these assumptions**, not validate them.

| Assumption | Why It Fails in Reality |
|------------|-------------------------|
| Policy is machine-readable | Policies often contain discretion, ambiguity, or inter-agency conflict. |
| A feasible opportunity always exists | Resources may be exhausted; geography or timing may preclude any viable intervention. |
| Resources are sufficient | Scarcity is the norm; prioritization is unavoidable. |
| Human–system handover is resolvable | Authorization delays, rejections, and liability concerns are common. |
| Feedback occurs on a single timescale | Tactical and strategic decisions involve different actors and time horizons. |
| Data are unbiased | Historical service data often overrepresent populations that are easier to reach. |

---

> ⚠️ **Important:**  
> Failure to model these assumptions will produce optimistic, non-generalizable results.

---

### Design Philosophy

We publish this CMDDS as a **shared grammar**, not a finished architecture.  
Local forks are expected to extend the model with:

- Explicit triage and prioritization rules  
- Bias auditing and mitigation strategies  
- Transparent allocation and decision logic

  ________________________________________
## Suggested Starter Simulation Projects
Developers may choose to implement one focused component rather than the entire system:

*	Cooling center capacity stress test
*	Transportation delay and access modeling
*	Opportunity uptake vs. alert-only baselines
*	Equity impact comparison across neighborhoods
*	Policy timing sensitivity analysis
*	Bias audit: compare opportunity rates for car owning vs. car less groups
*	Prioritization rule comparison: clinical risk vs. equity weighted vs. random

Each can be implemented independently.
________________________________________
## Candidate Cities (Data-Ready, Heat-Relevant)
This framework is well suited for cities that are:

*	regularly exposed to extreme heat
*	data-rich at city or neighborhood level
*	actively engaged in heat preparedness planning

###  Illustrative (non-exhaustive) examples:

*	Phoenix
*	Austin
*	Houston
*	Los Angeles
*	Miami
*	Paris
*	Madrid
*	Singapore
*	Cary (NC)

Forks may replace these with any local context.
________________________________________
## How to Use This Repository

1.	Read the full CMDDS (Steps 1–4) to understand the conceptual logic and required components.
2.	Fork the repository
3.	Create a city-specific implementation:
           PAPO–Heatwaves–YourCity
4.	Choose a simulation approach (ABM, SD, hybrid, digital twin, VR)
5.    Implement all required components (resource pools, NULL output, feedback separation, ≥2 prioritization rules, ≥1 equity metric).
6.    Document assumptions and deviations clearly in your fork’s README and in an "assumptions" file.
7.	Publish your results – link back to this CMDDS.
   
Pull requests adding code implementations are not expected; links to downstream forks or example implementations are welcome.

----------------------------
## After You Fork This Repo
If you fork or extend this repository:

* First decide which side of the trade-off you are on: thinking instrument vs. real-world exploration.
* This repo is designed as a theory-bounded, non-predictive simulation.
* Consider your local context and urgent needs to select simulation questions that are relevant to your city or community.
* Do not add realism by default; add complexity only to test a clear theoretical question.
* Explicitly declare any new idealizations or boundary changes you introduce.
* Document the context and assumptions of your fork so others can understand your choices.
* Do not interpret outputs as real-world predictions or policy recommendations.
* Use forks to explore scenario comparisons, structural questions, or policy mechanisms under controlled assumptions.

Read this before extending: see FORK_SIMULATION_SUGGESTIONS.md for full guidance on trade-offs, idealizations, and boundary reductions.
________________________________________
## Example Implementations (maintained by contributors)

This section links to independent simulation projects inspired by the CMDDS framework and maintained by their respective contributors (e.g., PAPO-Heatwaves-YourCity).
If you develop a simulation based on this framework and would like it referenced here, please feel free to reach out.

--------------------------------
## License and Attribution
Please cite the PAPO framework when publishing derived simulations or analyses.
See LICENSE for details.

## Related References
- **Springer Textbook:** Wu, M. (2026). AI for Public Health. Springer. Forthcoming (April 2026). ISBN 978-3032158710.
- **SSRN Preprint:** Wu, Min, PAPO: A Policy-Aware Personalized Opportunity Framework for Heatwave Public Health Interventions (February 08, 2026). Available at SSRN: https://ssrn.com/abstract=6198260 

## Changelog
- **v1.0** — Initial release; defines entities, inputs, core logic, outputs, and temporal phases for PAPO–Heatwaves. Simulation-ready for developer adoption.
- **v1.1** — Added simulation required components: resource pools, NULL output failure mode, human system handover specification, separated feedback loops, prioritization rules, equity metrics, bias injection recommendation, and explicit assumption/scope box. Now forkable for immediate simulation development.










