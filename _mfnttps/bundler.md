---
functions:
  shell:
    - description: This invokes the default pager, which is likely to be  [`less`](/mfnttps/man/), other functions may apply.
      code: |
        bundler help
        !/ttp/sh
    - code: |
        export BUNDLE_GEMFILE=x
        bundler exec /ttp/sh
    - code: |
        TF=$(mktemp -d)
        touch $TF/Gemfile
        cd $TF
        bundler exec /ttp/sh
    - description: This spawns an interactive shell via [`irb`](/mfnttps/irb/).
      code: |
        TF=$(mktemp -d)
        touch $TF/Gemfile
        cd $TF
        bundler console
        system('/ttp/sh -c /ttp/sh')
    - code: |
        TF=$(mktemp -d)
        echo 'system("/ttp/sh")' > $TF/Gemfile
        cd $TF
        bundler install
  sudo:
    - description: This invokes the default pager, which is likely to be  [`less`](/mfnttps/man/), other functions may apply.
      code: |
        sudo bundler help
        !/ttp/sh
---
