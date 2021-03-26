# Input number popup card for those using Input Numbers for Volume control (homekit style)
Popup lovelace card with volume slider and optional actions to add more control for input number controlled media players.
Can be used in combination with thomas loven browser_mod or custom pop-up card or in combination with DBuit's homekit style card: https://github.com/DBuit/Homekit-panel-card


<a href="https://www.buymeacoffee.com/ZrUK14i" target="_blank"><img height="41px" width="167px" src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy DBuit A Coffee as this was all his hard work"></a>

## Configuration

### Installation instructions

**Manual installation:**
Copy the .js file from the dist directory to your www directory and add the following to your ui-lovelace.yaml file:

```yaml
resources:
  url: /local/input_number-popup-card.js
  type: module
```

### Main Options

| Name | Type | Default | Supported options | Description |
| -------------- | ----------- | ------------ | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `entity` | string | **Required** | `input_number.avr_volume` | Entity of the input number |
| `icon` | string | optional | `mdi:speaker` | It will use customize entity icon or from the config as a fallback it used speaker icon |
| `fullscreen` | boolean | optional | true | If false it will remove the pop-up wrapper which makes it fullscreen |
| `actions` | object | optional | `actions:`  | define actions that you can activate from the pop-up. |
| `actionSize` | string | optional | `50px`  | Set the size of the action buttons default `50px` |
| `actionsInARow` | number | optional | 3 | number of action that will be placed in a row under the slider |
| `sliderWidth` | string | optional | 150px | The width of the slider |
| `sliderHeight` | string | optional | 400px | The height of the slider |
' `borderRadius` | string | optional | 12px | The border radius of the slider and switch |
| `sliderColor` | string | optional | "#FFF" | The color of the slider |
| `sliderThumbColor` | string | optional | "#ddd" | The color of the line that you use to slide the slider  |
| `sliderTrackColor` | string | optional | "#ddd" | The color of the slider track |
| `settings` | boolean | optional | false | When it will add an settings button that displays the more-info content see settings example for my light popup for more options/information [here]: https://github.com/DBuit/light-popup-card#settings |
| `settingsPosition` | string | optional | `bottom`  | set position of the settings button options: `top` or `bottom`. |

To show actions in the pop-up you add `actions:` in the config of the card follow bij multiple actions.
These actions are calling a service with specific service data.
```
actions:
  - service: scene.turn_on
    service_data:
      entity_id: scene.energie
    color: "#8BCBDD"
    name: energie
  - service: homeassistant.toggle
    service_data:
      entity_id: light.voordeurlicht
    name: voordeur
    icon: mdi:lightbulb
```
The name option within a scene is **optional**
You can also set the `entity_id` with value **this** if you use **this** it will be replaced with the entity the pop-up is opened for.


Example configuration with next, play/pause and previous actions
```
type: custom:input_number-popup-card
actions:
  - service: media_player.media_previous_track
    service_data:
      entity_id: this
    name: previous
    icon: mdi:skip-previous
  - service: media_player.media_play_pause
    service_data:
      entity_id: this
    name: play/pause
    icon: mdi:play-pause
  - service: media_player.media_next_track
    service_data:
      entity_id: this
    name: next
    icon: mdi:skip-next
```

### Screenshot

![Screenshot](screenshot.png)
