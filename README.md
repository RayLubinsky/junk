<!-- README.md -->

# Libra Experimental

  This is a demo of Sufia 6 (with hydra-head 9 / Solr 4 / Fedora 4), which will
  be a developmental testbed for work going into Libra 2.0.

## Contents                                                     <a name="top"/>

  This is a brief description of the items in this top-level directory;
  each is linked to a more detailed description below.
  Additionally, the [/lib/doc][lib_doc] directory contains more detailed
  documentation on concepts, conventions and techniques.
  <br/><br/>

| Item                      | Description                                     |
| ------------------------- | ----------------------------------------------- |
| [/app]       (#app)       | **Core Ruby-on-Rails application behaviors.**   |
| [/bin]       (#bin)       | Scripts and other executables.                  |
| [/config]    (#config)    | **Configuration and initialization code.**      |
| [/db]        (#db)        | **Database schema and migrations.**             |
| [/doc]       (#doc)       | Optional output from "rdoc" or "sdoc".          |
| [/jetty]     (#jetty)     | Development-only instance of hydra-jetty.       |
| [/lib]       (#lib)       | **Site-specific modules and classes.**          |
| [/log]       (#log)       | Log output from Rails and other applications.   |
| [/public]    (#public)    | **Root directory of the application web site.** |
| [/solr_conf] (#solr_conf) | Original(Sufia) Solr configuration files.       |
| [/test]      (#test)      | Text fixtures for rspec *et. al.*.              |
| [/tmp]       (#tmp)       | Temporary files.                                |
| [/vendor]    (#vendor)    | Local copies of modified gems.                  |

## Code directories

  These directories contain items that are central to the functioning of the
  deployed production-mode application, and which will change over time through
  development and maintenance.
  <br/><br/>
  
---

### [/app][app] - Rails application core                        <a name="app"/>

  The original contents of this directory was established by the Blacklight,
  Blacklight Advanced Search, Devise, Hydra Head, and Sufia generators.
  
> ###### Guidelines ![Developer Information][dev_info]

> Going forward, as much as possible, we will minimize the amount of custom
  code that is created in this directory by creating overriding modules and
  classes in [/lib][lib], [/lib/uva][lib_uva], and [/lib/libra][lib_libra]
  which will be mixed in to the code under [/app][app] using "require",
  "include", "extend", and other Ruby mechanisms that support code modularity.
  See the [developer documentation][lib_doc] for details on these strategies.
  
  \[[*Back to top*](#top)\]

---

### [/config][config] - Configuration and initialization     <a name="config"/>

  The configuration directory contains both initialization code (\*.rb files)
  and configuration data (\*.yml files).
  Some of these files are fundamental to Rails operation; others are required
  by Blacklight, Hydra and other gems.
  The code located there is run once at system initialization and is dedicated
  to providing configuration values for system objects prior to steady-state
  operation.

> ###### Guidelines ![Developer Information][dev_info]

> Although there is a fuzzy interface between code and data, particularly in
  modern languages like Ruby, we will strive to separate them as much as
  possible by ensuring that literal values are maintained in configuration
  data files rather than directly in code files.
  See the [developer documentation][lib_doc] for details on these strategies.

  \[[*Back to top*](#top)\]

---

### [/db][db] - Database schema and migrations                   <a name="db"/>

  The database directory contains the database migrations, which are central to
  Rails' approach of managing the development of database tables.
  The most important information, however, is [schema.rb](/db/schema.rb) which
  describes the current state of database schemas for the application.

> ###### Guidelines ![Developer Information][dev_info]

> Database tables are a fundamental concept in Rails.
  Whenever there is need for a set of information that should be
  (a) always available to the application, and
  (b) have potential use-cases which require dynamic change,
  then it is always worth considering whether that information should be stored
  in a database table.
  See the [developer documentation][lib_doc] for details on these strategies.

  \[[*Back to top*](#top)\]

---

### [/lib][lib] - Site-specific modules, classes and definitions <a name="lib"/>

  This directory contains code and data which is unique to the application
  (Libra) and/or unique to the deployment environment (UVa Library).

> ###### Guidelines ![Developer Information][dev_info]

> Although it is tempting to simply add unique application behaviors directly
  in the [/app][app] directory hierarchy, encapsulating that information in
  the [/lib][lib] directory hierarchy has benefits:

> * Avoids the possibility that gem generators change the meaning of your code
> * Supports the possibility of code sharing with future UVa Library applications
> * Makes the code more comprehensible to future developers.

> See the [developer documentation][lib_doc] for details on these strategies.
  
  \[[*Back to top*](#top)\]

---

## Other directories

  These directories contain items that are central to the functioning of the
  deployed production-mode application, but rarely change.
  <br/><br/>

---

### [/bin][bin] - Scripts and executables                       <a name="bin"/>

  This directory contains system executable code, mostly in the form of scripts
  that are run to perform basic operational functions.

> ###### Guidelines ![Developer Information][dev_info]

> Add executables here to provide tools for development, testing and production
  as needed.  Although the system-provided programs are Ruby scripts, new items
  may be shell scripts, compiled executables, etc.
  
> However, if the task that is being implemented is highly integrated with the
  application (particularly if it relies on the results of rake tasks), a
  better approach might be to create a Rake task in [/lib/tasks][lib_tasks]
  which will have direct access to the information and would not be reliant on
  extracting the information from the output of Rake tasks.
  
  \[[*Back to top*](#top)\]

---

### [/public][public] - Web application static files         <a name="public"/>
  
  In production mode, these files are never handled by the Rails application
  itself; but are served up by the web server application (Apache).
  
> ###### Guidelines ![Developer Information][dev_info]

> Limit the files here to the ones that are truly static, since this directory
  is effectively off-limits to the production-mode application.
  If there are benefits to dynamic generation of the contents of a file, it
  may be preferable to add logic to the Rails application to handle the route
  to that file rather than ceding control to the web server.

  \[[*Back to top*](#top)\]
  
---

## Operational directories

  These directories are central to the functioning of the deployed
  production-mode application, but either rarely change or their change is
  managed automatically by the running application.
  <br/><br/>

---

### [/log][log] - Output from Rails and other services          <a name="log"/>

  The Rails application directs STDOUT and STDERR output to a file in this
  directory named for the execution environment (production.log,
  development.log, etc).
  Other applications may also be configured to send their output to this
  directory.
    
> ###### Guidelines ![Developer Information][dev_info]

> Allowing the production-mode application to write into the code directory
  hierarchy might not be the best approach for performance and administrative
  reasons.
  One solution might be to replace [/log] with a symbolic link to a location on
  a different partition (perhaps even via NFS).
  We may ultimately want to make use of logging mechanisms that do not simply
  write STDOUT and STDERR to file(s) in this directory.

  \[[*Back to top*](#top)\]

---

### [/tmp][tmp] - Temporary files                               <a name="tmp"/>

  The temporary directory holds transient and cached information for the
  running application.
      
> ###### Guidelines ![Developer Information][dev_info]

> Allowing the production-mode application to write into the code directory
  hierarchy might not be the best approach for performance and administrative
  reasons.
  One solution might be to replace [/tmp] with a symbolic link to a location on
  a different partition (perhaps even via NFS).

  \[[*Back to top*](#top)\]
  
---

## Development subdirectories

  These directories contain items are only relevant in non-production
  environments.
  <br/><br/>

---

### [/test][test] - Automated testing support                  <a name="test"/>

  This directory supports automated testing by providing a location to manage
  test fixtures and test cases.

> ###### Guidelines ![Developer Information][dev_info]

> Test development with [RSpec](http://rspec.info/) provides a basic framework
  for automated testing, but requires some work to come up with a set of tests
  that exercise the code in a useful way.
  
> At a minimum, the tests should be able to detect regression (when known-good
  code breaks due to recent changes in the code base).
  However, the promise of "Test Driven Development" is that the tests
  themselves should express the requirements of the system; in this view a
  successful run of the tests should be an assurance that the system has been
  designed in accordance with the requirements.
  
> See the [developer documentation][lib_doc] for details on these strategies.

  \[[*Back to top*](#top)\]

---

### [/vendor][vendor] - Customized local gem versions        <a name="vendor"/>

  This directories contains gems that have been modified by Sufia and/or Hydra
  developers.
  
> ###### Guidelines ![Developer Information][dev_info]

> In general, we will avoid modifying the contents of this directory.
  The preferred strategy for overriding gem functionality is to add "patch
  code" to [/lib/ext][lib_ext] to limit the changes to just the definitions
  that need to be modified.

  \[[*Back to top*](#top)\]

---

### [/doc][doc] - Optional generated documentation              <a name="doc"/>

  This directory is created by the "rdoc" or "sdoc" programs to provide an
  HTML-formatted display of programming documentation extracted from the code.
  
> ###### Guidelines ![Developer Information][dev_info]

> This directory may or may not appear in the code directory and can be removed
  at will because it is easily re-creatable.
  
  \[[*Back to top*](#top)\]

---

### [/jetty][jetty] - Development-only Jetty/Solr/Fedora      <a name="jetty"/>

  This directory is generated by [hydra-jetty](https://github.com/projecthydra/hydra-jetty)
  to provide local Solr and Fedora instances.

> ###### Guidelines ![Developer Information][dev_info]

> Nothing in this directory is used in the deployed application for any
  environment.  Deployed production, development and test environments rely on
  separately-maintained Solr and Fedora instances.

  \[[*Back to top*](#top)\]

---

### [/solr_conf][solr_conf] - Original Sufia Solr configuration files <a name="solr_conf"/>

  This directory contains Sufia Solr configuration files that are used to
  initialize the generic [/jetty][jetty] directory.

> ###### Guidelines ![Developer Information][dev_info]

> Nothing in this directory is used in the deployed application for any
  environment.

  \[[*Back to top*](#top)\]

---

<!--  Markdown reference definitions in this file should be maintained so that
      the entire set of lines below this comment can used as a template for
      other Markdown files.  (However, because the references have to be
      relative to the page, the links will have to be adjusted so that the
      leading '/' is replaced with the relative path.) -->

<!-----------------------------------------------------------------------------
Directory link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[app]:        /app/README.md                  "Rails application core"
[app_asst]:   /app/assets/README.md           "Application styling (CSS/Javascript/images)"
[app_cont]:   /app/controllers/README.md      "Application route handlers"
[app_help]:   /app/helpers/README.md          "Controller/view shared code"
[app_mail]:   /app/mailers/README.md          "E-mail generation support"
[app_model]:  /app/models/README.md           "Object classes mapping on to database rows"
[app_view]:   /app/views/README.md            "Display components"
[bin]:        /bin/README.md                  "Scripts and executables"
[config]:     /config/README.md               "Configuration and initialization"
[config_env]: /config/environments/README.md  "Per-environment Rails configuration"
[config_ini]: /config/initializers/README.md  "Rails application initializers"
[config_loc]: /config/locales/README.md       "Interface configuration and internationalization"
[db]:         /db/README.md                   "Database schema and migrations"
[doc]:        /doc/README.md                  "Optional generated documentation"
[jetty]:      /jetty/README.md                "Development-only Jetty/Solr/Fedora"
[lib]:        /lib/README.md                  "Site-specific modules, classes and definitions"
[lib_asst]:   /app/assets/README.md           "Application styling (CSS/Javascript/images)"
[lib_doc]:    /lib/doc/README.md              "Internal developer documentation"
[lib_ext]:    /lib/ext/README.md              "Extensions and overrides"
[lib_libra]:  /lib/libra/README.md            "Libra-specific modules, classes and definitions"
[lib_tasks]:  /lib/tasks/README.md            "Libra rake tasks"
[lib_uva]:    /lib/uva/README.md              "UVaLibrary-specific modules, classes and definitions"
[log]:        /log/README.md                  "Output from Rails and other services"
[public]:     /public/README.md               "Web application static files"
[solr_conf]:  /solr_conf/README.md            "Original Sufia Solr configuration files"
[test]:       /test/README.md                 "Automated testing support"
[test_cont]:  /test/controllers/README.md     "Controller tests"
[test_fixt]:  /test/fixtures/README.md        "Test fixtures and simulated data for automated testing"
[test_help]:  /test/helpers/README.md         "Helper tests"
[test_int]:   /test/integration/README.md     "Automated testing support"
[test_model]: /test/models/README.md          "Model tests"
[tmp]:        /tmp/README.md                  "Temporary files"
[tmp_cache]:  /tmp/cache/README.md            "Cached compiled assets"
[tmp_pids]:   /tmp/pids/README.md             "System process ID for running services"
[tmp_sess]:   /tmp/sessions/README.md         "User session information"
[tmp_sock]:   /tmp/sockets/README.md          "System socket endpoints"
[vendor]:     /vendor/README.md               "Customized local gem versions"

<!-- Topic link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[top]:        /README.md                      "Top-level README file"
[dev_info]:   /lib/doc/images/info_16x16.png  "Developer information"
[markdown]:   /lib/doc/markdown.md            "How to work with Markdown files"
[plugin]:     /lib/doc/markdown/plugin.md     "Markdown Plugin for RubyMine"
[tips]:       /lib/doc/tips.md                "Advanced Ruby Tips'"
[yaml]:       /lib/doc/yaml.md                "Conventions for config/*.yml files"
