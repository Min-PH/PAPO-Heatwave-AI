# Governance FAQ — PAPO–Heatwaves

**Version:** 1.0
**Applies to:** CMDDS_PAPO_v1.2-heatwave.md and later

This file exists so you don't have to read the full CMDDS just to figure out whether anything in it applies to you. It's linked from the README on purpose — it's meant to be found, not stumbled on.

---

### "I'm forking this to explore, learn, or run a class/thesis simulation. Do I need to do anything?"

No. Fork it, run it, break it. Nothing in the Pre-Deployment Checklist applies to exploratory or research use — that's explicitly what the CMDDS calls "the trade-off: thinking instrument vs. real-world exploration," and thinking-instrument use has no gate.

### "Does the EU AI Act apply to my fork?"

Probably not, if you're staying in research/simulation — Article 2 and Recital 29 generally carve out systems developed and used solely for R&D, testing, or simulation before being placed on the market. But that's a general statement about the law, not a legal opinion about your specific fork, and it's not something a README disclaimer can settle for you. If your use is genuinely exploratory, you're very likely fine. If you're not sure which category you're in, see the next question.

### "How do I know if I've crossed from 'research' into 'deployment'?"

Rule of thumb: if PAPO's outputs are informing decisions about resources or contact for real people — even a small pilot, even "just this one cooling center" — you've crossed the line, regardless of what you call the project. That's when the Pre-Deployment Checklist in the main CMDDS applies (governance-approved equity metric, bias injection with a disparity-delta threshold, a documented human-authorization boundary, etc.). It exists because this framework touches vulnerability classification and resource allocation for real people during real heat events — the checklist isn't paperwork for its own sake, it's the minimum content that let the MOKG-PH review (internal case analysis, unpublished) sign off on the framework's other required components.

### "This all sounds like a lot. Can I just skip it if I'm 'basically' doing research?"

If you're not exposing a real population to PAPO-driven recommendations, yes, skip it — nothing here requires you to. If you are, no amount of framing changes that, and skipping it isn't something this repo (or I) can wave through for you. That determination is on you and, where relevant, your institution's own review process and legal counsel — not on a disclaimer in a GitHub file.

### "Where do I go next?"

- Research/simulation only → nothing further needed, use the CMDDS as-is.
- Considering real-world use → read the Pre-Deployment Checklist and Simulation-First Protocol (Step 3.5) in `CMDDS_PAPO_v1.2-heatwave.md`, and get your own legal/compliance read on your jurisdiction. This repo gives you the design requirements, not a compliance sign-off.

---

*This FAQ is a plain-language index into the CMDDS, not a substitute for it or for legal advice. If the two ever disagree, the CMDDS governs.*
