<!-- lib/doc/markdown.md -->

# Documenting with Markdown

  Markdown (*.md) files are useful for providing text-based documentation
  embedded within the directory hierarchy of a project.
  
  One significant use of this format is within GitHub, where Markdown files are
  displayed as formatted documentation files when browsing through a project.
  In particular, if a directory has a "README.md" file, that is formatted and
  displayed automatically by GitHub when browsing to that project directory.
  
## Markdown plugin for RubyMine

  If you install the Markdown plugin in RubyMine (File|Settings|Plugins) you
  can more fully use Markdown files for documentation purposes while coding or
  viewing the project through RubyMine.  The plugin adds two features:

  - **Markdown syntax highlighting** <br/>
    This makes the contents of the file easier to read even displayed as text
    in RubyMine. <br/><br/>

  - **Markdown preview tab** <br/>
    This adds adds a "Preview" tab to the bottom of the window for a Markdown
    file which displays the file in formatted form.

  To add these features, install the Markdown plugin from **File|Settings**
  under the **Plugins** selection.  Check the box to the right of the
  "Markdown" entry and press "OK" to install the plugin.  After installation,
  options for the plugin will found in the **Other Settings** selection.

## Markdown Features

  Both GitHub and the RubyMine Markdown plugin implement extensions to the
  original [Markdown][markdown].

### Styling text

  - Surround text with a single _underline_ or *star* for *italic* text.
  - Surround text with double _underlines_ or *stars* for **bold** text.
  - Surround text with backticks for `highlighted` text (which is treated as
    code so no formatted honored within the backticks).
  
#### Styling words

| Effect                | Combination                 | Text Tab  | Preview | GitHub  | Example         |
| --------------------- |:---------------------------:|:---------:|:-------:|:-------:|:---------------:|
| Italic                | \_sample\_                  | Y         | Y       | Y       | _sample_        |
| Italic                | \*sample\*                  | Y         | Y       | Y       | *sample*        |
| Bold                  | \*\*sample\*\*              | Y         | Y       | Y       | **sample**      |
| Bold                  | \_\_sample\_\_              | Y         | Y       | Y       | __sample__      |
| Highlight             | \`sample\`                  | Y         | Y       | Y       | `sample`        |
| Bold-Italic           | \*\*\*sample\*\*\*          | **N**     | Y       | Y       | ***sample***    |
| Bold-Italic           | \*\*\_sample\_\*\*          | **N**     | Y       | Y       | **_sample_**    |
| Bold-Italic           | \_\*\*sample\*\*\_          | **N**     | Y       | Y       | _**sample**_    |
| Bold-Italic           | \*\_\_sample\_\_\*          | **N**     | Y       | Y       | *__sample__*    |
| Bold-Italic           | \_\_\*sample\*\_\_          | **N**     | Y       | Y       | __*sample*__    |
| Bold-Italic           | \_\_\_sample\_\_\_          | **N**     | Y       | Y       | ___sample___    |
| Highlight Italic      | \*\`sample\`\*              | **N**     | Y       | Y       | *`sample`*      |
| Highlight Bold        | \*\*\`sample\`\*\*          | **N**     | Y       | Y       | **`sample`**    |
| Highlight Bold-Italic | \*\*\*\`sample\`\*\*\*      | **N**     | Y       | Y       | ***`sample`***  |
  
#### Styling phrases

| Effect              | Combination                   | Text Tab  | Preview | GitHub  | Example                 |
| ------------------- |:-----------------------------:|:---------:|:-------:|:-------:|:-----------------------:|
| Italic              | \*first middle last\*         | Y         | Y       | Y       | *first middle last*     |
| Bold                | \*\*first middle last\*\*     | Y         | Y       | Y       | **first middle last**   |
| Highlight           | \`first middle last\`         | Y         | Y       | Y       | `first middle last`     |
| Italic in Bold      | \*\*first \*middle\* last\*\* | **N**     | Y       | Y       | **first *middle* last** |
| Italic in Bold      | \*\*first \_middle\_ last\*\* | **N**     | Y       | Y       | **first _middle_ last** |
| Italic in Bold      | \_\_first \*middle\* last\_\_ | **N**     | Y       | Y       | __first *middle* last__ |
| Italic in Bold      | \_\_first \_middle\_ last\_\_ | **N**     | Y       | Y       | __first _middle_ last__ |
| Highlight in Bold   | \*\*first \`middle\` last\*\* | **N**     | Y       | Y       | **first `middle` last** |
| Bold in Italic      | \*first \*\*middle\*\* last\* | **N**     | Y       | **N**   | *first **middle** last* |
| Bold in Italic      | \_first \*\*middle\*\* last\_ | **N**     | Y       | Y       | _first **middle** last_ |
| Bold in Italic      | \*first \_\_middle\_\_ last\* | **N**     | Y       | Y       | *first __middle__ last* |
| Bold in Italic      | \_first \_\_middle\_\_ last\_ | **N**     | Y       | **N**   | _first __middle__ last_ |
| Highlight in Italic | \*first \`middle\` last\*     | **N**     | Y       | Y       | *first `middle` last* |
  
#### Error cases

  *If a space precedes the final star... *
  the star is displayed and text is still italic.*            <br/>
  * No italics at all if a space follows the initial star.*   <br/>

  **If a space precedes the final pair of stars... **
  the stars are displayed and text is still bold.**           <br/>
  ** No bold at all if a space follows the initial star.**    <br/>

  Note that `   highlighting works even with spaces next to backticks    `
  but space after the leading backtick and before the final backtick is
  removed. <br/>
  
  <br/>

---

### Horizontal rules

  Any of the following lines will make a horizontal separator line:

      ---     Three or more "-" in a row
      - - -   Three or more "- " in a row
      ***     Three or more "*" in a row
      * * *   Three or more "* " in a row

  <br/>

---

### Lists

  **_NOTE_: The Markdown plugin and GitHub seem to handle the formatting of
  lists very differently.  It might take some effort to make any given list
  show up properly in both settings.**

  Precede lines with "\*", "\-", "\+" and/or numbers to show them in a list:
  
  1. Item 1   (original tag: "1.")
  * Item 2    (original tag: "\*")
  * Item 3    (original tag: "\*")
  4. Item 4   (original tag: "4.")
  - Item 5    (original tag: "\-")
  - Item 6    (original tag: "\-")
  7. Item 7   (original tag: "7.")
  + Item 8    (original tag: "\+")
  + Item 9    (original tag: "\+")
  10. Item 10 (original tag: "10.")

  Note that numbered items are re-numbered for you, and that they're treated
  differently in terms of line separation before and after each.

  **Nested lists**:

18. Item 1                                        (original tag: "18.")
  + Subitem 1-1 (indented two spaces)             (original tag: "\+")
  * Subitem 1-2 (indented two spaces)             (original tag: "\*")

22. Item 2 (original tag: "22.")
    * Subitem 2-1 (indented four spaces)          (original tag: "\*")
      + Subitem 2-1-1 (indented six spaces)       (original tag: "\+")
        * Subitem 2-1-1-1 (indented eight spaces) (original tag: "\*")
      - Subitem 2-1-2 (indented six spaces)       (original tag: "\-")
        * Subitem 2-1-2-1 (indented eight spaces) (original tag: "\*")
    * Subitem 2-2 (indented four spaces)          (original tag: "\*")

33. Item 3 (original tag: "33.")
  - Subitem 3-1 (indented two spaces)             (original tag: "\-")
    * Subitem 3-1-1 (indented four spaces)        (original tag: "\*")
      + Subitem 3-1-1-1 (indented six spaces)     (original tag: "\+")
    * Subitem 3-1-2 (indented four spaces)        (original tag: "\*")
      * Subitem 3-1-2-1 (indented six spaces)     (original tag: "\*")
  + Subitem 3-2 (indented two spaces)             (original tag: "\+")

  **Or**:

- Item 1                                          (original tag: "\-")
  43. Subitem 1-1 (indented two spaces)           (original tag: "43.")
  34. Subitem 1-2 (indented two spaces)           (original tag: "33.")

* Item 2                                          (original tag: "\*")
    1. Subitem 2-1 (indented four spaces)         (original tag: "1.")
      2. Subitem 2-1-1 (indented six spaces)      (original tag: "2.")
        + Subitem 2-1-1-1 (indented eight spaces) (original tag: "\+")
      4. Subitem 2-1-2 (indented six spaces)      (original tag: "4.")
        + Subitem 2-1-2-1 (indented eight spaces) (original tag: "\+")
    6. Subitem 2-2 (indented four spaces) (6)

* Item 3                                          (original tag: "\*")
  7. Subitem 3-1 (indented two spaces)            (original tag: "7.")
    8. Subitem 3-1-1 (indented four spaces)       (original tag: "8.")
      * Subitem 3-1-1-1 (indented six spaces)     (original tag: "\*")
    9. Subitem 3-1-1 (indented four spaces)       (original tag: "9.")
      * Subitem 3-1-1-1 (indented six spaces)     (original tag: "\*")
  10. Subitem 3-2 (indented two spaces)           (original tag: "10.")

#### Markdown plugin Preview

  The Preview is oriented toward 4-space indentation units so the depth of the
  list nesting (as identified by the displayed indentation and bullet/numbering
  style) only changes if the indentation changes by 4 or more spaces.  In the
  examples above, 

#### GitHub

  GitHub Markdown is oriented toward 2-space indentation units, so every
  indentation in the examples above changes the nesting depth.  This strategy
  is heavily biased toward numbered lists; if a numbered item is the first
  list item then the rest of the list will be treated as numbered.

<br/>

---

### Block quotes

  Precede lines with "\>" to group into a shaded box.  Style processing will
  occur within the lines.

> Item *one*              <br/>
> Item **two**            <br/>

> Continued after a gap   <br/>

  The "\>" must be at start of the line, otherwise the text is displayed
  literally.

 > Item *one*             <br/>
 > Item **two**           <br/>

 > Continued after a gap  <br/>

  Split lines.

> Item *one*              <br/>
  second line of item one <br/>
  third line of item one  <br/>

> Item **two**            <br/>
  second line of item two <br/>
  third line of item two  <br/>

  Block quotes can contain headers and other Markdown elements.

> # Item one
> Item one (a)    <br/>
> * List part 1   <br/>
> * List part 2   <br/>
> Item one (b)    <br/>
> ## Subitem
> Subitem (a)     <br/>
> > Interior quote part 1 ( *italic* )  <br/>
> > Interior quote part 2 ( **bold** )  <br/>
>   <br/>
> Subitem (b)     <br/>

<br/>

---

### Code blocks

  Lines indented by four spaces are displayed as a shaded block without
  additional formatting.

    print "Hello, world!\n";
    $a = 0;
    while ($a < 10) {
    print "$a...\n";
    $a++;
    }

  Everything between two lines with "```" are displayed in a box without
  additional formatting.

```
  index:
    general:                    Settings that are applicable to all environments
      base:
```
<br/>

---

## Markdown Extensions

  In addition to standard Markdown syntax, the RubyMine plugin support several
  additional syntax features listed below.  These are optional features which
  can be turned on or turned off through the **Markdown** setting panel
  accessed from **File|Settings** under the **Other Settings** selection. 

### Fenced Code Blocks (PHP Markdown Extra style)

  Everything between two lines with "~~~" are displayed in a box without
  additional formatting.

~~~
  print "Hello, world!\n";
  $a = 0;
  while ($a < 10) {
  print "$a...\n";
  $a++;
  }
~~~

  *Reference*:
  https://michelf.ca/projects/php-markdown/extra/#fenced-code-blocks <br/>
  <br/>

---

### Definition Lists (PHP Markdown Extra style)

  Single-line term followed by a definition line consisting of a colon and text.
  
  Apple
  :   Pomaceous fruit of plants of the genus Malus in 
      the family Rosaceae.
  
  Orange
  :   The fruit of an evergreen tree of the genus Citrus.
  
  *Reference*: https://michelf.ca/projects/php-markdown/extra/#def-list <br/>
  <br/>

---

### Abbreviations (PHP Markdown Extra style)

  **_NOTE_: This does not seem to work in the Markdown Preview tab**

  Support for HTML \<abbr\> tags, which allows definition of abbreviations so
  that any place the abbreviation is used, abbreviation text is substituted in
  the formatted document.

##### Example

  The definition lines do not appear in the formatted output.
  
  *[INST]:  University of Virginia
  *[PROG]:  Libra Institutional Repository
  
  Abbreviation for INST expanded: INST <br/>
  Abbreviation for PROG expanded: PROG <br/>
  
  *Reference*: https://michelf.ca/projects/php-markdown/extra/#abbr <br/>
  <br/>

---

### Tables (MultiMarkdown style)

  You can create tables that are readable as text and also formatted nicely as
  Markdown viewable through the Markdown plugin "Preview" tab and through the
  GitHub display of the page.
  
  Although the main reason to have Markdown documentation embedded in the
  project code directory is to make it readily available when programming
  (especially through the RubyMine IDE), the other reason is to make the
  project more understandable when viewing the code through GitHub.
  
  ***Tip***: Avoid table constructs that work in the Preview tab but not in
  GitHub, or *vice versa*.  The following table features should be avoided:
  
  **Multirow headers**
  :   GitHub only accepts one row for column headers.
  
  **Table titles**
  :   GitHub does not honor the \[title\] construct that follows the table.

  *Reference*: http://fletcher.github.io/MultiMarkdown-4/tables.html <br/>

##### Example 1: For easier reading as a text file

| Left justified  | Centered Cells | Right justified |
| --------------- |:--------------:|----------------:|
| Content         | *Long Cell*                     ||
| Content         || *Short Cell*                    |
| Content         | **Cell**       | Cell            |
|                                                |||
| New section     | More           | Data            |
| And more        | With an escaped '\|'            ||
| And more        | xxx            | yyy             |

##### Example 2: Same table (multiline column headers)

|Left justified<br/>LJ two<br/>LJ three|Centered Cells<br/>CC two<br/><br/>|Right justified<br/>RJ two<br/>RJ three|
|--|:-:|-:|
|       Content |        *Long Cell*||
|Content||*Short Cell*|
|     Content      |    **Cell**|Cell       |
| |||
|New section| More           | Data            |
|And more       | With an escaped '\|'            ||
|And more       | xxx            | yyy             |

##### Example 3: Similar table (from reference)

  **_NOTE_: The "New Section" part does not seem to work in the Markdown
  Preview tab**
  <br/><br/>

|               |          Grouping            ||
| First Header  | Second Header | Third Header  |
  ------------- |:-------------:| -------------:|
  Content       |          *Long Cell*         ||
  Content       |   **Cell**    |          Cell |

  New section   |     More      |          Data |
  And more      | With an escaped '\|'         ||

<br/>

---

### Strikethrough (Pandoc/GitHub style)

  **_NOTE_: This does not seem to work in the Markdown Preview tab**

  To strikeout a section of text with a horizontal line, begin and end it with
  "\~\~".

  ~~This is a deleted sentence.~~                               <br/>
  This is ~~deleted text~~ in a sentence.                       <br/>
  This is ~~ not deleted text ~~ just text with literal tildes. <br/>
  
  *Reference*: http://pandoc.org/demo/example9/pandocs-markdown.html#strikeout <br/>
  <br/>

---

### References

  [What is Markdown?]     (http://whatismarkdown.com/)                                      <br/>
  [Markdown syntax]       [markdown]                                                        <br/>
  [PHP Markdown Extra]    [php_extra]                                                       <br/>
  [MultiMarkdown tables]  [tables]                                                          <br/>
  [Pandoc strikeout]      [strikeout]                                                       <br/>
  [GitHub Markdown]       [github]                                                          <br/>
  [Markdown Basics]       (https://help.github.com/articles/markdown-basics/)               <br/>
  [Mastering Markdown]    (https://guides.github.com/features/mastering-markdown/)          <br/>

<!-- Topic link references used above:
REF --------- LINK -------------------------- TOOLTIP ------------------------>
[github]:     https://help.github.com/articles/github-flavored-markdown/
[markdown]:   http://daringfireball.net/projects/markdown/syntax
[php_extra]:  https://michelf.ca/projects/php-markdown/extra/
[strikeout]:  http://pandoc.org/demo/example9/pandocs-markdown.html#strikeout
[tables]:     http://fletcher.github.io/MultiMarkdown-4/tables.html
