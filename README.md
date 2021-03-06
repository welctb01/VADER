# VADER
Technical Prompt Q2

Visual Aid for Deterring Enemy R2D2s (VADER) is a simulator to practice traversing a battlefield with randomly distributed Remote Radio Detection Devices (R2D2).  

The GUI:  
The top row displays the status of your three platoons.  When your platoon detects an R2D2, the number of detected R2D2s is displayed next to the platoon label.  The x any y offset to the detected R2D2s is displayed under the platoon label.  The tick label is a counter and increments each time you move a platoon.  The show detections checkbox will show the number of times your platoons have been detected by an R2D2.  The show R2D2s checkbox will show the hidden locations of R2D2s when enabled.  With each mouse click/key press the R2D2’s will once again be hidden to discourage the user to keep the R2D2 locations visible.  The reset button starts a new simulation.

How to Play:  
Click on a platoon you want to move.  Once a platoon is selected you can click on the tile you want to move to or use the directional arrow keys to move the platoon.  The goal is to move all of your platoons to the safe zone with minimal R2D2 detections.

Assumptions/Info:  
You have three platoons to move to the safe zone.  All three platoons will start at the same locations, with one platoon at (0,0).  I assumed there were more than one platoon and that they would be in close proximity to each other but not all at (0,0).  The battlefield was reduced to a 25x25 grid to simplify the problem and allow the simulation to be completed faster. Each platoons sensor has a 75% chance of detecting/reporting an R2D2 detection and can detect at a range of 4 tiles (Manhattan distance).  An R2D2 has a 100% chance of detecting a platoon and can detect at a range of 5 tiles (Manhattan distance).

Lessons Learned:  
The most effective strategy observed was to travel along the edges to the safe zone.  The battlefield (grid) needs more tiles around the platoon starting locations (north and west) and around the safe zone (south and east).  With the current setup (origin at top-leftmost tile and safe zone at bottom-rightmost tile) following the edges is the most effective strategy.  Adding additional tiles will discourage the user from traveling out of the way to get to an edge making the simulator more realistic.  

Another effective strategy was to travel in a pair with a leading platoon and a trailing platoon at least five tiles behind.  The platoons will only travel south and west to minimize the number of required moves and hopefully reduce the total number of detections.  Once the leading platoon had a detection the trailing platoon would branch off going south if the leader was going west and vice versa.  Once the platoon branched off they become the leader and the other platoon backtracks to the branch to follow the leader.  This continues until the two platoons reach the safe zone.  Once the two platoons are safe the third platoon travels the path discovered by the first two platoons assuming this was a relatively safe path.  If there were more than three platoons each subsequent platoon would follow this path as well.

Files:  
Vader.zip - source code (Java)  
Vader.jar - runnable jar file to run the simulation  
screenshot.png - sceenshot of the simulation

![Test Image 4](https://github.com/welctb01/VADER/blob/master/screenshot.PNG)
