---
layout: page
title: Contribute
---
## TTP
Tactic, Technique, and Procedure

## Structure

Each MFNttp is defined in a file in the [`_mfnttps/`] folder named as `<ttp name>.md`, such file consists only of a [YAML] front matter which describes the ttpary and its functions.

The full syntax is the following:

```
---
description: Optional description of the ttp
functions:
  FUNCTION:
    - description: Optional description of the example
      code: Code of the example
    - ....
  FUNCTION:
    - description: Optional description of the example
      code: Code of the example
    - ...
  ...
resources: |
  <insert links here>
  <another link>
  ->delete the entire resources section to include header 
  if you do not have any links to add <-
---
```

Where `FUNCTION` is one of the values described in the [`_data/functions.yml`] file.

Feel free to use any file in the [`_mfnttps/`] folder as an example.

## Pull request process

Vendor software is accepted as well as standard Unix ttparies. Binaries and techniques that only works on certain operating systems and versions are accepted and such limitations shall be noted in the `description` field.

Before sending a pull request of a new ttp or function, ensure the following:

1. Verify the function works on at least one type of modern Unix system.
2. All new ttps must either be wrapper scripts that optimize common processes
like 'searchnse' and 'searchsploit'
3. Do not attempt to include ttps that simply offer menus to invoke other ttps (there are of course are exceptions)

Pull requests adding new functions in [`_data/functions.yml`] are allowed and subjected to project maintainers vetting.

[YAML]: http://yaml.org/
[`_mfnttps/`]: https://github.com/MFNttps/MFNttps.github.io/tree/master/_mfnttps
[`_data/functions.yml`]: https://github.com/MFNttps/MFNttps.github.io/blob/master/_data/functions.yml
