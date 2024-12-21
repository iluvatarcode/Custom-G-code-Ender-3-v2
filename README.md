# Custom-G-code-Ender-3-v2
Custom g-code for a ender 3 v2 with autoleveling. 

; Ender 3 Custom Start G-code
M104 S195 ; start warming extruder to 195
M190 S60 ; preheat bed for abl
G28 ; home
;G29  abl if needed (auto bed leveling)
M420 S1; Use mesh redundant.
;*** Start Preheating ***
M190 S{material_bed_temperature_layer_0} ; heat to setting
M109 S{material_print_temperature_layer_0} ﻿T0 ; heat to setting
;*** End Preheating ***
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
M300 P250 ; play chime to indicate print starting
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish



//_______________________
; Ender 3 Custom End G-code
G91 ;Relative positioning
G1 E-2 F2700 ;Retract a bit
G1 E-2 Z0.2 F2400 ;Retract and raise Z
G1 X5 Y5 F3000 ;Wipe out
G1 Z10 ;Raise Z more
G90 ;Absolute positioning

G1 X0 Y200 ;Y{machine_depth} Present print
M106 S0 ;Turn-off fan
M104 S0 ;Turn-off hotend
M140 S0 ;Turn-off bed

M84 X Y E ;Disable all steppers but Z


__________________

Important settings
Retraction retract speed 40mm/s
