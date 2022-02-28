## SQL Commands, SQL Scripts, Bash Scripts, and other documentation for Data Guard

##### RELATED PAGES
- [DATABASE COMMON PARAMETERS](./index.md)
- [RMAN MONITORING SCRIPTS](./index.md)
- [DATAGUARD SQL, COMMANDS, AND PARAMETERS](./index.md)
- [DATAGUARD SQLS](./index.md)  


#### Monitoring script for Data Guard restore
```markdown
REM RMAN Progress
alter session set nls_date_format='dd/mm/yy hh24:mi:ss'
/
select SID, START_TIME,TOTALWORK, sofar, (sofar/totalwork) * 100 done,
sysdate + TIME_REMAINING/3600/24 end_at
from v$session_longops
where totalwork > sofar
AND opname NOT LIKE '%aggregate%'
AND opname like 'RMAN%'
/
SELECT name, free_mb, total_mb, free_mb/total_mb*100 as percentage FROM v$asm_diskgroup;
```

#### Copying password file from ASM AS GRID
```markdown
pwcopy +DATAC1/NOAHDB22_P8P_IAD/PASSWORD/pwdnoahdb22_p8p_iad.1227.1095070971 /tmp/pwdnoahdb22_p8p_iad 
```
#### Copying password file to ASM and setting parameter in server control AS GRID
```markdown
pwcopy /tmp/pwdnoahdb22_p8p_iad +DATAC1/NOAHDB22_P8P_IAD_DG/PASSWORD/pwdnoahdb22_p8p_iad_dg
srvctl modify database -d noahDB22_p8p_iad_DG -pwfile +DATAC1/NOAHDB22_P8P_IAD_DG/PASSWORD/pwdnoahdb22_p8p_iad_dg
```
