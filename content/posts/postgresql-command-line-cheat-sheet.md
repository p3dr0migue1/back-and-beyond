+++
date = '2025-10-01T16:29:28+01:00'
draft = false
tags = ['Postgres', 'SQL']
title = 'Postgresql Command Line Cheat Sheet'
+++

List databases
```sql
\list 
# or 
\l
```

Connect to a/switch database
```sql
\connect <database_name>
# or 
\c <database_name>
```

List tables in the current database
```sql
\dt
```

List indexes
```sql
\di
```

Display table schema
```sql
\d+ <table_name>
```

List user roles
```sql
\du
```

Pretty-format query results instead of the not-so-useful ASCII tables
```sql
\x
```

Export postgres table to CSV with headings
```sql
\COPY (SELECT id, name FROM <table_name>) TO '/path/file_name.csv' DELIMITER ',' CSV HEADER
```