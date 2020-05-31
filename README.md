# ESPHome Arduino Song Converter

## About

Converts piezo buzzer [Arduino Songs](https://github.com/robsoncouto/arduino-songs) to ESPHome scripts

The current songs are available in the songs directory in yaml form, though largely untested

Doesn't use the 90% note length feature to add separation between notes because it would double the total length of the
generated script due to needing a 10% rest for every note

Some of the songs, such as the Doom one, are likely too long to actually use without crashing

Block comments in note arrays could probably cause failures in some cases

## Usage
An ESP8266 device with a passive piezo buzzer is required. An esp8266_pwm output entry is used to 
drive the buzzer. The actual music playing is done by a script that controls the buzzer.

#### Example
```yaml
# Buzzer
output:
  - platform: esp8266_pwm
    pin: D1
    id: buzzer

# Nokia music script
script: 
  - id: play_song
    then:
      - output.set_level:
          id: buzzer
          level: 20%
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 659Hz
      - delay: 166ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 587Hz
      - delay: 166ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 370Hz
      - delay: 333ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 415Hz
      - delay: 333ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 554Hz
      - delay: 166ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 494Hz
      - delay: 166ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 294Hz
      - delay: 333ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 330Hz
      - delay: 333ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 494Hz
      - delay: 166ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 440Hz
      - delay: 166ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 277Hz
      - delay: 333ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 330Hz
      - delay: 333ms
      - output.esp8266_pwm.set_frequency:
          id: buzzer
          frequency: 440Hz
      - delay: 666ms
      - output.turn_off: buzzer
```