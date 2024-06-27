# Integrate LG heat pump under [Home Assistant](https://www.home-assistant.io)

This project shows how to configure [Home Assistant](https://www.home-assistant.io) to monitor the activity of your heat pump.

## Hardware requirements:
- [HA485 RS485-WIFI converter](https://www.securecom.eu/en/our-products/supplies-and-accessories) for MODBUS communication. This connects the heat pump to the local network.
- If you want to measure power consumption:
  - [ESP32-PICO-DevKitM-2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-pico-devkitm-2.html) (or any other ESPHome compatible [ESP32 DevKit](https://www.espressif.com/en/products/devkits))
  - SCT-013 30A/1V CT clamp

## Installation
- Enable MODBUS function on the heat pump panel with the DIP switch. Changing the DIP has no effect during operation, must be turned OFF and ON the heat pump to work with the new DIP settings and set MODBUS address to 1 on the LCD panel (according to [secrets.yaml](/lg-heatpump-home-assistant/secrets.yaml) -> slave_address).
- Configure [HA485 RS485-WIFI converter](https://www.securecom.eu/en/our-products/supplies-and-accessories) to your WIFI network and connect **A** and **B** wires to the heat pump.
- If you want to measure power consumption:
  - Build [ESPHome CT clamp current sensor](https://esphome.io/components/sensor/ct_clamp.html)
  - Update yaml file according to [esphome_ct_clamp.yaml](/power-measurement-esphome/esphome_ct_clamp.yaml)
  - Put the SCT-013 CT clamp to the one of the heat pump power wire
  - Fix the calibration filter if necessary
- Update [secrets.yaml](/lg-heatpump-home-assistant/secrets.yaml) and [configuration.yaml](/lg-heatpump-home-assistant/configuration.yaml) in the home assistant configuration folder
- Update [MODBUS](https://www.home-assistant.io/integrations/modbus) host address in [configuration.yaml](/lg-heatpump-home-assistant/configuration.yaml) to the IP address of the [HA485 RS485-WIFI converter](https://www.securecom.eu/en/our-products/supplies-and-accessories)
- Install [card-mod 3](https://github.com/thomasloven/lovelace-card-mod) in home assistant to show cards correctly
- Update your cards according to [cards.yaml](/lg-heatpump-home-assistant/cards.yaml)

## The heat pump status in IDLE and COOLING mode

<p align="center">
  <img src="https://github.com/xilard/home-assistant-lg-heatpump/assets/25320041/5449e5e5-0818-476a-8b49-b2ca6daedc2f" />
</p>

## History graph of COOLING

<p align="center">
  <img src="https://github.com/xilard/home-assistant-lg-heatpump/assets/25320041/daf7f0b4-9293-4542-aaf8-24cc14883003" />
</p>
