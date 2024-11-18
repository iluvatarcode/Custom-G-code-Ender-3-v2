# Custom-G-code-Ender-3-v2
Custom g-code for a ender 3 v2 with autoleveling. 

; Ender 3 Custom Start G-code
M190 S60 ; pre-heat bed for abl 
M104 S180 ; start warming extruder to 180
G28 ; home
G29 ; abl
M40; So it uses the mesh
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
; G0 Z2.0 F3000 ; Commented out default move
G0 X2.0 Y20 Z0.3 F5000.0 ; Changed x-coordinate of this move
G0 X2.0 Y200.0 Z0.3 F1500.0 ; Big long wipe, parallel to other lines
G0 Z2.0 F3000 ; Lift to not scratch when moving to real start of job
