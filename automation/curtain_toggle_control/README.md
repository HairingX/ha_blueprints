# Curtain Toggle Control

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FHairingX%2Fha_blueprints%2Fblob%2Fmain%2Fautomation%2Fcurtain_toggle_control%2Fcurtain_toggle_control.yaml)

Toggles one or more curtains (covers) from any trigger(s), like a dimmer button.

## How it decides

The cover **state** tells whether a curtain is moving. When it reports `open` or `closed`, the **position** (with a margin) decides whether it is at an end position:

| Effective state | Rule |
|---|---|
| Moving | state is `opening` / `closing` |
| Closed | state `closed`, or `open` with position ≤ margin |
| Fully open | state `open` with position ≥ 100 − margin |
| Partial | state `open` otherwise (or no position reported) |

| On press | Action |
|---|---|
| Any curtain moving | Stop all |
| All closed | Open all |
| Partial, last direction **closing** *(direction memory set)* | Open all |
| Fully open, or partial otherwise | Close all |

Curtains that are `unavailable`/`unknown` are ignored when deciding.

## Inputs

| Input | Required | Description |
|---|---|---|
| Control triggers | Yes | One or more triggers (button long press, switch, etc.) |
| Curtain(s) | Yes | One or more `cover` entities, or a cover group helper |
| Direction memory | No | `input_boolean` remembering last direction (**on** = opening, **off** = closing). See below. |
| End position margin | No | Percent from 0/100 that still counts as closed/fully open. Default `2`. |

### Direction memory updates

| Event | Helper |
|---|---|
| Blueprint opens / curtain reports `opening` | on |
| Blueprint closes / curtain reports `closing` or `closed` | off |
| Reports `open` at position ≥ 100 − margin | on |
| Reports `open` at position ≤ margin | off |
| Reports `open` mid-way (stopped) | unchanged |
| Reports `open` without position | on, unless it came from `closing` (= stopped while closing) |

## Requirements

- Home Assistant 2026.10.0 or newer.
- A cover integration that reports `opening`/`closing` promptly. With slow-polling integrations the stop branch may not trigger.

## Notes

- Runs in `queued` mode (max 10, overflow ignored silently) so state changes are not dropped while a press is being handled.
- If several curtains always move together, consider a cover group helper (created in the UI) and select that instead. One direction memory helper is shared by all selected curtains.
