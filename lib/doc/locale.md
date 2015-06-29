<!-- lib/doc/locale.md -->

# Conventions for \*.en.\*.yml I18n configuration files

  This directory holds YAML data files which hold the text for labels, buttons,
  messages, etc., which are processed by the I18n subsystem to handle
  internationalization.
  Files ending with "en.yml" are the English versions of the text.

  The YAML files are processed into Hashes which are accessible through the
  `I18n.t` method.
  The argument to that method is a dotted notation which describes the path of
  keys in the YAML hierarchy where the value can be found.

  The I18n internationalization subsystem has a rich interface for acquiring
  its hierarchical hashes of information from sources other than YAML files.
  This could provide a generalized mechanism for storing configuration
  information in a central location and only using local YAML files as
  emergency fall-backs.

## Contents                                                     <a name="top"/>

  [Localization files] (#files) <br/>


## Localization files                                         <a name="files"/>

  The /config/locales directory holds the following files:
  
| File                              | Description                         |
| --------------------------------- | ----------------------------------- |
| en.yml                            | Unused sample file.                 |
| [blacklight.en.yml] (#blacklight) | Overrides of Blacklight gem values. |
| [devise.en.yml]     (#devise)     | Overrides of Devise gem values.     |
| [libra.en.yml]      (#libra)      | Libra application-specific values.  |
| [solr.en.yml]       (#solr)       | Solr fields (experimental).         |
| [sufia.en.yml]      (#sufia)      | Overrides of Sufia gem values.      |

  \[[*Back to top*](#top)\]

---

### [blacklight.en.yml][blacklight_en]                   <a name="blacklight"/>

  The contents of blacklight.en.yml are just the overridden values; all other
  values are provided from gems:
  
  [*\<blacklight\>*/config/locales/blacklight.en.yml][bl_gem] <br/>
  [*\<blacklight-gallery\>*/config/locales/blacklight-gallery.en.yml][bl_gallery] <br/>

  \[[*Back to top*](#top)\]

---

### [sufia.en.yml][sufia_en]                                  <a name="sufia"/>

  The contents of sufia.en.yml are just the overridden values; all other
  values are provided from gems:
  
  [*\<sufia\>*/config/locales/sufia.en.yml][sufia_gem] <br/>
  [*\<sufia\>*/sufia-models/config/locales/sufia.en.yml][sufia_models] <br/>

  \[[*Back to top*](#top)\]

---

### [devise.en.yml][devise_en]                               <a name="devise"/>

  The contents of devise.en.yml were a completion duplication of the gem's
  [configuration file][devise_gem], so all text displayed by Devise is
  defined by the internal configuration file.

  \[[*Back to top*](#top)\]

---

### [libra.en.yml][libra_en]                                  <a name="libra"/>

  The contents of libra.en.yml intended to go beyond internationalizing strings
  to establish mechanisms for dynamically defining drop-down lists, dialog
  contents and other elements.
  
> ###### Guidelines ![Developer Information][dev_info]
  
> This is still a concept that is under development; the file currently
  contains some speculative entries and copies of all of the strings from
  Libra 1.x for perspective.

  \[[*Back to top*](#top)\]

---

### [solr.en.yml][solr_en]                                     <a name="solr"/>

  This is an experimental attempt at transforming the configuration information
  that is traditionally embedded in the [catalog controller][catalog] into
  configuration values that could be more easily administered.
  
> ###### Guidelines ![Developer Information][dev_info]
  
> This is still a concept that is under development and may end up being
  deferred.

  \[[*Back to top*](#top)\]

---

<!-- Topic link references used above:
REF ------------- LINK -------------------------------------- TOOLTIP -------->
[dev_info]:       images/info_16x16.png                       "Developer information"
[blacklight_en]:  ../../config/locales/blacklight.en.yml      "/config/locales/blacklight.en.yml"
[devise_en]:      ../../config/locales/devise.en.yml          "/config/locales/devise.en.yml"
[sufia_en]:       ../../config/locales/sufia.en.yml           "/config/locales/sufia.en.yml"
[libra_en]:       ../../config/locales/libra.en.yml           "/config/locales/libra.en.yml"
[solr_en]:        ../../config/locales/solr.en.yml            "/config/locales/solr.en.yml"
[catalog]:        ../../app/controllers/catalog_controller.rb "/app/controllers/catalog_controller.rb"

<!-- External link references used above:
REF ------------- LINK ------------------------------------------------------->
[bl_gem]:         https://github.com/projectblacklight/blacklight/tree/master/config/locales/blacklight.en.yml
[bl_gallery]:     https://github.com/projectblacklight/blacklight-gallery/tree/master/config/locales/blacklight-gallery.en.yml
[sufia_gem]:      https://github.com/projecthydra/sufia/tree/master/config/locales/sufia.en.yml
[sufia_models]:   https://github.com/projecthydra/sufia/tree/master/sufia-models/config/locales/sufia.en.yml
[devise_gem]:     https://github.com/plataformatec/devise/tree/master/config/locales/en.yml