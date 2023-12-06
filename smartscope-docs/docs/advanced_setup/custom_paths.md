
[:material-tag-outline: Added in 0.9.2]()

## Definition

By default, the data structure in Smartscope follows the `AUTOSCREENDIR/groupName/YYYYMMDD_session/` scheme. In some cases where the facility needs the data to be organized differently, it is possible to specify a path for groups or individual user.

!!! note "File Permissions"

    Make sure that the SmartScope container can write files to these locations to avoid permission issues.

!!! warning "Before Starting"

    `USE_CUSTOM_PATHS` environment variable must be set to True for any custom path definition to take effect.
    This variable is located in `smartscope.conf`

## Custom User Path

These custom paths will affect all the sessions assigned to that specific user. The final location will be `CUSTOM_PATH/YYYMMDD_session/`

## Custom Group Path

These custom paths will affect all the sessions in a given group unless a specific user with a customized path is assigned to the session. The final location will be `CUSTOM_PATH/YYYMMDD_session/`


## Add a custom Path

Both types of custom path described above can be set in a similar manner.

Go to the admin portal, usually `http://localhost:48000/admin/`

* Click on the `Custom Group Paths` or `Custom User Paths` and then click on `+ add` button in the upper-right corner.
* From the dropdown, select the user or group
* Enter the absolute path in the path field
* Click Save

## Priority of session search through the possible Paths

The session can be in any of the following location. SmartScope will look in the order through all the possible locations for the session.

1. Custom User Path (if defined)
2. Custom Group Path (if defined)
3. AUTOSCREENDIR/group/ (if USE_STORAGE=True)
4. AUTOSCREENSTORAGE/group/ (if USE_LONGTERMSTORAGE=True)
5. AWS/group (if USE_AWS=True)






