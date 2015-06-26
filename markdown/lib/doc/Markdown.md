<!-- lib/doc/Markdown.md -->

# Documenting with Markdown for RubyMine

  Although Markdown (*.md) files can simply stand alone as text files, if you
  install the Markdown plugin (File|Settings|Plugins) you can more fully use
  Markdown format files for documentation purposes.

## Markdown plugin

  The plugin adds two features to RubyMine:

  + *Markdown syntax highlighting*
    This makes the contents of the file easier to read even displayed as text.
    
  + *Markdown preview tab*
    This adds adds a "Preview" tab to the bottom of the window for a Markdown
    file which displays the file in formatted form.

  To add these features, install the Markdown plugin from **File|Settings**
  under the **Plugins** selection.  Check the box to the right of the
  "Markdown" entry and press "OK" to install the plugin.  After installation,
  options for the plugin will found in the **Other Settings** selection.

## Markdown Features

### Styling text

  Surround text with a single _underline_ or *star* for _italic_ text.
  Surround text with two stars for **bold** text.
  <br/><br/>

| Effect      | Combination         | Text Tab  | Preview | Example       |
| ----------- | ------------------- |:---------:|:-------:| ------------- |
| Italic      | \_sample\_          | Y         | Y       | _sample_      |
| Italic      | \*sample\*          | Y         | Y       | *sample*      |
| Bold        | \*\*sample\*\*      | Y         | Y       | **sample**    |
| Bold-Italic | \*\*\*sample\*\*\*  | N         | Y       | **_sample_**  |
| Bold-Italic | \*\*\_sample\_\*\*  | N         | Y       | **_sample_**  |
| Bold-Italic | \_\*\*sample\*\*\_  | N         | Y       | _**sample**_  |
[*Styling words*]

| Effect      | Combination                   | Text Tab  | Preview | Example                 |
| ----------- | ----------------------------- |:---------:|:-------:| ----------------------- |
| Bold-Italic | \*\*first \_sample\_ last\*\* | N         | Y       | **first _sample_ last** |
| Bold-Italic | \_first \*\*sample\*\* last\_ | N         | Y       | _first **sample** last_ |
| Bold-Italic | \*\*first \*sample\* last\*\* | N         | Y       | **first *sample* last** |
| Bold-Italic | \*first \*\*sample\*\* last\* | N         | Y       | *first **sample** last* |
[*Styling sentences*]

  *If a space precedes the final star... *
  the star is displayed and text is still italic.*            <br/>
  * No italics at all if a space follows the initial star.*   <br/>

  **If a space precedes the final pair of stars... **
  the stars are displayed and text is still bold.**           <br/>
  ** No bold at all if a space follows the initial star.**    <br/>
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

  Precede lines with "\*", "\-" and/or "\+" to show them in a list:

  * Item 1
  - Item 2
  + Item 3

  Precede lines with numbers for a numbered list:

  1. Item 1
  2. Item 2
  3. Item 3

  **Nested lists**:

1. Item 1
  * Subitem 1-1 (indented two spaces)
  * Subitem 1-2 (indented two spaces)
2. Item 2
    * Subitem 2-1 (indented four spaces)
      - Subitem 2-2 (indented six spaces)
        * Subitem 2-2-2 (indented eight spaces)
3. Item 3
  - Subitem 3-1 (indented two spaces)
    * Subitem 3-1-1 (indented four spaces)
      - Subitem 3-1-2 (indented six spaces)

  **Or**:

* Item 1
  1. Subitem 1-1 (indented two spaces)
  2. Subitem 1-2 (indented two spaces)
* Item 2
    1. Subitem 2-1 (indented four spaces)
      2. Subitem 2-2 (indented six spaces)
        3. Subitem 2-2-2 (indented eight spaces)
* Item 3
  1. Subitem 3-1 (indented two spaces)
    2. Subitem 3-1-1 (indented four spaces)
      3. Subitem 3-1-2 (indented six spaces)
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
  Markdown.
  
  ***Tip***: begin the table title with a break (\<br/\>) to create a gap
  between the table and the preceding text.

  *Reference*: http://fletcher.github.io/MultiMarkdown-4/tables.html <br/>

##### Example 1: For easier reading as a text file

|                 | Grouping                        ||
| Left justified  | Centered Cells | Right justified |
| --------------- |:--------------:|----------------:|
| Content         | *Long Cell*                     ||
| Content         || *Short Cell*                    |
| Content         | **Cell**       | Cell            |
|                                                |||
| New section     | More           | Data            |
| And more        | With an escaped '\|'            ||
| And more        | xxx            | yyy             |
[<br/> *Figure 1*]

##### Example 2: Same table

| |       Grouping||
|Left justified              |Centered Cells |Right justified|
|--|:-:|-:|
|       Content |        *Long Cell*||
|Content||*Short Cell*|
|     Content      |    **Cell**|Cell       |
| |||
|New section| More           | Data            |
|And more       | With an escaped '\|'            ||
|And more       | xxx            | yyy             |
[<br/> *Figure 2*]

##### Example 3: Similar table (from reference)

  **_NOTE_: The "New Section" part does not seem to work in the Markdown
  Preview tab**
  <br/><br/>

|               |          Grouping            ||
  First Header  | Second Header | Third Header  |
  ------------- |:-------------:| -------------:|
  Content       |          *Long Cell*         ||
  Content       |   **Cell**    |          Cell |

  New section   |     More      |          Data |
  And more      | With an escaped '\|'         ||
[<br/> *Figure 3*]

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

  Markdown syntax       http://daringfireball.net/projects/markdown/syntax              <br/>
  PHP Markdown Extra    https://michelf.ca/projects/php-markdown/extra/                 <br/>
  MultiMarkdown tables  http://fletcher.github.io/MultiMarkdown-4/tables.html           <br/>
  Pandoc strikeout      http://pandoc.org/demo/example9/pandocs-markdown.html#strikeout <br/>
  GitHub Markdown       https://help.github.com/articles/github-flavored-markdown/      <br/>
