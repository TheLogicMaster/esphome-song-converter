# ESPHome Arduino Song Converter

Converts piezo buzzer [Arduino Songs](https://github.com/robsoncouto/arduino-songs) to ESPHome scripts

The current songs are available in the songs directory in yaml form, though largely untested

Doesn't use the 90% note length feature to add separation between notes because it would double the total length of the
generated script due to needing a 10% rest for every note

Some of the songs, such as the Doom one, are likely too long to actually use without crashing

Block comments in note arrays could probably cause failures in some cases