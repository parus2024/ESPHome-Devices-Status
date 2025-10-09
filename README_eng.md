# ESPHome Devices Status

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/yourusername/esphome-devices-status/blob/main/LICENSE)  
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2023.10+-green.svg)](https://www.home-assistant.io/)

This is a project for **Home Assistant** that provides a dynamic Lovelace card for monitoring the status of **ESPHome**-based devices. The card automatically scans ESPHome devices, sorts them by online/offline status, and allows displaying additional metrics (uptime, WiFi signal, IP address) as well as actions (device reboot).

## Features

- **Automatic device discovery**: The card uses a `binary_sensor` with `device_class: connectivity` to detect ESPHome devices.  
- **Sorting**: Ability to sort devices by `friendly_name` or `entity_id`.  
- **Filters and toggles**: Show or hide uptime, WiFi signal, IP address, and reboot button.  
- **Status separation**: Devices are grouped into "Online" and "Offline" sections.  
- **Interactivity**: Buttons to reboot devices and toggles to control filters.  
- **Customizable design**: Uses `card_mod` for styling (gray border, no shadow).  

## Installation

1. **Clone the repository** or download the files:  
   ```bash
   git clone https://github.com/yourusername/esphome-devices-status.git
   ```

2. **Add to Home Assistant**:  
   - Make sure you have the ESPHome integration and required custom components installed (see Dependencies).  
   - Copy the contents of the `esphome_devices_status.yaml` file (or equivalent) into your `ui-lovelace.yaml` or add it as a new card via the Lovelace UI.  
   - If using `auto-entities`, ensure it is installed.  

3. **Configure your ESPHome devices**:  
   - Devices must have a `binary_sensor` with `device_class: connectivity` (e.g., `esphome_device_status`).  
   - Additional sensors: `sensor.esphome_device_uptime`, `sensor.esphome_device_wifi_signal`, `sensor.esphome_device_esp_ip_address`.  
   - Button entity: `button.esphome_device_esp_reboot`.  

## Usage

- **Add the card to your dashboard**: In Lovelace UI, select "Manual card" and paste the YAML configuration.  
- **Toggles**:  
  - `Uptime`: Shows device uptime.  
  - `WiFi`: WiFi signal strength.  
  - `IP`: Device IP address.  
  - `Reboot`: Button to reboot the device (requires a `button` entity).  
- **Sorting**: Use `input_select.esphome_sort_by` to choose sorting by name or ID.  
- **Status**: The card updates automatically when device statuses change.  

## Configuration

The card uses the following entities (make sure they exist in your Home Assistant):  

- `input_select.esphome_sort_by` (options: `friendly_name`, `entity_id`).  
- Filter toggles: `input_boolean.show_uptime`, `input_boolean.show_wifi`, `input_boolean.show_ip`, `input_boolean.show_reboot`.  
- Device sensors: `binary_sensor.*_status`, `sensor.*_uptime`, `sensor.*_wifi_signal`, `sensor.*_esp_ip_address`.  
- Buttons: `button.*_esp_reboot`.  

## Dependencies

- **Home Assistant** version 2023.10 or newer.  
- **HACS** (Home Assistant Community Store) to install custom components:  
  - [card-mod](https://github.com/thomasloven/lovelace-card-mod) — for styling.  
  - [auto-entities](https://github.com/thomasloven/lovelace-auto-entities) — for dynamic entity lists.  
  - [multiple-entity-row](https://github.com/benct/lovelace-multiple-entity-row) — for grouping entities.  
- **ESPHome** integration in Home Assistant.  
- Your ESPHome devices must be configured with appropriate sensors (see [ESPHome documentation](https://esphome.io/)).  

## Screenshots

*(Add screenshots of the display, HA dashboard, or demo videos here)*

- [YAML card code](esphome_device_status.yml)  
- [Screenshot](device_status_card.jpg)  
- [YouTube Video](https://youtu.be/YKkLL0JR7so)  

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.  

## Contacts

- Telegram: [https://t.me/parus_smart](https://t.me/parus_smart)
