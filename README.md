# Home Assistant Blueprints

A collection of automation blueprints for Home Assistant to simplify common smart home scenarios.

## 📋 Available Blueprints

| Blueprint | Version | Description | Quick Install | Documentation |
|-----------|---------|-------------|---------------|---------------|
| **🎛️ Lutron Pico Fan Control** | v1.0 | Control ceiling fans and lights with a Lutron Pico 5-button remote. Features single press fan control and long press light dimming. | [![Install](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fbillchurch%2Fha-blueprints%2Frefs%2Fheads%2Fmain%2Fpico_fan_5_simple.yml) | [View Docs](docs/pico_fan_control.md) |
| **💨 Bath Fan Automation** | v1.0 | Smart bathroom fan control based on humidity levels with manual override support. Automatically manages ventilation to prevent moisture buildup. | [![Install](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fbillchurch%2Fha-blueprints%2Frefs%2Fheads%2Fmain%2Fbath_fan.yml) | [View Docs](docs/bath_fan_automation.md) |
| **💧 Moisture Sensor Notifications** | v1.2 | Critical water leak detection system with multi-channel alerts including iOS notifications, TTS announcements, and persistent UI warnings. | [![Install](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fbillchurch%2Fha-blueprints%2Frefs%2Fheads%2Fmain%2Fmoisture_sensor_notifications.yml) | [View Docs](docs/moisture_sensor_notifications.md) |

## 🚀 Quick Start

1. Click on any documentation link above to learn more about each blueprint
2. Use the **Import Blueprint** button in each doc to add it to your Home Assistant
3. Configure the automation using the detailed setup instructions provided

## 📁 Repository Structure

```text
ha-blueprints/
├── README.md                           # This file
├── docs/                              # Documentation
│   ├── pico_fan_control.md
│   ├── bath_fan_automation.md
│   └── moisture_sensor_notifications.md
├── pico_fan_5_simple.yml              # Lutron Pico blueprint
├── bath_fan.yml                       # Bath fan blueprint
└── moisture_sensor_notifications.yml   # Moisture sensor blueprint
```

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## 📄 License

These blueprints are provided as-is for use with Home Assistant. Feel free to modify and adapt them to your needs.

## 🔗 Resources

- [Home Assistant Blueprint Documentation](https://www.home-assistant.io/docs/blueprint/)
- [Home Assistant Community Forum](https://community.home-assistant.io/)
- [Report Issues](https://github.com/billchurch/ha-blueprints/issues)