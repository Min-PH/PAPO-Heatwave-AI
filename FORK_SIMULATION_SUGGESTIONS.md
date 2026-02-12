# Fork Simulation Suggestions
**Version:** 1.1 (Simulation-Ready Extensions)  
**Date:** 2026-02-12  

This repository is designed as a theory-bounded, non-predictive simulation. It serves as a thinking instrument for exploring conditional behaviors under controlled assumptions, not as a real-world mirror.

## Core Trade-off

This repository is designed as a **theory-bounded, non-predictive simulation**.  
It serves as a *thinking instrument* for exploring conditional behaviors under controlled assumptions — not as a real-world mirror.

| Thinking Instrument | Real-World Exploration |
|---------------------|------------------------|
| Tight boundaries, deliberate idealizations | Loose boundaries, high realism |
| Focus on mechanisms, comparison, theory testing | Focus on prediction, replication, operational use |
| Small, interpretable, fast | Large, data-heavy, harder to interpret |
| Results are comparative signals | Results are estimates or forecasts |


This repo intentionally prioritizes **clarity, interpretability, and structural transparency** over realism.

Forks that move toward real-world exploration must add substantial complexity and document all departures explicitly.

> **v1.1 Requirement:**  
> Even as a thinking instrument, every valid PAPO-Heatwaves simulation must implement the core required components defined in CMDDS Step 4. These are non-negotiable regardless of trade-off position.

---

## Idealizations

* Actors: simplified agents with limited state variables
* Policies: rule-based or deterministic levers
* Information: perfect or near-perfect information
* Time: discrete time steps

These choices are deliberate to focus on mechanisms, not realistic outcomes.

### v1.1 Clarification

The following are **not idealizations**, but required specifications correcting prior underspecification:

- Resource pools as exhaustible, location-aware objects  
- Explicit `NULL` output when no opportunity is feasible  
- Separated tactical and strategic feedback loops  
- Normative prioritization rules under scarcity  
- Defined equity metrics  

These are architectural commitments, not simplifications.

---

## Boundary Reductions

* External systems are excluded or held constant
* Feedback loops beyond scope are truncated
* Population and spatial heterogeneity may be aggregated

Results should not be extrapolated beyond these boundaries.

> **v1.1 Clarification:**  
> Explicit assumptions are listed in CMDDS Step 4 (Scope Box).  
> Simulations should stress-test these assumptions — not validate them.

Forks may relax boundaries but must document each change and its justification.

---

## Required Components for Any PAPO-Heatwaves Fork

Any fork claiming PAPO-Heatwaves compliance must include:

| Component | Requirement |
|------------|------------|
| Resource pools | Cooling centre slots, transport vehicles, volunteers — exhaustible, spatially located, replenished over time. |
| Feasibility failure | Opportunity engine outputs `NULL` when no resource is available or constraints cannot be met. Escalation pathways (waitlist, manual review) must be modeled. |
| Feedback separation | Tactical loop (minutes/hours) for real-time reallocation; strategic loop (months/years) for policy updates. Conflation is not permitted. |
| Prioritization rule | At least two rules from the enumerated set (clinical risk only, equity-weighted, random, easiest first, worst-off first) must be compared under scarcity. |
| Equity metric | At least one equity metric (equal allocation, equal outcomes, prioritarian, sufficientarian) must be defined before simulation and reported disaggregated by group. |

### Strongly Recommended

- **Bias injection:** Train opportunity ranker on historically biased data; compare with fairness-constrained version.
- **Failure mode injection:** Introduce sensor noise, policy conflict, or resource shock.

Forks omitting required components should not use the PAPO-Heatwaves name. They are derivative models inspired by PAPO, not implementations of the CMDDS.

---

## Forking Guidance

When extending this repository:

1. **Declare your trade-off position** (thinking instrument vs. real-world exploration) in your README.
2. Select simulation questions relevant to your city or community.
3. Implement all required components if claiming compliance.
4. If deviating, label your model as derivative and document differences.
5. Explicitly declare any new idealizations or boundary changes.
6. Use an `/assumptions/` directory for plain-language documentation.

Include:

- City or region modeled  
- Data sources (if any)  
- Encoded policy rules  
- Parameter values and justification  
- Deviations from core CMDDS logic  

Add complexity only to answer clear theoretical questions.  
Comparative results (e.g., “equity-weighted prioritization reduces disparity by X% vs. clinical risk only”) are the goal.  
Single-point forecasts are not.

Frame results as:

> “Under these assumptions, we observe…”

Not:

> “This policy will produce…”

---
## Relationship to the Main Repository

This repository is a **CMDDS (Conceptual Model Design Documentation for Simulation)** — not a codebase.

We do **not** accept pull requests that add simulation code.

Instead, we encourage you to:

- Fork this repository  
- Build your simulation in your own fork  
- Publish your fork publicly or privately  
- Cite or link back to this CMDDS  
- Share insights, lessons learned, or links to your fork via GitHub Issues  

---

## Final Principle

> “Now fork it, break it, and document what breaks.”

The value of this CMDDS lies not in its correctness, but in its clarity.

By making assumptions explicit and components required, we ensure that when you adapt the framework, you know exactly what you are changing — and why.

That awareness is the foundation of rigorous, equity-aware simulation.

---

## Changelog

### v1.0
- Initial fork guidance  
- Defined thinking instrument vs. real-world exploration  
- Specified idealizations and boundary reductions  
- Outlined general forking principles  

### v1.1
- Added required components table (resource pools, `NULL` output, feedback separation, prioritization rules, equity metrics)  
- Added bias injection and failure mode recommendations  
- Added explicit assumptions documentation requirement  
- Aligned with CMDDS v1.1 simulation requirements  
