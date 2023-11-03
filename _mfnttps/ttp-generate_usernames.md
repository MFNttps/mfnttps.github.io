---
functions:
  ttp-tip:
    - description: Generate Usernames Combinations 
      code: |
         python2 usernamer.py -n "brian moore" > usernames
         python2 usernamer.py -n "sarah lorem" >> usernames
         python2 usernamer.py -n "mike ross" >> usernames
         python2 usernamer.py -n "claire madison" >> usernames
resources: |
  https://raw.githubusercontent.com/jseidl/usernamer/master/usernamer.py
---