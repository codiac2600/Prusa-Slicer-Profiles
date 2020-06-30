# Prusa Slicer Profiles for Stock Marlin and Original Prusa Firmware 


### Firmware
* [SKR Bear Firmware](https://github.com/codiac2600/SKR-Bear-Marlin)
* [Prusa Firmware](https://github.com/prusa3d/Prusa-Firmware)

## Start Gcode 

### Stock Marlin ABL

G90 ; Use absolute positioning
M83  ; extruder relative mode

M140 S[first_layer_bed_temperature] ; set bed temp
M109 S150 ; Set extruder temp before bed level
M190 S[first_layer_bed_temperature] ; wait for bed temp

G28 ; home all without mesh bed level
G29 ; Mesh Bed Level
G1 X0 Z0.6 Y-3.0 F3000.0 ; Move off the grid to prep for purge

M109 S[first_layer_temperature] ; wait for extruder temp

G92 E0.0
G1 X100.0 E30  F1000.0 ; intro line
G92 E0.0

### Stock Marlin UBL

G90 ; Use absolute positioning
M83  ; extruder relative mode

M140 S[first_layer_bed_temperature] ; set bed temp
M109 S150 ; Set extruder temp before bed level
M190 S[first_layer_bed_temperature] ; wait for bed temp

G28 ; home all without mesh bed level
G29 L1 ; Load Mesh in slot 1
G29 J ; 3 point alignment
G1 X0 Z0.6 Y-3.0 F3000.0 ; Move off the grid to prep for purge

M109 S[first_layer_temperature] ; wait for extruder temp

G92 E0.0
G1 X100.0 E30  F1000.0 ; intro line
G92 E0.0

### Stock Prusa Firmware

G90 ; absolute positioning 
M83  ; extruder relative mode
M140 S[first_layer_bed_temperature] ; set bed temp
M109 S160 ; Set extruder temp before bed level
M190 S[first_layer_bed_temperature] ; wait for bed temp


G28 W ; home all without mesh bed level
G80 ; mesh bed leveling set 3x3, 5x5, or 7x7 in settings menu

G1 Y-3.0 Z0.6 F1000.0 ; go outside print area for purge

M109 S[first_layer_temperature] ; wait for extruder temp

G92 E0.0
G1 Z0.2 E8 ; Purge Bubble
G1 X60.0 E9.0  F1000.0 ; intro line
G1 X100.0 E12.5  F1000.0 ; intro line
G92 E0.0





