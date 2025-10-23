# HELIOS-KWL-ESPhome-display

An ESPHome-based display and control interface for HELIOS KWL EC 270/370 Pro (<2014) ventilation systems, featuring a 1.3" SH1106 OLED, rotary encoder, and Home Assistant integration.

This project is based on my [Helios EC Pro Home Assistant integration](https://github.com/MomoRC-tech/helios-ec-pro-homeassistant), have a look.

**Note:** The Home Assistant entity names in the configuration (YAML) may need to be changed to match your own setup. Please adjust the entity IDs to those used in your Home Assistant instance.


<a href="docs/images/diagram.png">
  <img src="/HELIOS DIY BCU.jpg" alt="System diagram" width="420">
</a>

## Features

- **OLED Display:** 1.3" SH1106 (128x64) via I2C, shows live sensor data, weather, fan level, and system status.
- **Rotary Encoder:** Adjusts fan level and toggles auto/manual mode, with push-button input.
- **Home Assistant Integration:** Reads and controls entities such as fan level, auto mode, filter alert, and temperature sensors.
- **Status Icons:** Wi-Fi and Home Assistant connection status displayed on the OLED.
- **Overlay Preview:** Encoder changes show a temporary overlay before sending commands to Home Assistant.
- **Debug Logging:** Entity values and encoder actions are logged for troubleshooting.

## Hardware

- ESP8266 (eg. ESP8266 D1 Mini)
- SH1106 128x64 OLED display (I2C, SDA=D2, SCL=D1)
- Rotary encoder (A=D5, B=D6, Button=D7)

## Quick Start

1. Clone this repository.
2. Edit `helios-display-esp8266.yaml` to match your Wi-Fi and Home Assistant entity names.
3. Flash the ESP8266 with ESPHome.
4. Add the device to Home Assistant via ESPHome integration.

## Configuration Highlights

- Reads Home Assistant entities:
	- `sensor.helios_ec_pro_lufterstufe` (fan level)
	- `binary_sensor.helios_ec_pro_automatikmodus_aktiv` (auto mode)
	- `binary_sensor.helios_ec_pro_filterwechsel_erforderlich` (filter alert)
	- Weather and duct temperature sensors
- Rotary encoder changes are previewed and sent to Home Assistant after a short delay.
- OLED updates every 500ms for responsive display.

## Release Automation

Releases are automatically created and include the latest YAML configuration as an asset.

## License

MIT
