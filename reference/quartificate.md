# Transform Google Doc to Quarto book

Transform Google Doc to Quarto book

## Usage

``` r
quartificate(gdoc_id, path, render = FALSE, fix_lists = FALSE)
```

## Arguments

- gdoc_id:

  ID of the Google Document.

- path:

  A path, where to create the Quarto book. It will be created if needed.

- render:

  Logical. Whether to render the resulting Quarto book.

- fix_lists:

  Logical. Whether to try and fix lists, see Details.

## Value

Nothing.

## Details

If your Google Document contains lists whose items span several lines,
you might get better results with the `fix_lists` parameter set to
`TRUE`. The problem is that in Google Docs lists, from the second line
lines in items have a small indentation. Pandoc tends to interpret this
as a blockquote. We try to fix that by merging blockquotes in their
previous sibling, when that previous sibling is a list item.

## Examples

``` r
if (FALSE) { # interactive()
id <- googledrive::drive_find(
    q = "name contains 'My Example Document'"
  )$id
 quarto_dir <- withr::local_tempdir()
 quartificate::quartificate(id, quarto_dir, render = TRUE)
}
```
