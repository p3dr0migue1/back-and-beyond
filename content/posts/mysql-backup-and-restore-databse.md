+++
date = '2024-11-04T22:27:20Z'
draft = false
tags = ['MySQL', 'SQL']
title = 'Mysql Backup and Restore Databse'
+++

To dump (backup) your database data into a `.sql` file, run:
```bash
mysqldump -u root -p database_name > database_dump_file.sql
# you will be asked to provide the root password
```

Back up your MySQL Database with Compress

If your mysql database is very big, you might want to compress the output of `mysqldump`. Just use the mysql backup command below and pipe the output to gzip, then you will get the output as gzip file.
```bash
mysqldump -u root -p database_name | gzip -9 > database_backup_file.sql.gz
```

To restore your database from a `.sql` file:

* Create an appropriately named database on the target machine;
* Load the file using the mysql command;

```bash
mysql -u root -p database_name < database_backup_file.sql
```

To restore compressed backup files you can do the following:
```bash
gunzip < backup_file.sql.gz | mysql -u root -p database_name
```

If you need to restore a database that already exists, you'll need to use `mysqlimport` command. The syntax for `mysqlimport` is as follows:
```bash
mysqlimport -u root -p database_name backup_database_file.sql
```
