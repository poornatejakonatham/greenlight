# Notes

## Uninstall PostgreSQL

### List all Postgres related packages:

    dpkg -l | grep postgres

    ii  postgresql-12                              12.8-0ubuntu0.20.04.1                       amd64        object-relational SQL database, version 12 server
    ii  postgresql-client-12                       12.8-0ubuntu0.20.04.1                       amd64        front-end programs for PostgreSQL 12
    ii  postgresql-client-common                   214ubuntu0.1                                all          manager for multiple PostgreSQL client versions
    ii  postgresql-common                          214ubuntu0.1                                all          PostgreSQL database-cluster manager

### Remove all above listed pacakges:

    sudo apt-get --purge remove postgresql-12 postgresql-client-12 postgresql-client-common postgresql-common

### Remove the following folders

    sudo rm -rf /var/lib/postgresql/
    sudo rm -rf /var/log/postgresql/
    sudo rm -rf /etc/postgresql/

### Remove the postgres user:

    sudo deluser postgres

## Install newer version.

### Create the file repository configuration:

    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

### Import the repository signing key:

    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

### Update the package lists:

    sudo apt-get update

### Install the latest version of PostgreSQL:

If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':

    sudo apt-get -y install postgresql