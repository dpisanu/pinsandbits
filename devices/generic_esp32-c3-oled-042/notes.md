# Notes: Generic ESP32-C3 OLED 0.42"

## ⚠️ Wi-Fi antenna ⚠️

The onboard antenna on this unit performs poorly.

Observed behavior:

- Default or high transmit power prevented reliable Wi-Fi connection.
- In some cases the board could connect but not hold a stable connection.
- Reducing Wi-Fi output power made the connection usable.

Current known-good setting is at 10db. 
Test in 5db steppings starting from 5db.

## OLED controller and visible area

The working display model on this unit is **SH1106 128x64**

The I2C address for the board is **0x3C**

The visible top-left corner is approximately:

```text
x = 27
y = 9
```

The following display model settings did not work on this unit:

- SSD1306 128x64
- SSD1306 72x40

## Display 

### Display model test matrix

| Model setting | Result |
|---|---|
| SSD1306 72x40 | Does not work on this unit |
| SSD1306 128x64 | Does not work on this unit |
| SH1106 128x64 | Working on this unit |

### Display size terminology

`72x40` and `128x64` describe pixel resolution:

```text
72x40   = 72 pixels wide, 40 pixels high
128x64  = 128 pixels wide, 64 pixels high
```

The tiny 0.42" OLED only has a small visible area, roughly:

```text
72 pixels wide
40 pixels high
```

With this board, there are two different sizes involved:

```text
Physical visible OLED area:  about 72x40 pixels
Controller memory layout:    behaves like 128x64 pixels
```

The display controller can be addressed as if it has a larger internal drawing buffer:

```text
128 pixels wide
64 pixels high
```

Simplified 128×64 controller canvas:

```text
+------------------------------------------------+
|                                                |
|                           hidden pixels        |
|                                                |
|          visible 72x40 OLED area               |
|          starts around x=27, y=9               |
|          +----------------------------+        |
|          | HELLO                      |        |
|          |                            |        |
|          |                            |        |
|          +----------------------------+        |
|                                                |
+------------------------------------------------+
```

Current working drawing origin:

```text
X = 27
Y = 9
```

## Onboard blue LED

The onboard blue LED is connected to **GPIO8** and is inverted on this unit.

GPIO8 may produce strapping-pin warnings during build/compile. Avoid using GPIO8 for external peripherals unless that interaction is intentional and tested.

## TODO

- Confirm whether another unit from the same order uses the same OLED controller.
- Measure RSSI and packet stability at different Wi-Fi output power values.
