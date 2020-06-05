# Precise trigger
Trigger for Kalliope

## Installation
```bash
kalliope install --git-url https://github.com/corus87/kalliope_trigger_precise.git
```
To use precise you need to install precise-engine. 
[Here](https://github.com/MycroftAI/mycroft-precise/releases) you can find the binary data for your platform. 

For installation on the raspberry follow these instructions:

```bash
cd your_starter_kit/resources/trigger/precise
wget https://github.com/MycroftAI/mycroft-precise/releases/download/v0.3.0/precise-engine_0.3.0_armv7l.tar.gz
tar -xvzf precise-engine_0.3.0_armv7l.tar.gz
rm precise-engine_0.3.0_armv7l.tar.gz
```

## Parameters

| parameter    | required | type    | default | choices         | comment                                                                                          |
|--------------|----------|---------|---------|-----------------|--------------------------------------------------------------------------------------------------|
| pb_file      | TRUE     | string  |         |                 | Path to the precise wake word.                                                                   |
| sensitivity  | FALSE    | string  | 0.5     | between 0 and 1 | Increasing the sensitivity value lead to better detection rate, but also higher false alarm rate.|

## Example settings

```yaml
# This is the trigger engine that will catch your magic work to wake up Kalliope.

default_trigger: "precise"

# Trigger engine configuration
triggers:
  - precise:
      pb_file: "trigger/precise_models/your_wake_word.pb"
```

## Available Precise wake words

[Here](https://github.com/MycroftAI/precise-data/tree/models) and [here](https://github.com/MycroftAI/precise-community-data) you can find some available wake words. 
You need the wake_word.pb and wake_word.pb.params file, both need to be in the same directory. 

## Create your own wake word

To create your own wake word, follow the instructions [here](https://github.com/MycroftAI/mycroft-precise/wiki/Training-your-own-wake-word#how-to-train-your-own-wake-word). 
You can find some additional information [here](https://community.rhasspy.org/t/mycroft-precise-installation-and-use/)
## Note

You have to add the path to the trigger folder in your settings.
E.g.:
```
# ---------------------------
# resource directory path
# ---------------------------
resource_directory:
  trigger: "resources/trigger"
  neuron: "resources/neurons"
  stt: "resources/stt"
  tts: "resources/tts"
```