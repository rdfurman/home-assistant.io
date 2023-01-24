---
title: Honeywell Total Connect Comfort (US)
description: Instructions on how to integrate Honeywell thermostats within Home Assistant.
ha_category:
  - Climate
  - Sensor
ha_release: pre 0.7
ha_iot_class: Cloud Polling
ha_config_flow: true
ha_codeowners:
  - '@mkmer'
  - '@rdfurman'
ha_domain: honeywell
ha_platforms:
  - climate
  - sensor
ha_integration_type: integration
---

The Honeywell integration integrates Home Assistant with _US-based_ [Honeywell Total Connect Comfort (TCC)](https://mytotalconnectcomfort.com/portal/) climate systems.

If your system is compatible with this integration, then you will be able access it via [https://mytotalconnectcomfort.com/portal/](https://mytotalconnectcomfort.com/portal/) (note the `/portal/`).

There is currently support for the following device types within Home Assistant:

- [Overview: Supported Devices](#overview-supported-devices)
- [Configuration](#configuration)
- [Climate](#climate)
- [Sensor](#sensor)

## Overview: Supported Devices

Home Assistant is integrated with the following devices through [https://mytotalconnectcomfort.com/portal/](https://mytotalconnectcomfort.com/portal/):

- Thermostats
  - Every thermostat is exposed as a `climate` entity
  - Example devices: TH6320R1004
- Sensors
  - A Temperature `sensor` entity.
  - A Humidity `sensor` entity.
  - Example devices: C7089R1013

Others devices like Security systems are not currently supported by this integration.

## Configuration

{% include integrations/config_flow.md %}

## Climate

All supported Honeywell Thermostat models are exposed as a `climate` entities. State changes to the thermostat are reported to Home Assistant through the [https://mytotalconnectcomfort.com/portal/](https://mytotalconnectcomfort.com/portal/) API.

Given a thermostat named `Upstairs` then the climate entity is created with a name such as `climate.upstairs`.

TODO: Talk about setting the temp behavior. According to Mike:
"
if you put the device in HOLD then set a temperature, it should set a permanent hold.  If you put it in away mode, it also should set a permanent hold at the configured away temperature (for heat and cool respectively).  Then taking it out of HOLD or AWAY should restore to following schedule.
"

That seems to be how it works. Now time to document it.

## Sensor

This integration will add Home Assistant sensors for the following:
|Sensor|Value|
--- | ---
|Outdoor temperature | Average temperature of all Honeywell Wireless Outdoor Sensors|
|Outdoor humidity | Average humidity of all Honeywell Wireless Outdoor Sensors|