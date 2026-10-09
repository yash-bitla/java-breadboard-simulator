# Breadboard Simulator

A desktop simulator for digital logic circuits on a breadboard, written in Java Swing. You place 74xx logic chips on the board, wire their pins, set the inputs, and read the outputs.

This was a college course project from 2020. It is archived and not maintained.

![The breadboard with a 7408 chip placed across the center gap](assets/4.png)

## What it does

- **A breadboard of 64 columns.** Rows A to E and F to J are connected in each column, the same as on a real board.
- **Six logic chips.** Each one is a 14-pin chip that sits across the center gap.

  | Chip | Gates |
  |---|---|
  | 7408 | Four 2-input AND |
  | 7432 | Four 2-input OR |
  | 7404 | Six NOT |
  | 7400 | Four 2-input NAND |
  | 7402 | Four 2-input NOR |
  | 7486 | Four 2-input XOR |

- **Pin actions.** Select a pin to add a chip, an input, an output, Vcc or ground, or to connect it to another pin with a wire.
- **Checks before it runs.** The simulator reports a chip with no Vcc on pin 14 or no ground on pin 7, a gate with only some of its pins connected, and a chip that no gate uses.
- **Inputs and outputs.** A separate window has a switch for each input and a lamp for each output. The outputs change when you change a switch.

## Screenshots

| Pin menu | Chip menu |
|---|---|
| ![The menu that opens when you select a pin](assets/2.png) | ![The menu to select a logic chip](assets/3.png) |

| Outputs with the inputs off | Outputs with the inputs on |
|---|---|
| ![The input and output window](assets/5.png) | ![The input and output window after a change](assets/6.png) |

## Code

All classes are in the package `tryout`, in `src/tryout/`.

| File | Content |
|---|---|
| `Simulator.java` | The `main` method. Opens the window with the board. |
| `BreadBoard.java` | The board, the state of each pin, and the wires |
| `Connect.java` | The menu that opens when you select a pin |
| `ICOption.java` | The menu to select a chip |
| `PinOption.java` | The window to connect one pin to another |
| `Gates.java` | The checks and the logic of each chip |
| `Display.java` | The window with the input switches and the output lamps |

## Build

The code compiles with JDK 17:

```bash
javac -d out src/tryout/*.java
```

## Limits

- **The program does not start from this repository.** It loads 12 small icon images at startup (for example `breadboard_pin.png`, `input_on.png` and `output_off.png`), and those files were not uploaded with the code. The screenshots above are from the original version.
- **It needs an old JDK.** The board extends `java.applet.Applet`, which is deprecated and marked for removal. JDK 17 compiles it with a warning.
- **Digital logic only.** It has no analog parts and no timing: an output changes at once.
- **No tests.** The state of the board is in static fields, so the logic cannot be tested without the windows.
