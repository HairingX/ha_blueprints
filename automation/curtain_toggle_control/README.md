# Curtain Toggle Control

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FHairingX%2Fha_blueprints%2Fblob%2Fmain%2Fautomation%2Fcurtain_toggle_control%2Fcurtain_toggle_control.yaml)

Toggles one or more curtains (covers) from any trigger(s):

| Current state | Action |
|---|---|
| Any curtain opening/closing | Stop all |
| All curtains closed | Open all |
| Any curtain open | Close all |

Curtains that are `unavailable`/`unknown` are ignored when deciding.

## Inputs

| Input | Required | Description |
|---|---|---|
| Control triggers | Yes | One or more triggers (button long press, switch, etc.) |
| Curtain(s) | Yes | One or more `cover` entities, or a cover group helper |

## Requirements

- Home Assistant 2026.10.0 or newer.
- A cover integration that reports `opening`/`closing` promptly. Decisions are based on the cover's live state; with slow-polling integrations the stop branch may not trigger.

## Notes

- Runs in `single` mode; presses arriving while a run is in progress are ignored silently.
- A curtain stopped mid-way reports `open`, so the next press closes it.
- If several curtains always move together, consider a cover group helper (created in the UI) and select that instead.
