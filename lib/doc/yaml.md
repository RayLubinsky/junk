<!-- lib/doc/yaml.md -->

# Conventions for config/*.yml files

  In order to make it easier to produce developer configurations which test out
  the behavior of the associated deployed configuration (while still preserving
  avoiding update of data in the shared deployment environments), config/*.yml
  files have been modified to arrange values in modular groups under a single
  'index' key.

  The actual environment settings appear at the end of each configuration file
  after an *empty* '_environments_' key.  Both the 'index' and 'environments'
  keys (and their contents) are ignored by code which uses the configuration
  file that code is only interested in the top-level hash key which is the same
  as the current Rails.env value.

## Layout

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
  <br/><br/>

---
