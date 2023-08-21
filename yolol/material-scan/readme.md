# Material Scanner

The AHIS Mowteng features a material scanner to identify asteroids regarding their contents and size (kilovoxel and stack-size).

## Control Interface

The Control Interface lets you initiate a material scan and read the findings.

## Setup

The Material Scanner Assembly consists of:

- a Hybrid Button
- an Advanced Grid Display
- a Material Point Scanner (Assembly)
- a Rangefinder & a Progress Bar 12x24

It further needs:
- a YOLOL rack with a Chip Core (3 slots)
- 3 basic YOLOL chips
- a Memory Relay
- one YOLOL memory chip

### Hybrid Button

The button starts the material scan by activating the Material Point Scanner and Rangefinder devices.

Its device field **ButtonState** must be renamed to **Scan**. The **ButtonStyle** value must be changed to **1**.

### Advanced Grid Display

The current working state and scan results are rendered on this display.

Change the following device fields to these values:

| Device Field | Value |
| --- | --- |
| LayerGridSize | 25 |
| ShowCursor | 0 |
| MoveCursor | 0 |

Some fields of the device also needs to be renamed according to the pattern "MSD" (**M**aterial **S**canner **D**isplay):

| Original Device Field Name | Renamed Device Field Name |
| --- | --- |
| SelectedLayer | MSDL |
| GridLayerTextHue | MSDLTH |
| CursorX | MSDX |
| CursorY | MSDY |
| ClearLayerGrid | MSDCL |
| Input | MSDI |

### Progress Bar 12x24 - Distance

This shows the distance from the Rangefinder/Material Point Scanner Assembly to the target. 

### Progress Bar 12x24 - Credit Value

This display is currently _unused_. <br>
Change the device field **PanelValue** to **CreditValue** and its value to **INOP**.

See Future-Tech for more information.

### Material Point Scanner

The actual scanning device that does the work.<br>

Rename the device field **Scan** to **DoScan**. Leave everything else untouched.

### Rangefinder

## YOLOL

### Register global variables

Some global state variable are used to control the behaviour of the material scanner.<br>
A Memory Relay and a Memory Chip are used to register these variables. 

| Variable | Usage |
| --- | --- |
| MSS | stores the current **M**aterial **S**can **S**tate |
| MSSIdle | Idle state |
| MSSScanning | Scanning state |
| MSSReset | Reset state (wipes the display) |

Note that the input and output sides of the memory relay must be in the same network as all other devices.

### Chips

Put the contents of all YOLOL files into a basic YOLOL Chip and let the magic do its trick.

## Future-Tech

It was planned to also estimate the credit value of an asteroid, based on their contents/materials. Unfortunately there are 2 problems with this idea:

1. The user has to change and adapt to market prices for each resource regularly.
2. The YOLOL code is not flexible enough to do this properly.

We're skipping this feature right now, but keep in on the roadmap for later.