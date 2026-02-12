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

## Boundary Reductions

* External systems are excluded or held constant
* Feedback loops beyond scope are truncated
* Population and spatial heterogeneity may be aggregated

Results should not be extrapolated beyond these boundaries.

## Forking Guidance
When forking or extending this repository:

* Decide which side of the trade-off your fork targets: thinking instrument vs. real-world exploration.
* Consider your local context and urgent needs to select simulation questions that matter for your city or community.
* Explicitly declare any new idealizations or boundary changes you introduce.
* Document the context and assumptions of your fork so others can understand your choices.
* Add complexity only to test clear theoretical questions.
* Focus on scenario comparisons, structural questions, or policy mechanisms under controlled assumptions.
* Do not treat outputs as predictions or policy recommendations.

By following these suggestions, forks can remain aligned with the main repository while enabling meaningful, context-aware exploration of the model.
