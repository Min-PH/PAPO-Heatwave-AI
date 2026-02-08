Fork Simulation Suggestions
This repository is designed as a theory-bounded, non-predictive simulation. It serves as a thinking instrument for exploring conditional behaviors under controlled assumptions, not as a real-world mirror.
Core Trade-off
Thinking Instrument vs. Real-World Exploration
• Simulations with tight boundaries and idealizations are useful for reasoning, comparison, and theory testing.
• Simulations that try to mirror reality quickly become large, data-heavy, and hard to interpret.
• This repo intentionally prioritizes clarity, interpretability, and structure over realism.
Idealizations
• Actors: simplified agents with limited state variables
• Policies: rule-based or deterministic levers
• Information: perfect or near-perfect information
• Time: discrete time steps
These choices are deliberate to focus on mechanisms, not realistic outcomes.
Boundary Reductions
• External systems are excluded or held constant
• Feedback loops beyond scope are truncated
• Population and spatial heterogeneity may be aggregated
Results should not be extrapolated beyond these boundaries.
Forking Guidance
When forking or extending this repository:
• Decide which side of the trade-off your fork targets: thinking instrument vs. real-world exploration.
• Consider your local context and urgent needs to select simulation questions that matter for your city or community.
• Explicitly declare any new idealizations or boundary changes you introduce.
• Document the context and assumptions of your fork so others can understand your choices.
• Add complexity only to test clear theoretical questions.
• Focus on scenario comparisons, structural questions, or policy mechanisms under controlled assumptions.
• Do not treat outputs as predictions or policy recommendations.
By following these suggestions, forks can remain aligned with the main repository while enabling meaningful, context-aware exploration of the model.