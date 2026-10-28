# Single Button Advanced Light Switch

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FHairingX%2Fha_blueprints%2Fblob%2Fmain%2Fautomation%2Fsingle_button_advanced_light_switch%2Fsingle_button_advanced_light_switch.yaml)

One push button for a light: press to switch it on or off, hold to dim it up or down.

## What it does

| Button | Action |
|---|---|
| Pressed shorter than *Hold threshold* | Light off if it is on, on if it is off |
| Held | Dims towards the upper or lower bound until released |

The dim direction is the opposite of the last one, kept in *Last Transition State*. Without that helper, the light dims down above half brightness and up below it.

Runs in `queued` mode (max 2).

## Inputs

| Input | Default | Description |
|---|---|---|
| Push button | - | `binary_sensor` or `input_boolean` that is `on` while the button is pressed |
| Light | - | The `light` to control |
| Last Transition State | none | `input_number` that keeps the last dim direction (-1 / 1) |
| Hold threshold | 0.8 s | How long a press must last to count as a hold |
| Brightness transition | 4.0 s | Time for a full dim from one bound to the other |
| Overshoot amount | 0 | Brightness added past the point where the button was released (-15 to 15) |
| Overshoot correction transition | 0.3 s | Transition time for that correction |
| Lower brightness bound | 0.1 % | Lowest brightness when dimming |
| Upper brightness bound | 100 % | Highest brightness when dimming |

## Notes

- A short press also writes the direction to *Last Transition State*, even when no helper is selected, so selecting one is recommended.
- Writes its dim calculations to the system log at `info` level while dimming.
