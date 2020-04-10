[![Build Status](https://travis-ci.com/tbrowder/Excel-Text-Template-Raku.svg?branch=master)](https://travis-ci.com/tbrowder/Excel-Text-Template-Raku)

# Excel::Text::Template

Use a text template to generate an `Excel` `*.xlsx` file

## DESCRIPTION

This module provides the capability of using a text template
to generate an Excel file. It is a WIP and has no working code
at the moment. If you are interested in the concept, please
star the project, follow it, and file a feature request issue.

The project will use several Perl modules which will have to
be installed for the distro to work (I use `cpanm` for that):

+ Perl modules required:

    + `Excel::Writer::XLSX`
    + `Spreadsheet::XLSX`

## GENESIS

This project started when I was trying to automate creating forms for
my tax return. I have a need to generate multiple workbooks, one
worksheet per workbook, from a template, and am designing my own
format for that purpose. I will use the `Raku` language to parse the
text-file template, then, with the aid of the `Raku` module
`Inline::Perl5`, I will read my xlsx data files with one of the Perl
xlsx readers and then use this module to write new, filtered files in
the form of the template.

I am just starting, but I'm looking at a template format something like
this, one line per row, cells separated by pipes (`|`), key/value
attribute pairs (using a syntax similar to `Raku`) following the cell content:

``` Raku
# This is a comment. The following row describes one xlsx row with four columns (the
# first column being empty) and it has an ending comment.
# Comments are stripped to the end-of-line eol before parsing the row.

| some text | 5.26 | ="some formula" :color(red) :width(2) # comment...

# empty rows are ignored, the worksheet will have all rows padded with empty cells
# to the maximum number of cells found on any row

# another comment and more rows following
|  # this is a row with two empty cells
```

I plan to use `Raku`'s grammar to parse the template file.


AUTHOR
======

Tom Browder, `<tom.browder@gmail.com>` (`tbrowder` on IRC `#raku`)

COPYRIGHT & LICENSE
===================

Copyright (c) 2020 Tom Browder, all rights reserved.

This program is free software; you can redistribute it or modify
it under the same terms as Raku itself.

See that license [here](./LICENSE).
