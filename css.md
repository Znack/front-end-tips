# CSS

## Common requirements
#### Use [Pixel Perfect Extension](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi) if client has provided you with the design mockups
Always set appropriate scale for the web-page to be able compare all dimensions

#### Don't use styles from external sources
CDN is not exteremely usefull. Possibility that user's browser has already cached the library with appropriate version is very low

#### Don't use @import directive for loading styles
You had better concatenate all files by gulp or webpack

#### Divide all `.css` files into separate modules
Each module should be less than 500 lines

#### Don't put two css rules on one line, use line breaks
Even if you have one rule for given selector - create separate line for this

#### Don't forget about hidden layers in files with design
Almost every interactive element (button, input or link) has separate styles for hover or pressed states

#### Always try to make page as liquid as possible
Use static layout only by demand of the client

#### Keep a footer at the Bottom of the page
There are plenty methods over the web, how to do it. For old browser use absolute position and simple padding without negative margins

#### Use lower-case-hyphenated for class names
Don't use mySuperAwesomeElement or my_super_awesome_element

#### Give names to classes that reflect the meaning, not the styles
Prefer "loading" to "big-yellow-spinny-thing"

## Requirements about css rules
#### Don't use `!important`
In 99% cases you can just increase the priority of the selector

#### Don't use `position: absolute` where it is possible
The flow of the elements is important very much - try to break it as rare as possible

#### Don't move elements with "top", "bottom", "left" or "right" rules that has `position: relative`
Relative position is quite confusing, so always try to move elements only with margin or padding. Move elements only in exceptional cases

#### Don't use negative margins
However it is valid property and W3C allows it, the negative margins are more confusing than `position: absolute`. There is [great guide](https://www.smashingmagazine.com/2009/07/the-definitive-guide-to-using-negative-margins/) about such margins, but all techniques can be replaced with more obvious solutions.

#### Define default styles for `<html>`
Set background color, font-family, font-size and font color for `<html>`. Remember that font-size of html tag will be reference point for the `rem`s font sizes.

#### Define `cursor: pointer` for interactive elements that does not support it by default
Set `cursor: pointer` for all clickable `<div>`s, `<span>`s etc

#### Don't break proportion when using `<img />`
Don't set width and height simultaneously, if design requires set both dimension use `background-image: url(...)` and `background-size: cover`

#### Avoid duplicating and redundant rules
This will simplify your code and will make life of your colleagues much easier

#### Define styles for adaptive view inside @media right after primarily rules
Try to keep all styles of one element in one place including media queries


## Fonts
#### Use .ttf, .svg (and .eot if IE<9 is required) for included files
Use [Font Squirrel](https://www.fontsquirrel.com/) for generating there files. Only .ttf file will be enough for almost all your clients if you have dropped the support of IE<9, please check [this blog post](https://www.fontsquirrel.com/blog/2010/12/how-to-use-the-generator)

#### If there are non-latin symbols add appropriate subsettings
Check that your font file contains needed symbols. If you use [Font Squirrel](https://www.fontsquirrel.com/) for font's files generation and "expert" mode is enabled check the appropriate checkboxes.

#### Use the same name for different styles of fonts
The italic and light/bold versions of fonts usually are separate files with different names, but please keep the font name in CSS the same. The example is:
```
@font-face {
    font-family: "Lato";
    src: url("../fonts/lato-regular.woff2") ...;  /* Pay attention: font is regulat and "..." replaced for other formats */
    font-weight: 400;
    font-style: normal; 
}
@font-face {
    font-family: "Lato";
    src: url("../fonts/lato-italic.woff2") ...;  /* Pay attention: font is regular italic and "..." replaced for other formats */
    font-weight: 400;
    font-style: italic; 
}
@font-face {
    font-family: "Lato"; 
    src: url("../fonts/lato-light.woff2") ...;  /* Pay attention: font is light and "..." replaced for other formats */
    font-weight: 300;
    font-style: normal; 
}
@font-face {
    font-family: "Lato";
    src: url("../fonts/lato-lightitalic.woff2") ...;  /* Pay attention: font is light italic and "..." replaced for other formats */
    font-weight: 300;
    font-style: italic; 
}
```

#### Learn all popular CSS units
You should know differences between `px`, `em`, `%`, `rem`, `vw`, `vh`, `vmin`, `vmax`. Prefer `rem` for elements without specific requirements (for example static size or relative to window width)

#### Always specify one Web safe font and subset for each `font-family`
Example: `font-family: Helvetica, Arial, sans-serif;`
`Helvetica` is a pluggable font with separate file.
`Arial` is a Web safe font.
`sans-serif` is a subset, that will be used if Arial is not supported by client.
Subset can be 'Serif', 'Sans-serif', 'Monospace' and very rarely 'Cursive'.
For 'Serif' we prefer Georgia, for 'Sans-serif' Arial and for 'Monospace' Courier New. We have never used in practice 'Cursive' yet, although you can use Comic Sans for default value :)

#### If font name contains white space, digits, or punctuation characters other than hyphens quote them
For example `font-family: "Times New Roman", serif.`






