# openHAB Material Design Icons

This project creates a set of icons for use with [openHAB 2](https://www.openhab.org) from the [Material Design Icons](https://www.materialdesignicons.com) (MDI).

## Use

Type `python3 mdi.py --help` from the command line for more information.

The program uses as many defaults as possible, but any of those can be overwritten with a command line argument

```bash
$ python3 mdi.py --help
usage: mdi.py [-h] [-f FILE] [-i INPUT-PATH] [-o OUTPUT-PATH] [-n] [-q] [-e]

optional arguments:
  -h, --help            show this help message and exit
  -f FILE, --file FILE  get input/output mapping from FILE (default:
                        ./mdi.yaml)
  -i INPUT-PATH, --input-path INPUT-PATH
                        read icons from INPUT-PATH (default:
                        ./download/MaterialDesign-master/icons/svg)
  -o OUTPUT-PATH, --output-path OUTPUT-PATH
                        write icons to OUTPUT-PATH (default:
                        ./iconset)
  -n, --dry-run         parse yaml file for errors (default: False)
  -q, --quiet           don't print status messages to stdout (default: True)
  -e, --empty           empty output folder first (default: False)
```

## Pre-requisites

Install the required libraries:
```
pip3 install -r requirements.txt
```

The script expects the source icons in the input folder. 
[Download the repo as a ZIP](https://github.com/Templarian/MaterialDesign/archive/master.zip) and extract it there first.

## Design

The icon set is built around default colors.
A good overview of available colors can be found [at W3 Schools](https://www.w3schools.com/colors/colors_groups.asp).

The icon colors used are. you can change them in the mdi.py script global

- green: "#32CD32" (lime green)
- orange: "#FF8C00" (dark orange)
- yellow: "#FFD700" (gold)
- red: "#DC143C" (crimson)
- blue: "#0000CD" (medium blue)
- grey: "#C0C0C0" (silver)

Skin colors (based on [emoji](http://blog.emojipedia.org/apple-2015-emoji-changelog-ios-os-x/)):

- skin type 1 and 2: "#FFDBB6"
- skin type 3: "#ECBA8D"
- skin type 4: "#CF8B5D"
- skin type 5: "#AD5C2B"
- skin type 6: "#614235"

Icon colors follow the dynamic state or value when possible. For example:

- Switch ON = green
- Switch OFF = red
- Contact CLOSED = green
- Contact OPEN = red

Gradients, for example for the dimmed `light` states, can be computed with tools like the [color gradient table generator](http://www.herethere.net/~samson/php/color_gradient/) or [RGB Color Gradient Maker](http://www.perbang.dk/rgbgradient/).

The main color is defined in mdi.py line 196 -> change that if you want black icons.

## Different sets

You can create your personal set of icons. This should preferably cover at least the classic icons, but can be extend to your personal preferences.

### Minimal set

Any icon set should at least contain an icon for [each channel category](https://www.eclipse.org/smarthome/documentation/development/bindings/thing-definition.html#channel-categories).
A minimal set is included in the project as `minimal.yaml`.

### Classic

openHAB currently includes an extended 'classic' set of icons.
The classic set `classic.yaml` includes an alternative for any of these icons, including the minimal set.
When you install the classic set, none of the original icons should be visible.

### Extended (default)

An extended set of mapped icons. 
This includes the classic as well as a lot of extra usable icons.
The set is available as `mdi.yaml`

## Configuration

The script parses a YAML configuration file `mdi.yaml`. This file parses (a selected part of) the MDI library and creates a set of .svg icons from the source.

You can specify the source icon, the destination icon, the color of the destination icon and any alias for the icon.
The color should be a valid HTML RGB code (e.g. `#FF00FF`).

## Building the iconset

To build the iconset:

1. Run `python3 mdi.py` from the command line to create the .svg icons in a subfolder `iconset`.
2. Run the `icon_convert.sh` script to create the corresponding .png files.

## Using the iconset

That's easy. Just copy all files from the `iconset` folder to your openHAB configuration in the folder `icons/classic`.
