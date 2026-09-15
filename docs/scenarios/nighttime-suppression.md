# Scenario: Nighttime Suppression

> **Document status: Canonical scenario.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Index: [README.md](README.md).

---

## Scenario 1 — Good Night in the Primary Bedroom

### What the household experiences

David says, "Good night," in the Primary Bedroom. The lights fade, the shades close, the doors lock, and
the house goes quiet.

For the rest of the night, the Primary Bedroom behaves differently.

### What each responsibility does

| Step | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves Room Context → Primary Bedroom |
| 2 | Identity | Asserts David, identity_confidence_band: Very High |
| 3 | Operational Trust | Confirms David may set Nighttime mode for this Room |
| 4 | Concierge | Executes the routine through governed interfaces |
| 5 | Truth | Establishes the fact: **the Primary Bedroom is in Nighttime mode** |
| 6 | Operational Trust | Nighttime restrictions now apply to this Room |

**Note the separation.** Concierge ran the routine. Truth holds the resulting mode as a fact. Operational
Trust interprets that fact as a restriction. The mode is not a Concierge variable.

---

## Scenario 2 — Music does not arrive

Tom walks into the Primary Bedroom with Follow-Me active. The music does not follow, and the home does
not ask.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Truth | The Primary Bedroom is in Nighttime mode |
| 2 | Continuity | Transfer intent present; eligibility evaluated |
| 3 | Operational Trust | Nighttime prohibits incoming media **and** prohibits interruption |
| 4 | Concierge | Takes no action, and records a non-action trace |

```yaml
action_taken: none
action_suppressed: media.transfer
suppression_reason: destination_room_mode_prohibits_incoming_media
alternative_considered: ask_before_transfer (blocked by nighttime interruption policy)
```

> "I did not move the music into the Primary Bedroom because the room is in Nighttime mode, and
> Nighttime mode does not allow music to arrive on its own. I also did not ask, because Nighttime mode
> does not allow me to interrupt."

**Suppression is a deliberate outcome, not a failure.** The session remains active where it was.

---

## Scenario 3 — A reminder waits

Stewardship reports that a filter-replacement obligation became due at 11 PM.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Stewardship | The obligation is `due`; significance is routine |
| 2 | Truth | The Primary Bedroom is in Nighttime mode; the Home is in quiet hours |
| 3 | Operational Trust | Routine notifications are suppressed during quiet hours |
| 4 | Concierge | **Defers** the notification to the morning, and records the deferral |

**Stewardship owns the obligation. It does not own the notification.** Stewardship did not decide to
wait; Concierge did, under Operational Trust policy.

---

## Scenario 4 — A safety condition does not wait

At 2 AM, a water-leak sensor reports.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Truth | A leak is detected in the Utility area |
| 2 | Stewardship | The safety obligation is unmet; significance is high |
| 3 | Operational Trust | Nighttime suppression **does not apply** to safety-critical escalation |
| 4 | Concierge | Wakes the household, escalating through the permitted channel |

**Suppression policy is scoped by experience class.** Media may be suppressed while care escalations are
not. The ceiling rule restricts what is permitted; it does not silence what must be heard.

---

## Scenario 5 — The rest of the home is unaffected

David is asleep in the Primary Bedroom. Tom is awake in the Den, listening to music at normal volume.

Nothing about Nighttime mode in the Primary Bedroom restricts the Den.

**Room-scoped policy applies to the Room.** A Room mode is not a Home mode, and the two must not be
conflated. If the household wants a whole-home quiet period, that is a Home-scoped policy — and where
both apply, the most restrictive sets the ceiling.

---

## Scenario 6 — The mode cannot be established

The Primary Bedroom's presence and mode evidence is unavailable after a restart.

| Step | Responsibility | Action |
|---|---|---|
| 1 | Truth | Publishes the Room mode as `unknown`; does not retain the last value as current |
| 2 | Operational Trust | `unknown` is **not** permission; returns `undecidable` for incoming media |
| 3 | Concierge | Does not transfer; does not interrupt; records the reason |

> "I couldn't tell what mode the Primary Bedroom is in, so I left the music where it was."

**Unknown is never treated as false, and never treated as permission.** Both Truth and Operational Trust
fail closed.

---

## Rules demonstrated

1. A Room mode is a **Truth fact**, not a Concierge variable.
2. Restriction is interpreted by **Operational Trust**, not by whoever set the mode.
3. Suppression is a decision, and is traced.
4. Non-action is explainable.
5. Suppression scope depends on experience class — safety is not silenced.
6. Room-scoped policy does not leak into other Rooms.
7. Unknown fails closed everywhere.

---

## Related documents

- [../models/truth.md](../models/truth.md)
- [../models/operational-trust.md](../models/operational-trust.md)
- [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md)
- [why-did-this-happen.md](why-did-this-happen.md)
