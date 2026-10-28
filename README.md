# ha_blueprints

Home Assistant blueprints. Each blueprint lives in its own folder under its domain (`automation/`, `script/`), with a README and an import button.

## Automation blueprints

| Blueprint | Description |
|---|---|
| [Alarm Light](automation/alarm_light/) | Keep one light at full strength and flash another while the alarm is on |
| [Alarm Speaker](automation/alarm_speaker/) | Play a sound on a speaker, over and over, while the alarm is on |
| [Curtain Toggle Control](automation/curtain_toggle_control/) | Toggle one or more curtains from any trigger(s): stop if moving, open if closed, otherwise close |
| [Single Button Advanced Light Switch](automation/single_button_advanced_light_switch/) | Press a button to switch a light on/off, hold it to dim up or down |

## Import

Click the **Import** badge in a blueprint's README, or in Home Assistant go to *Settings → Automations & Scenes → Blueprints → Import Blueprint* and paste the GitHub URL of the `.yaml` file.
