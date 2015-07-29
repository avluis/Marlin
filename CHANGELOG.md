===========================================
# Ez3D Phoenix - Modified FW
===========================================

## [1.0.0] - 2015-07-29
### Merge
- Reverting/Moving over Phoenix to Marlin Release branch.

### Changed
- The Phoenix branch will now track the Marlin Release branch to keep things as stable as possible.
- Z-Probe and Z-Servo branches are now merged with this branch.

### Notes:
- You will need to modify Configuration.h to suit your Phoenix if you have a Z-Probe or Servo.
- Just enable PHOENIX_Z_PROBE or PHOENIX_Z_SERVO according to your hardware.
- I am making these changes from prior branches and not from actual hardware - so if you encounter
- any issues, I ask that you contact me with your configuration and ready to diagnose as I no
- longer have a Phoenix of my own to test with.

## [0.0.9-beta] - 2015-01-06
### Merge
- Updated to the latest Marlin Firmware
-- Marlin now lives here:
[Marlin]: https://github.com/MarlinFirmware/Marlin

### Changed
- Some settings have been set to Marlin defaults (they are not needed for the Phoenix to function)

### Notes:
- Enough changes to Marlin have been made to function with Phoenix.
- I will be working on the Z-Probe Branch indefinitely and will only be updating this branch
- when enough changes to Marlin warrant an update.
- Need testers with no Z-Probe (of any kind), with Inductive Z-Probes and micro-switch.
- The goal is to create a robust set of configurations for those Phoenix configurations
- to submit to Marlin so they end up in the examples folder (this will benefit us all).
- If you are in the Phoenix group, you know how to contact me.
- Otherwise, make use of the issue tracker on GitHub (and join the G+ Phoenix Group)

## [0.0.8-beta] - 2014-12-19
### Added
- Corrected Motor Current settings (more setting are available for 'other' Phoenix models)
*Configuration_adv.h*
    #define DIGIPOT_MOTOR_CURRENT { 135, 135, 185, 135, 135 } // Phoenix 01

### Changed
- Bringing this back to defaults
*Configuration.h*
    #define PID_dT ((OVERSAMPLENR * 10.0)/(F_CPU / 64.0 / 256.0))

- Always tweaking PID values
*Configuration.h*
    #define DEFAULT_Kp 11.37
    #define DEFAULT_Ki 0.93
    #define DEFAULT_Kd 67.43

- Reduced travel area (can't travel this far)
*Configuration.h*
    #define Y_MAX_POS 190

### Disabled
- Here are the other settings
*Configuration_adv.h*
     #define DIGIPOT_MOTOR_CURRENT { 115, 115, 115, 115, 115 } // Phoenix 05
     #define DIGIPOT_MOTOR_CURRENT { 100, 100, 100, 100, 100 } // Phoenix 06
     #define DIGIPOT_MOTOR_CURRENT { 185, 185, 185, 185, 185 } // Phoenix 07
     #define DIGIPOT_MOTOR_CURRENT { 135, 60, 60, 60, 60 } // Phoenix 06

- No need for this to be on
*Configuration.h*
    #define TEMP_SENSOR_2 0

- Testing this Phoenix supplied setting
*Configuration_adv.h*
    #define SD_FINISHED_STEPPERRELEASE false

### Merge
- Updated to the latest Marlin Firmware

## [0.0.7-beta] - 2014-12-15
### Added
- CHANGELOG.md to zip directory (will be included with build releases from now on.
- Making use of `STRING_CONFIG_H_AUTHOR` to include name, build info and build number.
*Configuration.h*
    #define STRING_CONFIG_H_AUTHOR "(Luis E Alvarado, Ez3D Phoenix Mod FW, 0.0.7-beta)"

### Changed
- Increased retract distance after homing for z axis.
*Configuration_adv.h*
    #define Z_HOME_RETRACT_MM 3

- Tweaking acceleration values to reduce Y belt slipping (needs testing!).
*Configuration.h:*
    #define DEFAULT_MAX_FEEDRATE {200, 100, 150, 25}
    #define DEFAULT_MAX_ACCELERATION {2500,500,1000,10000}
    #define DEFAULT_ACCELERATION 1000

### Disabled
- Until I know what it does (Marlin does not state anything on this):
*Configuration.h*
    #define TEMPERATURE_SENSORS 3

### Notes
- Slowly adding comments to source to make it easier for others to track what changes I am making to Marlin (and for myself for 'those' days). Also removed comments to files that won't be seeing any changes from me, e.g; Marlin.ino
- I need input from users of this firmware, I'm trying to make this as good as possible for Phoenix users. Even for those that have given up on Ez3D and are stuck with a barely working, or not working at all, Phoenix.

## [0.0.6-alpha] - 2014-12-13
### Changed
- Tweaking acceleration values to reduce belt slipping.
*Configuration.h:*
    #define XY_TRAVEL_SPEED 5000
    #define DEFAULT_MAX_ACCELERATION {3000,2000,3000,10000}
    #define DEFAULT_ACCELERATION 2500
    #define DEFAULT_XYJERK 15.0

## [0.0.5-alpha] - 2014-12-12
### Changed
- Minor tweaks to dial in PID values for the stock extruder.
*Configuration.h*
    #define HEATER_0_MINTEMP 2
    #define BED_MINTEMP 2
    #define HEATER_0_MAXTEMP 280
    #define BED_MAXTEMP 130
    #define PID_MAX 255
    #define DEFAULT_Kp 10.92
    #define DEFAULT_Ki 0.47
    #define DEFAULT_Kd 62.82
*Configuration_adv.h*
    #define WATCH_TEMP_PERIOD
    #define WATCH_TEMP_INCREASE

## [0.0.4-alpha] - 2014-12-11
### Added
- Tweaks to help the Ez3D software "find" the Phoenix 3D Printer (not guaranteed).
*Configuration.h*
    #define CUSTOM_MENDEL_NAME "Ez3D Phoenix"
    #define EZ3D_MACHINE_MODEL_PHOENIX
    #define TEMPERATURE_SENSORS 3
*pins.h*
    #define EXTRUDER_FAN_PIN 8

### Changed
- From now on, new builds will have the extruder fan turns on automatically when extruder0 is over 50 Celcius.
*Configuration_adv.h*
    #define EXTRUDER_0_AUTO_FAN_PIN 8
*pins.h*
    #define FAN_PIN -1

- Initial PID tuning.
*Configuration.h*
    #define DEFAULT_Kp 13.34
    #define DEFAULT_Ki 0.9
    #define DEFAULT_Kd 75.19
    #define DEFAULT_bedKp 504.79
    #define DEFAULT_bedKi 98.75
    #define DEFAULT_bedKd 645.12
    #define PID_MAX 245
    #define PID_FUNCTIONAL_RANGE 60

- Making use of a known temperature table.
*Configuration.h*
    #define TEMP_SENSOR_0 1
    #define TEMP_SENSOR_2 1
    #define TEMP_SENSOR_BED 1

- Changed retract distance after homing.
*Configuration_adv.h*
    #define X_HOME_RETRACT_MM 2
    #define Y_HOME_RETRACT_MM 5
    #define Z_HOME_RETRACT_MM 2

- Tweaked default values for PLA and ABS.
*Configuration.h*
    #define PLA_PREHEAT_HOTEND_TEMP 190
    #define PLA_PREHEAT_HPB_TEMP 60
    #define PLA_PREHEAT_FAN_SPEED 230
    #define ABS_PREHEAT_HOTEND_TEMP 225
    #define ABS_PREHEAT_HPB_TEMP 80
    #define ABS_PREHEAT_FAN_SPEED 230

### Enabled
- Quick Home for control software that use it.
*Configuration_adv.h*
    #define QUICK_HOME

- Removed extruder minimun temperature - handle this with care!
*Configuration.h*
    #define EXTRUDE_MINTEMP 0

### Disabled
- Dangerous extrude and lengthy extrude (will let you use the extruder at all times).
*Configuration.h*
    #define PREVENT_DANGEROUS_EXTRUDE
    #define PREVENT_LENGTHY_EXTRUDE

## [0.0.3-alpha] - 2014-12-11
# "ABS build"

### Changed
- Extruder fan can now be controlled by 3D control software.
*Configuration_adv.h*
    #define EXTRUDER_0_AUTO_FAN_PIN -1
*pins.h*
    #define FAN_PIN 8

## [0.0.2-alpha] - 2014-12-11
# "PLA build"

### Changed
- Enable on-board fan to turn on when dictated by Marlin (when stepper drivers are enabled, etc.)
*Configuration_adv.h*
    #define CONTROLLERFAN_PIN 2
*pins.h*
    #define FAN_PIN -1

- Extruder fan turns on automatically when extruder0 is over 50 Celcius.
*Configuration_adv.h*
    #define EXTRUDER_0_AUTO_FAN_PIN 8

- EEPROM functionality enabled.
*Configuration.h*
    #define EEPROM_SETTINGS
    #define EEPROM_CHITCHAT

- Travel limits set to:
*Configuration.h*
    #define X_MAX_POS 300
    #define X_MIN_POS 0
    #define Y_MAX_POS 195
    #define Y_MIN_POS 0
    #define Z_MAX_POS 200
    #define Z_MIN_POS 0

### Disabled
- `ENDSTOPS_ONLY_FOR_HOMING`
*Configuration_adv.h*
    #define ENDSTOPS_ONLY_FOR_HOMING

## [0.0.1-alpha] - 2014-12-10
### Notes
*Initial build:*
- Removes some of Ez3D's changes to function with other control software.
- Changes are done via firmware only, no modification to hardware, no need to move T2 to T3.

## Links
[GitHub]: https://github.com/avluis/Marlin/tree/Marlin_phoenix
[Archived]: https://www.dropbox.com/sh/4k6cxtwi6mrev4x/AACbAkAC9fTnTcYgQjkfhWSca?dl=0
[Rambo Docs]: https://www.dropbox.com/sh/oku1ld76927fydj/AAADQjdIOsz2c1Ea-Jv7zGQVa?dl=0