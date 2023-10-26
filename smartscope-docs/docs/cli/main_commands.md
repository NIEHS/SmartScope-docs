## Autoscreen

This is the main command to start the imaging workflow in smartscope. This command can be useful for testing purposes or if any breaking issues happen in the web UI that prevents a run to start from there.

Synthax: `./smartscope.sh run autoscreen SESSION_ID`

Where:

-  SESSION_ID: can usually be found in the url of the session.

## Download Test files

[:material-tag-outline: Added in 0.9.2]()

This commands downloads the optional image bank used to run SmartScope in fake scope mode. This is mainly for demonstration or development purposes.

Synthax: `./smartscope.sh run download_testfiles`

## Measure Atlas to Search offset

[:material-tag-outline: Added in 0.9.2]()

This command aims at mimicking the `Shift To Marker` behavior from SerialEM to shift the stage position coordinates between magnifications, especially from the Atlas (Mapping) to Search.
SmartScope automatically recenters to the squares after navigating to them. However, certain systems have a larger offset which makes the recentering fails sometimes.
This script will use the history of recentering events from the database and average it to set the offset parameters for a given detector.
Before settings the values, the user will be shown the value and its standard deviation and will need to confirm the change.

Synthax: `./smartscope.sh run get_atlas_to_search_offset DETECTOR_NAME`

Where:

- DETECTOR_NAME: Is the name of the detector as created in the admin portal.
