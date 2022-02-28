## SQL Commands for Database

[GO BACK TO INDEX](./index.md)  

##### RELATED PAGES
- [DATABASE COMMON PARAMETERS](./index.md)
- [RMAN MONITORING SCRIPTS](./index.md)
- [DATAGUARD SQL, COMMANDS, AND PARAMETERS](./index.md)
- [DATAGUARD SQLS](./index.md)  

### General commands
```markdown
# Get the alert log location, can run as Oracle or GRID
col inst_id format 9
col name format a21
set pages 40
col value format a70
set lines 222
SELECT * FROM V$DIAG_INFO;

# Get the size of a specific table in GB
select segment_name,sum(bytes)/1024/1024/1024 GB from user_segments where segment_type='TABLE' and segment_name=upper('&TABLE_NAME') group by segment_name;

# Get the total size occupied by a user in GB
SELECT sum(bytes)/1024/1024/1024 as "Size in GB"
from dba_segments
WHERE owner = UPPER('&schema_name'); 
```
