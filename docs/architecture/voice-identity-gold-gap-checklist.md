# Voice Identity Gold Gap Checklist

This checklist turns the Home Assistant Gold bar into a practical gap list for
Voice Identity.

It is intentionally opinionated toward the current Voice Identity shape: a
service-oriented, local-first custom integration.

Use it to decide what still needs to land before we would describe the
integration as Gold-ready.

---

## Priority 1: User-Facing Polish

- [ ] Add translations for all user-facing strings.
- [ ] Make setup, options, diagnostics, repairs, and recovery copy fully
      Home Assistant native and user friendly.
- [ ] Remove or shorten release-oriented wording from user-facing docs where it
      does not help day-to-day setup or troubleshooting.
- [ ] Make the integration's setup and recovery path understandable without
      reading source code.

Why this is first:

Gold requires a polished end-user experience, not only a solid technical core.

---

## Priority 2: Full-Surface Validation

- [ ] Add tests that cover the integration end to end, not only the release
      readiness and hardening slices.
- [ ] Cover config flow, options flow, runtime service registration, diagnostics,
      repairs, health, telemetry, and identity context surfaces.
- [ ] Add regression tests for failure and recovery behavior that users are most
      likely to hit.
- [ ] Keep tests deterministic and independent of the developer machine state.

Why this is second:

Gold expects automated tests that protect the whole integration, not just a
subset of release gates.

---

## Priority 3: Home Assistant-Native Setup And Recovery

- [ ] Confirm whether the integration needs reconfigure or reauth support, and
      add it if the setup path can change after initial install.
- [ ] Make setup and recovery flows follow standard Home Assistant patterns.
- [ ] Ensure failures surface through Home Assistant-native diagnostics and
      repair guidance rather than custom ad hoc UI.
- [ ] Avoid duplicate state models when Home Assistant registries or runtime
      helpers already provide the right source of truth.

Why this is third:

Gold rewards integrations that feel native and recover cleanly when something is
misconfigured or temporarily unavailable.

---

## Priority 4: Discoverability And UX Completeness

- [ ] Confirm whether any part of Voice Identity should be surfaced as devices,
      entities, or only services.
- [ ] If devices or entities exist, give them stable names, unique IDs, and
      translation keys.
- [ ] If device discovery is applicable to a future feature, define it in the
      architecture before implementation.
- [ ] Ensure any user-facing actions have clear descriptions and troubleshooting
      paths in the docs.

Why this matters:

Gold expects the integration to be easy to understand and easy to use from the
Home Assistant UI.

---

## Priority 5: Documentation And Supportability

- [ ] Expand the end-user docs so setup, usage, troubleshooting, and limitations
      are easy to find.
- [ ] Separate maintainer runbook content from user-facing install/help content.
- [ ] Keep the README and release notes aligned with the current installed
      behavior.
- [ ] Document any non-applicable Gold rules explicitly so reviewers do not have
      to guess.

Why this is fifth:

Gold is not just about code quality. It includes documentation that lets users
and maintainers understand what the integration does and how to recover when it
does not.

### Non-Applicable Gold Rules For Voice Identity

These items should be documented as intentionally out of scope rather than left
as open gaps:

- Device discovery is not applicable because Voice Identity is service-only.
- Firmware update support is not applicable because Voice Identity does not
      manage hardware.
- Device/entity presentation is not required unless the integration adds a
      concrete runtime surface that needs it later.
- Reauth is not required unless a future external dependency introduces
      credentials or expiring access.

---

## Likely Gold Finish Line For Voice Identity

Voice Identity is close to the Gold bar when all of the following are true:

- the UI and copy are translated and Home Assistant native
- the integration has complete setup and recovery behavior for its actual
  runtime model
- the full integration surface is covered by automated tests
- docs explain setup, operation, failure handling, and limitations without
  requiring source dives

For a service-oriented integration, automatic device discovery and firmware
update support may be non-applicable. If so, document that explicitly instead of
treating it as an unfilled gap.
