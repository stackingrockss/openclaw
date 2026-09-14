# Home pin persistence proof — PR 148582

Source head: 6b68eba245b34331225a763b8c8ac691f0c8dd2e (runtime unchanged from 2c972752).

Built full normal Gateway and Control UI; no mocked WebSocket transport.
Two isolated fixture Gateways, fresh preferences and existing Usage/Automations pins + dark theme.
No real credentials, provider calls, external channels, or operator workspace/state used.
Chromium clicks Edit pinned items -> Home, moves the same session into Projects, reloads,
then uses an independent clean browser profile and a new normal dashboard login handoff.
Independent CLI config readback verifies the disk-persisted boolean and unrelated settings.
Real sessions.list readback verifies the same session ID, label, and Projects category.
Repinning preserves custom page pins. Reset pinned items intentionally restores page defaults,
repins Home, and preserves the conversation's grouping and unrelated dark theme.

Result: 2/2 tests pass (95.10 seconds), 2026-09-14 UTC.
Command: OPENCLAW_CAPTURE_UI_PROOF=1 pnpm test:ui:e2e ui/src/e2e/sidebar-home-pin.real-gateway.e2e.test.ts

The populated transcript remains covered by the separate mock-Gateway browser test;
this real-Gateway proof covers durable preference synchronization and session metadata/identity.
Not installed on a live user Gateway. Maintainer product acceptance remains pending.
