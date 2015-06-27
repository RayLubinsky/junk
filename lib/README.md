<!-- lib/README.md -->

# The /lib directory

  This is the location for code that should exist independently from code in
  the [/app][app] directory.
  In some situations, this is a clear distinction -- for example:
  <br/><br/>

        Libra interactions with SIS
        Virgo interactions with Firehose
        Support for UVaLib configuration mechanisms

  In other cases, the choice between putting a module or class somewhere under
  [/app][app] versus somewhere under [/lib][lib] is less clear-cut.

  The general intent is that code which is focused on practices and/or services
  unique to UVa Library (and therefore code that might be applicable across a
  number of applications).

  So, whenever possible, create code here to override inherited Sufia/Hydra
  behaviors or to implement UVa-specific behaviors and then use "require" and
  "include" within [/app][app] files to mix in that code into the appropriate
  places.
  

# Contents                                                      <a name="top"/>

  This is a brief description of the items in this directory;
  each is linked to a more detailed description below.
  <br/><br/>

| Item                | Description                                   |
| ------------------- | --------------------------------------------- |
| [assets]  (#assets) | UVa Library images, Javascript, CSS.          |
| [doc]     (#doc)    | Internal developer documentation.             |
| [ext]     (#ext)    | System and gem overrides ("monkey patches").  |
| [libra]   (#libra)  | Libra-specific modules and classes.           |
| [tasks]   (#tasks)  | Libra rake tasks.                             |
| [uva]     (#uva)    | UVa Library-specific modules and classes.     |

## [lib/assets][lib_asst] - UVa Library images, Javascript, CSS <a name="assets"/>

  TODO
  
  [Back to top](#top)

## [lib/doc][lib_doc] - Internal developer documentation        <a name="doc"/>

  This directory is the location for development notes that are applicable
  across the entire project.
  
  Individual directories may also have their own README.md (or other Markdown
  files) where it is important to describe the usage of the files within that
  directory, or to document conventions in force that may not be evident within
  the code itself.
  
  [Back to top](#top)

## [lib/ext][lib_ext] - System and gem overrides                <a name="ext"/>

  TODO
  
  [Back to top](#top)

## [lib/libra][lib_libra] - Libra-specific modules and classes <a name="libra"/>

  TODO
  
  [Back to top](#top)

## [lib/tasks][lib_tasks] - Libra rake tasks                  <a name="tasks"/>

  TODO
  
  [Back to top](#top)

## [lib/uva][lib_uva] - UVa Library-specific modules and classes <a name="uva"/>

  TODO
  
  [Back to top](#top)

<!-----------------------------------------------------------------------------
Directory link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[app]:        /app/README.md                  "Rails application core"
[lib]:        /lib/README.md                  "Site-specific modules, classes and definitions"
[lib_asst]:   /app/assets/README.md           "Application styling (CSS/Javascript/images)"
[lib_doc]:    /lib/doc/README.md              "Internal developer documentation"
[lib_ext]:    /lib/ext/README.md              "Extensions and overrides"
[lib_libra]:  /lib/libra/README.md            "Libra-specific modules, classes and definitions"
[lib_tasks]:  /lib/tasks/README.md            "Libra rake tasks"
[lib_uva]:    /lib/uva/README.md              "UVaLibrary-specific modules, classes and definitions"
