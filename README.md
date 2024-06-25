# Integrate LG heat pump under [Home Assistant](https://www.home-assistant.io)

This project shows how to configure [Home Assistant](https://www.home-assistant.io) to monitor the activity of your heat pump.

## Hardware requirements:
- [HA485](https://www.securecom.eu/en/our-products/supplies-and-accessories) RS485-WIFI converter for MODBUS communication
- If you want to measure power consumption:
  - [ESP32-PICO-DevKitM-2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-pico-devkitm-2.html) or any [ESP32 DevKit](https://www.espressif.com/en/products/devkits)
  - SCT-013 30A/1V CT clamp

## Installation
- Enable MODBUS with DIP switch on the heat pump panel. The DIP changes no effect during operation, must be turned OFF and ON the heat pump for the new DIP settings. Moreover set MODBUS address to 1 with the LCD panel (according to secrets.yaml -> slave_address).
- Configure [HA485](https://www.securecom.eu/en/our-products/supplies-and-accessories) RS485-WIFI converter to your WIFI network and connect A and B wires to the heat pump.
- If you want to measure power consumption:
  - Build [ESPHome CT clamp current sensor](https://esphome.io/components/sensor/ct_clamp.html)
  - Update yaml file according to esphome_ct_clamp.yaml
  - Put the SCT-013 CT clamp to the one of the heat pump power wire
  - Fix the calibration filter if necessary
- Update secret.yaml and configuration.yaml in the home assistant configuration folder
- Update modbus IP address in configuration.yaml to the [HA485](https://www.securecom.eu/en/our-products/supplies-and-accessories)
- Install [card-mod 3](https://github.com/thomasloven/lovelace-card-mod) in home assistant to show cards correctly
- Update your cards according to cards.yaml
