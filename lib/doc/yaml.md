<!-- lib/doc/yaml.md -->

# Conventions for \*.yml configuration files

## Basic /config/*.yml

  The expected contents of a file depends on the gem that uses that file for
  configuration.
  
  Some gems simply expect a list of YAML keys and values (e.g. analytics.yml,
  resque-pool.yml, secrets.yml, tinymce.yml).
  
  The rest of the files are expected to have top-level keys for each
  environment (that is, each value that `Rails.env` might have depending on how
  the RAILS_ENV environment variable is set).
  The key/value settings under a given top-level key apply only if the current
  environment matches that key.
  
  Occasionally, you will see some configuration files that take advantage of
  YAML anchors (markers beginning with **&**).
  An anchor represents a way to refer to a tree of values so that it can be
  inserted into another tree later in the file.
  For example:
  
```yaml
  common: &ANCHOR
    key1a: common_value

  production:
    <<: *ANCHOR
    key2a: prod_value

  development:
    <<: *ANCHOR
    key2a: dev_value
```

  will result in the following Hash when loaded:
  
```ruby
  {
    'common'      => { 'key1a' => 'common_value' }
    'production'  => { 'key1a' => 'common_value', 'key2a' => 'prod_value' }
    'development' => { 'key1a' => 'common_value', 'key2a' => 'dev_value' }
  }
```

  The gem that wants this information will only be looking for the top-level
  key that matches the current environment, so it will never notice the extra
  top-level key.
  The net result is that the gem will see the right values for the production
  environment while the maintainer of the file only has to remember to change
  the value of 'key1a' in one place.

## Libra conventions

  To this end, the Libra configuration files have been reworked to make full
  use of anchors so that values shared across many combinations of
  configurations only have to be changed in one place.

  In order to make it easier to produce developer configurations which test out
  the behavior of the associated deployed configuration (while still preserving
  avoiding update of data in the shared deployment environments), config/*.yml
  files have been modified to arrange values in modular groups under a single
  'index' key.

  The actual environment settings appear at the end of each configuration file
  after an *empty* 'environments' key.  Both the 'index' and 'environments'
  keys (and their contents) are ignored by code which uses the configuration
  file that code is only interested in the top-level hash key which is the same
  as the current Rails.env value.

## Layout                                                       <a name="top"/>

```yaml
index:
  general:                    Settings that are applicable to all environments
    base:
      SERVICEA:               General settings for service A
        common:               Service A settings for every environment
          KEY1: VALUE1
          KEY2: VALUE2
          ...
        production:           Service A settings specific to production environments.
          KEY1: VALUE1
          KEY2: VALUE2
          ...
        development:          Service A settings specific to development environments.
        test:                 Service A settings specific to test environments.
        
      SERVICEB:               General settings for service B (if there is one)
        common:               Service B settings for every environment
        production:           Service B settings specific to production environments.
        development:          Service B settings specific to development environments.
        test:                 Service B settings specific to test environments.
        
      ...                     Additional service settings (if any)

    project:
      SERVICEA:               Project-specific settings for service A
      SERVICEB:               Project-specific settings for service B
      ...
      
   deployments:
     uvalib:                  Settings for UVa Library deployments.
       SERVICEA:
       SERVICEB:
       ...
       default:               The settings for UVa Library deployments based on
                              the service selected.
                              
     local:                   Settings for local operation.
       SERVICEA:
       SERVICEB:
       ...
       default:               The settings for local operation based on the
                              service selected.
       
   configurations:
     uvalib:                  Specific combinations of settings for UVa deployments.
       server:
       workstation:
     local:                   Specific combinations of settings for local operation.
       standalone:

environments:                 An empty key (really there just so that when
                              collapsing the hierarchy of values in RubyMine
                              then the comment on the next lines does not
                              disappear).

uvalib_production:            These are the official environment names for use
uvalib_development:           on the UVa Library services.
uvalib_test:

production:                   The standard Rails environment names are all
development:                  associated with local operation.
test:
```

  Note that the "production" environment associated with local (developer
  workstation) settings however it should otherwise behave as the deployed
  production environment ("uvalib_production") for the purpose of checking the
  behavior of the program with all of the optimizations and conditional code
  that would be exercised in the deployed production environment.

  \[[*Back to top*](#top)\]
