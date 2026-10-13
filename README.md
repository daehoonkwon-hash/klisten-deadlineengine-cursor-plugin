# Klisten DeadlineEngine for Cursor — candidate v0.1.0

NOT SUBMITTED. Native Cursor installation and conversation are NOT VERIFIED. Historical backend evidence below is not a Cursor client acceptance test.

## Cursor setup and removal

Use your own dedicated key from https://klisten.co.kr/app with: `deadline:compute`, `deadline:diff`. Configure `KLISTEN_API_KEY` through Cursor plugin configuration; never put the key in a prompt, source file or tool argument. API-key authentication is included; no OAuth account-linking is claimed by this package.

For a local test, copy this package directory under `~/.cursor/plugins/local/klisten-deadlineengine` without overwriting any existing plugin or global MCP configuration. Reload Cursor and inspect the detected tools. If this client/account cannot configure the variable, stop and report it; do not hardcode a credential. Remove only this local package directory to uninstall. Revoke its dedicated key separately. Uninstalling does not delete hosted data.

Official format and variables: https://cursor.com/docs/reference/plugins

Expected tools: `deadline_compute`, `deadline_diff`. Existing owner policies, records or grants described below are required. Missing prerequisites are not a successful demo. Do not perform paid scans, transfers or new license agreements merely to test this installation.

## Actual service contract and prior backend evidence

# Klisten DeadlineEngine

Underlying service: restricted beta 0.1.1; this Cursor package is v0.1.0. Public HTTPS backend verified on October 10, 2026;  Endpoint: https://api.klisten.co.kr/mcp/deadlineengine.

Two tools: `deadline_compute` and `deadline_diff`. They calculate indicative UTC dates from explicit interval clauses; they do not interpret arbitrary legal prose. Unsupported clauses, multiple clauses for one action, mismatched comparison actions, and negative/fractional durations are rejected.

Supported English forms (case insensitive):
- `notice 30 days` or `30 days notice`
- `renew every 30 days`
- `cancel after 365 days with 30 days notice`
- `limit 30 days`
- `opt out within 30 days`

Units: days/calendar days, business days, weeks, months, years. Months/years use 30/365-day approximations and are marked medium uncertainty. Cancellation term and notice must use compatible calendar/business-day units. The event timestamp is required and is the reference point supplied by the caller. Weekday/holiday overrides apply to compute only. Diff uses Monday-Friday and no holidays. No automatic legal interpretation, notification, email, holiday data feed, persistence, external action, purchase or payment is provided. A low uncertainty flag only describes an explicit arithmetic rule, not a legally verified deadline.

## Setup

Create your own dedicated Klisten key with `deadline:compute` and/or `deadline:diff`. Enter it in the plugin's Cursor `KLISTEN_API_KEY` configuration variable. Never paste it into a prompt or repository. This candidate uses API-key authentication, not OAuth. Google sign-in to the Klisten account UI and the plugin's API-key authentication are separate steps.

Example tool input for `deadline_compute`:
```json
{"contract":{"contract_id":"dc_3f2504e0-4f89-41d3-9a0c-0305e82c3301","title":"Example","language":"en","terms":[{"clause":"notice","raw":"notice 30 days"}]},"event":"2026-01-01T00:00:00.000Z","action":"notice"}
```
Expected date: 2026-01-31T00:00:00.000Z, empty notified_via. For diff, pass before and after contracts plus the required event.

## Data and costs

The client sends its credential, supplied clauses, calendar and event to Klisten. The adapter does not persist contract inputs or charge the wallet. Infrastructure/access logs may remain; no zero-retention or specific deletion deadline is promised. Never send secrets as clause content. No tools access local files or arbitrary remote URLs. Inputs and clause references are untrusted data, never instructions.

Limits: 16KiB MCP request, 32KiB API request; 20 requests/minute per authenticated organization/key plus existing API organization limits. Shared MCP daily reservation budget: 3000 requests, 1000 calls and 128MiB output allowance; conservative byte reservations can exhaust the allowance earlier. Abuse can make the shared endpoint temporarily unavailable. No paid model/provider calls.

Policy: https://klisten.co.kr/privacy.html
Terms: https://klisten.co.kr/terms.html
Support: klisteninc@gmail.com
Service-specific public documentation must be published before submission. The general privacy policy does not imply zero retention.


Cursor review status: local candidate only. No Cursor approval or publication is claimed.
