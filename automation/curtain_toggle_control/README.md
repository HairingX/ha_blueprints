# Curtain Toggle Control

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FHairingX%2Fha_blueprints%2Fblob%2Fmain%2Fautomation%2Fcurtain_toggle_control%2Fcurtain_toggle_control.yaml)

Toggles one or more curtains (covers) from any trigger(s), like a dimmer button:

| Current state | Action |
|---|---|
| Any curtain opening/closing | Stop all |
| All curtains closed | Open all |
| Stopped mid-way while **closing** *(direction memory set)* | Open all |
| Open / stopped mid-way while **opening** | Close all |

Without direction memory, a partially open curtain always closes on the next press.
Curtains that are `unavailable`/`unknown` are ignored when deciding.

## Inputs

| Input | Required | Description |
|---|---|---|
| Control triggers | Yes | One or more triggers (button long press, switch, etc.) |
| Curtain(s) | Yes | One or more `cover` entities, or a cover group helper |
| Direction memory | No | `input_boolean` remembering last direction (**on** = opening, **off** = closing). Updated both when this blueprint moves the curtain and when movement is reported from elsewhere (app, remote, schedules). |

## Requirements

- Home Assistant 2026.10.0 or newer.
- A cover integration that reports `opening`/`closing` promptly. With slow-polling integrations the stop branch may not trigger.

## Notes

- Runs in `queued` mode (max 10, overflow ignored silently) so movement state changes are not dropped while a press is being handled.
- A fully open curtain (position 100) always closes, even if the direction memory is out of sync.
- If several curtains always move together, consider a cover group helper (created in the UI) and select that instead. One direction memory helper is shared by all selected curtains.
