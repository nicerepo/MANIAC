# MANIAC

## Description
MANIAC is a modern dynamic binary instrumentation engine for Android and Fuchsia.

## Project Structure
* [`maniac_manager`](https://github.com/nicerepo/maniac_manager): A Flutter-based frontend for managing modules.
* [`maniacd`](https://github.com/nicerepo/maniacd): Process-detection watchdog that monitors `zygote`.
* [`maniacj`](https://github.com/nicerepo/maniacj): The library injector module.
* [`maniacli`](https://github.com/nicerepo/maniacli): Set of command line tools for developing MANIAC modules.
* [`maniacrun`](https://github.com/nicerepo/maniacrun): The IPC/bootstrap program.

## FAQ
### How does it differ from Xposed?
The aims are similar, but implementation details greatly differ.
* MANIAC modules work further down the stack, as the engine primarily instruments native code as opposed to ART/Dalvik. Without the constraints of a process VM, MANIAC modules are far more capable.
* MANIAC requires no permanent modification of the host system, as it only needs a single root-privileged process to bootstrap the runtime environment.

### Where can I find more modules to install?
The project is currently in a pre-alpha stage and no official modules repository exist as of yet. Refer to the [`maniac_demo`](https://github.com/nicerepo/maniac_demo) project for building your own modules.

## Technical Details (WIP)
### Execution Flow
Users may install pre-programmed modules via MANIAC manager. `maniacrun` bootstraps the DBI environment by communicating with various sub-modules of MANIAC.

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
All of the components are free software released under the GNU General Public License (GPLv3) unless otherwise stated. Refer to the individual repository for more information.

## Prior Art
* CydiaSubstrate (@saurik)
* Liberation (@Razzilient)
* Frida (frida.re)
