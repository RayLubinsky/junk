<!-- lib/ext/README.md -->

# Overrides and Extensions

  This directory is the location for core extensions, gem overrides and other
  "monkey patches".
  
  Some code projects follow a convention of locating patches within the
  config/initializers directory -- the primary reason being that some patches
  need to be in place early enough in the initialization process so that the
  overridden definitions will be in effect as soon as possible.
  
  Instead, we will maintain the definitions under [lib/ext][lib_ext] and only
  include code under config/initializers to require 'lib/ext'.

## Layout

  This is a brief description of the items in this top-level directory;
  each is linked to a more detailed description below.
  <br>&nbsp;</br>

| File or directory     | Description                                       | Usage                   |
| --------------------- | ------------------------------------------------- | ----------------------- |
| **rails**             | Overrides of Rails constructs.                    |
| **ruby**              | Overrides of Ruby constructs.                     |
| **ruby/integer**      | Overrides of **class Integer**.                   |
| **ruby/kernel**       | Overrides of **module Kernel**.                   |
| **ruby/string**       | Overrides of **class String**.                    |
| [rails.rb] (rails.rb) | Load all files from the lib/ext/ruby directory.   | require 'lib/ext/ruby'  |
| [ruby.rb]  (ruby.rb)  | Load all files from the lib/ext/rails directory.  | require 'lib/ext/rails' |

## Special Notes

### [rails/envclass.rb](rails/envclass.rb)

  This code replaces **Rails.env** and **Rails.env=*** with class methods that
  create instance of **Rails::EnvClass**, which augments
  **ActiveSupport::StringInquirer** to treat all variations on the "production"
  environment as "production".

<!-----------------------------------------------------------------------------
Directory link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[lib_ext]:    /lib/ext/README.md              "Extensions and overrides"
