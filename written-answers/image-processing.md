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

Answer: A `high-pass filter` in the frequency domain keeps the `high frequencies` — edges, fine detail and noise — and suppresses the `low frequencies`, which carry the smooth, slowly varying background. The result is a sharpened image with edges standing out.

   The Butterworth high-pass filter transfer function
   ```
                        1
      H(u,v) = ---------------------------
                1 + [ D0 / D(u,v) ]^(2n)
   ```
   ```
      D(u,v) = sqrt( (u - M/2)^2 + (v - N/2)^2 )
               the distance of the point (u,v) from the centre of the
               frequency rectangle

      D0 = cut-off frequency (the radius of the stop band)
      n  = order of the filter
   ```

   Behaviour
   ```
      D(u,v) = 0    ->  H = 0        the DC term is removed
      D(u,v) = D0   ->  H = 0.5      the half-power point
      D(u,v) >> D0  ->  H -> 1       high frequencies pass unchanged
   ```

   Response curve
   ```
      H(u,v)
        1 |                    _____________________
          |               ___/
      0.5 |............../....................... n = 4 (sharp)
          |          ___/
          |      ___/                              n = 1 (gentle)
        0 |____/________________________________ D(u,v)
          0        D0
   ```
   - The `order n` controls how sharp the transition is. A low n gives a gradual roll-off; a high n approaches the ideal brick-wall filter.

   How it is applied
   ```
      1. Read the image f(x,y)
      2. Multiply by (-1)^(x+y) to centre the spectrum
      3. Take the 2-D FFT  ->  F(u,v)
      4. Multiply point by point :  G(u,v) = H(u,v) . F(u,v)
      5. Take the inverse FFT
      6. Take the real part and multiply by (-1)^(x+y) again
      7. The result g(x,y) is the sharpened image
   ```

   ```mermaid
   flowchart LR
       A[Input image] --> B[2-D FFT]
       B --> C[Multiply by H u,v]
       C --> D[Inverse FFT]
       D --> E[Sharpened image]
   ```

   Why Butterworth is preferred over the ideal filter
   - An `ideal` high-pass filter cuts everything below D0 abruptly. That sharp cut in the frequency domain becomes a `sinc` function in the spatial domain, which produces visible `ringing` — false ripples along every edge.
   - The Butterworth response is `smooth and monotonic`, with no ripple in either band, so ringing is greatly reduced. At n = 1 there is essentially none; it reappears mildly at n = 4 or higher.
   - A `Gaussian` high-pass filter removes ringing completely but cuts less sharply, so Butterworth is the usual compromise.

   Uses
   - Sharpening blurred images and enhancing edges before edge detection.
   - Removing slowly varying illumination or shading across a photograph.
   - Medical and satellite image enhancement, where fine detail matters.
   - As part of `homomorphic filtering`, which compresses brightness range and enhances contrast at the same time.

   - Practical point: because the DC term is set to zero, the output loses its average brightness and looks dark. A `high-frequency emphasis` filter fixes this by using `H' = a + b.H(u,v)`, which keeps some of the low frequencies while still boosting the detail.

## Edge Detection (1)

1. **What are the basic objectives of canny edge detection method?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

Answer: The `Canny edge detector`, given by John F. Canny in 1986, was designed by first writing down mathematically what an ideal edge detector should do, and then finding the operator that satisfies it. Those three requirements are its basic objectives.

   1. Good detection (low error rate)
   - Find `as many real edges as possible` while producing `as few false edges as possible`.
   - A false edge is noise mistaken for an edge; a missed edge is a real boundary the detector failed to mark. Both must be minimised.
   - Achieved by smoothing the image with a `Gaussian filter` first, which removes the noise that would otherwise be reported as edges.

   2. Good localization
   - The marked edge pixel should lie `as close as possible to the centre of the true edge` in the original image.
   - Achieved by computing the gradient after smoothing, and then applying `non-maximum suppression`, which keeps only the pixel at the exact ridge of the gradient and deletes its neighbours.

   3. Minimal response (single response per edge)
   - A single real edge must be marked `only once`. The detector must not return a thick band or several parallel lines for one boundary.
   - Achieved again by `non-maximum suppression`, which thins the gradient ridge down to a one-pixel-wide line.

   The five steps that implement these objectives
   ```mermaid
   flowchart LR
       A[Input image] --> B[1. Gaussian smoothing]
       B --> C[2. Gradient magnitude<br/>and direction]
       C --> D[3. Non-maximum<br/>suppression]
       D --> E[4. Double thresholding]
       E --> F[5. Hysteresis<br/>edge tracking]
       F --> G[Final edges]
   ```
   ```
      1. Smooth with a Gaussian of standard deviation sigma  -> removes noise
      2. Compute the gradient, usually with Sobel masks

            G = sqrt(Gx^2 + Gy^2)        theta = arctan(Gy / Gx)

      3. Non-maximum suppression : along the gradient direction, keep a pixel
         only if it is larger than both its neighbours; otherwise set it to 0
      4. Double threshold : classify each surviving pixel

            G > T(high)              -> strong edge, definitely keep
            T(low) < G < T(high)     -> weak edge, keep only if connected
            G < T(low)               -> discard

      5. Hysteresis : keep a weak edge only if it touches a strong edge,
         directly or through a chain of weak ones
   ```

   Why hysteresis matters
   - A single threshold either breaks real edges into fragments (threshold too high) or lets noise through (too low). Using two thresholds with connectivity gets both: strong evidence starts an edge, and weaker evidence is trusted only where it continues one.
   - The usual ratio is `T(high) : T(low) = 2:1 or 3:1`.

   Advantages and cost
   ```
      Advantages : accurate localisation, one-pixel-thin edges, strong noise
                   immunity, adjustable through sigma and the two thresholds
      Cost       : slower and more complex than Sobel or Prewitt;
                   results depend on choosing sigma and the thresholds well
   ```
   - Choosing `sigma` is a trade-off: a large sigma removes more noise but blurs and displaces the edges; a small sigma keeps fine detail but lets noise through.

   - In short: Canny's three objectives are `detect every real edge and nothing else`, `mark it in the right place`, and `mark it exactly once` — and the five processing steps above exist purely to satisfy them.

## Morphological Operations (1)

1. **Define: (i) Erosion and Dilation; (ii) Opening and Closing.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

Answer: `Morphological operations` process the `shape` of objects in a binary (or grayscale) image. Each one slides a small shape called a `structuring element (SE)` over the image and decides each output pixel from the neighbourhood the SE covers.

   (i) Erosion and Dilation

   `Erosion` — written `A (-) B`
   - An output pixel is set to 1 only if the structuring element fits `entirely inside` the object at that position. In grayscale, the output is the `minimum` of the neighbourhood.
   - Effect: objects `shrink`, boundaries move inward, thin connections break, and small isolated specks of noise disappear.
   ```
      Before erosion              After erosion (3x3 SE)
      0 0 0 0 0 0 0               0 0 0 0 0 0 0
      0 1 1 1 1 1 0               0 0 0 0 0 0 0
      0 1 1 1 1 1 0               0 0 1 1 1 0 0
      0 1 1 1 1 1 0               0 0 0 0 0 0 0
      0 0 0 0 0 0 0               0 0 0 0 0 0 0
      0 0 1 0 0 0 0               0 0 0 0 0 0 0   <- the lone speck is gone
   ```
   - Uses: removing salt noise, separating objects that touch, and finding the boundary by `A - erosion(A)`.

   `Dilation` — written `A (+) B`
   - An output pixel is set to 1 if the structuring element `overlaps` the object at all. In grayscale, the output is the `maximum` of the neighbourhood.
   - Effect: objects `grow`, boundaries move outward, small holes and narrow gaps are filled, and broken lines are joined.
   ```
      Before dilation             After dilation (3x3 SE)
      0 0 0 0 0                   0 1 1 1 0
      0 0 1 0 0                   1 1 1 1 1
      0 1 1 1 0        ->         1 1 1 1 1
      0 0 1 0 0                   1 1 1 1 1
      0 0 0 0 0                   0 1 1 1 0
   ```
   - Uses: filling small holes, bridging gaps in broken characters before OCR, and thickening thin features.
   - The two are `duals`: eroding the object is the same as dilating the background.

   (ii) Opening and Closing

   `Opening` — written `A o B = dilate( erode(A, B), B )`
   - `Erosion followed by dilation`, with the same structuring element.
   - The erosion removes small objects and thin bridges; the dilation restores the surviving objects to roughly their original size.
   - Effect: `removes small objects, thin protrusions and narrow bridges` while keeping the shape and size of the larger objects. It smooths the outside of a contour.
   ```
      Two blobs joined by a thin neck  ->  opening separates them
      Small specks of noise            ->  opening removes them completely
   ```
   - Uses: removing salt noise, separating touching objects, size-based filtering.

   `Closing` — written `A . B = erode( dilate(A, B), B )`
   - `Dilation followed by erosion`, with the same structuring element.
   - The dilation fills small holes and gaps; the erosion shrinks the object back to its original size.
   - Effect: `fills small holes and narrow gaps` and joins nearby objects, while keeping the overall size. It smooths the inside of a contour.
   ```
      A letter with a broken stroke    ->  closing repairs it
      Small holes inside a shape       ->  closing fills them
   ```
   - Uses: removing pepper noise, closing gaps in broken text before OCR, filling small internal holes.

   Summary

   | Operation | Definition | Effect on object size | Removes |
   |---|---|---|---|
   | Erosion | SE must fit inside | Shrinks | Small objects, thin lines |
   | Dilation | SE must overlap | Grows | Small holes, gaps |
   | Opening | Erode then dilate | Roughly unchanged | Small objects, thin bridges, outward spikes |
   | Closing | Dilate then erode | Roughly unchanged | Small holes, narrow gaps, inward notches |

   - Both opening and closing are `idempotent`: applying them twice gives the same result as applying them once. That is why they are used as shape filters rather than as repeated operations.
   - `Top-hat transform` = A - opening(A), which extracts the small bright details that opening removed; `bottom-hat` = closing(A) - A does the same for dark details. Both are used to correct uneven illumination.
