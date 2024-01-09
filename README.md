# Manuel de Codage Icons

This is a Javascript library that can create SVG images for hieroglyphs encoded in the Manuel de Codage (MdC) standard.

The library will generate SVG images for all hieroglyphs on a page - similar to the way amazingfonts produce icons. The default is to look for all the spans of the class `token-glyphs`, and produce the SVG as the innerHTML based on the MdC code in the `@title` attribute. So it will produce Hieroglyphs for all elements of the following form:

```
<span class="token-glyphs" title="M17-X1"></span>
```

You initiate the function as follows:

```
<script>MdCIcons.draw();</script>
```

Each SVG will combine base glyphs into carats. The base glyphs (gardiner numbers) will be generated in a hidden DIV. Base glyphs that have a unicode symbol will (by default) be generated as text elements, while all glyphs that do not have a unicode symbol will be loaded as raw SVG over Ajax. So the base glyph A1 will be generated as text (𓀀) while A71 is not in the Unicode block, so it will be loaded from a file A71.svg at the specified server, by default from the JavaScriptSesh project: ![https://raw.githubusercontent.com/rosmord/JavaScriptSesh/master/images/glyphs/A71.svg](https://raw.githubusercontent.com/rosmord/JavaScriptSesh/master/images/glyphs/A71.svg).  

The `draw` function can take a JSON object as its argument, where options can be specified:

| Features | Values | Description |
|----------|---------|------------|
| lineheight | int | height of the SVG image |
| unicode | bool | when set to false, the system will always use SVG images from the glyph URL |
| svgurl | string | URL where there the individual glyphs will be loaded from |


You can try out this library on [JSFiddle](https://jsfiddle.net/maartenes/ovgr912c/)

## Related projects

[JavaScriptSesh](https://github.com/rosmord/JavaScriptSesh)
