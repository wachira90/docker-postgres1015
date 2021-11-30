# pg_dump command example ( Backup )
## Dumping a database called dangerousdb into an SQL file:
````
pg_dump dangerousdb > db.sql
````
## Backing up the dangerousdb in with a tar format:
````
pg_dump -U postgres -F c dangerousdb > dangerousdb.tar
````
## Saving the dangerousdb in a directory format runs this command:
````
pg_dump -U postgres -F d dangerousdb > db1_backup
````
## Large databases that want smaller file formats may use the utility with a compression tool like gzip when running the backup.
````
pg_dump -U postgres dangerousdb | gzip > dangerousdb.gz
````
## Reloading a script into a newly created database called nowdb:
````
psql -d nowdb -f db.sql
````
## Dumping a single table is possible by using the -t option and specifying the database and tab name (here: dangerousdb; tallytab)
````
pg_dump -t tallytab dangerousdb > db.sql
````
## Dumping selected tables by putting in conditions. Here the command will dump all tables that start with "sam" in the "ple" schema, but will exclude the table "samson."
````
pg_dump -t 'ple.sam*' -T ple.samson dangerousdb > db.sql
````


# pg_restore command example ( Restore )
### Restoring a backup with a .tar file name requires that the user consider whether the database already exists, and what the format of the backup is.

## If the database dbcooper already exists, the following command will restore it:
````
pg_restore -U postgres -Ft -d dbcooper < dbcooper.tar
````
## If the database doesn't yet exist, tweaking the command like the following will restore it:
````
pg_restore -U postgres -Ft -C -d dbcooper < dbcooper.tar
````
## The following command will restore a backup from a backup file i.e. name: back_it_on_up.sql
````
psql -f back_it_on_up.sql
````
