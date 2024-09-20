SmartScope comes with a few protocols that essentially dictate which steps are going to be performed during the imaging process and which algorithms are going to be used.

Some protocols come with a `-precise` variant. The main differences with their regular counterpart are:

- Eucentric height performed at the medium mag rather than the square mag. This is more precise as the hole pattern from the square mag can lead to erroneous cross-correlation.
- Hole re-centering should be more precise. This allows to start beam-image shift imaging with less initial image-shift.

When setting up a grid, all the protocols are availble via a dropdown menu with a additional default `auto` choice. This option follows a set of rule to select the best protocol for the grid and imaging type.  Here's a breakdown of these rules:

!!! note

    The `auto` will never select the `-precise` variant of a protocol. It has to be manually selected.

- SPA-Ptolemy -> Selected for all holey grids if tilt angle is 0 in the imaging parameters.
- SPA -> Selected for holey grid if tilt angle is not 0.
- NegativeStain -> Selected if the grid type is `Negative Stain` or `Lacey`

??? tip "Advanced - Changing the rules for `auto`"

    These rules can be modified in a settings file. More details [here](/api/protocol/auto_protocol/)