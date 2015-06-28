<!-- config/README.md -->

# The /config directory

  This directory contains both initialization code (\*.rb files) and
  configuration data (\*.yml files).

## Contents                                                     <a name="top"/>

  This is a brief description of the items in this directory;
  each is linked to a more detailed description below.

### Directories

| Item                                  | Description                                 |
| ------------------------------------- | ------------------------------------------- |
| [**environments**]  (#envs)           | Rails per-environment application settings. |
| [**initializers**]  (#init)           | Code run during application startup.        |
| [**locales**]       (#loc)            | Internationalized display values.           |

### Initialization code files                               <a name="top-code"/>

| Item                                  | Description                                 |
| ------------------------------------- | ------------------------------------------- |
| [application.rb]    (#app)            | Rails application settings.                 |
| [boot.rb]           (#boot)           | Application startup code.                   |
| [environment.rb]    (#env)            | Initialization code.                        |
| [routes.rb]         (#routes)         | Mappings of web routes to methods.          |

### Configuration data files                               <a name="top-data"/>

| Item                                  | Description                                 |
| ------------------------------------- | ------------------------------------------- |
| [analytics.yml]     (#anal)           | Google Analytics.                           |
| [blacklight.yml]    (#blacklight)     | Solr index connection.                      |
| [browse_everything_providers.yml](#be)| Browse Everything gem.                      |
| [database.yml]      (#db)             | Database connection.                        |
| [fedora.yml]        (#fedora)         | Fedora repository connection.               |
| [jetty.yml]         (#jetty)          | Development-only web container connection.  |
| [redis.yml]         (#redis)          | Redis key-value data store connection.      |
| [resque-pool.yml]   (#resque-pool)    | Resque queueing settings.                   |
| [role_map.yml]      (#rolemap)        | Settings for [hydra-access-controls][hydra_acl] (currently unused). |
| [secrets.yml]       (#secrets)        | Web client session secret key.              |
| [tinymce.yml]       (#tinymce)        | Web client editor settings.                 |

## Rails configuration

### /config/environments                                       <a name="envs"/>

  Rails application settings that are specific to a particular environment
  (as indicated by `Rails.env`).
  Application configuration values that are common across all environments can
  be provided in [application.rb](#app); those values do not have to be (and
  should not be) duplicated in the files in this directory.
  
> ###### Guidelines ![Developer Information][dev_info]
  
> To ensure that the development and deployed versions of environment settings
  are in sync, focus on providing the appropriate values in
  [uvalib_production.rb][deployed_prod],
  [uvalib_development.rb][deployed_dev], and
  [uvalib_test.rb][deployed_test], then have
  [production.rb][prod], [development][dev], and [test.rb][test] incorporate
  the associated file with "require_relative" and only adjust the values that
  are wrong for the non-deployed setting.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/application.rb](application.rb)                    <a name="app"/>

  Application configuration values that are common across all environments.
  
> ###### Guidelines ![Developer Information][dev_info]

> In fact, [application.rb](#app) should also provide configuration values
  that are common across *most* environments.
  The minority of cases where a value should be different can be explicitly
  set in the environment file where it needs to be overridden.

  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/routes.rb](routes.rb)                           <a name="routes"/>

  This code defines the routes that the application handles by mapping
  partial URL patterns to the controllers and methods that respond to those
  patterns.
  
> ###### Guidelines ![Developer Information][dev_info]

> Ideally, all of the routes handled by a controller should be expressed within
  a "resources" block, but sometimes this is not possible.  Only fall back on
  the approach of mapping individual routes to individual methods if necessary.
  Use "namespace" and other Routes DSL constructs where ever possible.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/database.yml](database.yml)                         <a name="db"/>

  Per-environment settings for database connections.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/secrets.yml](secrets.yml)                      <a name="secrets"/>

  Per-environment settings for web client session secret keys.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

---

## Application and gem configuration

### /config/locales                                             <a name="loc"/>

  This directory holds YAML data files which hold the text for labels, buttons,
  messages, etc., which are processed by the I18n subsystem to handle
  internationalization.
  Files ending with "en.yml" are the English versions of the text.
  
  The YAML files are processed into Hashes which are accessible through the
  `I18n.t` method.
  The argument to that method is a dotted notation which describes the path of
  keys in the YAML hierarchy where the value can be found.
  
### Localization files
  
| File              | Description                         |
| ----------------- | ----------------------------------- |
| en.yml            | Unused sample file.                 |
| blacklight.en.yml | Overrides of Blacklight gem values. |
| devise.en.yml     | Overrides of Devise gem values.     |
| libra.en.yml      | Libra application-specific values.  |
| solr.en.yml       | Solr fields (experimental).         |
| sufia.en.yml      | Overrides of Sufia gem values.      |
  
> ###### Guidelines ![Developer Information][dev_info]
  
> The `solr.en.yml` and `libra.en.yml` files are an attempt at maintaining
  more than just text in these configuration files.

> The I18n internationalization subsystem has a rich interface for acquiring
  its hierarchical hashes of information from sources other than YAML files.
  This could provide a generalized mechanism for storing configuration
  information in a central location and only using local YAML files as
  emergency fall-backs.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/blacklight.yml](blacklight.yml)                   <a name="solr"/>

  Per-environment settings for Solr index connections.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/fedora.yml](fedora.yml)                         <a name="fedora"/>

  Per-environment settings for Fedora repository connections.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/redis.yml](redis.yml)                            <a name="redis"/>

  Per-environment settings for Redis key-value data store connections.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/resque-pool.yml](resque-pool.yml)               <a name="resque"/>

  Per-environment settings for Resque queueing settings.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/browse_everything_providers.yml](browse_everything_providers.yml) <a name="be"/>

  API keys for cloud storage providers.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/tinymce.yml](tinymce.yml)                      <a name="tinymce"/>

  Setup values for the TinyMCE client-side Javascript WYSIWYG editor.
  See http://www.tinymce.com/.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/analytics.yml](analytics.yml)                     <a name="anal"/>

  API keys for Google Analytics.

> ###### Guidelines ![Developer Information][dev_info]

> *Not currently used.*
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/jetty.yml](jetty.yml) - development-only         <a name="jetty"/>

  Settings for the development-only Jetty web container connection.

> ###### Guidelines ![Developer Information][dev_info]

> *Not used in production.*

  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/role_map.yml](role_map.yml)                    <a name="rolemap"/>

  Settings for [hydra-access-controls][hydra_acl] (currently unused).
  
> ###### Guidelines ![Developer Information][dev_info]

> *Not used.*
  Most Hydra code uses the concepts of "role" and "group" interchangeably.
  We need to replace this with true Role-Based Access Control.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

---

## Startup code

### /config/initializers                                       <a name="init"/>

  This directory contains code which is run once at the start of the
  application.
  
> ###### Guidelines ![Developer Information][dev_info]

> *Not used in production.*

  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/environment.rb](environment.rb)                    <a name="env"/>

  Despite the name, this code loads the initializers from the
  /config/initializers directory.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

### [/config/boot.rb](boot.rb)                                 <a name="boot"/>

  Application startup code which engages Bundler to load all of the gems listed
  in the Gemfile.
  
  <div style="text-align:right">\[[Back to top](#top)\]</div>

<!-- Topic link references used above:
REF ------------- LINK ------------------------------ TOOLTIP ---------------->
[dev_info]:       ../lib/doc/images/info_16x16.png "Developer information"
[deployed_dev]:   environments/uvalib_development.rb
[deployed_prod]:  environments/uvalib_production.rb
[deployed_test]:  environments/uvalib_test.rb
[dev]:            environments/development.rb
[prod]:           environments/production.rb
[test]:           environments/test.rb
[hydra_acl]:      https://rubygems.org/gems/hydra-access-controls
