# sigsci-sounds
Listen to the soothing sounds of attacks and anomalies.

### Description

The [Signal Sciences] (https://signalsciences.com) web protection platform offers a rich API that enables limitless integrations and automation. Or, at lease only limited by your imagination. As an example of this, sigsci-sounds is a utility to audibility monitor when Signal Sciences detects attack or anomaly events against your web site. You literally can listen to your site being attacked.

The utility is configurable so you can define which attacks or anomalies you want to hear.

Note: obviously you must be a Signal Sciences customer to make use of this utility.

### Requirements

- Golang support
- OS X (currenlty, sigsci-sounds was built & tested on OS X, and uses default commands and sound files found on OS X)
- A Signal Sciences API account.

### Instructions

If you have `make` on your system run `make install`, be sure your `$GOPATH` is set. Or you can run `make run` to build and run `sigsci-sounds`.

By default `sigsci-sound` will look for the configuration file in its current direcotry, e.g. `./sigsci-sounds.conf`. However, you can export a different location using the variable `SIGSCI_SOUNDS_CONFIG`, e.g. `export SIGSCI_SOUNDS_CONFIG=/etc/sigsci/sigsci-sonds.conf`.

The configuration file is JSON format. It requires your API account username and password, and at least one tag entry. See the provided [configuration file] (https://github.com/foospidy/sigsci-sounds/blob/master/sigsci-sounds.conf) as an example.

#### Defining a tag entry

Each entry requires three fields: name, sound, and text.

- __name__ is the actual tag "short name" you want to monitor for. This can be a Signal Sciences default sytem tag, or a custom tag.
- __sound__ is the absolute path to the sound file you want to play for the specified tag name. Optionally, you can set this value to `say`, which will cause your system to speak the text configured in the __text__ field.
- __text__ is the text to be spoken by the system when the configured tag event occurs. This only occurs when the __sound__ field has the value of `say`. This field must be presetn, and at minimum an empty value, e.g. `"text": ""`

