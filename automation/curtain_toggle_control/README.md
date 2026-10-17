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
| Last direction helper | No | `input_boolean` set **on** when opening, **off** when closing (in the collapsed *Advanced* section) |

## Requirements

- Home Assistant 2026.10.0 or newer.

## Notes

- Runs in `queued` mode (max 10, overflow ignored silently) so curtain state changes are not dropped while a button press is being handled.
- If several curtains always move together, consider a cover group helper (created in the UI) and select that instead.
