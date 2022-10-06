# Blueprints for Home Assistant
Blueprints could be added with following:

1. Go to `Settings / Automation & Scenes / Blueprints` and press `Import Blueprint` in the lower right corner.
2. Paste github url of the needed yaml file and press `Preview Blueprint`.
3. Read a description and press `Import Blueprint`.

## Turn on/off Switch on Time

> Link to the file:
> ```
> https://github.com/LoSk-p/home-assistant-blueprints/blob/main/control_switch_on_time.yaml
> ```

After you've added the blueprint press `Create Automation` near it:

![blueprints](./media/blueprints.jpg)

Then fill nessessary fields:

- `Switch State` and `Switch` must be **the same entity id** of controlled switch device.
- `Turn on time` and `Turn off time` is the time when you want tu turn on/off your switch.
- `Wait time` is the delay to turn off the switch if it was turned on by user.

![create_blueprint](./media/create_blueprint.jpg)