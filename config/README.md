<!-- config/README.md -->

# The /config directory

  This directory contains both initialization code (\*.rb files) and
  configuration data (\*.yml files).

# Contents                                                      <a name="top"/>

  This is a brief description of the items in this directory;
  each is linked to a more detailed description below.
  <br/><br/>

| Item                          | Description                                   |
| ----------------------------- | --------------------------------------------- |
| [**environments**]  (#envs)   | Rails per-environment application settings.   |
| [**initializers**]  (#init)   | Code run during application startup.                    |
| [**locales**]       (#loc)    | Internationalized display values.                    |
| [application.rb]    (#app)    | x.          |
| [boot.rb]           (#boot)   | x.          |
| [environment.rb]    (#env)    | x.          |
| [routes.rb]         (#routes) | x.          |
| [lib/doc]           (#doc)    | Internal developer documentation.             |
| [lib/ext]           (#ext)    | System and gem overrides ("monkey patches").  |
| [lib/libra]         (#libra)  | Libra-specific modules and classes.           |
| [lib/tasks]         (#tasks)  | Libra rake tasks.                             |
| [lib/uva]           (#uva)    | UVa Library-specific modules and classes.     |

# Rails configuration

> Rails configuration.

## config/environments                                         <a name="envs"/>

  TODO
  
  [Back to top](#top)

## [config/environment.rb](environment.rb)                      <a name="env"/>

  TODO
  
  [Back to top](#top)

## [config/routes.rb](routes.rb)                             <a name="routes"/>

  TODO
  
  [Back to top](#top)

## [config/database.yml](database.yml)                           <a name="db"/>

  TODO
  
  [Back to top](#top)

## [config/secrets.yml](secrets.yml)                        <a name="secrets"/>

  TODO
  
  [Back to top](#top)

# Gem configuration

> Gem configuration.

## [config/blacklight.yml](blacklight.yml)                     <a name="solr"/>

  TODO
  
  [Back to top](#top)

## [config/fedora.yml](fedora.yml)                           <a name="fedora"/>

  TODO
  
  [Back to top](#top)

## [config/redis.yml](redis.yml)                              <a name="redis"/>

  TODO
  
  [Back to top](#top)

## [config/resque-pool.yml](resque-pool.yml)                 <a name="resque"/>

  TODO
  
  [Back to top](#top)

## [config/browse_everything_providers.yml](browse_everything_providers.yml) <a name="be"/>

  TODO
  
  [Back to top](#top)

## [config/tinymce.yml](tinymce.yml)                        <a name="tinymce"/>

  TODO
  
  Client-side WYSIWYG editor in Javascript.
  
  See http://www.tinymce.com/.
  
  [Back to top](#top)

## [config/analytics.yml](analytics.yml)                       <a name="anal"/>

  TODO
  
  [Back to top](#top)

## [config/role_map.yml](role_map.yml)                      <a name="rolemap"/>

  TODO
  
  [Back to top](#top)

## [config/jetty.yml](jetty.yml) - development-only           <a name="jetty"/>

  TODO
  
  [Back to top](#top)

# Application configuration

> Application configuration.

## config/locales                                               <a name="loc"/>

  TODO
  
  [Back to top](#top)

# Startup code

> Startup code.

## config/initializers                                         <a name="init"/>

  TODO
  
  [Back to top](#top)

## [config/boot.rb](boot.rb)                                   <a name="boot"/>

  TODO
  
  [Back to top](#top)

## [config/application.rb](application.rb)                      <a name="app"/>

  TODO
  
  [Back to top](#top)

In order to make it easier to produce developer configurations which test out
the behavior of the associated deployed configuration (while still preserving
avoiding update of data in the shared deployment environments), config/*.yml
files have been modified to arrange values in modular groups under a single
'index' key.

The actual environment settings appear at the end of each configuration file
after an *empty* '_environments_' key.  Both the 'index' and 'environments' keys
(and their contents) are ignored by code which uses the configuration file that
code is only interested in the top-level hash key which is the same as the
current Rails.env value.
