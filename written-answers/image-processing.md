<!-- TOC START -->
**Table of Contents** — 5 subtopics · 7 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Computer Graphics (Vector & Raster)](#computer-graphics-vector--raster-3) | 3 |
| 2 | [Color Models](#color-models-1) | 1 |
| 3 | [Frequency Domain Filtering](#frequency-domain-filtering-1) | 1 |
| 4 | [Edge Detection](#edge-detection-1) | 1 |
| 5 | [Morphological Operations](#morphological-operations-1) | 1 |

<!-- TOC END -->

---

## Computer Graphics (Vector & Raster) (3)

1. **(ক) Vector এবং Raster graphics- এর সংজ্ঞাসহ পার্থক্য লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.) Vector graphics
   - An image described by `mathematical objects` — points, lines, curves and polygons — each with its own coordinates, colour and thickness. The file stores the `instructions to draw` the picture, not the picture itself.
   - Because the picture is redrawn from equations at whatever size is asked for, it can be scaled to any size with `no loss of quality`.
   - Formats: `SVG, AI, EPS, PDF, CDR`.

   Raster graphics
   - An image stored as a `grid of pixels`, each holding a colour value. Also called a bitmap.
   - The number of pixels is fixed at creation, so enlarging the image stretches those pixels and the result looks blocky — `pixelation`.
   - Formats: `JPEG, PNG, GIF, BMP, TIFF`.

   ```
      Vector : a circle stored as  centre (50,50), radius 25, red
               -> a few bytes, redrawn perfectly at any size

      Raster : the same circle stored as
               +--+--+--+--+--+
               |  |##|##|  |  |
               +--+--+--+--+--+     -> one value per pixel, fixed resolution
               |##|##|##|##|  |
               +--+--+--+--+--+
   ```

   Difference

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | Stored as | Mathematical paths and shapes | A grid of pixels |
   | Scaling | Any size, no quality loss | Enlarging causes pixelation |
   | Resolution | Independent | Fixed at creation |
   | File size | Small for simple artwork | Large, grows with resolution |
   | Editing | Each object edited separately | Pixels edited; objects are not separable |
   | Best for | Logos, text, icons, maps, CAD drawings | Photographs, scanned images, realistic scenes |
   | Colour detail | Limited; hard to show subtle gradation | Excellent; every pixel has its own colour |
   | Rendering | Must be computed each time — slower | Displayed directly — faster |
   | Formats | SVG, AI, EPS, PDF, CDR | JPEG, PNG, GIF, BMP, TIFF |
   | Software | Illustrator, CorelDRAW, Inkscape | Photoshop, GIMP, MS Paint |

   - Practical point: a logo must be `vector`, so it prints correctly on a business card and on a billboard from the same file. A photograph must be `raster`, because no equation can describe the millions of subtly different colours in a real scene.
   - Conversion is easy one way and hard the other: vector to raster is `rasterization` and happens whenever a vector image is displayed; raster to vector needs `tracing`, which is approximate.

2. **(b) Differentiate between vector graphics and raster graphics. What are the applications of computer Graphics?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888-889 (ET: N/A)]*

   Answer: Vector graphics
   - The image is described by `mathematical objects` — points, lines, curves and polygons — each with coordinates, colour and thickness. The file stores the instructions to draw the picture.
   - It is redrawn from those equations at whatever size is requested, so it scales to any size with `no loss of quality`.
   - Formats: `SVG, AI, EPS, PDF, CDR`.

   Raster graphics
   - The image is a `grid of pixels`, each storing a colour value. Also called a bitmap.
   - The pixel count is fixed at creation, so enlarging stretches the pixels and the result becomes blocky — `pixelation`.
   - Formats: `JPEG, PNG, GIF, BMP, TIFF`.

   Difference

   | Point | Vector graphics | Raster graphics |
   |---|---|---|
   | Stored as | Mathematical paths | A grid of pixels |
   | Scaling | Any size, no quality loss | Enlarging causes pixelation |
   | Resolution | Independent | Fixed at creation |
   | File size | Small for simple artwork | Large, grows with resolution |
   | Editing | Objects edited individually | Pixel-level editing only |
   | Best for | Logos, icons, text, maps, CAD | Photographs, scans, realistic images |
   | Colour detail | Limited gradation | Excellent, per-pixel colour |
   | Display speed | Slower — must be computed | Faster — shown directly |
   | Software | Illustrator, CorelDRAW, Inkscape | Photoshop, GIMP |

   Applications of computer graphics
   - `User interfaces` — every window, icon, menu and button on a screen is computer graphics. This is by far the largest use.
   - `CAD and CAM` — designing buildings, machines, circuits and vehicles, with automatic dimensioning and 3D visualisation before anything is built.
   - `Entertainment` — video games, animated films, visual effects, and the real-time 3D rendering behind them.
   - `Medical imaging` — reconstructing CT, MRI and ultrasound scans into 2D slices and 3D models for diagnosis and surgical planning.
   - `Scientific visualisation` — turning simulation data into pictures: weather models, fluid flow, molecular structure, finite element analysis.
   - `Presentation graphics` — charts, graphs and infographics that make numerical data understandable.
   - `GIS and cartography` — digital maps, satellite imagery, route planning and navigation.
   - `Simulation and training` — flight simulators, driving simulators, and military and surgical training systems, where real practice would be dangerous or costly.
   - `Virtual and augmented reality` — immersive environments for training, design review, retail and gaming.
   - `Image processing` — enhancing, restoring and analysing photographs and satellite images.
   - `Desktop publishing and advertising` — layout of books, newspapers, posters and packaging.
   - `Textile, architecture and fashion design` — pattern design and photorealistic preview before manufacture.

   - The two forms are used together in practice: an advertisement uses `vector` for the logo and text so they stay sharp at any size, and `raster` for the photograph.

3. **Raster Image কাকে বলে?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) A `raster image` is an image stored as a rectangular `grid of pixels`, where each pixel holds a colour value. It is also called a `bitmap` image.

   - The word raster comes from the way the picture is drawn — row by row, left to right and top to bottom, exactly as a CRT screen scans.
   ```
      A 5 x 4 raster image = 20 pixels

      +----+----+----+----+----+
      | W  | W  | K  | K  | W  |     each cell holds one colour value
      +----+----+----+----+----+
      | W  | K  | K  | K  | K  |
      +----+----+----+----+----+
      | K  | K  | W  | W  | K  |
      +----+----+----+----+----+
      | W  | K  | K  | K  | W  |
      +----+----+----+----+----+
   ```

   Key properties
   - `Resolution` — the number of pixels, written as width x height, for example 1920 x 1080. It is fixed when the image is created.
   - `Bit depth` — the number of bits per pixel, which decides how many colours are possible.
   ```
      1 bit   :  2 colours (black and white)
      8 bit   :  256 colours or 256 grey levels
      24 bit  :  16.7 million colours (8 bits each for R, G and B)
      32 bit  :  24-bit colour plus an 8-bit alpha (transparency) channel
   ```
   - `File size` grows with both:
   ```
      Size = width x height x bit depth / 8   bytes

      1920 x 1080 x 24 / 8 = 6,220,800 bytes ~= 6 MB uncompressed
   ```
   - `Scaling` — enlarging a raster image stretches its fixed pixels, so the result looks blocky. This is `pixelation`, the main limitation of the format.

   Formats
   ```
      JPEG : lossy compression, best for photographs, no transparency
      PNG  : lossless, supports transparency, best for screenshots and graphics
      GIF  : 256 colours, supports simple animation
      BMP  : uncompressed, very large
      TIFF : lossless, used in printing and scanning
      RAW  : the sensor's unprocessed output, used in professional photography
   ```

   Where raster images come from
   - Digital cameras, scanners, screenshots, and painting programs — anything that captures or paints real-world detail.

   - The alternative is `vector` graphics, which stores mathematical shapes instead of pixels and therefore scales to any size without loss. Raster is used for photographs, vector for logos and diagrams.

## Color Models (1)

1. **(ক) বিভিন্ন Color model-এর নাম লিখুন। CMY color model-এর ব্যবহার কী?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.) A `colour model` is a mathematical way of describing a colour as a set of numbers, so a computer can store, transmit and reproduce it.

   Names of the main colour models

   `RGB` (Red, Green, Blue)
   - An `additive` model: colours are made by adding light. All three at full gives white; all three off gives black.
   - Used by anything that `emits` light — monitors, TVs, cameras, scanners, projectors.

   `CMY / CMYK` (Cyan, Magenta, Yellow, and Key = black)
   - A `subtractive` model: colours are made by removing wavelengths from white light with ink. All three at full gives black; none gives white (the paper).
   - Used by anything that `prints` — inkjet and laser printers, offset printing.

   `HSV / HSI / HSB` (Hue, Saturation, Value / Intensity / Brightness)
   - Describes colour the way people do: `hue` is the colour name, `saturation` its purity, `value` its brightness.
   - Used in image editing tools, colour pickers, and in image processing where colour must be separated from lighting.

   `YUV / YCbCr / YIQ`
   - Separates `luminance (Y)` — the brightness — from `chrominance (U, V)` — the colour.
   - Used in television broadcasting, JPEG and MPEG compression, because the eye is far more sensitive to brightness than to colour, so the colour channels can be compressed harder.

   `CIE XYZ and CIE Lab`
   - Device-independent models based on how the human eye actually responds. `Lab` is perceptually uniform, so equal numeric changes look like equal colour changes.
   - Used as the reference for colour management and conversion between devices.

   `Grayscale`
   - A single intensity value per pixel, 0 to 255. Used in medical imaging, document scanning and most image-processing algorithms.

   Use of the CMY colour model
   - `Colour printing` is its purpose. Ink on paper does not emit light; it `absorbs` some wavelengths and reflects the rest, so the arithmetic is subtractive.
   ```
      Cyan    absorbs RED     ->  reflects green + blue
      Magenta absorbs GREEN   ->  reflects red + blue
      Yellow  absorbs BLUE    ->  reflects red + green
   ```
   - Conversion from RGB is simply the complement:
   ```
      C = 1 - R
      M = 1 - G
      Y = 1 - B          (with all values normalised to 0-1)
   ```
   ```
      Additive (RGB)             Subtractive (CMY)
         R + G = Yellow             C + M = Blue
         G + B = Cyan               M + Y = Red
         R + B = Magenta            C + Y = Green
         R+G+B = White              C+M+Y = Black (in theory)
   ```

   Why printers actually use CMYK, not CMY
   - Mixing all three inks in practice gives a `muddy dark brown`, not a true black, because real inks are not perfect.
   - Printing three layers of ink to make black wastes expensive colour ink, soaks the paper and dries slowly.
   - Black text would look blurred, since three plates would have to register perfectly.
   - So a separate `K` (black) ink is added — cheaper, sharper and genuinely black. This is called `black generation` and `under-colour removal`.

   - Practical consequence: a design that looks bright on an RGB monitor often looks duller when printed, because the CMYK `gamut` — the set of colours it can reproduce — is smaller than the RGB gamut. That is why designers work in CMYK for anything destined for print.

## Frequency Domain Filtering (1)

1. **How does Butterworth High pass Filter works?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

## Edge Detection (1)

1. **What are the basic objectives of canny edge detection method?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

## Morphological Operations (1)

1. **Define: (i) Erosion and Dilation; (ii) Opening and Closing.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*
