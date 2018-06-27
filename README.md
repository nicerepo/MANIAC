# MANIAC

## Description
MANIAC is a modding platform for Android and Fuchsia.

## Project Structure
* [`maniac_manager`](https://github.com/nicerepo/maniac_manager): flutter-based frontend
* [`maniacd`](https://github.com/nicerepo/maniacd): process-detection watchdog
* [`maniacj`](https://github.com/nicerepo/maniacj): modular library injector
* [`maniacli`](https://github.com/nicerepo/maniacli): set of command line tools for developing MANIAC packages
* [`maniacrun`](https://github.com/nicerepo/maniacrun): runtime environment

## Technical Details
### Execution Flow
```
+----------+             +----------+
| manager  |             | maniacd  |
+----------+             +----------+
     |                         |
     | on user command         | on zygote fork
     |                         |
     V                         V
+-----------------------------------+
|              maniacrun            |
+-----------------------------------+
                  | with contol.json
     +-------------------------+
     |            |            |
     V            V            V
+----------+             +----------+
| maniacj  |     ...     | maniacx  |
+----------+             +----------+
```

## Project Timeline
### 2018
- [x] initial public release

### 2019
- [ ] libmaniac_gui

### 2020
- [ ] initial Fuchsia support

### 202x
- [ ] libmaniac_art
- [ ] libmaniac_mono

## Copying
MANIAC is free software. You may freely distribute it under the terms of the license agreement found in LICENSE.

## Prior Art
* CydiaSubstrate (@saurik)
* Liberation (@Razzilient)
* Frida (frida.re)
