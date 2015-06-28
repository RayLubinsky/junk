<!-- lib/README.md -->

# The /lib directory

  This is the location for code that should exist independently from code in
  the [/app][app] directory.
  In many situations, the choice between putting a module or class somewhere
  under [/app][app] versus somewhere under [/lib][lib] is fairly clear --
  for example:
  <br/>

        Libra interactions with SIS
        Virgo interactions with Firehose
        Support for UVaLib configuration mechanisms

  The general intent is that code which is focused on practices and/or services
  unique to UVa Library (and therefore code that might be applicable across a
  number of applications).

  So, whenever possible, create code here to override inherited Sufia/Hydra
  behaviors or to implement UVa-specific behaviors and then use "require" and
  "include" within [/app][app] files to mix in that code into the appropriate
  places.

## Contents                                                     <a name="top"/>

  This is a brief description of the items in this directory;
  each is linked to a more detailed description below.
  <br/><br/>

| Item                    | Description                                   |
| ----------------------- | --------------------------------------------- |
| [/lib/assets] (#assets) | UVa Library images, Javascript, CSS.          |
| [/lib/doc]    (#doc)    | Internal developer documentation.             |
| [/lib/ext]    (#ext)    | System and gem overrides ("monkey patches").  |
| [/lib/libra]  (#libra)  | Libra-specific modules and classes.           |
| [/lib/tasks]  (#tasks)  | Libra rake tasks.                             |
| [/lib/uva]    (#uva)    | UVa Library-specific modules and classes.     |

### [/lib/doc][lib_doc] - Internal developer documentation      <a name="doc"/>

  Development notes that are applicable across the entire project. 
  
  Individual directories may also have their own README.md where it is
  important to note the usage of the files within that directory, or to
  document conventions in force that may not be evident within the code itself.
  
> ###### Guidelines ![Developer Information][dev_info]

> A README.md for each directory that needs it is still the best way to
  highlight important facts about that directory, but if a README gets too long
  it would be worth considering refactoring it to present the most important
  facts there and provide links to one or more Markdown files in this directory
  to address all of the details. 
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/lib/libra][lib_libra] - Libra-specific modules and classes <a name="libra"/>

  The location for code that is specific to this application.  In some cases,
  this will be code that is unique to the application.  In other cases, this
  will be application-specific variations of definitions from [/lib/uva][lib_uva].
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/lib/uva][lib_uva] - UVa Library-specific modules and classes <a name="uva"/>

  The location for code which may be of general use to UVa Library applications
  (including this one).
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/lib/ext][lib_ext] - System and gem overrides              <a name="ext"/>

  This directory is the location for core extensions, gem overrides and other
  "monkey patches".  Put definitions here; if required during initialization,
  use "require" references to this code where needed in /config/initializers.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/lib/tasks][lib_tasks] - Libra rake tasks                <a name="tasks"/>

  Rake tasks to support Libra development and operations.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/lib/assets][lib_asst] - UVa Library images, Javascript, CSS <a name="assets"/>

  The location for assets (images, Javascript, CSS) that are specific to
  UVa Library or to the application.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

<!-----------------------------------------------------------------------------
Directory link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[app]:        ../app/README.md                "Rails application core"
[lib]:        ../lib/README.md                "Site-specific modules, classes and definitions"
[lib_asst]:   assets/README.md                "Application styling (CSS/Javascript/images)"
[lib_doc]:    doc/README.md                   "Internal developer documentation"
[lib_ext]:    ext/README.md                   "Extensions and overrides"
[lib_libra]:  libra/README.md                 "Libra-specific modules, classes and definitions"
[lib_tasks]:  tasks/README.md                 "Libra rake tasks"
[lib_uva]:    uva/README.md                   "UVaLibrary-specific modules, classes and definitions"

<!-- Topic link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[dev_info]:   doc/images/info_16x16.png       "Developer information"
