# Scenario: Stewardship Obligations

> **Document status: Canonical scenario.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Index: [README.md](README.md).

---

## Scenario 1 — The garage door after the threshold

### What the household experiences

At 10:15 PM, the garage door is still open. The home closes it and says so.

### What each responsibility does

| Step | Responsibility | Statement |
|---|---|---|
| 1 | **Truth** | The garage door is open, and the current time is after 10 PM |
| 2 | **Stewardship** | The home's security-care obligation is unmet |
| 3 | **Operational Trust** | Automatic closing is permitted at Autonomous level for this household |
| 4 | **Concierge** | Close the door, notify, and explain |

> **Stewardship never closes the door. Stewardship states that the obligation is unmet.**

This is the separation that keeps the framework coherent. Four responsibilities, four different
statements, one outcome.

### What the home can say afterwards

> "I closed the garage door at 10:15 because it's set to be secured after 10, and you've allowed me to
> close it on my own."

---

## Scenario 2 — The same condition, a different policy

The same household, configured differently. Automatic closing requires confirmation.

| Step | Responsibility | Action |
|---|---|---|
| 1–2 | Truth, Stewardship | Identical to Scenario 1 |
| 3 | Operational Trust | `permitted_with_confirmation` |
| 4 | Concierge | Asks: "The garage door is still open. Shall I close it?" |

**The facts did not change. The obligation did not change. Only the authority changed.** This is why
Operational Trust must be a separate responsibility: the same condition must be able to produce
different behavior without rewriting the model of the home.

---

## Scenario 3 — The piano

### What the household experiences

The Music Room humidity drops to 31%. The humidifier turns on, and the caretaker is notified.

### What each responsibility does

| Step | Responsibility | Statement |
|---|---|---|
| 1 | **Foundation asset model** | The piano requires 40–60% relative humidity — a declared property of the thing |
| 2 | **Room Configuration** | The Music Room humidity sensor is an eligible contributor |
| 3 | **Truth** | The Music Room is at 31% relative humidity, confidence high, 1 of 1 contributor |
| 4 | **Stewardship** | The piano's preservation obligation is unmet; significance is high — irreplaceable |
| 5 | **Operational Trust** | Humidifier control is permitted autonomously; caretaker notification requires no confirmation |
| 6 | **Concierge** | Raise humidity, notify the caretaker, and explain |

### The distinction that must not collapse

| Question | Owner |
|---|---|
| What is this thing, and what does it require? | Foundation asset model |
| Is its environment currently within limits? | Truth |
| Does it matter, and is the obligation met? | Stewardship |
| Am I allowed to do something about it? | Operational Trust |
| What should happen now? | Concierge |

**The asset model and Stewardship cooperate without becoming the same thing.**

---

## Scenario 4 — Absence of evidence is not compliance

The Music Room humidity sensor fails.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Truth | Publishes Music Room humidity as `unknown`; does not retain the last reading as current |
| 2 | Stewardship | Obligation state is **`unknown`**, not `met` |
| 3 | Concierge | Reports that the piano's preservation obligation can no longer be verified |

> "I can't tell whether the Music Room humidity is in range — the sensor isn't reporting. The piano's
> preservation check is unverified."

**An obligation whose governing fact is unknown is `unknown`, never `met`.** A silent sensor must never
look like a satisfied obligation.

---

## Scenario 5 — Pet medication

### What the household experiences

At 8 AM, the home reminds David that the dog's medication is due. David is away. At 8:30 the home tells
Tom.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Stewardship | The pet medication obligation is `due`; accountability is David; significance is health |
| 2 | Truth | David is not present in the Home |
| 3 | Stewardship | Escalation **intent** applies after the grace period |
| 4 | Operational Trust | Health escalation to another adult household member is permitted |
| 5 | Concierge | Escalates to Tom, and explains |

**Stewardship supplied the escalation intent. Concierge performed the escalation.** Stewardship does not
send notifications.

The **Pet is not a Person.** It has its own obligations, its own accountability, and its own significance.

---

## Scenario 6 — Conflicting obligations

The rare-book collection requires humidity below 45%. The piano requires at least 40%. A heatwave pushes
the Music Room to a point where satisfying one degrades the other.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Truth | Reports the current conditions with confidence and provenance |
| 2 | Stewardship | Reports **both** obligations, with their significance — and **surfaces the conflict** |
| 3 | Stewardship | Does **not** silently prefer one |
| 4 | Operational Trust | Establishes whether Concierge may act unilaterally on a significance-weighted conflict |
| 5 | Concierge | Surfaces the trade-off to the household and explains what each choice costs |

> "The books and the piano want different humidity right now. I can favour one or the other — the books
> are more sensitive to being over-humidified, the piano to being under-humidified."

**Conflicting obligations are surfaced, not silently resolved.**

---

## Scenario 7 — A repeatedly unmet obligation

The HVAC filter obligation has been overdue for three months across four reminders.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Stewardship | State `overdue`; escalation intent increases per policy |
| 2 | Stewardship | **The pattern itself becomes reportable** |
| 3 | Concierge | Raises it differently — not as a fifth identical reminder |

A home that repeats the same ignored reminder indefinitely is not behaving well. Stewardship records the
pattern; Concierge changes its approach.

---

## Rules demonstrated

1. Stewardship owns the obligation; Concierge owns the action and the notification.
2. The same condition plus a different policy produces different behavior.
3. The asset model and Stewardship cooperate without collapsing.
4. `unknown` obligation state is never `met`.
5. Escalation intent is Stewardship's; escalation is Concierge's.
6. Conflicting obligations are surfaced, never silently resolved.
7. Significance drives prioritisation and escalation, and is recorded with provenance.

---

## Related documents

- [../models/stewardship.md](../models/stewardship.md)
- [../models/asset.md](../models/asset.md)
- [../contracts/stewardship-contract.md](../contracts/stewardship-contract.md)
- [../assessment/assessment-to-platform.md](../assessment/assessment-to-platform.md)
