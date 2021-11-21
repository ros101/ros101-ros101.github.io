---
layout: notes
---
# The case of 737 MAX - Reflections

[The development of MCAS was rushed](./incident), without proper specifications, documentation, or testing, and it was part of a bigger process suffering delays and economic pressure.

It made me feel uneasy because that context is extremely familiar. I worked on several projects in the same conditions and, although there were never lives at stake, incidents happened. The post-mortem analysis always points the finger to a specific feature in the software, and, sometimes, to a missing control in the QA phases.

Risks of incidents could be mitigated with a risk assessment analysis during the development. The process consists of risk discovery followed by a mitigation strategy. It must be iterated until the risk is considered negligible.

In the case 737 MAX:

| Risk | Mitigation|
|------|-----------|
| a faulty sensor could give incorrect input to MCAS | using second sensors adds redundancy |
| above + also the second sensor gives incorrect input to MCAS | if the reading of the sensor differs by more than a safety factor, MCAS should be disabled |
| above + sensors agree within the safety factor | pilots' commands outweighs MCAS' |
| above + due to a malfunction MCAS command outweighs pilots' | mitigation: pilots can disable MCAS with a trigger |
| above + the trigger does not work | none, the risk is negligible.|

When designing new software, I should always include a risk discovery step to add safeguards against incidents. I should also make stakeholders aware of hidden risks.
