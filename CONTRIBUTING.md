# Contributing Guidelines

## File and Directory Naming Conventions

The FAIMS-Tools autogen typically takes a `module.xml` file and produces three
directories: `module`, `tests` and `wireframe`. Consequently, these four files
and directories should be present in module repositories.

In addition to these, other directories are common:

* `data` - Files which will be uploaded to the module's `data` directory on the
  server.
* `logic` - Handwritten BeanShell files for each of the module's features.
  These are sourced using the `@SOURCE` directive in the `module.xml` file's
  `<logic>` tag.
* `vocab` - An XML file for each vocab entry (i.e. `<opts>` element) in the
   `module.xml` file.

Other directories can be made if appropriate.

In addition to these directories, it's common to define `postproc.sh` and
`preproc.sh` to post- and pre-process the autogen's output or input.

## Coding Style

* An 80-character line limit is encouraged but not enforced.

* Each file in the `logic` directory should start with a heading that makes it
  easy to see where it was sourced from when reading the generated
  `module/ui_logic.bsh` file. For example, if a file `logic/my-feature.bsh`
  exists, it's reasonable for its first line to be `/*** MY FEATURE ***/`.

* Although BeanShell allows their omission, types should be given in function
  signatures and when defining variables. This acts as documentation and
  improves the performance of your code.

* Refs to UI elements should be a `final String` whose name starts with `REF_`.
  Example: `final String REF_SELECT_USER = "User/User/Select_User"`. They should
  be global variables, even if only used in the scope of a function. This allows
  the unit testing script to check if the `module.xml` file contains that ref.
