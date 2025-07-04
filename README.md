# Home Assistant Blueprints

## Pico Fan – Simple 5-Button

[![lutron-pico-5-sm](https://github.com/user-attachments/assets/cf32fe42-f5b9-4c31-a494-aec0eef93773)](https://github.com/user-attachments/assets/a84b5c26-0ceb-466c-8867-16a8ad78388e)

This Home Assistant blueprint allows you to control a ceiling fan and optional light using a Lutron Pico 5-button remote (model PJ2-3BRL-GXX-F01). The blueprint supports both single presses for fan control and long presses for light dimming.

### Features

- **Single Press Controls**: Control fan speed with up/down buttons
- **Long Press Controls**: Dim lights with continuous brightness adjustment
- **Middle Button**: Toggle light (if configured) or fan (if no light)
- **On/Off Buttons**: Turn fan on/off
- **Configurable Dimming**: Adjust brightness step size and dimming rate

### Button Functions

| Button | Single Press | Long Press |
|--------|-------------|------------|
| **ON** | Turn fan on | - |
| **UP** | Increase fan speed | Brighten light continuously |
| **MIDDLE** | Toggle light (or fan if no light) | - |
| **DOWN** | Decrease fan speed | Dim light continuously |
| **OFF** | Turn fan off | - |

### Prerequisites

1. **Lutron Caseta Integration**: Ensure the Lutron Caseta integration is installed and configured
2. **Pico Remote**: A Lutron Pico 5-button remote (PJ2-3BRL-GXX-F01) paired with your Caseta hub
3. **Fan Entity**: A fan entity in Home Assistant
4. **Light Entity** (optional): A light entity for dimming control

### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fbillchurch%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fpico_fan_5_simple.yml)

1. **Download the Blueprint**:
   - Copy the blueprint YAML content
   - Save it to your Home Assistant `blueprints/automation/` directory

2. **Import via UI**:
   - Go to **Settings** → **Automations & Scenes** → **Blueprints**
   - Click **Import Blueprint**
   - Paste the blueprint URL or upload the file

### Configuration

#### Required Inputs

- **Lutron Pico**: Select your Pico remote device
- **Fan**: Select the fan entity to control

#### Optional Inputs

- **Light**: Select a light entity for dimming control (leave empty to disable light features)
- **Brightness Step Percentage**: How much to change brightness per step (1-25%, default: 10%)
- **Dimming Rate**: How fast to change brightness during long press (100-1000ms, default: 200ms)

### Setup Instructions

1. **Create New Automation**:

   ```bash
   Settings → Automations & Scenes → Automations → Create Automation → Use Blueprint
   ```

2. **Select Blueprint**:
   - Choose "Pico Fan Simple 5-Button with Long Press"

3. **Configure Inputs**:
   - **Lutron Pico**: Select your paired Pico remote
   - **Fan**: Choose your ceiling fan entity
   - **Light** (optional): Choose your light entity
   - **Brightness Step**: Adjust to your preference (default 10%)
   - **Dimming Rate**: Adjust to your preference (default 200ms)

4. **Save Automation**:
   - Give your automation a descriptive name
   - Click "Save"

### Example Configuration

```yaml
alias: penelope - pico - fan - light
description: ""
use_blueprint:
  path: billchurch/pico_fan_5_simple.yml.yaml
  input:
    light_entity: light.pen_fan
    pico_remote: 5f1fee7421ad0638ec5fca2c0ab451b7
    fan_entity: fan.pen_fan
```

### Troubleshooting

#### Common Issues

1. **Blueprint Import Errors**:
   - Ensure the YAML syntax is correct
   - Check that all required fields are present

2. **Remote Not Responding**:
   - Verify the Pico remote is properly paired with Caseta hub
   - Check that the device ID is correct in the automation

3. **Light Dimming Not Working**:
   - Ensure the light entity supports brightness control
   - Check that the light entity is properly configured

4. **Fan Speed Control Issues**:
   - Verify the fan entity supports speed control
   - Check fan entity attributes in Developer Tools

#### Debugging Steps

1. **Check Entity States**:

   ```bash
   Developer Tools → States
   ```

2. **Monitor Automation Traces**:

   ```bash
   Settings → Automations & Scenes → [Your Automation] → Traces
   ```

3. **Review Logs**:

   ```bash
   Settings → System → Logs
   ```

### Customization

#### Adjusting Long Press Threshold

The blueprint uses a 300ms threshold to detect long presses. To modify this:

1. Edit the blueprint YAML
2. Change the timeout value in both UP and DOWN button sections:

   ```yaml
   timeout: "00:00:00.3"  # Change to desired duration
   ```

#### Modifying Brightness Limits

- **Maximum brightness**: Modify the condition in the UP button section
- **Minimum brightness**: Modify the condition in the DOWN button section

### Support

For issues or questions:

- Check the [Home Assistant Community Forum](https://community.home-assistant.io/t/pico-fan-simple-5-button-remote-for-lutron-caseta-haiku-or-any-fan/901507)
- Review the [Lutron Caseta Integration Documentation](https://www.home-assistant.io/integrations/lutron_caseta/)
- Consult the [Home Assistant Blueprint Documentation](https://www.home-assistant.io/docs/blueprint/)

## Bath Fan Automation

This automation uses humidity sensors to control a fan with a manual override and timer.

1. Add two helpers in Home Assistant (if setting up mutiple bath fans be sure to give each helper a unique name for that bathroom):
   - Input Boolean: `input_boolean.bath_fan_manual_override`
   - Input Number: `input_number.bath_fan_override_duration` (min: 5, max: 60)

2. In your dashboard (Lovelace):

```yaml
   type: entities
   title: Bath Fan Control
   entities:
     - entity: switch.guest_bathroom_exhaust_fan
       name: Fan Switch
     - entity: input_boolean.bath_fan_manual_override
       name: Manual Override Active
     - entity: input_number.bath_fan_override_duration
       name: Override Duration (minutes)
```

3. Import this blueprint and create an automation.

4. Select your fan switch and humidity sensors.

5. Optionally point to the helpers above.

6. Set thresholds and duration as needed.

✅ When a user manually turns on the fan, it will run for the configured time and not conflict with humidity automation.

✅ When humidity rises above threshold, the fan will auto-turn on if override is inactive.

✅ When humidity drops below threshold, the fan will auto-turn off unless in override.
