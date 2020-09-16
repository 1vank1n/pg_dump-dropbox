# Description

1. Create dump all databases of PostgreSQL server.
2. Compress gzip (filename looks like `database.sql.gz`)
2. Upload to Dropbox via [Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader)
4. (Un)Remove local backups (configure via SAVE_LOCAL)

# Installation

    git clone https://github.com/1vank1n/psqldump-dropbox.git

# Usage

    Two steps.

    *First*. Register your app in dropbox. For hint, just start `bash dropbox_uploader.sh`

    *Second*. Edit `VARS` section in `psql2dropbox.sh`.

    PSQL_USER=""
    BACKUPS_DIR="./backups" -- folder for local backups
    REMOTE_FOLDER="example" -- folder for dropbox
    DROPBOX_UPLOADER="./dropbox_uploader.sh" -- path to dropbox_uploader.sh script
    DROPBOX_UPLOADER_CONFIG="./.dropbox_uploader" -- config of dropbox_uploader
    SAVE_LOCAL=false -- save/remove files in BACKUPS_DIR after they uploaded to Dropbox

    *Third*. Create `~/.pgpass` with auth credentials for postgres. Line for every user in format 'hostname:port:database:username:password'. [More info](https://www.postgresql.org/docs/current/libpq-pgpass.html)

# Crontab

    0 0 * * * cd /root/DIRECTORY_WITH_SCRIPTS; ./psql2dropbox.sh &>> ./psql2dropbox.log
