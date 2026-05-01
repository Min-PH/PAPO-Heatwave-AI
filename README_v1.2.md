### PAPO–Heatwaves-AI (CMDDS for PAPO-Heatwaves) Readme File

# Readme: CMDDS — PAPO Heatwave Framework
## Conceptual Model Design Documentation for Simulation (CMDDS)
**Version:** 1.2  
**Date:** 2026-05-01  
**Author:** Min Wu  
**Affiliation:** Zilber College of Public Health, University of Wisconsin-Milwaukee  
**Contact / GitHub:** https://github.com/Min-PH/PAPO-Heatwave-AI

**Cite:** Min Wu. CMDDS for PAPO–Heatwave v1.2 – Conceptual Simulation Framework. Zenodo. DOI: 10.5281/zenodo.18637394

> **★ v1.2 update note (May 2026).** This version integrates findings from the MOKG-PH analytical review of PAPO–Heatwave (Case #002-C, April 2026). The review confirmed strong alignment with MOKG-PH principles in 8 of 10 design decisions and identified two pre-deployment resolutions plus several elevations from "recommended" to "required" status for Complex cases. All v1.1 content is preserved; v1.2 additions are marked with ★ throughout this README and the main CMDDS document.

## Overview
This repository contains the Conceptual Model Design Documentation for Simulation (CMDDS) for PAPO–Heatwaves — a policy-aware, opportunity-oriented framework for simulating heatwave response at the city or community level.

★ **v1.2 framing.** The CMDDS now serves a dual role: it remains a developer-facing simulation grammar, and it is also the Stage 1 knowledge-graph specification and Simulation-First Protocol artifact for PAPO under the MOKG-PH governance framework. Forks targeting operational deployment must satisfy the new Pre-Deployment Checklist before any real population is exposed to PAPO-driven recommendations.

Version 1.2 carries forward all v1.1 simulation requirements and adds the following Complex-case requirements derived from the MOKG-PH review:

* Exhaustible, location-aware resource pools (v1.1)
* Null output failure mode — ★ now framed as a required architectural element of PAPO, not an optional fork-level extension
* Separated tactical (real-time) and strategic (post-event) feedback loops (v1.1)
* Prioritization rules under scarcity — ★ rule selection clarified as a normative governance decision requiring sign-off
* Equity metrics — ★ pre-selection elevated to a required governance action before any simulation run
* ★ Bias injection — elevated from Recommended to Required for Complex cases; disparity delta must be measured against a governance-approved threshold
* ★ Underserved-population equity pathways (rural, language barrier, no digital access) — added as required entity nodes
* ★ Human-system handover boundary — explicit governance sign-off required before Stage 2 deployment authorization
* ★ Simulation-First Protocol (new Step 3.5) — seven required components for Complex cases
* ★ Pre-Deployment Checklist — consolidates all gate requirements before live deployment

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

*	A complete CMDDS artifact for PAPO–Heatwaves v1.2
*	Clear system purpose, boundaries, and explicitly listed assumptions
*	Non-negotiable translation logic from policy → personalized opportunity
*	Simulation-required components: resource pools, failure modes, feedback separation, prioritization rules, equity metrics, ★ bias injection, ★ underserved-population pathways
*	★ A formalized Simulation-First Protocol (7 components) for Complex-case pre-deployment review
*	★ A Pre-Deployment Checklist for forks targeting operational deployment
*	Simulation-ready questions and outputs
*	A clean conceptual "core" designed for reuse

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

Core logic must be preserved. Context-specific variables (demographics, resource locations, policy thresholds) change per fork.

________________________________________
## CMDDS Structure (v1.2)
This CMDDS is organized into four steps plus a new Simulation-First Protocol section:

### Step 1 — System Purpose & Simulation Questions
Defines answerable simulation questions, such as:

*	How quickly do policy-triggered opportunities reach vulnerable populations?
*	Where do capacity bottlenecks emerge under extreme heat?
*	How do timing and access constraints affect equity outcomes?
*	What happens when no feasible opportunity exists?
*	Which prioritization rule minimizes equity gaps under scarcity?
*	★ How do underserved populations (rural / isolated, language barrier, no digital access) fare relative to digitally reachable urban populations?
*	★ When historical data is biased, what is the disparity delta — and does a fairness constraint close it to a governance-approved threshold?

To reduce implementation difficulty, the framework supports small, modular simulation projects, rather than a single monolithic model.

### Step 2 — Conceptual Entities, Attributes, and States
Defines simulation entities including:

*	Individuals / households
*	Policy and institutional systems
*	Opportunity resources (cooling centers, transport, volunteers)
*	Environmental context
*	★ Underserved-population equity pathways (rural / isolated, limited-English-proficiency, no-digital-access) — required nodes

v1.1 Requirement: Resources must be modeled as exhaustible, location-aware pools with dynamic availability.

★ **v1.2 Requirement (elevated from v1.1 Recommendation):** Bias injection — train opportunity rankers on historically biased data, measure the disparity delta, apply a fairness constraint, and confirm the delta meets a governance-approved threshold before deployment.

### Step 3 — Policy-to-Feasible-Opportunity Logic
Defines the core translation mechanism:

*	policy triggers → eligibility rules
*	vulnerability + context → feasible micro-opportunities
*	If no feasible opportunity exists → output NULL (required architectural element)
*	Opportunity delivery under human-system handover — ★ authorization boundary must be specified per deployment **with explicit governance sign-off**
*	Two feedback loops (tactical + strategic) — must be separated
*	★ Strategic loop must include explicit pathways for revising eligibility when post-season data reveals systematic under-reach of underserved populations

This logic must be preserved across implementations, regardless of simulation method.

### ★ Step 3.5 — Simulation-First Protocol (NEW in v1.2)

Complex cases require a structured pre-deployment gate with seven required components:

1. Synthetic population scenarios (Pre- and During-Heatwave phases)
2. Prioritization rule comparison (≥2 rules)
3. Resource scarcity stress test
4. Equity metric pre-selection (governance-approved before run)
5. Timing sensitivity test (6h / 12h / 24h delays)
6. Bias injection test (disparity delta vs. governance threshold)
7. Failure mode / null output coverage (all five trigger types)

A fork that completes all seven and documents results in a public log entry has met the Complex-case pre-deployment gate. A fork that omits any component has not.

### Step 4 — Outputs, Interpretation, and Limits
Defines:

*  What simulation outputs mean — and what they do not.
*  Explicit assumptions (policy machine-readable, resources sufficient, data unbiased, etc.) — all are stress-test targets.
*  Prioritization rules (clinical risk only, equity weighted, random, easiest first, worst off first) — at least two must be compared. ★ Final rule selection requires governance sign-off.
*  Equity metrics (equal allocation, equal outcomes, prioritizing, sufficient) — ★ choose, document, and obtain governance approval **before** any simulation run.
*  Ethical boundaries, non-goals, and interpretation guidance are explicit.

## Required Components for a Valid PAPO Simulation

Any fork claiming to implement **PAPO–Heatwaves** must include the following components.  
★ marks components elevated or added in v1.2.

| Component            | Requirement |
|----------------------|------------|
| Resource pools       | Cooling center slots, transport vehicles, volunteers — exhaustible, spatially located, and replenished over time. |
| Null output failure mode | Opportunity engine must output `NULL` when no resource is available or constraints cannot be satisfied. ★ Null output is a required architectural element of PAPO, not an optional fork-level extension. Escalation pathways must be explicitly modeled for all five trigger types (resource exhaustion, geographic inaccessibility, policy conflict, non-response, cascading depletion). |
| Feedback separation  | Tactical loop (minutes/hours) for real-time reallocation; strategic loop (months/years) for policy updates. Conflation of loops is not permitted. |
| Prioritization rule  | At least two rules from the enumerated prioritization set must be compared under scarcity conditions. ★ Final rule selection is a normative governance decision requiring documented sign-off. |
| Equity metric        | At least one equity metric must be defined *before* simulation and reported in disaggregated form by group. ★ Selection is a required governance action before any run; defaulting to "no metric" is not permitted. |
| ★ Bias injection (Required for Complex cases) | Train the opportunity ranker on historically biased data; measure disparity delta; apply fairness constraint; confirm delta meets governance-approved threshold. Elevated from Recommended in v1.1. |
| ★ Underserved-population equity pathways | Rural / geographically isolated, limited-English-proficiency, and no-digital-access populations modeled as explicit entity nodes with non-digital delivery channels (voice, in-person, trusted community intermediary). |
| ★ Human-system handover boundary | Specified in writing per deployment, with explicit governance sign-off, before Stage 2 deployment authorization. Low-risk reversible actions may be automated; physical-safety actions require human authorization. |

---

### Strongly Recommended Enhancements

- **Failure mode injection:**  
  Introduce perturbations such as sensor noise, policy conflict, or sudden resource shocks.

- **Cross-context validation:**  
  ★ Where possible, pair an open-data-ready metro fork with a less-resourced or rural fork to offset systematic exclusion of resource-constrained contexts from validation.

> ★ **Note on bias injection:** Previously listed under "Strongly Recommended" in v1.1, bias injection has been elevated to a required component for any Complex-case deployment in v1.2. See the Required Components table above.

## Assumptions – Read Before Forking

This CMDDS deliberately simplifies several real-world complexities.  
Simulations should **stress-test these assumptions**, not validate them.

| Assumption | Why It Fails in Reality |
|------------|-------------------------|
| Policy is machine-readable | Policies often contain discretion, ambiguity, or inter-agency conflict. |
| A feasible opportunity always exists | Resources may be exhausted; geography or timing may preclude any viable intervention. ★ Null output is required, not optional. |
| Resources are sufficient | Scarcity is the norm; prioritization is unavoidable. |
| Human–system handover is resolvable | Authorization delays, rejections, and liability concerns are common. ★ Governance sign-off on the handover boundary is required before deployment. |
| Feedback occurs on a single timescale | Tactical and strategic decisions involve different actors and time horizons. |
| Data are unbiased | Historical service data often overrepresent populations that are easier to reach. ★ Bias injection testing is required for Complex cases. |
| ★ Underserved populations are reachable through standard channels | Rural, language-barrier, and no-digital-access populations are systematically under-reached unless explicit equity pathways are modeled. |

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
- ★ Explicit equity pathways for underserved populations
- ★ Documented human-system handover boundaries with governance sign-off

  ________________________________________
## ★ Pre-Deployment Checklist (NEW in v1.2)

Before any real population is exposed to PAPO-driven recommendations, the deployment fork must satisfy every item below. Full details are in the main CMDDS document.

| # | Requirement |
|---|---|
| 1 | Per-city parameterization of resource pools, population vulnerability, and policy constraints |
| 2 | All seven Simulation-First Protocol components run and documented |
| 3 | Bias injection performed; disparity delta measured against governance-approved threshold |
| 4 | Equity metric selected, documented, and approved before simulation run |
| 5 | Prioritization rule compared (≥2 rules) and deployment rule approved by governance |
| 6 | Human-system handover boundary specified in writing with governance sign-off |
| 7 | Underserved-population equity pathways modeled as explicit nodes |
| 8 | Null output escalation pathways implemented and verified for all five trigger types |
| 9 | Jurisdictional compliance check completed for the deployment city |
| 10 | Rollback trigger and human-in-the-loop gate configured for live operation |

Items 6 and 7 were the two pre-deployment resolutions flagged by the MOKG-PH review (Case #002-C). They are not optional.

________________________________________
## Suggested Starter Simulation Projects
Developers may choose to implement one focused component rather than the entire system:

*	Cooling center capacity stress test
*	Transportation delay and access modeling
*	Opportunity uptake vs. alert-only baselines
*	Equity impact comparison across neighborhoods
*	Policy timing sensitivity analysis
*	Bias audit: compare opportunity rates for car-owning vs. car-less groups
*	Prioritization rule comparison: clinical risk vs. equity weighted vs. random
*	★ Underserved-population reach analysis: compare opportunity rates across rural / language-barrier / no-digital-access populations vs. digitally reachable urban baseline
*	★ Disparity-delta measurement: trained ranker with and without fairness constraint

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

> ★ **Equity sentinel for city selection (v1.2).** Open-data-ready cities may overrepresent well-resourced urban contexts. Forks should flag — and where possible offset — the systematic exclusion of rural or less-resourced jurisdictions from validation.
________________________________________
## How to Use This Repository

1.	Read the full CMDDS (Steps 1–4 plus Step 3.5 Simulation-First Protocol) to understand the conceptual logic and required components.
2.	Fork the repository.
3.	Create a city-specific implementation:  
        PAPO–Heatwaves–YourCity
4.	Choose a simulation approach (ABM, SD, hybrid, digital twin, VR).
5.    Implement all required components: resource pools, NULL output (architectural), feedback separation, ≥2 prioritization rules, ≥1 equity metric, ★ bias injection, ★ underserved-population pathways, ★ documented human-system handover boundary.
6.    ★ For deployment-bound forks: run all seven Simulation-First Protocol components and complete the Pre-Deployment Checklist.
7.    Document assumptions and deviations clearly in your fork's README and in an "assumptions" file.
8.	Publish your results — link back to this CMDDS.

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
* ★ If the fork is intended for real-world pilot deployment (not exploratory simulation only), complete the Pre-Deployment Checklist and document the seven Simulation-First Protocol components publicly.

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
- **Springer Textbook:** Wu, M. (2026). *AI for Public Health*. Springer. ISBN 978-3032158710.
- **SSRN Preprint:** Wu, Min, *PAPO: A Policy-Aware Personalized Opportunity Framework for Heatwave Public Health Interventions* (February 08, 2026). Available at SSRN: https://ssrn.com/abstract=6198260
- **★ MOKG-PH Case Report:** Wu, M. (April 2026). *PAPO-Heatwave MOKG-PH Case Analysis Report* (Case #002-C). MOKG-PH framework analysis that triggered this v1.2 update; identifies five structural gaps in MOKG-PH v1.1 (resolved in MOKG-PH v1.2) and two pre-deployment resolutions for PAPO forks.

## Changelog
- **v1.0** — Initial release; defines entities, inputs, core logic, outputs, and temporal phases for PAPO–Heatwaves. Simulation-ready for developer adoption.
- **v1.1** — Added simulation-required components: resource pools, NULL output failure mode, human-system handover specification, separated feedback loops, prioritization rules, equity metrics, bias injection recommendation, and explicit assumption/scope box. Now forkable for immediate simulation development.
- **★ v1.2 (May 2026)** — Integrates findings from the MOKG-PH analytical review of PAPO–Heatwave (Case #002-C, April 2026):
    1. Bias injection elevated from Recommended to Required for Complex cases; disparity delta must meet governance-approved threshold.
    2. Human-system handover boundary requires explicit governance sign-off before Stage 2 deployment authorization.
    3. Equity metric pre-selection elevated to a required governance action before any simulation run.
    4. Underserved-population equity pathways added as required entity nodes (rural / isolated, limited-English-proficiency, no-digital-access).
    5. Null output reframed as a required architectural element of PAPO, not an optional fork-level extension.
    6. Prioritization rule selection clarified as a normative governance decision requiring sign-off.
    7. Simulation-First Protocol formalized as a new Step 3.5 with seven required components for Complex cases.
    8. New Pre-Deployment Checklist consolidating all gate requirements before live deployment.
    9. New simulation question category (Bias & Fairness) added to Step 1.
    10. Equity sentinel added to candidate-city selection to flag systematic exclusion of rural / less-resourced contexts.

All v1.1 content is preserved; v1.2 additions are marked with ★ throughout.
