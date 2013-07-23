Use mbackup to push files to Joyent's Manta service.  mbackup will run a checksum via Manta on the remote file and compare to your local file.  If the local file and remote file checksums don't match, the script will exit with an error.

Since mbackup is intended only to provide a simple cli interface to backups in Manta, it will by default store your files in 'backups' directory by data type and hostname.  For example:

```
mbackup postgres my_table.date.gz
```
will place a file called 'my_table.date.gz' in Manta under your stor/backups 'directory':
```
> mls /$MANTA_USER/stor/backups/postgres/$(hostname)/
my_table.date.gz
```
