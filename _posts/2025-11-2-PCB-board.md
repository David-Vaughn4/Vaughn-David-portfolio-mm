I prepared a PCB file in Makera Cam and milled it out on a Makera Carvera machine. Below is a picture of my milled PCB board (really its the two that are shared between Evan, Jake, and myself):

<img src="https://github.com/user-attachments/assets/7f304899-2663-4428-833c-5f2758a4fe02" width=500 height=500/>

This is the detailed workflow I created for both preparing the file and milling it out:

## Preparing Design:
1. Open new 3D project
2. Set material to PCB: Edit→Material→PCB
3. Set dimensions
    - X = 127mm
    - Y = 101mm
    - Z = 1.7mm
4. Download files from Fab drive: (blue folder named Dubick)
    - Resistance1-F_Cu.gbr
    - Resistance1-PTH.drl
    - Resistance1-Edge_Cuts.gbr
5. Import each of these files in MakeraCAM:
    - File→Import PCB→Downloads→Resistance1-Edge_Cuts.gbr→Open
    - File→Import PCB→Downloads→Resistance1-PTH.drl→Open
    - File→Import PCB→Downloads→Resistance1-F_Cu.gbr→Open
6. Anchor lower left corner:
    1. Select whole design (highlight over everything)
    2. Click "m" key
    3. Select lower left corner in "Anchor" diagram at the top of new pop up (in top right corner of screen)
    4. Under "Location" in pop up, set X to 6 and Y to 6 (offsets design from very edge of material)
    5. Design should have moved to align with axes given
7. Path:
    1. Under "2D Layers" menu, hide (eye with red cross through):
        - Resistance1-F_Cu.gbr_pad
        - Resistance1-PTH.drl_0.900 mm
        - Resistance1-PTH.drl_1.400 mm
    2. Select 2D Path (in tool bar)→2D Pocket
    3. Select whole (visible) design
    4. Set "End Depth" to .05mm
    5. Add tool x2
        - 8mm Corn
        - .2mm*30Engraving(Metal)
    6. Calculate
8. Drilling holes:
    1. 2D Path→2D drilling
    2. Under "2D Layers" menu, hide (eye with red cross through) all but file with holes to drill
    3. End Depth: 1.7mm
    4. Add tool: 8mm Corn
    5. Calculate
9. Outside cut:
    1. 2D Path→2D Contour
    2. Under "2D Layers" menu, hide (eye with red cross through) all but file with outside cut (Resistance1-Edge_Cuts.gbr)
    3. End Depth: 1.7mm
    4. Strategy: Outside
    5. Tabs: Custom
        - Tab Shape: Triangle
        - Select "Add"
        - Click 3 places on outer edge (spaced fairly evenly apart)
    6. Add tool: 8mm Corn
    7. Calculate
10. Path→Export→Export OR if you want to edit file on milling machine's computer, File→Save As, save file in downloads with .mkc format (file-type)
11. Upload file to your folder in Fab google drive

## Milling Design:
1. Installing material:
    1. Slightly loosen (not remove) all bolts in machine bed except the 3 that are fully within the metal jig/holder (use screwdriver on right side of machine)
        - If copper board already on bed with design milled into bottom left corner, remove and reorient if possible or else replace
    2. Orient PCB board on CNC machine so that your design will fit in bottom left corner (as it was displayed on Makera CAM)
    3. Adjust rectangular metal holders near middle of bed (keep bolts where they are, slide and rotate rectangular piece) to be able to slide material under loosened bolts, and then do so
    4. Move/rotate both rectangular metal back so that short end of rectangle with slot aligns with material (holding it down)
    5. Screw all loosened bolts down fairly tightly (securing material, not overly tight)
2. Running file:
    1. Download gcode.nc file from Fab google drive
    2. Open Cavera Controller
    3. Open file (top left corner) → Upload File → (should be in Downloads) select your gcode file (yourfilename.nc) → "Upload & Select" 
    4. Idle (top left) → COM Port ___ (some number)
    5. Additional settings (top right dropdown) → Display Manual Controls → Home
    6. Tool status → ensure Voltage>3.6V
    7. Second most right option on bottom bar → select (check) auto vacuum + select (check) auto-levelling; select Run
    8. Machine should touch down at 25 points on material and then file should run (whole design should be automatically milled)

## Issues:
We did not run into any major issues while preparing or milling this design because of our instructors' (Mr. Dubick and Mr. Budzichowski) close guidance.

## Files:
These are the Makera CAM and gcode files I used: [files](../assets/files/PCB%20board.zip)