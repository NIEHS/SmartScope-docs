SmartScope was intially designed for screening. Therefore, there are a few manual interventions steps that should be taken during the process. Setting up data collection in SmartScope is still much faster than using other packages.

### General Setup conditions

Here are some initial parameters for a data collection:

![Data collection parameters](/assets/data_collection_parameters.png)

#### Main parameters to consider:

- Save Frames: Higly important since you want to process the movies!
- Defocus parameters: Choose a range and a step to cycle defocus. Recommended initial values -1 um to -1.8 um with 0.2 um step.
- Holes per square: Should be set to 0 to enable data collection mode
- Multishot per hole: Optional but will increase throughput substancially. Instructions about how to set up multishot per hole [here](/usage/collection/multishot_per_hole/)
- Beam-image-shift grouping: This will depend on the microscope calibration for SPA collected without tilt, 7.5um radius with min group size of 9 is a good start. For tilted collection, we recomment 4 um and min group size of 4

#### Worflow-specific parameters

- Offset targeting: During collection, Offset Targeting is disabled unless an `Offset Distance` is specified. This allows to collect image that are off-centered from the holes for when particles prefer slightly thicker ice or the ice is simple too thin in the center of the holes.

- Delays: Delays for Recentering the beam, Zeroloss peak or Hardware dark acquisition can be specified depending on the type of hardware present in the microscope or the overall system stability.

#### Protocol choice

!!! warning

    Please follow the links for unique procedures related to the different protocols.

- We recommend using the `-precise` protocols for data collection. 
- For tilted collection, please use [SPA-Precise](/usage/acquisition_protocols/spa/). 
- For other collection, [SPA-Ptolemy-precise](/usage/acquisition_protocols/spa_ptolemy/) is preferred but [SPA-Precise](/usage/acquisition_protocols/spa/) is also a valid option.


### Step-by-step guide

1. Setup your run based on the above section
2. Wait for the atlas to complete
3. Pick your squares
    * To add square click on any squares that arent numbered that you wish to collect. Then select the `Actions` menu and `Add to Queue` (Last option).
    * To remove squares, click on the orange squares in the atlas image. Then select the `Actions` menu and `Add to Queue` (Last option).
    * If the Queue button is Grayed out, click the `X` button next to the `Actions` menu to clear selection and reselect.
4. Wait for a square to complete its acquisition
5. Click on the square and check if the holes were correctly identified.
    * If it's not satisfactory, it is possible to use the `extend lattice workflow` detailed below to add holes or completely correct the hole picking.
        1. Ensure some holes next to each others are currently identified. If one square already has good holes picked on any square, this should be enough and you may skip to step vi.
        
            1. For all square with the wrong patterns of few holes. Click `All Holes -> Delete Holes` in the square menus.
            2. Add 6-9 targets (shift+left click) on holes that are next to each other
            3. Click `New Targets -> Add targets` to add the positions.

        2. Ensure there is at least one hole (preferablly 3) on the square (follow instructions in step a. to add holes). Use the `All Holes -> Extend Lattice`. The first time this option is used, SmartScope will calculate the angle and spacing of the lattice from existsing holes. Then it will add targets following these parameters over the square.
        3. When you add targets use option `All Holes -> Extend Lattice` and then option `New Targets -> Add Targets`.
        4. (Optional) `All Holes -> Regroup BIS` follows by `All Holes -> Queue all holes`. This can also be done in bulk in step 7.
        6. Repeat steps b.-d. for all squares. 

6. Edit hole selection with the [Selector sliders](/usage/report/low_mag_maps/#edit-targets).
7. Regroup and reselect after editing the selectors.
8. Done!

