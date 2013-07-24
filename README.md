###Requirements
Requires a Joyent cloud account and Joyent's node.js cli tools (_npm install manta_).
See docs here: http://apidocs.joyent.com/manta/


###Usage
Use _mbackup_ to push files to Joyent's Manta service.  _mbackup_ will run a checksum via Manta on the remote file and compare to your local file.  If the local file and remote file checksums don't match, the script will exit with an error.

For simplicity, _mbackup_ will by default gzip and push your files to a 'backups' directory, sub-organized by data type and hostname.  For example:

```
mbackup postgres my_table.date.gz
```
will place a file called 'my_table.date.gz' in Manta under your stor/backups 'directory':
```
> mls /$MANTA_USER/stor/backups/postgres/$(hostname)/
my_table.date.gz
```
