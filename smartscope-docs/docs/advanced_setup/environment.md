# Complete list of environment variables

This section explains how to set up the environment variables for SmartScope

## General

* ALLOWED_HOSTS *Default: localhost*

    Comma separated list domains that are allowed to be used to connect to the server. Usually, it is the IP an/or hostname of the computer where SmartScope is installed. If you have a domain name.
    *e.g.* locahost,myhostname,mydomain.com

* DJANGO_SETTINGS_MODULE *Default: Smartscope.settings.server_docker*

    Useful to change if an instance will only be used as a worker.
    More details coming soon.

* USE_SSL *Default: false*

    If set to true, the nginx service will use a different config file to encrypt the connection. More setup will have to be done on the nginx service to enable that functionality

* CONFIG *Default: /opt/config*

    This will copy the smartscope configuration to a volume area where it can be persistent and edited

* EXTERNAL_PLUGINS_DIRECTORY *Default /opt/smartscope/external_plugins*

    The location of the directory where the external plugins are installed. It shouldn't need to be changed unless for development purposes.

* USE_STORAGE *Default: True*

    *options: True|False*
    If the instance should look in the main storage area for files. This option is required if the instance is connected to the microscope.
    Can be turned off if setting up an instance that can only view the results from other sources like a server that would only load files from AWS or long-term storage areas.
    This sotrage location is prioritized to load the files from as it should be the fastest accessible drive.

* USE_LONGTERMSTORAGE *Default: False*

    *options: True|False*
    If you plan on backing up the storage drive to another area with more storage space, the server can look for files in that area for displaying on the website.
    This storage area has second priority to load the files from if the data isn't present in the main storage any longer.

* USE_CUSTOM_PATHS *Default: False* 

    [:material-tag-outline: Added in 0.9.2]()

    Allows to override the default storage areas as the place where all the data gets saved. Specific paths can be set on a per-user or per-group basis. After enabling this, refer to the [Custom Paths section]().

* USE_AWS *Default: False* [:material-test-tube: Still feature incomplete]()

    *options: True|False*
    If true, the AWS section of the file will need to be filled up. SmartScope will automatically back up the data for each specimen once they're completed. The data can be loaded from AWS to display on the webpage after it's been removed from the main storage.
    This area has third priority to load the files from.

* USE_MICROSCOPE *Default: True*

    *options: True|False*
    If the instance of Smartscope being deployed is only going to serve as a viewing server that doesn't connect to the microscope, set to False. It will disable the links to setup and run sessions.

* WORKER_HOSTNAME *Default: localhost* [:material-test-tube: Currently unused]()

    If the webserver and worker (instance connected to the microscope) are not installed in the same computer.
    More details coming soon.

* DEFAULT_UMASK *Default: 003*

    Set the way the permissions will be set on the files created by smartscope. With umask 003, the files will inherit a 774 (rwxrwxr--) permission set allowing group write.

* LOGLEVEL *Default=INFO*

    *options: INFO|DEBUG*
    Set the sensitivity of logging. The default is INFO will print the most informative status updates while debug allows for more in-depth information.

* DEBUG  *Default=False*

    [:material-tools: Fixed in 0.9.1]() Now working properly

    Sets the server in debug mode to return traceback of the error on webpage loading instead of the regular return code.

## Fake-scope mode

* TEST_FILES *Default:/mnt/testfiles/*

    The location of the dummy files to run in "fake scope" mode.

## Database

* MYSQL_HOST *Default:db*

    IP address or hostname of the database server.

* MYSQL_PORT *Default:3306*

    Port for the mysql server. 3306 is the default if the default port for mariabDB.

* MYSQL_USERNAME *Default:root*

    Username for the mariaDB connection

* MYSQL_PASSWORD *Default:pass*

    [:material-tools: Fixed in 0.9.1]() Changed from MYSQL_ROOT_PASSWORD.

    Password for the user for mariaDB connection

* MYSQL_DATABASE *Default:smartscope*

    Name of the database in the mariaDB server

* MYSQL_SSL *Default:False*

    Wheter to connect to the database with SSL. This is instented to be used to connect for database over the clout

* MARIADB_RANDOM_ROOT_PASSWORD *Default:1*

    Only used when running in docker to initialize the database.

<!-- ## AWS connection information

.. note:: This feature is currently not functional in v0.8

This section is required if the USE_AWS=True and if the information is not stored in ~/.aws
Please view `AWS S3 <https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html>`_ information on these variables -->


