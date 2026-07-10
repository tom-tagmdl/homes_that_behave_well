# Platinum Target Checklist

This checklist defines the shared target for all Homes Platform integrations.

It is not a separate product requirement. It is the platform's design ceiling for
Home Assistant integrations that should be as close to Platinum quality as
practical.

Use this checklist when designing, reviewing, or refactoring any integration in
the platform.

---

## 1. Home Assistant Native Setup

- [ ] The integration uses Home Assistant-native setup patterns.
- [ ] Configuration is available through config flow where the integration supports user setup.
- [ ] Options flow exists where runtime reconfiguration is meaningful.
- [ ] The integration avoids custom setup UX when a native Home Assistant pattern already exists.
- [ ] The integration uses Home Assistant registries and helpers instead of parallel state systems.

---

## 2. User Experience

- [ ] The integration feels native to Home Assistant.
- [ ] UI elements follow Home Assistant interaction and visual patterns.
- [ ] Labels, entities, and devices are named clearly and consistently.
- [ ] The integration is translated where user-facing text is exposed.
- [ ] Reconfiguration, recovery, and diagnostics are accessible without manual file editing.

---

## 3. Reliability And Recovery

- [ ] The integration fails closed when dependencies are unavailable.
- [ ] Errors are handled deterministically and without leaking sensitive details.
- [ ] Offline, timeout, and partial-failure paths are defined.
- [ ] Re-authentication or recovery is surfaced when the integration depends on external access.
- [ ] The integration does not create log spam or noisy user interruptions during normal failure modes.

---

## 4. Observability

- [ ] Diagnostics are available and sanitized.
- [ ] Repairs or actionable recovery guidance are available when issues are expected or recoverable.
- [ ] Health or readiness surfaces exist for runtime status projection.
- [ ] Telemetry, if present, is privacy-safe and contract-limited.
- [ ] Logs and diagnostics avoid raw secrets, paths, embeddings, audio, or other sensitive internals.

---

## 5. Quality And Maintainability

- [ ] Code follows Home Assistant standards and platform guidance.
- [ ] Core behavior has automated tests.
- [ ] Regression coverage exists for setup, runtime, recovery, and release-sensitive flows.
- [ ] The implementation is typed and structured for long-term maintenance.
- [ ] Performance and resource use are considered, especially for recurring or realtime paths.

---

## 6. Release Readiness

- [ ] The integration can be distributed through HACS or the chosen release channel cleanly.
- [ ] Manifest, metadata, and packaging are valid for the target distribution path.
- [ ] Required validation workflows pass before release.
- [ ] Release notes and operational guidance exist for maintainers and users.
- [ ] Versioning is explicit and release artifacts are traceable.

---

## 7. Platform Governance

- [ ] The integration respects the shared contracts in this repository.
- [ ] Cross-repo behavior stays grounded in Homes That Behave Well.
- [ ] The integration does not invent a parallel source of truth when a platform contract already exists.
- [ ] Any new shared pattern is written back into this repository.

---

## Practical Ranking Guidance

Use this checklist as the platform target when judging maturity:

- Bronze: baseline setup, documentation, and tests.
- Silver: robust runtime behavior, recovery, and maintainership.
- Gold: polished user experience, discoverability, translations, and broad test coverage.
- Platinum: the Gold bar plus high technical quality, efficiency, and exceptional consistency.

For this platform, a strong integration should usually be designed to clear Gold and
then be pushed toward Platinum wherever the feature surface allows it.
