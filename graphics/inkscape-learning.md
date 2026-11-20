# Inkscape learning notes

**Date:** 20 November 2026

These notes record the work completed while learning Inkscape, so the next session can continue from here without repeating the same steps.

## What we worked on

The exercise was to turn a raster image of a black cat into an editable vector shape, then add editable text.

### 1. Opened and prepared the image

- Opened the black cat image in Inkscape.
- Duplicated the bitmap and renamed one object `Working Copy`.
- The Trace Bitmap preview for `Working Copy` appeared blank. Selecting `Image 2` produced a preview, so that was the image used for tracing.

### 2. Traced the bitmap

- Opened **Path → Trace Bitmap**.
- Chose **Single Scan → Brightness Cutoff**.
- Clicked **Apply**.
- Inkscape created a path object named `Path 2`.
- Selected the result with the Node tool. The visible nodes confirmed that the traced shape was an editable vector path.

The original bitmap and other image objects were hidden while inspecting the traced result.

### 3. Added text

- Used the Text tool (T) to add text.
- The text was initially black and difficult to see against the black cat.
- Changed the text colour to white using the palette.
- Changed the font to Linux Libertine and increased the size from 20 pt to 48 pt.
- Confirmed that the text remained selectable and editable when the SVG was opened in Firefox.

## What we learned about SVG

SVG is a container format. It can contain vector paths, editable text and embedded raster images together.

The traced cat silhouette was a vector path, but the SVG source also contained an embedded PNG image as Base64 data. Therefore, an SVG file is not automatically made entirely of vector elements just because its filename ends in `.svg`.

## Validation

Saved the work as `broken cat 2.svg` and opened it in Firefox.

Then checked it with SVG Genie. The reported results were:

- File size: 2963.31 KB
- Elements: 7
- Paths: 1
- ViewBox: 0 0 1312 1199
- Width: 1312
- Height: 1199
- Validation: valid SVG

The file was valid SVG, but it still contained embedded raster content. Validity and being fully vector are two different things.

## Next session

Continue learning Inkscape from this point. In particular:

1. Revisit the Layers and Objects panel and understand which bitmap and path objects are present.
2. Practise selecting, hiding and identifying the original bitmap and the traced path.
3. Learn how to check whether an SVG contains raster images as well as vector paths.
4. Continue with practical examples using real images rather than unrelated geometric exercises.

These notes describe what we actually did and observed. They do not assume that every part of the image has already been converted to vector.
