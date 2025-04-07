# Boiler Timer Automation  

## Overview  
This automation manages a boiler switch with a timer function. It allows you to:  
- Automatically turn off the boiler after a specified duration.  
- Display a countdown timer.  
- Control the boiler with preset durations (15, 30, 45, or 60 minutes) using dashboard buttons.  

## Features  
✅ Turns on the boiler and starts a countdown timer.  
✅ Supports different time durations (15, 30, 45, and 60 minutes).  
✅ Cancels the timer and turns off the boiler if the button is pressed again.  
✅ Works with a predefined blueprint for easy setup.  

## Setup  

### 1. **Install the Blueprint**  
Add blueprint using next URL:
> ```bash
> https://github.com/airalab/home-assistant-blueprints/blob/main/boiler_timer_toggle/boiler_timer_toggle.yaml
> ```
Or, save the following YAML as `boiler_timer_toggle.yaml` in your `blueprints/automation` folder.

### 2. Create Boiler Control Entities
Go to Settings->Devices->Helpers. 

Create timer. 

create helper with class "toggle" (or in configuration.yaml):

```
input_boolean:
  boiler_main:
    name: "Boiler 60 Minutes"
    initial: off
  boiler_15:
    name: "Boiler 15 Minutes"
    initial: off
  boiler_30:
    name: "Boiler 30 Minutes"
    initial: off
  boiler_45:
    name: "Boiler 45 Minutes"
    initial: off
```

### 3. Create Automations Using the Blueprint
```yaml
automation:
  - alias: "Boiler 60 Minutes"
    use_blueprint:
      path: boiler_timer_toggle.yaml
      input:
        boiler_switch: switch.boiler
        timer_entity: timer.boiler_timer
        trigger_entity: input_boolean.boiler_main
        duration: 60

  - alias: "Boiler 15 Minutes"
    use_blueprint:
      path: boiler_timer_toggle.yaml
      input:
        boiler_switch: switch.boiler
        timer_entity: timer.boiler_timer
        trigger_entity: input_boolean.boiler_15
        duration: 15

  - alias: "Boiler 30 Minutes"
    use_blueprint:
      path: boiler_timer_toggle.yaml
      input:
        boiler_switch: switch.boiler
        timer_entity: timer.boiler_timer
        trigger_entity: input_boolean.boiler_30
        duration: 30

  - alias: "Boiler 45 Minutes"
    use_blueprint:
      path: boiler_timer_toggle.yaml
      input:
        boiler_switch: switch.boiler
        timer_entity: timer.boiler_timer
        trigger_entity: input_boolean.boiler_45
        duration: 45

```
### 4. Add Dashboard Buttons
Add buttons to dashboard:

```yaml
type: entities
title: Boiler Control
entities:
  - entity: input_boolean.boiler_main
    name: Boiler 60 Minutes
  - entity: input_boolean.boiler_15
    name: Boiler 15 Minutes
  - entity: input_boolean.boiler_30
    name: Boiler 30 Minutes
  - entity: input_boolean.boiler_45
    name: Boiler 45 Minutes

```