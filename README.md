#  table-baseline.css
> A good start to your table styles that covers most of the challenges and a few edge cases

[![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

**NPM**
```
npm install --save table-baseline.css
```

**Download**
`https://raw.githubusercontent.com/paceaux/table-baseline/master/src/baseline.table.css`

## What does it do?
### It gives you a good start
Built on the typography-baseline foundations, it gives you a good, _small_ set of styles for tables to work with

### Gives you a "no-design" design
For those times where you need just a bit more than a [Normalize](http://necolas.github.io/normalize.css/), but way less than [Bootstrap](https://getbootstrap.com/), this gets your tables there. 

This is a fairly unopinionated approach to making sure that tables look like tables

## Browser Support
* Firefox
* Chrome
* Edge
* Safari
* Opera


## Usage
While this is relatively unopinionated, there are a few "opinions" to consider:

* `em` for for `font-size`
* a unitless `line-height`
* `rem` for left/right spacing
* text-spacing based on the golden ratio (.618 / 1.618)

### Fitting it into a CSS architecture
This would come after a reset / normalize and and after your set baseline styles. If you're a fan of [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), this is in the Elements layer.

### Modifying without Swearing or Heavy Drinking
One of the really annoying things about other CSS frameworks (cough cough <small>Bootstrap</small>) is that you mostly have to write new CSS to overwrite the existing styles. Often that means raising specificity, which is really stinking annoying. This is designed to avoid that by using [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)


The table baseline sets most of the CSS variables on the `table`. As CSS variables are subject to the cascade, you can override _any_ variable at any time by changing its value on the relevant selector. You can import this into your current CSS setup, and overwrite all the variables by setting new ones whereever makes sense.


All of the variables are prefixed with `table` so that they can't collide with any other css variables you may have. 

They also inherit values from the typography-baseline. But if you choose not to use it, that's totally fine! They all have default values. 


So if you want the `--tablePrimaryBgColor` to be different, you can write the following in your own stylesheet:

```
table.myClass {
    --tablePrimaryBgColor: #c0ffee;
}
```

No raising specificity. Just changing a variable. 

If you want to theme the header of the table, or even a particular widget, it's just:

```
.myClass thead {
    --tableAlternatingBgColor: #c0ffee;
}
```

#### Colors
All of the colors variables are abstractions from the color palette. This is so you can change these colors without having to touch your neutral palette. 

```
    --tableBaseTextColor: var(--colorNeutralDarker);
    --tableBodyPrimaryBgColor: transparent;
    --tableBodyAlternatingBgColor: rgba(165,165,165, .3);

    --tablePrimaryBgColor: var(--tableBodyPrimaryBgColor);
    --tableAlternatingBgColor: var(--tableBodyAlternatingBgColor);

```

#### Line Heights
The `--baseLineHeight` is applied to body copy, and the `--smallLineHeight` is used on titles:

```    
    --tableBaseLineHeight: var(--smallLineHeight, 1.2);
    --tableSmallLineHeight: 1;
```

#### Text Sizes
You have a minimum of 6 text sizes in two categories: `--table<n>TextSize` and `--table<n>TitleSize`. You have a "base" and then superlatives or diminutives to describe the deviation from that base. e.g.:


```
    --tableBiggestTextSize: var(--biggerTextSize, 1.2em);
    --tableBiggerTextSize: var(--bigTextSize, 1.1em);
    --tableBaseTextSize: var(--smallTextSize, .8em);
    --tableSmallerTextSize: var(--smallerTextSize, .75em);
    --tableSmallestTextSize: var(--smallerTextSize, .618em);
```

You may notice that title sizes overlap with base text sizes. This is intentional! You have the flexibility to have your smaller headings be the same as larger text, or to create new title sizes for your headings that won't overlap with the text. 


```
    --tableBiggestTitleSize: var(--baseTitleSize, 1.5em);
    --tableBiggerTitleSize: var(--biggestTextSize, 1.3em);
    --tableBaseTitleSize: var(--tableBiggestTextSize);
    --tableSmallerTitleSize: var(--tableBiggerTextSize);
    --tableSmallestTitleSize: var(--tableBaseTextSize);
```

#### Variables Set Per Section
The `tbody`, `tfoot`, and `thead` all rely on a few key variables:

* <var>--tableCellSize</var>
* <var>--tableHeaderSize</var>
* <var>--borderWidth</var>
* <var>--tablePrimaryBgColor</var>
* <var>--tableAlternatingBgColor</var>

The `<th>` and `<td>` elements use these variables for their presentation. This is so that you can theme each section of the table without having to raise specificity. You could just add this in a later stylesheet:

```
thead {
    --tablePrimaryBgColor: orange;
}
```




#### Font families
You have two font families to choose from.

```
    --tableBaseFontFamily: var(--baseFontFamily,  'Georgia','Times New Roman', 'serif');
    --tableTitleFontFamily: var(--titleFontFamily, 'Helvetica', 'Arial', 'sans-serif');
```

## Conventions and Standards

### Style guide
The CSS follows the guidelines established [here](https://gist.github.com/paceaux/f31e278613ab29b74a412a7eb5046422).

### Naming Conventions
CSS Variable names follow a convention established [here](https://gist.github.com/paceaux/8638765e747f5bd6387b721cde99e066#sassscssstylus-naming).


[license-image]: http://img.shields.io/npm/l/table-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/table-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=table-baseline.css

