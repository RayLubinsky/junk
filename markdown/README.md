<!-- README.md -->

# Libra Experimental

  This is a demo of Sufia 6 (with hydra-head 9 / Solr 4 / Fedora 4), which will
  be a developmental testbed for work going into Libra 2.0.

# Contents                                                      <a name="top"/>

  This is a brief description of the items in this top-level directory;
  each is linked to a more detailed description below.
  <br/><br/>

|---------------------------|-------------------------------------------------|
| [app]       (#app)        | **Core Ruby-on-Rails application behaviors.**   |
| [bin]       (#bin)        | Scripts and other executables.                  |
| [config]    (#config)     | **Configuration and initialization code.**      |
| [db]        (#db)         | **Database schema and migrations.**             |
| [doc]       (#doc)        | Optional output from "rdoc" or "sdoc".          |
| [jetty]     (#jetty)      | Development-only instance of hydra-jetty.       |
| [lib]       (#lib)        | **Site-specific modules and classes.**          |
| [log]       (#log)        | Log output from Rails and other applications.   |
| [public]    (#public)     | **Root directory of the application web site.** |
| [solr_conf] (#solr_conf)  | Original(Sufia) Solr configuration files.       |
| [test]      (#test)       | Text fixtures for rspec *et. al.*.              |
| [tmp]       (#tmp)        | Temporary files.                                |
| [vendor]    (#vendor)     | Local copies of modified gems.                  |

# Internal Developer Documentation

  Each directory that requires special annotation has a README file which
  documents the conventions used within the files contained in the directory.
  Additionally, the [lib/doc][lib_doc] directory contains files which document
  topics that are more global in scope.
  <br/><br/>

|-----------------------------------|---------------------------------------------------------|
| [config/README.md]    [config]    | Conventions for \*.yml configuration files.             |
| [lib/doc/README.md]   [lib_doc]   | Internal documentation overview.                        |
| [lib/doc/Markdown.md] [markdown]  | Techniques for Markdown documentation with RubyMine.    |
| [lib/doc/Tips.md]     [tips]      | Tips for advanced Ruby programming.                     |
| [lib/ext/README.md]   [lib_ext]   | Conventions for overriding system and gem definitions.  |


# Code directories

> These directories contain items that are central to the functioning of the
  deployed production-mode application, and which will change over time through
  development and maintenance.

## [/app][app] - Rails application core                         <a name="app"/>

  The original contents of this directory was established by the Blacklight,
  Blacklight Advanced Search, Devise, Hydra Head, and Sufia generators.
  
  Going forward, as much as possible, we will minimize the amount of custom
  code that is created in this directory in favor of creating modules and
  classes in [/lib][lib], [lib/uva][lib_uva], and [lib/libra][lib_libra] which
  will be mixed in to the modules and classes defined under [/app][app].
  
  [Back to top](#top)

## [/config][config] - Configuration and initialization      <a name="config"/>

  The configuration subdirectory contains both initialization code (\*.rb files)
  and configuration data (\*.yml files).
  
  TODO
 
  [Back to top](#top)

## [/db][db] - Database schema and migrations                    <a name="db"/>

  TODO
  
  [Back to top](#top)

## [/lib][lib] - Site-specific modules, classes and definitions <a name="lib"/>

  TODO
  
  [Back to top](#top)


# Other directories

> These directories contain items that are central to the functioning of the
  deployed production-mode application, but rarely change.

## [/bin][bin] - Scripts and executables                        <a name="bin"/>

  TODO
  
  [Back to top](#top)

## [/public][public] - Web application static files          <a name="public"/>
  
  In production mode, these files are never handled by the Rails application
  itself; but are served up by the web server application (Apache).
  
  [Back to top](#top)


# Operational directories

> These directories are central to the functioning of the deployed
  production-mode application, but either rarely change or their change is
  managed automatically by the running application.

## [/log][log] - Output from Rails and other services           <a name="log"/>

  TODO
  
  [Back to top](#top)

## [/tmp][tmp] - Temporary files                                <a name="tmp"/>

  TODO
  
  [Back to top](#top)


# Test directories

> These directories contain items that will also change over time through
  development and maintenance, but are not required by the production-mode
  application.

## [/test][test] - Automated testing support                   <a name="test"/>

  TODO
  
  [Back to top](#top)


# Development subdirectories

> These directories contain items are only relevant in non-production
  environments.

## [/doc][doc] - Optional generated documentation               <a name="doc"/>

  TODO
  
  [Back to top](#top)

## [/jetty][jetty] - Development-only Jetty/Solr/Fedora       <a name="jetty"/>

  TODO
  
  [Back to top](#top)

## [/solr_conf][solr_conf] - Original Sufia Solr configuration files <a name="solr_conf"/>

  TODO
  
  [Back to top](#top)

## [/vendor][vendor] - Customized local gem versions         <a name="vendor"/>

  TODO
  
  [Back to top](#top)
  
<!--  Markdown reference definitions in this file should be maintained so that
      the entire set of lines below this comment can be copied and pasted into
      another Markdown file to provide all of the needed references with
      consistent naming. -->

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
[markdown]:   /lib/doc/Markdown.md            "How to work with Markdown files"
[tips]:       /lib/doc/Tips.md                "Advanced Ruby Tips'"
[yaml]:       /lib/doc/YAML.md                "Conventions for config/*.yml files"
