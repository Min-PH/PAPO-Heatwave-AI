PAPO–Heatwaves-AI (CMDDS for PAPO-Heatwaves)

# CMDDS — PAPO Heatwave Framework
Conceptual Model Design Documentation for Simulation (CMDDS)
**Version:** 1.0  
**Date:** 2026-02-06  
**Author:** Min Wu  
**Affiliation:** Zilber College of Public Health, University of Wisconsin-Milwaukee  
**Contact / GitHub:** https://github.com/Min-PH/PAPO-Heatwave-AI


## Overview
This repository contains the Conceptual Model Design Documentation for Simulation (CMDDS) 
for PAPO–Heatwaves — a policy-aware, opportunity-oriented framework for simulating 
heatwave response at the city or community level.

The CMDDS specifies what should be simulated (purpose, entities, logic, and limits) 
without prescribing how to implement it. It is intentionally implementation-agnostic,
 enabling downstream developers to build:
•	agent-based simulations
•	system dynamics or hybrid models
•	digital twins of city heat-response systems
•	VR / immersive environments for training, planning, or public communication

Ongoing maintenance of this repository is minimal. Users are encouraged to fork this repo 
and implement simulations tailored to their own cities or use cases.
________________________________________
What This Repository Is (and Is Not)
This repository provides:
•	A complete CMDDS artifact for PAPO–Heatwaves
•	Clear system purpose, boundaries, and assumptions
•	Explicit translation logic from policy → personalized opportunity
•	Simulation-ready questions and outputs
•	A clean conceptual “core” designed for reuse

This repository does NOT provide:
•	Executable simulation code
•	City-specific parameter values
•	Weather forecasting or physiological heat models
•	Optimized or predictive outputs

Simulations built from this CMDDS are exploratory and comparative, not predictive.
________________________________________
Core Design Philosophy
PAPO–Heatwaves assumes that:
•	Heatwaves evolve faster than institutional decision cycles
•	Individuals face real constraints (mobility, access, cognition)
•	Policies only matter if they translate into feasible actions
•	Equity emerges from opportunity design, not alerts alone

The CMDDS separates core logic from local context:
Core logic stays the same. Context-specific variables change.
 PAPO–Heatwaves (core)
        ↓ fork
 PAPO–Heatwaves–YourCity
________________________________________
CMDDS Structure
This CMDDS is organized into four steps:

Step 1 — System Purpose & Simulation Questions
Defines answerable simulation questions, such as:
•	How quickly do policy-triggered opportunities reach vulnerable populations?
•	Where do capacity bottlenecks emerge under extreme heat?
•	How do timing and access constraints affect equity outcomes?
•	What breaks first: policy logic, resources, or delivery channels?

To reduce implementation difficulty, the framework supports small, modular simulation projects,
 rather than a single monolithic model.

Step 2 — Conceptual Entities, Attributes, and States
Defines simulation entities including:
•	Individuals / households
•	Policy and institutional systems
•	Opportunity resources (cooling centers, transport, volunteers)
•	Environmental context

Attributes are explicitly categorized as static, contextual, or dynamic.

Step 3 — Policy-to-Feasible-Opportunity Logic
Defines the core translation mechanism:
•	policy triggers → eligibility rules
•	vulnerability + context → feasible micro-opportunities
•	delivery under real-world constraints
•	feedback → state updates

This logic must be preserved across implementations, regardless of simulation method.

Step 4 — Outputs, Interpretation, and Limits
Defines what simulation outputs mean — and what they do not.
Ethical boundaries, non-goals, and interpretation guidance are explicit.
________________________________________
Suggested Starter Simulation Projects
Developers may choose to implement one focused component rather than the entire system:
•	Cooling center capacity stress test
•	Transportation delay and access modeling
•	Opportunity uptake vs. alert-only baselines
•	Equity impact comparison across neighborhoods
•	Policy timing sensitivity analysis

Each can be implemented independently.
________________________________________
Candidate Cities (Data-Ready, Heat-Relevant)
This framework is well suited for cities that are:
•	regularly exposed to extreme heat
•	data-rich at city or neighborhood level
•	actively engaged in heat preparedness planning

Illustrative (non-exhaustive) examples:
•	Phoenix
•	Austin
•	Houston
•	Los Angeles
•	Miami
•	Paris
•	Madrid
•	Singapore
•	Cary (NC)

Forks may replace these with any local context.
________________________________________
How to Use This Repository
1.	Read the CMDDS to understand the conceptual logic
2.	Fork the repository
3.	Create a city-specific implementation:
4.	PAPO–Heatwaves–YourCity
5.	Choose a simulation approach (ABM, SD, hybrid, digital twin, VR)
6.	Document assumptions and deviations clearly

Pull requests adding code implementations are not expected; links to downstream forks
 or example implementations are welcome.
________________________________________
Background and Conceptual Origins (Optional Reading)
The PAPO framework and its application to heatwaves are described in:
•	A Springer textbook chapter (DOI)
•	An SSRN preprint (link)

This repository provides a simulation-oriented CMDDS, not a reproduction of those publications.
No prior reading is required to use or extend this work.
________________________________________
License and Attribution
Please cite the PAPO framework when publishing derived simulations or analyses.
See LICENSE for details.

## Related References
- **Springer Textbook:** Min Wu. *AI for Public Health: PAPO–Heatwaves Chapter.* Springer, 2026. DOI: [Insert DOI]  
- **SSRN Preprint:** [Insert Link]  


## Changelog
- **v1.0** — Initial release; defines entities, inputs, core logic, outputs, and temporal phases for PAPO–Heatwaves. Simulation-ready for developer adoption.

