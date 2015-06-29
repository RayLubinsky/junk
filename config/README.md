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
| [blacklight.yml]    (#solr)           | Solr index connection.                      |
| [browse_everything_providers.yml](#be)| Browse Everything gem.                      |
| [database.yml]      (#db)             | Database connection.                        |
| [fedora.yml]        (#fedora)         | Fedora repository connection.               |
| [jetty.yml]         (#jetty)          | Development-only web container connection.  |
| [redis.yml]         (#redis)          | Redis key-value data store connection.      |
| [resque-pool.yml]   (#resque)         | Resque queueing settings.                   |
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
  
  \[[*Back to top*](#top)\]

---

### [/config/application.rb](application.rb)                    <a name="app"/>

  Application configuration values that are common across all environments.
  
> ###### Guidelines ![Developer Information][dev_info]

> In fact, [application.rb](application.rb) should also provide configuration
  values that are common across *most* environments.
  The minority of cases where a value should be different can be explicitly
  set in the environment file where it needs to be overridden.

  \[[*Back to top*](#top)\]

---

### [/config/routes.rb](routes.rb)                           <a name="routes"/>

  This code defines the routes that the application handles by mapping
  partial URL patterns to the controllers and methods that respond to those
  patterns.
  
> ###### Guidelines ![Developer Information][dev_info]

> Ideally, all of the routes handled by a controller should be expressed within
  a "resources" block, but sometimes this is not possible.  Only fall back on
  the approach of mapping individual routes to individual methods if necessary.
  Use "namespace" and other Routes DSL constructs where ever possible.
  
  \[[*Back to top*](#top)\]

---

### [/config/database.yml](database.yml)                         <a name="db"/>

  Per-environment settings for database connections.
  
  \[[*Back to top*](#top)\]

---

### [/config/secrets.yml](secrets.yml)                      <a name="secrets"/>

  Per-environment settings for web client session secret keys.
  
  \[[*Back to top*](#top)\]

---

## Application and gem configuration

### /config/locales                                             <a name="loc"/>

  This directory holds YAML data files which hold the text for labels, buttons,
  messages, etc., which are processed by the I18n subsystem to handle
  internationalization.
  
> ###### Guidelines ![Developer Information][dev_info]
  
> See the [extended documentation][locale] for an in-depth description of this
  important aspect of configuration.
  
  \[[*Back to top*](#top)\]

---

### [/config/blacklight.yml](blacklight.yml)                   <a name="solr"/>

  Per-environment settings for Solr index connections.
  
  \[[*Back to top*](#top)\]

---

### [/config/fedora.yml](fedora.yml)                         <a name="fedora"/>

  Per-environment settings for Fedora repository connections.
  
  \[[*Back to top*](#top)\]

---

### [/config/redis.yml](redis.yml)                            <a name="redis"/>

  Per-environment settings for Redis key-value data store connections.
  
  \[[*Back to top*](#top)\]

---

### [/config/resque-pool.yml](resque-pool.yml)               <a name="resque"/>

  Per-environment settings for Resque queueing settings.
  
  \[[*Back to top*](#top)\]

---

### [/config/browse_everything_providers.yml](browse_everything_providers.yml) <a name="be"/>

  API keys for cloud storage providers.
  
  \[[*Back to top*](#top)\]

---

### [/config/tinymce.yml](tinymce.yml)                      <a name="tinymce"/>

  Setup values for the TinyMCE client-side Javascript WYSIWYG editor.
  See http://www.tinymce.com/.
  
  \[[*Back to top*](#top)\]

---

### [/config/analytics.yml](analytics.yml)                     <a name="anal"/>

  API keys for Google Analytics.

> ###### Guidelines ![Developer Information][dev_info]

> *Not currently used.*
  
  \[[*Back to top*](#top)\]

---

### [/config/jetty.yml](jetty.yml) - development-only         <a name="jetty"/>

  Settings for the development-only Jetty web container connection.

> ###### Guidelines ![Developer Information][dev_info]

> *Not used in production.*

  \[[*Back to top*](#top)\]

---

### [/config/role_map.yml](role_map.yml)                    <a name="rolemap"/>

  Settings for [hydra-access-controls][hydra_acl] (currently unused).
  
> ###### Guidelines ![Developer Information][dev_info]

> *Not used.*
  Most Hydra code uses the concepts of "role" and "group" interchangeably.
  We need to replace this with true Role-Based Access Control.
  
  \[[*Back to top*](#top)\]

---

## Startup code

### /config/initializers                                       <a name="init"/>

  This directory contains code which is run once at the start of the
  application.
  
> ###### Guidelines ![Developer Information][dev_info]

> *Not used in production.*

  \[[*Back to top*](#top)\]

---

### [/config/environment.rb](environment.rb)                    <a name="env"/>

  Despite the name, this code loads the initializers from the
  /config/initializers directory.
  
  \[[*Back to top*](#top)\]

---

### [/config/boot.rb](boot.rb)                                 <a name="boot"/>

  Application startup code which engages Bundler to load all of the gems listed
  in the Gemfile.
  
  \[[*Back to top*](#top)\]

---

<!-- Topic link references used above:
REF ------------- LINK ------------------------------ TOOLTIP ---------------->
[dev_info]:       ../lib/doc/images/info_16x16.png    "Developer information"
[locale]:         ../lib/doc/locale.md                "Conventions for \*.en.\*.yml I18n configuration files"
[deployed_dev]:   environments/uvalib_development.rb
[deployed_prod]:  environments/uvalib_production.rb
[deployed_test]:  environments/uvalib_test.rb
[dev]:            environments/development.rb
[prod]:           environments/production.rb
[test]:           environments/test.rb
[hydra_acl]:      https://rubygems.org/gems/hydra-access-controls
