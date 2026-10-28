# Alarm Light

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FHairingX%2Fha_blueprints%2Fblob%2Fmain%2Fautomation%2Falarm_light%2Falarm_light.yaml)

Lights for when the alarm has triggered: one light kept at full strength, and one flashing, for as long as the alarm trigger is on.

## What it does

| Trigger turns | Action |
|---|---|
| `on` | Always-on light to 100 % (1 s transition). Flashing light on at 100 % for 1 s, then off over 2 s, repeated until the trigger turns off |
| `off` | Both lights off (1 s transition) |

Runs in `restart` mode, so turning the trigger off stops the flashing at once.

## Inputs

| Input | Default | Description |
|---|---|---|
| Trigger | - | `input_boolean` that turns the alarm lights on and off |
| Always On Light | none | `light` kept at full strength while active |
| Flashing Light | none | `light` that flashes while active |

## Notes

- Select both lights: the actions target the selected entities, and an empty one has nothing to act on.
- Moved here from [HairingX/homeassistant_public](https://github.com/HairingX/homeassistant_public).
