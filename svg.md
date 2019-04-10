
- table of contents -

- [What is SVG?](#what-is-svg)
- [The Benefits of Vectors Over Bitmaps](#the-benefits-of-vectors-over-bitmaps)
- [Adding SVG Code to the Page](#adding-svg-code)
- [Brief Rules on Creating SVGs in Adobe Illustrator](#brief-rules-on-creating-svgs-in-adobe-illustrator)
- [Export a SVG from Illustrator](#export-a-svg-from-illustrator)
- [Optimize Your SVG](#optimize-your-image)
- [Looking at SVG Syntax](#svg-syntax)
- [Styling SVG with CSS](#styling-svg-with-css)
- [HTML-Inlined SVG Images](#html-inlined-svg-images)
- [JavaScript and SVG](#manipulating-svg-with-javascript)
- [Animating SVG with CSS](#animating-svg-with-css)
- [Animating SVG with SMIL](#animating-svg-with-smil)
- [Animating SVG with JavaScript](#animating-svg-with-javascript)
- [Summary]


References
- [SVG Lava Lamp Overlays Tutorial](https://tympanus.net/codrops/2017/10/17/dynamic-shape-overlays-with-svg/)
- A Practical Guide to SVG on the Web, by Jake Giltsoff, for a quick and efficient overview. 
- A Pocket Guide to Writing SVG by Joni Trythall.
- Sara Soueidan on Making SVGs Responsive with CSS, Understanding SVG Coordinate Systems and Transformations and Styling And Animating SVGs With CSS.

Tools
- [Convert Your Image to SVG](https://www.online-convert.com)
- SVGeezy is a fallback Javascript plugin that changes the src of SVG's automatically to PNG's on older browsers that don't support SVG's.

Sandbox Examples
- [CSS Filters](https://codepen.io/lisilinhart/full/ddRBJb/)
- [SVG for Everybody](https://github.com/jonathantneal/svg4everybody)

---

# What is SVG?

SVG stands for Scalable Vector Graphics, and is graphical format for displaying two dimensional objects based on an underlying markup structure. SVG is a lightweight vector image format that’s used to display a variety of graphics on the Web and other environments with support for interactivity and animation. We are going to learn how to include SVGs on a web page, how to apply CSS to SVG, and lastly how to manipulate SVG.

#### About Vectors
Vectors are based on mathmatical expressions, composed of a series of paths, shapes, and more connecting points plotted on a x and y axis. As you may know from working with vectors in Adobe Illustrator or Sketch app, these files scale easily, take up less memory and keep sharp no matter what the size. SVG file format is ideal for logos,
vector-based illustrations, user interface controls, infographics,
charts, and icons; anything that looks like flat design or cut-out paper. 

#### About Bitmaps
Other formats are raster graphics or bitmaps, such as png, jpeg, and gifs; these by contrast are a file format ideal for photographs and more complex images, but as images are enlarged definition is lost and they become blocky and fuzzy. Issues such as halo effect, pixel contaimination, artifacts, anti aliasing battling with binary transparency, reveal themselves.

>Bitmap images are literally a map of bits on a fixed grid. A 100×100 PNG image will equal 10,000 pixels. Each pixel then requires four bytes for red, green, blue and transparency so the resulting file will be 40,000 bytes (plus a little more for meta data). 

To reduce the file size; .png and .gif use zip-like lossless compression while .jpg is lossy and removes less noticeable details for smaller files. .png files are larger but they allow you transparent backgrounds – great for logotypes, while gifs are suited to flat graphics as they have less artifacts, but they also can be animated.

### The Benefits of Vectors Over Bitmaps:
- lightweight, text based portable can be used both client and server
- generated and manipulated easily by a wide range of languages
-  open source
- easily index content as it is text based, good for assistsive tech
- stored entirely within the page,  additional HTTP requests not required
- styled with CSS, has its own DOM, easy to use with JavaScript
- the image can scale to any size without losing quality, scalable and resolution independent
- good choice for high resolution screens, retina screens, mobile, and has unviersal browser support (except no IE8, use svgweb for shims)
- the SVG files are smaller than an equivalent PNG or JPG file. For example, on a recent logo I made, the PNG image was 30KB and the SVG image was only 6 KB. Those savings add up for better perfomance 
- SVG backgrounds are transparent by default
- SVG elements can be easily generated and manipulated on the server or browser as it is written in code
- SVG can be a better choice for accessibility and SEO, as the language for the elements is easily read
- SVG are expressed using XML, so can be edited, modified or created in any text editor

---
## Brief Rules on Creating SVGs in Adobe Illustrator

Create simple shapes over paths. geometrical objects, such as `<line>`, `<circle>, <rect>, <ellipse>, <polygon> and <polyline>` are more maintainable, editable and file efficient than broken objects, like half circles, etc. Basic shapes come with a set of attributes that allow you to control the shape features, such as position (x, y, cx, cy) and dimensions (width & height), while paths don’t come with these attributes.

```HTML
<!-- this is better, shorter code, easier to read -->
<circle fill="#FFFFFF"
        stroke="#000"
        cx="28.1"
        cy="28.1"
        r="27.6"/>
 
<!-- versus -->
<path fill="#FFFFFF"
      stroke="#000"
      d="M55.7,28.1
         c0,15.2-12.4,27.6-27.6,27.6
         S0.5,43.3,0.5,28.1
         S12.9,0.5,28.1,0.5
         S55.7,12.9,55.7,28.1z"/>
```

- Follow good naming and grouping conventions, lowercase and no spaces just like naming an ID. The IDs and class names you use in Illustrator will be translated to IDs and class names in the generated code. Use layers to group related elements. Layers are translated into groups in code, so name these well too. Create layers/groups to wrap related elements together, especially if they might be animated as a whole.
- Save file as RGB
- Set file up as pixels
- Use the fewest possible number of points to create a shape. To simplify a path:
select the path > go to Object → Path → Simplify. Tweak the number of points. Make sure you have the Preview checked so can see how the path changes as you change the number of points. Get to the minimum number of points while keeping the image looking good.
- Whatever size you choose for your artboard will become the area of the SVG viewBox by default. Crop out any extra white space: select all the elements that should be included in your SVG, then > Select Object / Artboards / Fit to Selected Art from the menu bar.
- Don't use regular filters. To generate your effects as SVG code, you can use the SVG Filters available: Go to Effect > SVG Filters Select one of the filters available in that panel. 
- Don't use strokes. Object / Expand… from the menu. Expand both fills and strokes. 
- SVG drawings are transparent, you can add a background color in the css or directly to the SVG code: `svg { border-radius: 50%; background: #999; }`
- You can copy an element from Illustrator and paste it directly into an editor as SVG. 


### Export a SVG from Illustrator

Reference: [Vale Head] (https://www.youtube.com/watch?v=bWcweY66DL8)

Illustrator is recommended over Sketch as there are better options and more control for exporting. From Illustrator you have two options, you can use Save As or Export As SVG- which gives you cleaner output.

EXPORT AS... 

STEP 1. STYLING
- Internal CSS- will give you code blocks, class names are made up by Illus, can copy and paste into CSS

STEP 2. FONT
- FONT SVG- you can use web fonts 
- CONVERT TO OUTLINES- can give you a smaller files and sometimes not! I usually do this before exporting. Text converted to outlines will preserve the font face used, without having to use a web font to display it. This means you save a few extra HTTP requests and don’t risk displaying your text with a fallback font that won't look good.But, this does convert the text to an image so it is no less accessible, not searchable and not selectable. Add an alt txt in this case for screen readers.

STEP 3. IMAGE LOCATION
- EMBED IMAGE The Image Location option specifies whether any raster images will be embedded inline in your SVG or will be external with a link inside the SVG. This, again, depends on what you need. Inlining images inside the SVG can increase its file size dramatically.
- LINK - or use this one more commonly

STEP 4. OBJECT ID ONLY IN THE EXPORT AS DIALOGUE
- LAYER NAMES - use this one

STEP 5. DECIMAL POINTS
- Put 1
- unless, if you have a small icon with detailed shapes, you might need higher number
Minify - Don't Use
Responsive - won't define a width and height, either way is fine and easy to undo

FINAL STEP
- Click on SHOW CODE, copy the code and paste, and head to

### Optimize Your Image

[SVGOMG](https://jakearchibald.github.io/svgomg/) to optimize your image. 
Another editor to try is [SVG EDITOR](http://petercollingridge.appspot.com/svg-editor).

For SVGOMG: 
- Keep Prettify On
- Remove title - up to you
- Shapes to smaller paths, if you need specific shapes don't use
- Optimization tools usually remove any unused groupd and IDs

Copy and paste code and keep. Might want to clean up classes, and rename in a way that is meaningful, might want to put style block into actual CSS. 

If you want to make a SVG in Photoshop, to export from Photoshop, follow this tutorial <http://thenewcode.com/886/More-Tricks--Tips-For-Working-With-SVG-in-Adobe-CC>

---
## Styling SVG with CSS
Reference: <https://www.smashingmagazine.com/2014/11/styling-and-animating-svgs-with-css/>

Here is SVG code for a big pink dot:

```HTML
<svg width="580" height="400" xmlns="http://www.w3.org/2000/svg">
 <g>
  <title>background</title>
  <rect fill="#fff" id="canvas_background" height="402" width="582" y="-1" x="-1"/>
  <g display="none" overflow="visible" y="0" x="0" height="100%" width="100%" id="canvasGrid">
   <rect fill="url(#gridpattern)" stroke-width="0" y="0" x="0" height="100%" width="100%"/>
  </g>
 </g>
 <g>
  <title>Big Pink Dot</title>
  <rect stroke="#000" id="svg_3" height="289" width="396" y="49" x="101.5" fill-opacity="null" stroke-opacity="null" stroke-width="1.5" fill="#fff"/>
  <ellipse stroke="#ff0099" ry="82" rx="86.5" id="svg_1" cy="190" cx="300" stroke-width="1.5" fill="#ff0000"/>
 </g>
</svg>
```

We can use SVG on the web in two ways. We can use the SVG files as the src attribute of `<img>` tags. So, you can have listed:  

```<img src=”bigPinkDot.svg”>```

just like you would list PNGs and JPGs. 
When used within an HTML `<img>` tag or CSS background-url, SVGs act identically to bitmaps. The browser will disable any scripts, links, and other interactive features embedded into the SVG file.
```html
<!-- HTML image -->
<img src="myimage.svg" alt="a vector graphic" />
```
```css
/* CSS background */
.myelement {
  background-image: url('mybackground.svg');
}
```
 You can manipulate this SVG using CSS in an identical way to other images using transform, filters, etc. The results of using CSS with SVG are often superior to bitmaps, because SVGs can be infinitely scaled.

# CSS with SVG: 
Responsive SVG Images:
when creating a responsive website, it’s normally practical to omit <img> width and height attributes and allow an image to size to its maximum width via CSS:
```
img {
  display: block;
  max-width: 100%;
}
```

However, an SVG used as an image has no implicit dimensions. You might discover the max-width is calculated as zero and the image disappears entirely. To fix the problem, ensure a default width and height is defined in the `<svg>` tag:

```
<svg xmlns="http://www.w3.org/2000/svg" width="400" height="300">
```

### HTML-Inlined SVG Images
Second approach: SVGs can be placed directly into the HTML. We can also directly paste the source of the SVG in a `<div>` inside our HTML. We can then style these `divs`  the way we want, we can apply CSS, animations, or add interactivity with JavaScript. When this is done, they become part of the DOM and can be manipulated with CSS and JavaScript:

SVG is inlined directly into the HTML:

<svg id="invader" xmlns="http://www.w3.org/2000/svg" viewBox="35.4 35.4 195.8 141.8">
  <path d="M70.9 35.4v17.8h17.7V35.4H70.9zm17.7 17.8v17.7H70.9v17.7H53.2V53.2H35.4V124h17.8v17.7h17.7v17.7h17.7v-17.7h88.6v17.7h17.7v-17.7h17.7V124h17.7V53.2h-17.7v35.4h-17.7V70.9h-17.7V53.2h-17.8v17.7H106.3V53.2H88.6zm88.6 0h17.7V35.4h-17.7v17.8zm17.7 106.2v17.8h17.7v-17.8h-17.7zm-124 0H53.2v17.8h17.7v-17.8zm17.7-70.8h17.7v17.7H88.6V88.6zm70.8 0h17.8v17.7h-17.8V88.6z"/>
  <path d="M319 35.4v17.8h17.6V35.4H319zm17.6 17.8v17.7H319v17.7h-17.7v17.7h-17.7V159.4h17.7V124h17.7v35.4h17.7v-17.7H425.2v17.7h17.7V124h17.7v35.4h17.7V106.3h-17.7V88.6H443V70.9h-17.7V53.2h-17.7v17.7h-53.2V53.2h-17.7zm88.6 0h17.7V35.4h-17.7v17.8zm0 106.2h-35.5v17.8h35.5v-17.8zm-88.6 0v17.8h35.5v-17.8h-35.5zm0-70.8h17.7v17.7h-17.7V88.6zm70.9 0h17.7v17.7h-17.7V88.6z"/>
</svg>

<p>The SVG is now part of the DOM.</p>
No width or height attributes are defined for the SVG, so it can size to the containing element or be directly sized using CSS:


---
## SVG Syntax Glossary
---

`<svg>`

The `<svg>` tag embeds an SVG document inside the current document, HTML for instance. The tag has its own x and y coordinates, height and width, and its own unique id.

Here’s what an `<svg>` tag might look like:
```html
<svg width="580" height="400" xmlns="http://www.w3.org/2000/svg">
```
---
`<g>`

The `<g>` tag groups the elements together, and acts like a container for related graphic elements. A `<g>` element can even contain other `<g>` elements nested within it.

Here’s an example:
```html
<g> <title>background</title> <rect fill="#fff" id="canvas_background" height="402" width="582" y="-1" x="-1"/> <g display="none" overflow="visible" y="0" x="0" height="100%" width="100%" id="canvasGrid"> <rect fill="url(#gridpattern)" stroke-width="0" y="0" x="0" height="100%" width="100%"/> </g> </g>
```
---
`<rect>`

The `<rect>` element is an SVG basic shape representing a rectangle. The element can have various attributes, like coordinates, height, width, fill color, stroke color, and sharp or rounded corners.

Here’s an example:
```html
<rect id="svg_1" height="253" width="373" y="59" x="107.5" stroke-width="1.5" stroke="#000" fill="#fff"/>
```
---
`<use>`

The `<use>` element allows you to clone and reuse the graphical SVG elements including other elements like `<g>` `<rect>` as well as other `<use>` elements.

Here’s an example:

```html
<text y="15">black</text> <use x="50" y="10" xlink:href="#Port" /> <text y="35">red</text> <use x="50" y="30" xlink:href="#Port"/> <text y="55">blue</text> <use x="50" y="50" xlink:href="#Port" style="fill:blue"/
```
---
`<path>`

The `<path>` element defines a path of coordinates for a shape. The code for path tag might seem cryptic, but don’t be intimidated. The following example code can be read like this:

1. “M150 o” — Move to (150,0)

2. ”L75 200" — Draw a line to (75,200) from last position (which was (150,0)

3. “L255 200” — Draw a line to (225,200) from last position (which was (75,200)

4. “Z” — Close the loop (draw to starting point)

You probably don’t need to learn this since the code for path can be generated in any SVG editor, but it’s cool to know.

Here’s an example:
```html
<svg height="210" width="400"> <path d="M150 0 L75 200 L225 200 Z" /> </svg>
```
---
`<symbol>`

Finally, the `<symbol>` element defines symbols that are reusable. These symbols can only be rendered when called by the `<use>` element.

Here’s an example:

<svg> 
<symbol id="sym01" viewBox="0 0 150 110"> <circle cx="50" cy="50" r="40" stroke-width="8" stroke="red" fill="red"/> <circle cx="90" cy="60" r="40" stroke-width="8" stroke="green" fill="white"/> </symbol> <use xlink:href="#sym01" x="0" y="0" width="100" height="50"/> <use xlink:href="#sym01" x="0" y="50" width="75" height="38"/> <use xlink:href="#sym01" x="0" y="100" width="50" height="25"/> 
</svg>

```html
<svg> 
<symbol id="sym01" viewBox="0 0 150 110"> <circle cx="50" cy="50" r="40" stroke-width="8" stroke="red" fill="red"/> <circle cx="90" cy="60" r="40" stroke-width="8" stroke="green" fill="white"/> </symbol> <use xlink:href="#sym01" x="0" y="0" width="100" height="50"/> <use xlink:href="#sym01" x="0" y="50" width="75" height="38"/> <use xlink:href="#sym01" x="0" y="100" width="50" height="25"/> 
</svg>
```

---
viewBox

viewBox defines a co-ordinate space. In the code above, an 150×110 area starts at position 0,0.

---


# CSS Inlined SVG Backgrounds

An SVG can be inlined directly in CSS code as a background image. This can be ideal for smaller, reusable icons and avoids additional HTTP requests. For example:

```html
.mysvgbackground {
  background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600"><circle cx="400" cy="300" r="50" stroke-width="5" stroke="#f00" fill="#ff0" /></svg>') center center no-repeat;
}
```




 inline SVG's are better than font icons

 we first need to understand how our vector application exports SVG.

Export file with black fill and no strokes or stroke transparent
you'll be able to apply a stroke or fill via the CSS.

 #Illustrator SVG Export Behavior
At time of writing, the latest version of Illustrator CC exports to SVG as follows:

If you don't define a fill or stroke, or, you define only a fill, but that fill is black (completely black as in #000), the exported SVG paths and shapes will not contain a fill or stroke attribute:

```CSS
.filled-instance-off {
  stroke: #d08aaf;
  stroke-width: 5px;
  fill: transparent;
}
```

# Manipulating SVG with JavaScript

Just like we can do style overrides with CSS, we can also manipulate our SVG image with JavaScript. Manipulating SVG with JavaScript isn’t different than any other DOM element. We can use JavaScript, jQuery, or whatever other flavor of the month we’d like.

Here’s a really simple example of changing the fill attribute of the rect with the id of “inner.”

```javascript
function blackOutCenter() {
 document.getElementById("inner").setAttribute("fill", "#333");
}
```

Wired to a button, like in the working example, this uses the setAttribute method to update the fill attribute to #333.

We can also read the current attributes and then make decisions based on what we get back.

```javascript
function getFillColor() {
    svgRect = document.getElementById("inner");
    var fillColor = svgRect.getAttribute("fill");
}
```

Here is a simple SVG using a click function:
[Trigger SVG animation using button / JS](https://codepen.io/lambdacreatives/pen/uygzk)
---
## Using a JavaScript Library
There are JS libraries we can use, which make it really simple to create and manipulate SVG. Here are some popular libraries to consider:

- Snap.svg
- SVG.js
- Raphaël
- Velocity.js
- D3.js
- Vivus.js


## Animating SVG

### 1. Animating SVG with CSS

SVG elements can be targeted and styled with CSS. Meaning, you can apply animation through @keyframes.

**You might choose animating this way if...**
-The animation is fairly simple.
-You only need to animate properties that CSS can animate.
-You already know and are comfortable with CSS animations.

```html
<svg viewBox="0 0 127.9 178.4">
  <path id="left-leg" d="M37.6,138.8c0 ... " />
</svg>
.left-leg {
  fill: orange;
  animation: dance 2s infinite alternate;
}
@keyframes dance {
  100% {
    transform: rotate(3deg);
  }
}
```

## 2. Animating SVG with SMIL
There is a syntax for animations built right into SVG. Here's a very simple example:

```html
<svg viewBox="0 0 127.9 178.4">
  <path d="M37.6,138.8c0 ... ">
    <animate attributeName="fill" dur="5000ms" to="#f06d06" fill="freeze" />  
  </path>
</svg>
```
Here's a big tutorial on all that is SMIL. Not as popular as it once was.
[CSS tricks on SMIL](https://css-tricks.com/guide-svg-animations-smil/)

**You might choose animating this way if...**
You need to animate properties that CSS can't, like the shape itself.
You need other SMIL specific features, like beginning an animation when another ends without manually syncing durations/delays. Or interaction stuff, like beginning an animation on a click.

## Animating SVG with JavaScript
With JavaScript, you have access to things like requestAnimationFrame (or other loops), so you can animate just by way of rapidly changing property values. There are also frameworks out there for working with SVG that typically have animation stuff built in. Or animation frameworks that work with SVG. Like 
SnapSVG, <http://snapsvg.io/start/>, <https://davidwalsh.name/svg-animations-snap>
GreenSock, 
SVG.js, or 
Velocity.js.

Here's an example with SnapSVG:
<https://codepen.io/chriscoyier/pen/JoXbGN>

```html
<svg id="robot" viewBox="0 0 127.9 178.4">
  <circle id="left-pupil" cx="34.4" cy="15.4" r="4.8" />
</svg>
var s = Snap("#robot");
var leftPupil = s.select("#left-pupil");
leftPupil.animate({
  r: 50,
  fill: "lightgreen"
}, 1000);
```
**You might choose animating this way if...**
You're working in JavaScript anyway, perhaps your animation has to do with data you receive with JSON or the like.
You need JavaScript anyway, because you need the logic or math or something else really only possible there.
You're interested in the JavaScript solving some bugs for you.
The scope of your animation is rather large/complicated and you need the abstraction and organization JavaScript can provide.


Mozilla
https://developer.mozilla.org/en-US/docs/Web/API/SVGAnimationElement

Codepens

https://properdesign.co.uk/animating-svg-with-beginelement/


Warning
<https://svgontheweb.com/#javascript>
If you want to embed your scripts within the SVG file, remember to wrap them in <![CDATA[ ... ]]> again to prevent parsing errors. Scripts will not run if you use <img> or background-image as a security measure (i.e. to prevent potentially malicious code running on your page).

When working with external JS (i.e. not embeded within the SVG file), if you have your SVG inline you can target it as you would any other DOM element. If you use an <object> you can target it with contentDocument. You can get much more creative than the following, but here is an example:

Uses Tween and GSapp
https://medium.com/@LewisMenelaws/how-to-create-beautiful-svg-animations-easily-610eb2690ac3

Collection of SVG Animations
https://codepen.io/logoping/post/beautiful-svg-animations

CSS Only Animation

https://codepen.io/kylehenwood/pen/pPXNXE