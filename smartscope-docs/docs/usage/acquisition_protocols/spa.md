## SPA and SPA-precise protocol

!!! note

    This is the original protocol from SmartScope. It doesn't use the Ptolemy external plugin

### Unique features

- This protocol can acquire tilted data. This is useful for samples that show preferred orientation. The image-shift coordinates and defocus value are automatically corrected to keep the targeting and focus in range.

- The protocol requires a hole template reference saved in the `References` directory in the Smartscope directory of SerialEM PC.

    The file should be a cropped image from the View preset, centered on a hole.

    Save the image from SerialEM as `holeref.mrc`. 

    More details about creating the hole reference [below](#creating-a-hole-reference).


## Before starting

### Creating a hole reference

!!! tip

    A good hole reference from a UltrAUfoil or similar gold foil grid can be re-used for most sessions.

    The only time the holeref.mrc needs to be swapped is when using a different hole size.


This is a detailed procedure on how to create a hole template image.

1. Load a grid on the stage.
2. In SerialEM, take a `Search` image and center to a square.

    You may use the flu screen to find a suitable square.

3. Perform Eucentric height calculation.

    `Tasks -> Eucentricity -> Rough Eucentricity`

4. (Optional) If you're planning on collecting tilted data. You may tilt the stage to the expected angle to have a tilted reference image. This also works with an untilted image but hole centering can be improved with tilting.
5. Take a View image and center on a hole.
6. In the Camera `Setup` options, for `View`, select a cropping that would show a single hole.
7. Take another `View` image. Repeat step 5 until satisfied with the cropping.
8. Save the image.

    `File -> Save To Other`

    Name the image `holeref.mrc` and save it in the `References` folder in the SmartScope directory.

### Other info about the protocol

- The coordinates for the holes are calculated from the square magnification and are **not** refined at the medium (View) mag. The Search mag thus needs to be very well calibrated. We also highly recommend performing the [high-defocus calibrations in SerialEM](https://bio3d.colorado.edu/SerialEM/hlp/html/menu_calibration.htm#hid_calibration_high_defocus) to improve the targeting.

- For tilted data collection, we do not recommend using a beam-image-shift radius of more than 4um (3x3 hole pattern on R1.2/1.3) to ensure proper targeting. 

    !!! warning "Multi-shot per hole caveat"
    
        Multi-shot per hole should still work. Keep in mind that the illumination area is wider perpendiular to the tilt axis. SmartScope does not currently take this into account when setting up the multi-shot per hole patterns.






