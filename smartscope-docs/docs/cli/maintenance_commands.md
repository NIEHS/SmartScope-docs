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