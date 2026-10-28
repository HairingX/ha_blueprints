# Alarm Speaker

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FHairingX%2Fha_blueprints%2Fblob%2Fmain%2Fautomation%2Falarm_speaker%2Falarm_speaker.yaml)

Plays a sound on a speaker, over and over, for as long as the alarm trigger is on.

## What it does

| Trigger turns | Action |
|---|---|
| `on` | Sets the speaker's volume, then plays the selected media every *Loop length* seconds until the trigger turns off |
| `off` | Stops the speaker, clears its playlist and sets its volume to 30 % |

Runs in `restart` mode, so turning the trigger off stops the sound at once.

## Inputs

| Input | Default | Description |
|---|---|---|
| Trigger | - | `input_boolean` that turns the alarm sound on and off |
| Media | - | The media to play, and the speaker (media player) to play it on |
| Loop length | 3 s | Time between each start of the media (1-600 s) |
| Volume | 80 % | Volume while the alarm sounds |

## Notes

- After the alarm the volume is left at 30 %, not at what it was before.
- Moved here from [HairingX/homeassistant_public](https://github.com/HairingX/homeassistant_public).
