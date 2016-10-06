<!-- lib/ext/README.md -->

# Overrides and Extensions

  This directory is the location for core extensions, gem overrides and other
  "monkey patches".
  
  Some code projects follow a convention of locating patches within the
  config/initializers directory -- the primary reason being that some patches
  need to be in place early enough in the initialization process so that the
  overridden definitions will be in effect as soon as possible.
  
  Instead, we will maintain the definitions under [/lib/ext][lib_ext] and only
  include code under config/initializers to require 'lib/ext'.

## Contents                                                     <a name="top"/>

  This is a brief description of the items in this directory.
  <br/><br/>

| File or directory     | Description                                       | Usage                   |
| --------------------- | ------------------------------------------------- | ----------------------- |
| **rails**             | Overrides of Rails constructs.                    |
| **ruby**              | Overrides of Ruby constructs.                     |
| **ruby/integer**      | Overrides of **class Integer**.                   |
| **ruby/kernel**       | Overrides of **module Kernel**.                   |
| **ruby/string**       | Overrides of **class String**.                    |
| [rails.rb] (rails.rb) | Load all files from the lib/ext/ruby directory.   | require 'lib/ext/ruby'  |
| [ruby.rb]  (ruby.rb)  | Load all files from the lib/ext/rails directory.  | require 'lib/ext/rails' |

## Featured Items

### [/lib/ext/rails/envclass.rb][envclass]                 <a name="envclass"/>

  This code replaces **`Rails.env`** and **`Rails.env=`** with class methods
  that create an instance of **`Rails::EnvClass`**, which augments
  `ActiveSupport::StringInquirer` so that all variations on the standard
  environment names are reported appropriately.
  (For example, `Rails.env.production?` returns true for both "production"
  and "uvalib_production".

### [/lib/ext/ruby/string/snake_case.rb][snake_case]     <a name="snake_case"/>

  Adds method **`String#snake_case`** to translate strings of the form
  "MultiPartName" into "multi_part_name".

### [/lib/ext/ruby/integer/constants.rb][constants]       <a name="constants"/>

  Adds constants **`Integer::MAX`** and **`Integer::MIN`** for the largest and
  smallest native `Fixnum` values.

  \[[*Back to top*](#top)\]

<!-----------------------------------------------------------------------------
Directory link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[lib_ext]:    ../ext/README.md                "Extensions and overrides"

<!-- Topic link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[envclass]:   rails/envclass.rb               "Rails::EnvClass"
[snake_case]: ruby/string/snake_case.rb       "String#snake_case"
[constants]:  ruby/integer/constants.rb       "Integer::MAX, Integer::MIN"
