**Pipeline CuraEngine**

**1\. Slicing :** The first step in the pipeline is the slicing stage. This converts a 3D mesh into 2D layers. First it determines the heights at which to produce cross sections. Then it creates cross sections of every triangle at those heights, which will normally be a line. Then it stitches these lines together to form polygons wherever possible.

**2\. Generating Areas :** When given a set of layers, this stage divides each layer up into the areas that will be filled with the types of things we're going to print. What part is going to become wall? What part will be infill? Where will we place support?

* Divides each layer into functional areas:

  * Walls (perimeters)

  * Infill

  * Support structures

* Tags which parts of the polygons will serve which purpose.

**3\. Generating Paths :** This stage is the most complex part of CuraEngine. Here the areas that were generated in the previous step will be actually filled with lines. The order in which we print the lines is determined here also. The output of this stage is a set of LayerPlans, which contain the movement commands that the printer will eventually execute and in what order they will be executed.

* Fills the areas with print lines (toolpaths).

* Determines the print order for efficiency and print quality.

* Creates LayerPlans, an internal data structure containing movement commands and their sequence.

**4\. Inserts :** After the plan is created we can still make modifications to the plan to some extent. We have to insert commands to pre-heat and pre-cool the nozzles before an extruder switch. In order to predict how far ahead the nozzles must start heating and cooling, time estimates are generated for each path and the temperature change commands are inserted such that the time we need to heat or cool will be covered in the upcoming moves.

* Adds special control commands like preheat and cool instructions before tool changes.

* Calculates time estimates for each path to correctly schedule temperature changes.

**5\. G-code Export**

* Converts all LayerPlans (movement and inserts) into final G-code commands.

* G-code controls printer movements, extrusion, and temperature.