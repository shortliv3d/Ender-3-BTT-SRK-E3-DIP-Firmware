# Ender-3-BTT-SRK-E3-DIP-Firmware
BIGTREETECH-SRK-E3-DIP Board LCD bed leveling no BLT

[env:STM32F103R_bigtree]
(...)
build_flags       = !python Marlin/src/HAL/HAL_STM32F1/build_flags.py
  ${common.build_flags} -DDEBUG_LEVEL=0 -std=gnu++14 -DHAVE_SW_SERIAL
(...)
That is it, no additional change is required in this file.

Marlin/Configuration.h

#define SERIAL_PORT -1
#define SERIAL_PORT_2 2
#define MOTHERBOARD BOARD_BIGTREE_SKR_E3_DIP
#define CUSTOM_MACHINE_NAME "Ender-3"
#define DEFAULT_NOMINAL_FILAMENT_DIA 1.75
#define TEMP_SENSOR_BED 1
#define BED_MAXTEMP 125
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 93 }
#define DEFAULT_MAX_FEEDRATE          { 500, 500, 5, 50 }
#define INVERT_Y_DIR false
#define INVERT_Z_DIR true
#define X_BED_SIZE 235
#define Y_BED_SIZE 235
#define Z_MAX_POS 250
#define HOMING_FEEDRATE_XY (40*60)
#define DISPLAY_CHARSET_HD44780 WESTERN
#define SDSUPPORT
#define CR10_STOCKDISPLAY
Comment these lines (add // to line beginning:

  // Ultimaker
  //#define DEFAULT_Kp 22.2
  //#define DEFAULT_Ki 1.08
  //#define DEFAULT_Kd 114
  
Add these lines 

  // Creality Ender-3
  #define DEFAULT_Kp 21.73
  #define DEFAULT_Ki 1.54
  #define DEFAULT_Kd 76.55


#define X_DRIVER_TYPE  TMC2208
#define Y_DRIVER_TYPE  TMC2208
#define Z_DRIVER_TYPE  TMC2208
#define E0_DRIVER_TYPE TMC2208


#define PID_EDIT_MENU
#define PID_AUTOTUNE_MENU
chaned names of preheats, added PLA + at 215/80 and PETG at 240/80
#define PREHEAT_1_TEMP_HOTEND 215
#define PREHEAT_1_TEMP_BED     80
#define PREHEAT_1_FAN_SPEED   255 // Value from 0 to 255
#define PREHEAT_2_FAN_SPEED   255 // Value from 0 to 255

Mesh bed levelingThese changes are required in this file to make it work:

#define MESH_BED_LEVELING ---
#define RESTORE_LEVELING_AFTER_G28
#define MESH_INSET 35
#define LCD_BED_LEVELING
#define EEPROM_SETTINGS
#define EEPROM_AUTO_INIT

 Chaged ADVANCED_PAUSE_FEATURE for better pause behavior while using Cura:

#define NOZZLE_PARK_FEATURE
Marlin/Configuration_adv.h

Current for stepper motors to help run cooler 

#define X_CURRENT     760
#define Y_CURRENT     760
#define Z_CURRENT     760
#define E0_CURRENT    900


#define TMC_DEBUG

Personal changes listed below

#define QUICK_HOME
#define LCD_INFO_MENU
#define STATUS_MESSAGE_SCROLLING
#define LCD_SET_PROGRESS_MANUALLY
#define SCROLL_LONG_FILENAMES
#define BABYSTEPPING
#define DOUBLECLICK_FOR_Z_BABYSTEPPING
#define ADVANCED_PAUSE_FEATURE
