This section aims at enabling https encryption for the SmartScope application.

## Prerequisite

Before enabling HTTPS, it is important to obtain SSL certificates. Depending on your deployment type, you may get certificates from your institution IT department for an internal domain. For public facing deployment, you can obtain certifiates from your DNS provider or from [Let's Encrypt](https://letsencrypt.org/getting-started/).

!!! note

    The rest of this documentation assumes that you already have obtained SSL certificates from one of the above source.

## Setup steps

1. In `smartscope.conf` set the following values,

    * `USE_SSL=true`
    * `DEBUG=False`

2. In `smartscope.yml`, add an nginx section with SSL certificate and encryption key as volumes and forward ports 80 and 443. See example below:

    ```yaml
    version: "3"
    services:
    smartscope:
        # image: ghcr.io/niehs/smartscope:0.8-rc.2  #Change version here
        user: ${UID}:${GID} #This corresponds to the user running the smarscope.sh script
        volumes:
        ######## ADD YOUR MAIN DATA LOCATION ##########
        - ./data:/mnt/data
            # Example:
        # - /nfs/data/:/mnt/data/
        ######## ADD YOUR MICROSCOPES #########
        # The synthax from the microscope volumes is as follows:
        # - /path/to/where/serialem/will/write/files/:/mnt/your_scope_name_here/
        # Example:
        # - /mnt/gatan_Raid_X/smartscope/:/mnt/arctica/
        #
    nginx:
        volumes:
        - /usr/local/smartscope/ssl_certs/mydomain.crt:/opt/certs/smartscope.crt
        - /usr/local/smartscope/ssl_certs/mydomain.key:/opt/certs/smartscope.key
        ports:
        - 80:80
        - 443:443
    ```

3. Restart SmartScope.

4. Login via https.