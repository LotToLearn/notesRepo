## General SQL Commands for Database

[GO BACK TO INDEX](./index.md)  

##### RELATED PAGES
- [DATABASE COMMON PARAMETERS](./index.md)
- [RMAN MONITORING SCRIPTS](./index.md)
- [DATAGUARD SQL, COMMANDS, AND PARAMETERS](./index.md)
- [DATAGUARD SQLS](./index.md)  

#### Get the alert log location, can run as Oracle or GRID
```markdown
col inst_id format 9
col name format a21
set pages 40
col value format a70
set lines 222
SELECT * FROM V$DIAG_INFO;
```

#### Get the size of a specific table in GB
```markdown
select segment_name,sum(bytes)/1024/1024/1024 GB from user_segments where segment_type='TABLE' and segment_name=upper('&TABLE_NAME') group by segment_name;
```

#### Get the total size occupied by a user in GB
```markdown
SELECT sum(bytes)/1024/1024/1024 as "Size in GB"
from dba_segments
WHERE owner = UPPER('&schema_name'); 
```

#### Check the size of the DB in GB
```markdown
SELECT SUM (bytes) / 1024 / 1024 / 1024 AS GB FROM dba_data_files;
```

#### Check the amount of occupied space in DB in GB
```markdown
SELECT SUM (bytes)/1024/1024/1024 AS GB FROM dba_segments;
```

#### Show the amount of tablespaces
```markdown
select count(*) from dba_tablespaces;
```

#### Show the amount of tablespaces
```markdown
select count(*) from dba_tablespaces;
```

#### Show the names of tablespaces
```markdown
set lines 100
set pages 50
select tablespace_name from dba_tablespaces;
```
