
quaint-look-nice
================

A not-too-bad-looking theme for Quaint.


## Install

    npm install quaint-look-nice -g


## Sample configuration

This configuration entry must be added in the `plugins` field of
`quaint.json`:

```json
"look-nice": {
  "fonts": {
    "body": "serif",
    "nav": "g:Open Sans"
  },
  "backgrounds": {
    "nav": "purple"
  },
  "extra": "your-style.sass"
}
```


## Options

### extra

Path to a user-defined `sass` file (indented syntax). That code will
have access to all the variables defined by `quaint-look-nice` and can
be used for customization. It is appended at the very end.

### useNav

(default: true)

Whether to use a navbar or not. If false, the navbar style will not be
copied.

### fonts, font-sizes, borders, widths, paddings, backgrounds, colors

These maps define variables with the corresponding prefixes
(`font-xyz`, `font-size-xyz`, and so on).

**Google Fonts**: in `fonts`, any font name prefixed with `g:` will
cause the corresponding font on Google Fonts to be imported. See
[quaint-google-fonts](https://github.com/breuleux/quaint-google-fonts)
for more information.

The `defaults` section below lists all the default values for the
variables. Remember that if there is anything you cannot do with these
variables, you can write your own `sass` file and list it in the
plugin's `extra` option.


## Defaults

The following JSON contains the default values for all of
`quaint-look-nice`'s variables. Many of them are pegged to other
variables. Note that `fonts.body` corresponds to the `$font-body`
variable, and so on.

`tweak(color, percent)` changes a color's brightness by the given
percentage, if the color is dark it gets lighter, if it is light it
gets darker. `bwtext(color)` is black if the color is light, white if
the color is dark. `darken` and `lighten` are self-explanatory.

```json
{
   "fonts": {
      "body": "sans",
      "nav": "$font-body",
      "header": "$font-body",
      "title": "$font-header",
      "pre": "Monospace",
      "code": "$font-pre"
   },
   "font-sizes": {
      "body": "20px",
      "nav": "$font-size-body",
      "dropdown": "$font-size-body",
      "caret": "$font-size-nav * 0.8"
   },
   "borders": {
      "nav": "2px solid darken($background-nav, 20%)",
      "nav-dropdown": "10px solid $background-nav-dropdown"
   },
   "widths": {
      "body": "700px",
      "nav": "$width-body + 2 * $padding-body"
   },
   "paddings": {
      "body": "10px",
      "nav": "$padding-body",
      "td": "5px"
   },
   "backgrounds": {
      "body": "#fff",
      "nav": "$background-body",
      "nav-select": "tweak($background-nav, 20%)",
      "nav-dropdown": "tweak($background-nav, 10%)",
      "nav-dropdown-select": "tweak($background-nav-dropdown, 10%)",
      "pre": "$background-body",
      "code": "$background-body",
      "table": "tweak($background-body, 10%)",
      "table-odd": "tweak($background-table, 5%)",
      "table-header": "tweak($background-table, 20%)"
   },
   "colors": {
      "body": "tweak($background-body, 85%)",
      "nav": "bwtext($background-nav)",
      "nav-select": "bwtext($background-nav-select)",
      "nav-dropdown": "bwtext($background-nav-dropdown)",
      "nav-dropdown-select": "bwtext($background-nav-dropdown-select)",
      "link": "contrasting($background-body, #aaf, #00f)",
      "link-visited": "contrasting($background-body, #f8f, #808)",
      "pre": "bwtext($background-pre)",
      "code": "bwtext($background-code)",
      "table": "bwtext($background-table)",
      "table-odd": "bwtext($background-table-odd)",
      "table-header": "bwtext($background-table-header)",
      "header": "$color-body",
      "title": "$color-header"
   }
}
```


