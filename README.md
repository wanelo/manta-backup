###Requirements
Requires a Joyent cloud account and Joyent's node.js cli tools - `npm install manta`.
See docs here: http://apidocs.joyent.com/manta/


###Usage
Use `mbackup` to push files to Joyent's Manta service.  `mbackup` will run a checksum via Manta on the remote file and compare to your local file.  If the local file and remote file checksums don't match, the script will exit with an error.

For simplicity, `mbackup` will by default gzip and push your files to `/$MANTA_USER/stor/backups/$1/your_hostname/filename.gz`, organizing further sub-directories by data type and hostname.  For example:

```
mbackup postgres my_table.date.gz
```
will place a file called 'my_table.date.gz' in Manta under your stor/backups 'directory':
```
> mls /$MANTA_USER/stor/backups/postgres/$(hostname)/
my_table.date.gz
```

Alternatively, you can specify a target path as the 3rd argument.
