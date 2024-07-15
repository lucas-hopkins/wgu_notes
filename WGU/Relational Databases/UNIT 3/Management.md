
# Backups

## PostgreSQL Backup Tools

The pg_dump tool outputs all of the contents of all database objects into a single file. The script dumps contain SQL commands that are in plain-text files that can be used to reconstruct the database back to the state that it was in when the database was backed up.

```
pg_dump -U adminrole -W -F p mydb > c:\backup\mydb.sql
```

- The pg_dump is the command line tool.
- The -U adminrole specifics the user role that will be used to connect to the database. In this case, we are using the adminrole to login to perform the backup.
- The -W prompts the pg_dump command to prompt for the password on adminrole before it can continue.
- The -F specifies the output file format. In this case, the p stands for plain-text SQL script file.
- Then, we indicate the database that we want to backup, which is mydb.
- The > c: :\backup\mydb.sql is the output backup file name and path that we are backing up to. If you don’t pass in a path, you can just include the file name, which will output the backup file to the current directory that you are running the command in.

- The **-a** option will only dump out the data, but not the schema with the data definitions like the table structure. This approach is only useful if we back up the data in plain text, as it will allow us to export just the data.
- The **-s** will dump out just the object definitions like the tables, rather than including the data.
- The **-c** with the lowercase c will clean the database objects by drop statements first before creating them.
- The **-t** will only dump out specific tables that match the table name that is passed. For example, -t employee would only dump out the employee table.
- The **-T** with a capital T will dump out all tables other than the ones that are listed.
- The **-C** with a capital letter will start the output with a command to create the database and reconnect to the created database. This option allows you to avoid having to create the database first.


## Restore from Backup

The psql command will restore plain SQL script files that have been created by pg_dump and pg_dump tools.

```
psql -U adminrole -f backupfile.sql
```

The pg_restore focuses on restoring databases that are in a non-text format created from the pg_dump or pg_dumpall tools.

```
pg_restore -d mydb -f backup.tar
```

We also have options with the pg_restore:

- The **-a** option will only restore the data, but not create the schema. This would assume that the schema has already been created.
- The **-c** option will clean/drop the database objects before they are recreated.
- The **-C** with an uppercase C will create the entire database before restoring it. If the -d database is used, it will drop the current database and recreate it before the restoring is done.
- The **-f** can pass the filename if we include the file name.
- The **-s** will only create the schema but not restore the data into the database.
- With the -t option, we can specify the table name to restore.


### Types of Backups

* **Full Backup**
	* This provides a copy of the entire database and allows us to restore the data to the point in time when the database backup was made. Note that you can have database transactions running even when the database is still in the process of backing up the data.
* **Differential Backup**
	* They contain only the data that has changed since the last full backup. Differential backups are cumulative, not incremental. This means that the differential backup will save all of the changes since the last full backup, even if there are other differential backups run since the last full backup.
* **Incremental Backup**
	* Each incremental backup only contains the data from the last backup, regardless of whether it is a full backup, differential backup, or incremental backup. It is not cumulative.
