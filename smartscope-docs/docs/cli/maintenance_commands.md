## Backup Database

[:material-tag-outline: Added in 0.9.2]()

Automatically back up the database. Recommended to used before updating, especially when trying early releases. The backups will me saved to the backups directory in the installation area. The output file follows the `YYYYMMDD_backup.sql`

!!! note

    The location can be changed by the directory mounted /mnt/backups in the Smartscope container in the volumes section of smartscope.yml.

Synthax: `./smartscope.sh run backup_db`

## Restore Database

[:material-tag-outline: Added in 0.9.2]()

Launch the database restoration process. If a backup is not specified, the user is prompted to select from the existing files in the backups directory

!!! warning

    This will overwrite the current database. It is advised to create a backup first

Synthax: `./smartscope.sh run restore_db [BACKUP_FILE]`

Where:

- BACKUP_FILE (Optional): Name of one file in the backups directory. Just the file name. Usually under the `YYYYMMDD_backup.sql` format.

## Export Grid

[:material-tag-outline: Added in 0.9.3]()

Export all the database information about a single grid as a `.yaml` file to serve as a backup or a way to re-import into a new instance of SmartScope.

Synthax: `./smartscope.sh export_grid GRID_ID

Where:

- GRID_ID is the database id of the grid. I can be found in the url when looking at the grid.

The exported file will be saved in `/DATADIR/GROUP/SESSION/GRID/export.yaml`

## Import Grid

[:material-tag-outline: Added in 0.9.3]()

Reads and `export.yaml` file to re-import the data into a SmartScope instance.

First, put the grid directory of the grid to be imported in its expected `DATADIR/GROUP/SESSION/` directory

Synthax `./smartscope.sh import_grid /mnt/data/GROUP/SESSION/GRID/export.yaml [USER] [GROUP]`

Where:

- /mnt/data/GROUP/SESSION/GRID/export.yaml: Replace GROUP/SESSION/GRID/ with your specific path.
- USER (Optional): User account if the user should be overriden from the original `export.yaml`
- GROUP (Optional): Group name if the group should be overriden from the original `export.yaml`

!!! warning

    It is useful to override USER and GROUP if importing in a new instance where the orignal user and group may not exist. Not doing so in this case will give an error during the import process.


