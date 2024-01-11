# Manuel de Codage Icons

This is a Javascript library that can create SVG images for hieroglyphs encoded in the Manuel de Codage (MdC) standard. The most complete description of MdC can be found [here](http://www.catchpenny.org/codage/). The library is in principle intended for individual hieroglyphs to be displayed, not to support full MdC. This is done by the `draw` function. However, there is support for a more complete MdC code in the `parse` function. The `parse` function will first parse a complete MdC (or .gly) file into text and hieroglyphs, and then call upon the draw function to render the individual hieroglyphs it generated.

## draw

The library will generate SVG images for all hieroglyphs on a page - similar to the way for instance [fontawesome](https://fontawesome.com/) produces icons. The default is to replace for all the `span`s of the class `token-glyphs`, and produce the hieroglyph as an SVG image (the innerHTML) based on the MdC code in the `@title` attribute. So it will produce Hieroglyphs for all elements of the following form:

```
<span class="token-glyphs" title="M17-X1"></span>
```

You initiate the function as follows:

```
<script>MdCIcons.draw();</script>
```

Each SVG will combine base glyphs into carats. The base glyphs (gardiner numbers) will be generated in a hidden DIV. Base glyphs that have a unicode symbol will (by default) be generated as text elements, while all glyphs that do not have a unicode symbol will be loaded as raw SVG over Ajax. So the base glyph A1 will be generated as text (𓀀) while A71 is not in the Unicode block, so it will be loaded from a file A71.svg at the specified server, by default from the JavaScriptSesh project: ![https://raw.githubusercontent.com/rosmord/JavaScriptSesh/master/images/glyphs/A71.svg](https://raw.githubusercontent.com/rosmord/JavaScriptSesh/master/images/glyphs/A71.svg). It is possible to load all glyphs as SVG, which will result in more uniform glyphs, but the SVG will be heavier, and it will not be possible to copy the text from the SVG.

The `draw` function can take a JSON object as its argument, where the following options can be specified:

| Feature | Value | Description | Default value |
|----------|---------|------------|----|
| lineheight | int | height of the SVG image | 24px |
| unicode | bool | when set to false, the system will always use SVG images from the glyph URL | true |
| svgurl | string | URL where the individual glyphs will be loaded from | [JavaScriptSesh](https://raw.githubusercontent.com/rosmord/JavaScriptSesh/master/images/glyphs/) |
| css | string | URL for a CSS style sheet for the SVG | none |
| attr | string | Attribute to use for the MdC code  | title |
| class | string | Class to use for the hieroglyph elements  | token-glyphs |

You can try out the draw function on [JSFiddle](https://jsfiddle.net/maartenes/ovgr912c/)

## parse

The `parse` function is called similar to the `draw` function:

```
<script>MdCIcons.parse();</script>
```

The parse function looks for a div with @id="glydiv", and parse the innerText as MdC. It converts the plain text into text and span elements, and then converts the span elements into SVG images using the draw function.

## Related projects

[JavaScriptSesh](https://github.com/rosmord/JavaScriptSesh)
