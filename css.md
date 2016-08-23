# CSS

## Common requirements

#### CSS is dangerous
All CSS rules are global and almost all newbies misuse this feature. It is extremely easy to end up medium and large projects with overcomplicated styles. If you trapped - you couldn't change any style without modifying the whole bunch of other elements. To prevent these hazards learn and use various methods of organizing the styles:
1. [BEM](https://en.bem.info/)
2. [Simple CSS pattern](https://isobar-idev.github.io/code-standards/#css_a_simple_css_code_pattern)
3. [rscss](http://rscss.io/)


#### Use [Pixel Perfect Extension](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi) if your client has provided you with design mockups
 Always set appropriate zoom for the web page to be able to compare all dimensions

#### Don't use styles from external sources
 CDN is not extremely useful. Possibility that user's browser has already cached the library with appropriate version is very low

#### Don't use @import directive for loading styles in the production CSS
 Although nothing bad will happen if use imports that will be replace with such tools like Webpack

#### Divide all `.css` files into separate modules
 Each module should have less than 500 lines

#### Don't put two CSS rules in one line, use line breaks
 Even if you have one rule for given selector - create a separate line for this. This approach is helpful at least for checking diffs in your CVS

#### Don't forget about hidden layers in files with design
 Almost every interactive element (button, input or link) has separate styles for hover or pressed states

#### Always try to make page as liquid as possible
 Use static layout only if your client demands

#### Groups and sort style blocks
All styles of one block should be in one place. All styles should be sorted in order the block is located on the page.  
Good:
```
.header {...}
.header-search-form {...}
.header-search-input {...}

.content {...}
.content-heading {...}
.content-sidebar {...}
```    
Bad:
```
.header {...}
.content {...}
.header-search-form {...}
.content-heading {...}
.header-search-input {...}
.content-sidebar {...}
```

#### Keep a footer at the bottom of the page
 There are plenty methods over the web how to do it. For old browser use absolute position and simple padding without negative margins

#### Use lower-case-hyphenated for class names
 Don't use mySuperAwesomeElement or my_super_awesome_element

#### Give names to classes that reflect the meaning, not the styles
 Prefer "loading" to "big-yellow-spinny-thing"

## Requirements about CSS rules
#### Don't use `!important`
 In 99% cases you can just increase the priority of the selector

#### Don't use `position: absolute` where it is possible
  Flow of an elements is extremely important - try to break it as rare as possible

#### Don't move elements with "top", "bottom", "left" or "right" rules that have `position: relative`
 The relative position is quite confusing, so always try to move elements with margin or padding. Move elements in exceptional cases

#### Don't use negative margins
 However, it is valid property and W3C allows it,  negative margins are more confusing than `position: absolute`. There is the [great guide](https://www.smashingmagazine.com/2009/07/the-definitive-guide-to-using-negative-margins/) about such margins, but all techniques can be replaced with more obvious solutions.

#### Avoid fixed height and max-height
Fixed height can lead to confusion of your teammates and overlapped elements. You can use fixed height when there is no other way or it is a requirement of design:
1. For example, we have a slider, all elements have `position: absolute` and they move with JS scripts. Here we have to set height to the slider container because all children have `position: absolute`
2. In the design we have a list of blocks with fixed height, all overflowing content should be hidden.

#### Avoid fixed alignments
Always try to align elements dynamically (with `margin: 0 auto`, `vertical-align: middle` or modern flexboxes)

#### Define default styles for `<html>`
 Set background color, font-family, font-size and font color for `<html>`. Remember that font-size of `<html>` tag is a reference point for the `rem`s font sizes.

#### Define `cursor: pointer` for interactive elements that does not support it by default
 Set `cursor: pointer` for all clickable `<div>`s, `<span>`s etc

#### Don't break proportion when using `<img />`
 Don't set width and height simultaneously, if design requires set both dimension to use `background-image: url(...) no-repeat center center` and `background-size: cover`

#### Avoid duplicating and redundant rules
 This will simplify your code and will make life of your teammates much easier

#### Capitalize words with `text-transform: uppercase`
 If you have some words with only upper cased symbols use `text-transform: uppercase`. Exception is abbreviation
 
#### Define `:focus` styles for elements with `outline: none`
 Outline style is useful for users who fill forms with keyboard

#### Define styles for adaptive view inside @media right after primarily rules
 Try to keep all styles of one element in one place including media queries


## Fonts
#### Use `.ttf`, `.svg` (and `.eot` for IE less then 9) for included files
 Use [Font Squirrel](https://www.fontsquirrel.com/) for generating these files. The `.ttf` file will be enough for almost all modern browsers. Please check [this blog post](https://www.fontsquirrel.com/blog/2010/12/how-to-use-the-generator) to see the version of supported browsers for each font format

#### If there are non-latin symbols add appropriate subsettings
 Check that your font file contains needed symbols. If you use [Font Squirrel](https://www.fontsquirrel.com/) for font's files generation and "expert" mode is enabled, check the appropriate checkboxes.

#### Use the same name for different styles of fonts
 The italic and light/bold versions of fonts  are usually separate files with different names. Please keep the font name in CSS the same, the example is:
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
 `Helvetica` is a pluggable font with a separate file.  
 `Arial` is a Web safe font.  
 `sans-serif` is a subset, that will be used if Arial is not supported by a client.
 Subset can be 'Serif', 'Sans-serif', 'Monospace' and very rarely 'Cursive'.  
 For 'Serif' we prefer Georgia, for 'Sans-serif' Arial and for 'Monospace' Courier New. We have never used  'Cursive' in practice yet, although you can use Comic Sans for default value :)

#### Quote font name if it contains white space, digits or punctuation characters other than hyphens
For example `font-family: "Times New Roman", serif.`

## CSS implicit rules

#### Margin collapsing
[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing) says: 
> Top and bottom margins of blocks are sometimes combined (collapsed) into a single margin whose size is the largest of the margins combined into it, a behavior known as margin collapsing.

Be aware that margin of first child will move the parent  in most cases too (learn more in [the article on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing))

#### Parent will collapse if children float
Please, learn and remember [this thread](http://stackoverflow.com/questions/218760/how-do-you-keep-parents-of-floated-elements-from-collapsing) on StackOverflow.

#### Z-index only works on positioned elements (position:absolute, position:relative, or position:fixed).
> The problem with z-index is that very few people understand how it really works. It’s not complicated, but it if you’ve never taken the time to read its specification, there are almost certainly crucial aspects that you’re completely unaware of

Learn more [here](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/).



