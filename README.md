

# SmartSpray Irrigation System
### Homeassistant irrigation system for esp32 chipset.
## Overview

SmartSpray is an irrigation system controlled by Home Assistant and implemented on an ESP32 microcontroller using ESPHome. The system allows you to schedule and control irrigation zones based on various conditions such as temperature, rainfall, and specific time intervals.

## Dashboard

The `dashboard_layout.yaml` file defines the layout of the irrigation dashboard in Home Assistant.

#### Preview of the made home assistant dashboard.
![Preview of the made home assistant dashboard](./Pictures/irrigation.PNG)


### Irrigation Overview

- **Title:** Irrigation
- **Views:**
  - **Home:**
    - **Entities:**
      - Current time
      - Rainfall in the past day
      - Minimum temperature
    - **Zone Programming:**
      - Selectable start time
      - Individual day toggles
    - **Zones:**
      - Zone 1: Enable toggle and duration
      - Zone 2: Enable toggle and duration
      - Zone 3: Enable toggle and duration
      - Zone 4: Enable toggle and duration

## ESPHome Configuration

The `ESP32code.yaml` file contains the ESPHome configuration for the irrigation system.

### Substitutions

- `device_name`: irrigation
- `switch_id`: Irrigation
- `rainfall`: sensor.buienradar_rain_1d
- `temperature`: sensor.buienradar_temperature

### ESPHome Configuration

- Board: ESP32 development board
- Flash write interval: 1 minute

### WiFi Configuration

- SSID and password are set through secrets
- Fallback hotspot (captive portal) enabled in case of WiFi connection failure

### Home Assistant API

- API and OTA (Over-the-Air) updates enabled

### Time and Global Variables

- Home Assistant time integration for time synchronization
- Global variables for zone remainings and days to run

### Sensors

- Rainfall and temperature sensors imported from Home Assistant
- WiFi signal strength sensor
- Template sensors for zone remainings

### Switches and Buttons

- Template switches for each irrigation zone
- Template switches for each day of the week
- Template switches for enabling/disabling each irrigation zone

### GPIO Switches

- GPIO switches for controlling irrigation channels

### Scripts

- Various scripts for turning off valves and managing zone waiting times

### Time Automations

- Interval set to 1 second for time-based automations
- Checks conditions such as minimum temperature and maximum rainfall before triggering irrigation
- Time-based automations for starting each irrigation zone based on configured schedule

## Usage

1. Install the necessary Home Assistant elements and resources, including the [`multiple-entity-row`](https://github.com/benct/lovelace-multiple-entity-row) element.
2. Configure WiFi settings in ESPHome using secrets.
3. Adjust irrigation settings such as start time, zone durations, and conditions in Home Assistant.
4. Flash the ESP32 with the provided configuration.
5. Monitor and control the irrigation system through the Home Assistant dashboard.