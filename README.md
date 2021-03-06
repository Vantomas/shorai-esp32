# shorai-esp32
esp32 connected to shorai heat pump

This works great for me, but is at your own risk!

Hit me up on (https://discord.gg/wF8QsGe74s) if there is anything
i can help with

### PCB Schematic
![PCB Schematic](images/schematic.PNG?raw=true "PCB Schematic")

### PCB Layout
![PCB layout](images/pcb.PNG?raw=true "PCB layout")
U5 is a jumper, close the jumper to be powered from the heatpump. Remove jumper when powered from usb.


### Parts list

* 1 x ESP32-DevKitC
* 2 x EL817A Optocoupler (https://www.ebay.com/itm/Straight-Plug-Optocoupler-EL817-A-B-C-D-F-DIP-4-Compatible-PC817-Isolator/253795050804?hash=item3b175d2534:g:LjcAAOSwXVNbY~z3)
* 4 x 0.25w 1K resistors
* 1 x 0.25w 470R resistor
* 1 x 0.25w 10K resistor
* 1 x 0.25w 220R resistor
* 2 x 100uF (11mmx5mm) Capacitor 
* 1 x S05B-PASK-2 (header for connection cable)
* and 2.54mm header pins and sockets


### Home assistant Climate config part

```
climate:
  - platform: mqtt
    name: HeatPump
    unique_id: toshibaheatpump
    modes:
      - "auto"
      - "cool"
      - "heat"
      - "dry"
      - "fan_only"
    swing_modes:
      - "on"
      - "off"
    fan_modes:
      - "quiet"
      - "lvl_1"
      - "lvl_2"
      - "lvl_3"
      - "lvl_4"
      - "lvl_5"
      - "auto"
    power_command_topic: "heatpump/state/set"
    power_state_topic: "heatpump/state/state"
    mode_command_topic: "heatpump/mode/set"
    mode_state_topic: "heatpump/mode/state"
    current_temperature_topic: "heatpump/roomtemp"
    temperature_command_topic: "heatpump/setpoint/set"
    temperature_state_topic: "heatpump/setpoint/state"
    fan_mode_command_topic: "heatpump/fanmode/set"
    fan_mode_state_topic: "heatpump/fanmode/state"
    swing_mode_command_topic: "heatpump/swingmode/set"
    swing_mode_state_topic: "heatpump/swingmode/state"
    temp_step: 1
    precision: 1
```
