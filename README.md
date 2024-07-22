# SVGAndMe

<img src="gallery/peacockspider.png" alt="peacockspider" width=640/></br>


SVGAndMe turns .svg files into something useful for programmers.  You can use
 the parser to turn the .svg file into a document in memory that you can then
 use in your program.  You can also use the parser, and a drawing canvas
 to turn that .svg into an image to be used in your program, or saved to a file.
 Written in C++, SVGAndMe is intended to be self contained, and cross platform.
 It is a fairly complete library, supporting most of the SVG features found in 
 typical usage today.
 
# Gallery
Be sure to check the <a href="gallery">gallery</a> for example .svg files SVGAndMe can handle.
## Design Goal</br>
The general design goal of SVGAndMe is to support a high percentage
of SVG files found in the wild.  It is also a design goal to be as
cross platform as possible, not relying on any platform specific features, other
than the blend2d library, which is fairly portable.

It is NOT a goal to be a "complete" SVG library, as that task is nearly impossible,
and impractical for such a small library.

## Implementation</br>
SVGAndMe is fairly straightforward C++ code.  All the parsing is done with no 
external dependencies, leaving you with a clean SVGDocument that can be used
for multiple purposes.  Rendering is done using the blend2d graphics library 
as its implementation matches the drawing requirements of SVG.


## A bit about the blend2d library</br>
The blend2d library is a fast, multi-threaded 2D graphics library that was designed to be
fairly compatible with the SVG graphics features.  As such, most of the drawing features of SVG
are supported, from gradients, to shapes, to patterns, and beyond.  There are a few exceptions
in terms of missing features, but what is there supports 90% of the svg files that are
typically found in the wild.
 
While blend2d provides great support for the various raw graphics primitives, it does not
inherently support the more web focused aspects of SVG such as CSS, groupings, definitions, and the like.  
Here, svgandme fills the gaps, having a modest amount of support for style sheets, and some more esoteric features 
of the SVG specification.



## Usage</br>
 Look into the 'testy/' directory for some example projects.  'svgimage' shows the basics of how to 
 load a .svg file, and render it into an image, which can then be saved.  That's just the basics
 and can act as a starting point for using the library.

## Extra Notes</br>
SVG is an XML based grammar.  SVGAndMe contains a fairly robust XML parser which is zero memory allocating, and very fast.  This XML scanner is probably good enough to tackle most typical XML processing tasks, so it might serve as a jumping off point if you have more XML than just SVG to be processed in your applications.  Look at the 'xmlpull/' example for usage details.


# Documentation
SVGAndMe aspires to implement a lot of SVG that is in common usage.  The <a href="docs/README.md">docs</a> show what specifically is implemented, as well as the limitations.

# Roadmap
This code does not strive to be a 'complete' SVG implementation.  That task is highly improbable given the nature of the specs, and lack of consistency across multiple implementations.  What SVGAndMe strives to be is 'very useful' for most common cases.  Those common cases range from being able to render simple icons, to complex street maps.  Whereas there are a number of common features that a lot of the simpler parsers do not deal with (text, templated gradients, symbols, markers), SVGAndMe does implement these to varying degrees.

The roadmap of feature work is a combination of shoring up support for already existing features, as well as adding a couple of new major feature areas (filters, masks).

- Opportunistic bug fixing
- Opportunistic feature requests
- Make text-anchor work reliably
- Make text-align work reliably
- Make tspan element work correctly
- Support paint/style being applied inline, rather than from context
- Support backing store when using group and path elements
- Support global opacity on group and path elements
- Fixup coordinate system on Markers
- Fixup coordinate system on Symbols
- Add Support for Masks
- Add Support for Filters
- Improve performance for very small cases
- Remove usage of std library where allocations are done
